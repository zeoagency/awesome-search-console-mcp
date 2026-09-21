# Google Search Console API Surface & Protocol Architecture

A technical reference for developers building Model Context Protocol (MCP) servers and autonomous agents for Google Search Console (GSC).

---

## 1. Google Search Console API Surfaces

Google Search Console exposes four primary Webmaster Tools API services alongside two adjacent search protocols:

```text
                  ┌─────────────────────────────────────────┐
                  │       Agent / MCP Host Application       │
                  └────────────────────┬────────────────────┘
                                       │ (JSON-RPC 2.0 / stdio / HTTP)
                  ┌────────────────────▼────────────────────┐
                  │          GSC MCP Server Engine          │
                  └─────────┬───────────────────┬───────────┘
                            │                   │
         Google APIs Client │                   │ BigQuery Client
                            ▼                   ▼
      ┌───────────────────────────────┐   ┌───────────────────────────┐
      │     Google Search Central     │   │   Google Cloud BigQuery   │
      │       REST v3 Services        │   │     Bulk Data Export      │
      ├───────────────────────────────┤   ├───────────────────────────┤
      │ • searchAnalytics.query       │   │ • Daily Partitioned Tables│
      │ • urlInspection.index.inspect │   │ • Raw 100% Query Logs     │
      │ • sitemaps (list, get, submit)│   │ • Zero Row Truncation     │
      │ • sites (list, get, add)      │   └───────────────────────────┘
      │ • indexing.notifications      │
      └───────────────────────────────┘
```

### 1.1. Search Analytics Service (`searchAnalytics.query`)

- **Endpoint:** `POST https://www.googleapis.com/webmasters/v3/sites/{siteUrl}/searchAnalytics/query`
- **Key Dimensions:** `query`, `page`, `country`, `device`, `searchAppearance`, `date`.
- **Metrics Returned:** `clicks`, `impressions`, `ctr`, `position`.
- **Response Row Limit:** Hard ceiling of **25,000 rows per request**. Servers fetching deep multi-dimension matrices must implement automated pagination loops (`startRow` offset).
- **Data Freshness & Lag:** Standard data features a 2–3 day aggregation lag. Setting `dataState: "all"` queries preliminary "fresh data" covering the preceding 24 hours.

### 1.2. URL Inspection Service (`urlInspection.index.inspect`)

- **Endpoint:** `POST https://searchconsole.googleapis.com/v1/urlInspection/index:inspect`
- **Quota Limits:** Hard ceiling of **2,000 queries per day (QPD)** and **600 queries per minute (QPM)** per Google Cloud project.
- **Payload Coverage:**
  - Crawl state (`verdict`, `coverageState`, `lastCrawlTime`, `crawledAs`).
  - Indexing judgment (`robotsTxtState`, `indexingState`).
  - Canonical identification: `userCanonical` vs Google-selected `googleCanonical`.
  - Mobile usability and rich results validation.

### 1.3. Sitemaps Service (`sitemaps`)

- **Endpoints:** `GET`, `PUT`, and `DELETE` on `/sites/{siteUrl}/sitemaps/{feedpath}`.
- **Capabilities:** Submit XML sitemaps, inspect processing status, error counts, and indexed URL tallies.

### 1.4. Sites Service (`sites`)

- **Endpoints:** `GET` and `POST` on `/sites`.
- **Capabilities:** List verified properties, check permission levels (`siteOwner`, `siteFullUser`, `siteRestrictedUser`), and add new properties.

### 1.5. Google Indexing API (`indexing.notifications`)

- **Endpoint:** `POST https://indexing.googleapis.com/v3/urlNotifications:publish`
- **Scope Note:** Officially limited by Google to pages containing `JobPosting` or `BroadcastEvent` structured data, though widely used for accelerated discovery.
- **Quota:** 200 URL notifications per day per Google Cloud project (upgradeable via quota request).

### 1.6. BigQuery Bulk Data Export

- **Overview:** Enterprise sites configure automated daily streaming of GSC performance data into partitioned Google Cloud BigQuery tables (`searchdata_site_impression` and `searchdata_url_impression`).
- **Advantage for Agents:** Bypasses the 25,000-row API query limit and 16-month retention window, allowing agents to execute complex SQL joins across millions of search queries.

---

## 2. Property Format Architecture

Google Search Console supports two distinct property models:

| Property Type | Syntax Example | API Notation Requirement |
|---|---|---|
| **URL-prefix Property** | `https://example.com/` | Pass exact URL including scheme and trailing slash: `https://example.com/` |
| **Domain Property** | `example.com` | **MUST include prefix `sc-domain:`**: `sc-domain:example.com` |

> [!IMPORTANT]
> Failing to prepend `sc-domain:` when querying domain-level properties results in immediate `HTTP 400 Bad Request` errors from Google's API gateway. Mature MCP servers auto-detect bare domain strings and prepend `sc-domain:` automatically.

---

## 3. Token Economics & Compression

Piping uncompressed raw JSON from `searchAnalytics.query` into LLM contexts quickly exhausts tokens:

- **Raw JSON (5,000 rows):** ~35,000 to 50,000 tokens.
- **Compact Markdown Table:** ~4,000 to 7,000 tokens (85% reduction).
- **Embedded SQLite / SQL Tool:** ~500 tokens for schema + ~200 tokens per focused SQL answer (>95% reduction).
