# Awesome Search Console MCP [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

> A curated developer index and technical comparison of Model Context Protocol (MCP) servers and agentic tooling for **[Google Search Console](https://search.google.com/search-console)**.

Official links: [Google Search Console](https://search.google.com/search-console) · [Search Console API Docs](https://developers.google.com/webmaster-tools) · [Model Context Protocol](https://modelcontextprotocol.io/) · [Google Cloud Console](https://console.cloud.google.com/) · [Google Indexing API](https://developers.google.com/search/apis/indexing-api/v3/quickstart)

---

## Contents

- [Quick Comparison Matrix (60)](#quick-comparison-matrix)

1. [Persist and query data locally (9)](#1-persist-and-query-data-locally)
   - [Embedded SQLite data warehouses with sandboxed SQL (4)](#embedded-sqlite-data-warehouses-with-sandboxed-sql)
   - [Local dashboard engines with search analytics persistence (4)](#local-dashboard-engines-with-search-analytics-persistence)
   - [Quota-slot database tracking and batch synchronization (1)](#quota-slot-database-tracking-and-batch-synchronization)
2. [Manage multi-property and agency access (5)](#2-manage-multi-property-and-agency-access)
   - [Dynamic multi-account routing and credential isolation (1)](#dynamic-multi-account-routing-and-credential-isolation)
   - [Multi-tenant domain matching and dynamic siteUrl resolution (2)](#multi-tenant-domain-matching-and-dynamic-siteurl-resolution)
   - [Frictionless OAuth 2.0 PKCE browser onboarding (2)](#frictionless-oauth-20-pkce-browser-onboarding)
3. [Diagnose technical SEO and search algorithms (6)](#3-diagnose-technical-seo-and-search-algorithms)
   - [Keyword cannibalization and content decay diagnostics (2)](#keyword-cannibalization-and-content-decay-diagnostics)
   - [Multi-signal SEO audits with CrUX, IndexNow, and HTML reporting (2)](#multi-signal-seo-audits-with-crux-indexnow-and-html-reporting)
   - [CTR opportunity modeling and GEO attribution analytics (2)](#ctr-opportunity-modeling-and-geo-attribution-analytics)
4. [Automate indexing and URL lifecycle (4)](#4-automate-indexing-and-url-lifecycle)
   - [Batch URL inspection and indexing automation (2)](#batch-url-inspection-and-indexing-automation)
   - [Combined search analytics and Indexing API lifecycle (1)](#combined-search-analytics-and-indexing-api-lifecycle)
   - [Sitemap management and indexing feed inspection (1)](#sitemap-management-and-indexing-feed-inspection)
5. [Drive agents via CLI and native runtimes (5)](#5-drive-agents-via-cli-and-native-runtimes)
   - [Native compiled binaries with zero-dependency execution (1)](#native-compiled-binaries-with-zero-dependency-execution)
   - [Autonomous agent frameworks with GSC tool integration (1)](#autonomous-agent-frameworks-with-gsc-tool-integration)
   - [Claude Code command packs and skill extensions (3)](#claude-code-command-packs-and-skill-extensions)
6. [Connect unified marketing stacks (7)](#6-connect-unified-marketing-stacks)
   - [Unified Google Search Console and GA4 analytics bridges (2)](#unified-google-search-console-and-ga4-analytics-bridges)
   - [Cross-platform Google Marketing Platform suites (5)](#cross-platform-google-marketing-platform-suites)
7. [Bridge enterprise data lakes and hybrid extraction (3)](#7-bridge-enterprise-data-lakes-and-hybrid-extraction)
   - [BigQuery bulk export data lake bridges (1)](#bigquery-bulk-export-data-lake-bridges)
   - [Browser-automated rank tracking and SERP extraction (1)](#browser-automated-rank-tracking-and-serp-extraction)
   - [Crawl DOM integration and internal link analysis (1)](#crawl-dom-integration-and-internal-link-analysis)
8. [Query search analytics through lightweight proxies (21)](#8-query-search-analytics-through-lightweight-proxies)
   - [Token-optimized compact markdown proxies (5)](#token-optimized-compact-markdown-proxies)
   - [Comprehensive multi-endpoint Search Console API proxies (8)](#comprehensive-multi-endpoint-search-console-api-proxies)
   - [FastMCP and standard search analytics wrappers (6)](#fastmcp-and-standard-search-analytics-wrappers)
   - [Remote HTTP and cloud-hosted MCP servers (2)](#remote-http-and-cloud-hosted-mcp-servers)

- [Resources](#resources)
- [Reference](#reference)

---

## Quick Comparison Matrix

*60 projects. High-signal technical capability comparison across runtime, authentication, persistence, token formatting, and API coverage. Project names link internally to detailed listings below.*

| Project | Stars | Runtime | Search Analytics | URL Inspect | Sitemaps | Local DB | Auth Model | Output Format |
|:---|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| [acamolese/google-search-console-mcp](#acamolese-google-search-console-mcp) | ★ 8 | `Python` | ✓ (25k) | ✓ | ✓ | — | OAuth2 | Raw JSON |
| [ahonn/mcp-server-gsc](#ahonn-mcp-server-gsc) | ★ 273 | `Node` | ✓ (25k) | ✓ | ✓ | — | Service Account | Compact MD |
| [AkashRajpurohit/gsc-mcp](#AkashRajpurohit-gsc-mcp) | ★ 3 | `Node` | ✓ (25k) | ✓ | ✓ (Indexing) | — | Service Account | Raw JSON |
| [AKzar1el/mcp-gsc](#AKzar1el-mcp-gsc) | ★ 5 | `Node` | ✓ (25k) | ✓ | ✓ (Indexing) | — | OAuth PKCE | Compact MD |
| [AminForou/mcp-gsc](#AminForou-mcp-gsc) | ★ 1,612 | `Python` | ✓ | ✓ | ✓ | — | OAuth2 | Raw JSON |
| [ApollosWave/gsc-cli](#ApollosWave-gsc-cli) | ★ 8 | `Ruby` | ✓ | ✓ | ✓ (Indexing) | SQLite | Service Account | Compact MD |
| [avansaber/seo-monster](#avansaber-seo-monster) | ★ 242 | `Python` | ✓ (25k) | ✓ | ✓ | — | OAuth2 | Raw JSON |
| [bakissation/mcp-google-multi](#bakissation-mcp-google-multi) | ★ 11 | `Node` | ✓ (25k) | ✓ | ✓ | — | Multi-Account | Raw JSON |
| [bytefer/google-search-console-mcp](#bytefer-google-search-console-mcp) | ★ 19 | `Node` | ✓ | ✓ | ✓ | — | OAuth2 | Compact MD |
| [charlesdove977/search-console-mcp](#charlesdove977-search-console-mcp) | ★ 13 | `Python` | ✓ | ✓ | ✓ | — | OAuth2 | Raw JSON |
| [crawlseo/crawlseo](#crawlseo-crawlseo) | ★ 599 | `Node` | ✓ | ✓ | ✓ | — | OAuth2 | Compact MD |
| [Dataslayer-AI/Marketing-skills](#Dataslayer-AI-Marketing-skills) | ★ 23 | `Python` | ✓ | ✓ | ✓ | — | OAuth2 | Raw JSON |
| [Draivix/aidvertaiser](#Draivix-aidvertaiser) | ★ 20 | `Python` | ✓ (25k) | ✓ | ✓ (Indexing) | — | OAuth2 | Raw JSON |
| [eliazv/OpenFindability](#eliazv-OpenFindability) | ★ 4 | `Node` | ✓ | ✓ | ✓ | SQLite | Service Account | Raw JSON |
| [every-app/open-seo](#every-app-open-seo) | ★ 19,821 | `Node` | ✓ (25k) | ✓ | ✓ | — | OAuth2 | Raw JSON |
| [fenjo26/OpenGSC](#fenjo26-OpenGSC) | ★ 25 | `Node` | ✓ (25k) | ✓ | ✓ (Indexing) | SQLite | OAuth2 | Raw JSON |
| [FlorianBruniaux/google-search-console-mcp](#FlorianBruniaux-google-search-console-mcp) | ★ 12 | `Python` | ✓ (25k) | ✓ | ✓ (Indexing) | SQLite | Service Account | Raw JSON |
| [fourdots/Google-Marketing-MCPs-G.Ads-GA4-GSC-GTM](#fourdots-Google-Marketing-MCPs-G.Ads-GA4-GSC-GTM) | ★ 3 | `Python` | ✓ (25k) | ✓ | ✓ (Indexing) | — | OAuth2 | Raw JSON |
| [generalist-club/google-marketing-stack-mcp](#generalist-club-google-marketing-stack-mcp) | ★ 7 | `Node` | ✓ (25k) | ✓ | ✓ (Indexing) | — | OAuth2 | Raw JSON |
| [HeyPuter/gsc-mcp](#HeyPuter-gsc-mcp) | ★ 5 | `Node` | ✓ (25k) | ✓ | ✓ | — | OAuth2 | Raw JSON |
| [houtini-ai/better-search-console](#houtini-ai-better-search-console) | ★ 17 | `Node` | ✓ (25k) | ✓ | ✓ | SQLite | Service Account | Raw JSON |
| [houtini-ai/seo-audit](#houtini-ai-seo-audit) | ★ 20 | `Node` | ✓ (25k) | ✓ | ✓ (Indexing) | SQLite | Service Account | Compact MD |
| [houtini-ai/seo-crawler-mcp](#houtini-ai-seo-crawler-mcp) | ★ 16 | `Node` | ✓ | ✓ | ✓ | SQLite | Service Account | Raw JSON |
| [iannuttall/seo](#iannuttall-seo) | ★ 527 | `Node` | ✓ | ✓ | ✓ | SQLite | OAuth2 | Compact MD |
| [itsjwill/seoctopus](#itsjwill-seoctopus) | ★ 11 | `Node` | ✓ | ✓ | ✓ | SQLite | OAuth2 | Compact MD |
| [kLOsk/adloop](#kLOsk-adloop) | ★ 266 | `Python` | ✓ (25k) | ✓ | ✓ | — | OAuth2 | Raw JSON |
| [lionkiii/claude-seo-skills](#lionkiii-claude-seo-skills) | ★ 21 | `Python` | ✓ | ✓ | ✓ | — | OAuth2 | Raw JSON |
| [lionkiii/google-searchconsole-mcp](#lionkiii-google-searchconsole-mcp) | ★ 7 | `Node` | ✓ (25k) | ✓ | ✓ (Indexing) | — | OAuth2 | Raw JSON |
| [Magdoub/awesome-gsc-mcp](#Magdoub-awesome-gsc-mcp) | ★ 14 | `Node` | ✓ (25k) | ✓ | ✓ | — | Service Account | Compact MD |
| [mario-hernandez/google-seo-mcp-claude-code](#mario-hernandez-google-seo-mcp-claude-code) | ★ 12 | `Python` | ✓ | ✓ | ✓ (Indexing) | — | OAuth2 | Raw JSON |
| [MaxJafar/marketingovo](#MaxJafar-marketingovo) | ★ 2 | `Node` | ✓ (25k) | ✓ | ✓ (Indexing) | SQLite | OAuth2 | Raw JSON |
| [mehere14/SEO-Thermostat](#mehere14-SEO-Thermostat) | ★ 0 | `Python` | ✓ (25k) | ✓ | ✓ | SQLite | Service Account | Compact MD |
| [mikusnuz/gsc-mcp](#mikusnuz-gsc-mcp) | ★ 7 | `Node` | ✓ (25k) | ✓ | ✓ (Indexing) | — | Service Account | Raw JSON |
| [mintmcp/google-search-console-mcp](#mintmcp-google-search-console-mcp) | ★ 0 | `Node` | ✓ (25k) | ✓ | ✓ (Indexing) | — | OAuth2 | Raw JSON |
| [Mrshahidali420/google-search-console-mcp](#Mrshahidali420-google-search-console-mcp) | ★ 3 | `Python` | ✓ | ✓ | ✓ (Indexing) | SQLite | OAuth2 | Raw JSON |
| [N-O-P-E/nope-marketplace](#N-O-P-E-nope-marketplace) | ★ 9 | `Node` | ✓ | ✓ | ✓ | — | Cookie | Raw JSON |
| [nalyk/gsccli](#nalyk-gsccli) | ★ 5 | `Node` | ✓ (25k) | ✓ | ✓ (Indexing) | — | Service Account | Raw JSON |
| [ncosentino/google-search-console-mcp](#ncosentino-google-search-console-mcp) | ★ 14 | `C# / AOT` | ✓ (25k) | ✓ | ✓ | — | Service Account | Raw JSON |
| [noduslabs/mcp-server-gsc](#noduslabs-mcp-server-gsc) | ★ 0 | `Node` | ✓ | ✓ | ✓ | — | Service Account | Compact MD |
| [popiliadam/platinum-seo-engine](#popiliadam-platinum-seo-engine) | ★ 27 | `Python` | ✓ (25k) | ✓ | ✓ (Indexing) | — | Service Account | Raw JSON |
| [powehi-eu/google-suite-seo-mcp](#powehi-eu-google-suite-seo-mcp) | ★ 5 | `Go` | ✓ (25k) | ✓ | ✓ | — | Service Account | Raw JSON |
| [Rachit8484/geoseo-mcp](#Rachit8484-geoseo-mcp) | ★ 3 | `Python` | ✓ (25k) | ✓ | ✓ (Indexing) | SQLite | OAuth2 | Raw JSON |
| [samalyxx/gsc-seo-mcp](#samalyxx-gsc-seo-mcp) | ★ 6 | `Node` | ✓ (25k) | ✓ | ✓ (Indexing) | — | Service Account | Raw JSON |
| [sarahpark/google-search-console-mcp](#sarahpark-google-search-console-mcp) | ★ 9 | `Node` | ✓ (25k) | ✓ | ✓ (Indexing) | — | Service Account | Compact MD |
| [saurabhsharma2u/search-console-mcp](#saurabhsharma2u-search-console-mcp) | ★ 293 | `Node` | ✓ (25k) | ✓ | ✓ (Indexing) | — | Multi-Account | Raw JSON |
| [serpfire/gsc-mcp-server](#serpfire-gsc-mcp-server) | ★ 11 | `Node` | ✓ (25k) | ✓ | ✓ (Indexing) | SQLite | OAuth2 | Raw JSON |
| [Shin-sibainu/google-search-console-mcp-server](#Shin-sibainu-google-search-console-mcp-server) | ★ 30 | `Node` | ✓ (25k) | ✓ | ✓ (Indexing) | — | OAuth2 | Compact MD |
| [SimplerSoftwareIO/seo-ai-agent](#SimplerSoftwareIO-seo-ai-agent) | ★ 3 | `Python` | ✓ (25k) | ✓ | ✓ (Indexing) | SQLite | Service Account | Raw JSON |
| [sodam-ai/SoDam-SeoMedic](#sodam-ai-SoDam-SeoMedic) | ★ 16 | `Node` | ✓ | ✓ | ✓ | SQLite | Service Account | Raw JSON |
| [sofianbettayeb/gsc-mcp-server](#sofianbettayeb-gsc-mcp-server) | ★ 5 | `Node` | ✓ (25k) | ✓ | ✓ (Indexing) | — | OAuth2 | Raw JSON |
| [stroniarz/gsc-mcp](#stroniarz-gsc-mcp) | ★ 1 | `Python` | ✓ (25k) | ✓ | ✓ | — | OAuth2 | Compact MD |
| [stufently/google-webtools-mcp](#stufently-google-webtools-mcp) | ★ 7 | `Node` | ✓ (25k) | ✓ | ✓ (Indexing) | — | Service Account | Raw JSON |
| [sudomichael/search-console-mcp](#sudomichael-search-console-mcp) | ★ 7 | `Node` | ✓ (25k) | ✓ | ✓ | — | OAuth PKCE | Compact MD |
| [Suganthan-Mohanadasan/Suganthans-BigQuery-MCP-Server](#Suganthan-Mohanadasan-Suganthans-BigQuery-MCP-Server) | ★ 43 | `Node` | ✓ (25k) | ✓ | ✓ | — | Service Account | Compact MD |
| [Suganthan-Mohanadasan/Suganthans-GSC-MCP](#Suganthan-Mohanadasan-Suganthans-GSC-MCP) | ★ 130 | `Node` | ✓ (25k) | ✓ | ✓ | — | Service Account | Compact MD |
| [surendranb/google-search-console-mcp](#surendranb-google-search-console-mcp) | ★ 38 | `Python` | ✓ (25k) | ✓ | ✓ (Indexing) | — | Service Account | Raw JSON |
| [thatseoagent/mcp](#thatseoagent-mcp) | ★ 2 | `Node` | ✓ | ✓ | ✓ (Indexing) | SQLite | OAuth2 | Raw JSON |
| [VKirill/ohmy-seo](#VKirill-ohmy-seo) | ★ 10 | `Node` | ✓ (25k) | ✓ | ✓ (Indexing) | SQLite | Multi-Account | Raw JSON |
| [vmandic/searchconsole-mcp](#vmandic-searchconsole-mcp) | ★ 3 | `Node` | ✓ (25k) | ✓ | ✓ | — | Service Account | Compact MD |
| [Yoshyaes/creator-seo-mcp](#Yoshyaes-creator-seo-mcp) | ★ 2 | `Python` | ✓ (25k) | ✓ | ✓ | — | OAuth2 | Raw JSON |

---

## 1. Persist and query data locally

*9 projects. Embedded relational databases, automated 25k-row ingestion daemons, and local search analytics warehouses for SQL querying.*

### Embedded SQLite data warehouses with sandboxed SQL

*4 projects. Syncs historical search performance into local SQLite tables, exposing sandboxed SQL tools to LLMs for sub-second queries.*

| Project | What it does |
|---|---|
| <a id="houtini-ai-seo-audit"></a>[**houtini-ai/seo-audit**](https://github.com/houtini-ai/seo-audit) | Syncs Search Console performance into a local SQLite data warehouse with automated 25k-row pagination. Exposes a sandboxed SQL execution tool allowing LLMs to run custom multi-table queries without context exhaustion. |
| <a id="fenjo26-OpenGSC"></a>[**fenjo26/OpenGSC**](https://github.com/fenjo26/OpenGSC) | Provides a self-hosted web dashboard powered by an embedded SQLite database and a 46-tool MCP server. Ingests daily search performance slices for offline SQL analytics and automated reporting. |
| <a id="serpfire-gsc-mcp-server"></a>[**serpfire/gsc-mcp-server**](https://github.com/serpfire/gsc-mcp-server) | Stores search metrics locally using better-sqlite3 with Write-Ahead Logging (WAL). Calculates automated query cannibalization and performance drops across local historical baselines. |
| <a id="houtini-ai-better-search-console"></a>[**houtini-ai/better-search-console**](https://github.com/houtini-ai/better-search-console) | Synchronizes GSC performance metrics into a local SQLite database for offline analysis. Enables agents to query historical query and page performance without consuming Google API quotas. |

### Local dashboard engines with search analytics persistence

*4 projects. Local-first web dashboards and marketing ops systems that persist search analytics alongside site performance data.*

| Project | What it does |
|---|---|
| <a id="mehere14-SEO-Thermostat"></a>[**mehere14/SEO-Thermostat**](https://github.com/mehere14/SEO-Thermostat) | Unifies Search Console, GA4, and PostHog metrics inside a local-first SQLite persistence layer. Automates multi-source search performance tracking with local dashboard visualization. |
| <a id="MaxJafar-marketingovo"></a>[**MaxJafar/marketingovo**](https://github.com/MaxJafar/marketingovo) | Operates an open-source marketing operations platform with local SQLite persistence for Search Console and GA4 data. Tracks historical search visibility alongside crawl diagnostics. |
| <a id="sodam-ai-SoDam-SeoMedic"></a>[**sodam-ai/SoDam-SeoMedic**](https://github.com/sodam-ai/SoDam-SeoMedic) | Persists Search Console performance trends into a local database for Korean search intelligence. Pairs ranking diagnostics with automated site health audits. |
| <a id="eliazv-OpenFindability"></a>[**eliazv/OpenFindability**](https://github.com/eliazv/OpenFindability) | Provides an open-source local desktop dashboard integrating Search Console, App Store, and revenue metrics into an embedded database for unified findability reporting. |

### Quota-slot database tracking and batch synchronization

*1 projects. Tracks daily API quota slots, job submissions, and site URLs within local persistence to prevent rate-limit exhaustion.*

| Project | What it does |
|---|---|
| <a id="Mrshahidali420-google-search-console-mcp"></a>[**Mrshahidali420/google-search-console-mcp**](https://github.com/Mrshahidali420/google-search-console-mcp) | Tracks site URLs, job submissions, and API quota slots in an embedded SQLite database. Implements rolling daily quota replenishment to prevent 429 rate-limit rejections. |

---

## 2. Manage multi-property and agency access

*5 projects. Dynamic account routers, multi-tenant credential isolation, and frictionless OAuth 2.0 onboarding for agencies managing multiple client properties.*

### Dynamic multi-account routing and credential isolation

*1 projects. Routes tool calls across multiple Google accounts using dedicated connection names or encrypted client vaults.*

| Project | What it does |
|---|---|
| <a id="bakissation-mcp-google-multi"></a>[**bakissation/mcp-google-multi**](https://github.com/bakissation/mcp-google-multi) | Switches dynamically between multiple Google accounts with parallel fanout support. Allows agency agents to execute cross-client Search Console queries using dedicated account connection parameters. |

### Multi-tenant domain matching and dynamic siteUrl resolution

*2 projects. Accepts dynamic property parameters per tool call, automatically normalizing sc-domain prefixes and trailing slashes.*

| Project | What it does |
|---|---|
| <a id="saurabhsharma2u-search-console-mcp"></a>[**saurabhsharma2u/search-console-mcp**](https://github.com/saurabhsharma2u/search-console-mcp) | Implements a 3-tier domain matching hierarchy that automatically resolves dynamic siteUrl parameters, domain properties (sc-domain:), and URL prefixes without process restarts. |
| <a id="VKirill-ohmy-seo"></a>[**VKirill/ohmy-seo**](https://github.com/VKirill/ohmy-seo) | Routes Search Console queries through AES-256 encrypted multi-account vaults. Supports dynamic account parameter passing across Google, Yandex, and Metrika properties. |

### Frictionless OAuth 2.0 PKCE browser onboarding

*2 projects. Zero-setup browser sign-in using OAuth 2.0 PKCE, eliminating manual Google Cloud Console and Service Account key creation.*

| Project | What it does |
|---|---|
| <a id="sudomichael-search-console-mcp"></a>[**sudomichael/search-console-mcp**](https://github.com/sudomichael/search-console-mcp) | Provides a frictionless 30-second OAuth 2.0 PKCE browser sign-in for Claude Desktop and Cursor. Eliminates manual Google Cloud Console configuration and Service Account key generation. |
| <a id="AKzar1el-mcp-gsc"></a>[**AKzar1el/mcp-gsc**](https://github.com/AKzar1el/mcp-gsc) | Exposes 21 Search Console tools over a hosted remote MCP server with OAuth 2.0 PKCE onboarding. Validates protocol prefixes and supports domain-level property switching. |

---

## 3. Diagnose technical SEO and search algorithms

*6 projects. Specialized analytics engines executing local algorithmic calculations for keyword cannibalization, content decay, and audit reporting.*

### Keyword cannibalization and content decay diagnostics

*2 projects. Identifies URLs competing for identical queries and calculates Pareto content decay curves to alert on ranking drops.*

| Project | What it does |
|---|---|
| <a id="Suganthan-Mohanadasan-Suganthans-GSC-MCP"></a>[**Suganthan-Mohanadasan/Suganthans-GSC-MCP**](https://github.com/Suganthan-Mohanadasan/Suganthans-GSC-MCP) | Detects keyword cannibalization and computes Pareto content decay curves using local algorithmic heuristics. Features proactive Slack and email alerting for ranking anomalies. |
| <a id="Yoshyaes-creator-seo-mcp"></a>[**Yoshyaes/creator-seo-mcp**](https://github.com/Yoshyaes/creator-seo-mcp) | Analyzes Search Console performance weighted by monetization and conversion value. Highlights high-intent keyword opportunities that drive creator revenue. |

### Multi-signal SEO audits with CrUX, IndexNow, and HTML reporting

*2 projects. Combines Search Console data with Core Web Vitals, IndexNow feeds, and white-label HTML audit generators.*

| Project | What it does |
|---|---|
| <a id="FlorianBruniaux-google-search-console-mcp"></a>[**FlorianBruniaux/google-search-console-mcp**](https://github.com/FlorianBruniaux/google-search-console-mcp) | Exposes 61 technical SEO tools connecting Search Console with CrUX performance, IndexNow feeds, and schema validation. Tracks drift across local SQLite snapshots. |
| <a id="acamolese-google-search-console-mcp"></a>[**acamolese/google-search-console-mcp**](https://github.com/acamolese/google-search-console-mcp) | Generates white-label technical SEO audit reports in English and Italian from 17 read-only tools. Ships as a single Docker container and portable .mcpb desktop bundle. |

### CTR opportunity modeling and GEO attribution analytics

*2 projects. Models empirical CTR curves across positions and calculates geographic attribution performance across search surfaces.*

| Project | What it does |
|---|---|
| <a id="samalyxx-gsc-seo-mcp"></a>[**samalyxx/gsc-seo-mcp**](https://github.com/samalyxx/gsc-seo-mcp) | Models empirical CTR curves to uncover underperforming search rankings. Evaluates keyword opportunities and inspects indexing status through unified TypeScript schemas. |
| <a id="Rachit8484-geoseo-mcp"></a>[**Rachit8484/geoseo-mcp**](https://github.com/Rachit8484/geoseo-mcp) | Correlates Search Console geographic search metrics with IndexNow instant submission. Analyzes localized search visibility across regional search surfaces. |

---

## 4. Automate indexing and URL lifecycle

*4 projects. Batch URL inspection, real-time Google Indexing API submission, and automated XML sitemap CRUD operations.*

### Batch URL inspection and indexing automation

*2 projects. Inspects crawl status, mobile friendliness, and index state in bulk, with direct Indexing API submission integration.*

| Project | What it does |
|---|---|
| <a id="nalyk-gsccli"></a>[**nalyk/gsccli**](https://github.com/nalyk/gsccli) | Executes high-throughput batch URL inspection and Google Indexing API submission from a senior-grade CLI with MCP support. Features robust retry mechanisms and JSON streaming. |
| <a id="ApollosWave-gsc-cli"></a>[**ApollosWave/gsc-cli**](https://github.com/ApollosWave/gsc-cli) | Provides a zero-gem CLI and AI agent engine integrating Search Console analytics with Google Indexing API publishing. Automates indexing requests and crawl verification. |

### Combined search analytics and Indexing API lifecycle

*1 projects. Unified MCP tools managing search performance analysis alongside real-time URL_UPDATED and URL_DELETED notifications.*

| Project | What it does |
|---|---|
| <a id="mikusnuz-gsc-mcp"></a>[**mikusnuz/gsc-mcp**](https://github.com/mikusnuz/gsc-mcp) | Exposes 13 tools uniting Search Analytics with real-time Google Indexing API submission. Manages URL_UPDATED and URL_DELETED notifications directly from LLM workflows. |

### Sitemap management and indexing feed inspection

*1 projects. Submits XML sitemaps, inspects feed warnings, and monitors indexed URL ratios across verified properties.*

| Project | What it does |
|---|---|
| <a id="bytefer-google-search-console-mcp"></a>[**bytefer/google-search-console-mcp**](https://github.com/bytefer/google-search-console-mcp) | Provides complete sitemaps CRUD operations and XML feed validation alongside search analytics. Monitors indexed URL ratios and sitemap crawl errors. |

---

## 5. Drive agents via CLI and native runtimes

*5 projects. Native compiled binaries, CLI-first developer tools, and Claude Code skill extensions built for headless agent loops.*

### Native compiled binaries with zero-dependency execution

*1 projects. Ahead-of-Time (AOT) compiled native binary without Node.js or Python runtime dependencies, providing instant cold starts.*

| Project | What it does |
|---|---|
| <a id="ncosentino-google-search-console-mcp"></a>[**ncosentino/google-search-console-mcp**](https://github.com/ncosentino/google-search-console-mcp) | Compiles to a standalone native AOT C# binary with zero Node.js or Python runtime dependencies. Delivers sub-millisecond cold starts and zero garbage collection overhead for local agents. |

### Autonomous agent frameworks with GSC tool integration

*1 projects. Production Python frameworks pairing LLM reasoning engines directly with Google Search Console tool bindings.*

| Project | What it does |
|---|---|
| <a id="SimplerSoftwareIO-seo-ai-agent"></a>[**SimplerSoftwareIO/seo-ai-agent**](https://github.com/SimplerSoftwareIO/seo-ai-agent) | Pairs GPT-4o autonomous reasoning engines with Search Console tool definitions. Orchestrates multi-step search audits, keyword analysis, and recommendation generation. |

### Claude Code command packs and skill extensions

*3 projects. Prompt-driven command extensions and skill plugins tailored for interactive terminal workflows in Claude Code.*

| Project | What it does |
|---|---|
| <a id="mario-hernandez-google-seo-mcp-claude-code"></a>[**mario-hernandez/google-seo-mcp-claude-code**](https://github.com/mario-hernandez/google-seo-mcp-claude-code) | Integrates Search Console tool definitions directly into Claude Code CLI interactive sessions. Enables natural language SEO diagnostics from developer terminal prompts. |
| <a id="lionkiii-claude-seo-skills"></a>[**lionkiii/claude-seo-skills**](https://github.com/lionkiii/claude-seo-skills) | Provides 42 specialized SEO commands for Claude Code, integrating Search Console analytics with Ahrefs backlink data. Enables rapid site health inspections. |
| <a id="N-O-P-E-nope-marketplace"></a>[**N-O-P-E/nope-marketplace**](https://github.com/N-O-P-E/nope-marketplace) | Automates Search Console and Google Cloud management through open-source Claude Code plugins. Exposes modular tools for headless agency workflows. |

---

## 6. Connect unified marketing stacks

*7 projects. Multi-platform MCP servers integrating Search Console with GA4, Google Ads, GTM, and third-party advertising platforms.*

### Unified Google Search Console and GA4 analytics bridges

*2 projects. Bridges search visibility with post-click user engagement, sessions, and conversions within a unified dual-tool server.*

| Project | What it does |
|---|---|
| <a id="stufently-google-webtools-mcp"></a>[**stufently/google-webtools-mcp**](https://github.com/stufently/google-webtools-mcp) | Bridges Search Console organic search data with Google Analytics 4 sessions and conversions. Formats output into compact Markdown tables to conserve LLM context tokens. |
| <a id="kLOsk-adloop"></a>[**kLOsk/adloop**](https://github.com/kLOsk/adloop) | Unifies Search Console search queries with Google Ads conversion tracking. Monitors organic keyword rankings and paid search efficiency within a single agent interface. |

### Cross-platform Google Marketing Platform suites

*5 projects. Comprehensive multi-tool servers exposing 40 to 140+ tools across Search Console, GA4, Google Ads, Sheets, and Tag Manager.*

| Project | What it does |
|---|---|
| <a id="fourdots-Google-Marketing-MCPs-G.Ads-GA4-GSC-GTM"></a>[**fourdots/Google-Marketing-MCPs-G.Ads-GA4-GSC-GTM**](https://github.com/fourdots/Google-Marketing-MCPs-G.Ads-GA4-GSC-GTM) | Exposes 146 tools across Search Console, GA4, Google Ads, and Tag Manager in an enterprise mono-daemon. Supports extensive cross-service marketing workflows. |
| <a id="generalist-club-google-marketing-stack-mcp"></a>[**generalist-club/google-marketing-stack-mcp**](https://github.com/generalist-club/google-marketing-stack-mcp) | Provides 44 tools uniting Search Console, GA4, Google Sheets, GTM, and PageSpeed Insights. Streamlines automated end-to-end digital marketing reporting. |
| <a id="thatseoagent-mcp"></a>[**thatseoagent/mcp**](https://github.com/thatseoagent/mcp) | Supplies 55 tools connecting Search Console search analytics with Google Analytics tracking. Provides pre-built prompt templates for digital marketing agents. |
| <a id="powehi-eu-google-suite-seo-mcp"></a>[**powehi-eu/google-suite-seo-mcp**](https://github.com/powehi-eu/google-suite-seo-mcp) | Exposes a comprehensive suite of Google marketing and search tools. Bridges Search Console performance with Google Workspace integrations. |
| <a id="Dataslayer-AI-Marketing-skills"></a>[**Dataslayer-AI/Marketing-skills**](https://github.com/Dataslayer-AI/Marketing-skills) | Provides agency-tailored marketing tool definitions connecting Search Console with multi-channel analytics. Simplifies cross-platform client reporting. |

---

## 7. Bridge enterprise data lakes and hybrid extraction

*3 projects. Enterprise BigQuery bulk export query engines, crawl DOM internal link mergers, and browser-automated rank extraction.*

### BigQuery bulk export data lake bridges

*1 projects. Queries Google Cloud BigQuery daily partitioned export tables, bypassing Search Console API rate limits and row caps.*

| Project | What it does |
|---|---|
| <a id="Suganthan-Mohanadasan-Suganthans-BigQuery-MCP-Server"></a>[**Suganthan-Mohanadasan/Suganthans-BigQuery-MCP-Server**](https://github.com/Suganthan-Mohanadasan/Suganthans-BigQuery-MCP-Server) | Queries Google Cloud BigQuery GSC bulk export partitioned tables directly. Bypasses Search Console's 25,000-row API truncation and quota limits for enterprise analysis. |

### Browser-automated rank tracking and SERP extraction

*1 projects. Pairs Playwright browser automation for live rank checking with official Search Console API performance reporting.*

| Project | What it does |
|---|---|
| <a id="itsjwill-seoctopus"></a>[**itsjwill/seoctopus**](https://github.com/itsjwill/seoctopus) | Combines official Search Console API metrics with Playwright browser automation for stealth SERP rank tracking. Detects ranking discrepancies between API data and live search results. |

### Crawl DOM integration and internal link analysis

*1 projects. Merges live HTML crawl graphs with Search Console query performance to evaluate internal link equity.*

| Project | What it does |
|---|---|
| <a id="houtini-ai-seo-crawler-mcp"></a>[**houtini-ai/seo-crawler-mcp**](https://github.com/houtini-ai/seo-crawler-mcp) | Crawls site DOM architecture and merges internal linking graphs with Search Console query performance. Identifies orphaned pages and internal link equity bottlenecks. |

---

## 8. Query search analytics through lightweight proxies

*21 projects. Fast, lightweight MCP proxies connecting LLMs directly to Search Console API endpoints with varying token formatting.*

### Token-optimized compact markdown proxies

*5 projects. Formats API responses into compact Markdown tables or CSV strings, reducing LLM context window token consumption by up to 85%.*

| Project | What it does |
|---|---|
| <a id="ahonn-mcp-server-gsc"></a>[**ahonn/mcp-server-gsc**](https://github.com/ahonn/mcp-server-gsc) | Provides a lightweight TypeScript MCP server returning search analytics in clean, token-efficient Markdown tables. Eliminates redundant JSON wrapper tokens. |
| <a id="stroniarz-gsc-mcp"></a>[**stroniarz/gsc-mcp**](https://github.com/stroniarz/gsc-mcp) | Returns structured, filtered search performance data formatted to minimize LLM token usage. Employs Python FastMCP with strict input schema validation. |
| <a id="sarahpark-google-search-console-mcp"></a>[**sarahpark/google-search-console-mcp**](https://github.com/sarahpark/google-search-console-mcp) | Provides safe, read-only Search Console query analysis with zero mutation endpoints. Compacts performance metrics to preserve context window capacity. |
| <a id="AkashRajpurohit-gsc-mcp"></a>[**AkashRajpurohit/gsc-mcp**](https://github.com/AkashRajpurohit/gsc-mcp) | Implements a secure, local read-only TypeScript MCP server with strict Zod validation. Publishes to npm for zero-install execution via npx. |
| <a id="iannuttall-seo"></a>[**iannuttall/seo**](https://github.com/iannuttall/seo) | Formats Search Console query and page metrics into ultra-compact Markdown output. Built by a senior engineer with clean zero-dependency architectural design. |

### Comprehensive multi-endpoint Search Console API proxies

*8 projects. Feature-complete servers exposing Search Analytics, Sitemaps CRUD, Site Verification, and URL Inspection through clean Zod schemas.*

| Project | What it does |
|---|---|
| <a id="vmandic-searchconsole-mcp"></a>[**vmandic/searchconsole-mcp**](https://github.com/vmandic/searchconsole-mcp) | Exposes complete Search Console API coverage with compact Zod schemas and comprehensive error handling. Handles multi-dimension breakdowns and filtering. |
| <a id="noduslabs-mcp-server-gsc"></a>[**noduslabs/mcp-server-gsc**](https://github.com/noduslabs/mcp-server-gsc) | Calculates period-over-period search performance comparisons and trend anomalies. Features clean, safe read-only tool implementations. |
| <a id="Magdoub-awesome-gsc-mcp"></a>[**Magdoub/awesome-gsc-mcp**](https://github.com/Magdoub/awesome-gsc-mcp) | Exposes 27 tools with built-in token-bucket rate limiting and response caching. Protects Google Cloud quotas while serving multi-date search queries. |
| <a id="Shin-sibainu-google-search-console-mcp-server"></a>[**Shin-sibainu/google-search-console-mcp-server**](https://github.com/Shin-sibainu/google-search-console-mcp-server) | Provides multi-dimension Search Console query tools with robust error recovery. Supports Japanese and international character sets. |
| <a id="lionkiii-google-searchconsole-mcp"></a>[**lionkiii/google-searchconsole-mcp**](https://github.com/lionkiii/google-searchconsole-mcp) | Stores Google OAuth tokens locally to enforce strict data privacy and local-only execution. Provides clean search analytics and inspection tools. |
| <a id="surendranb-google-search-console-mcp"></a>[**surendranb/google-search-console-mcp**](https://github.com/surendranb/google-search-console-mcp) | Wraps Google Search Console APIs in standard TypeScript MCP tools for search performance reporting and query dimension analysis. |
| <a id="sofianbettayeb-gsc-mcp-server"></a>[**sofianbettayeb/gsc-mcp-server**](https://github.com/sofianbettayeb/gsc-mcp-server) | Provides a clean TypeScript MCP server exposing Search Console queries with date-range filters and position metrics. |
| <a id="charlesdove977-search-console-mcp"></a>[**charlesdove977/search-console-mcp**](https://github.com/charlesdove977/search-console-mcp) | Implements multi-dimension Search Console performance querying with customizable date comparisons and position tracking. |

### FastMCP and standard search analytics wrappers

*6 projects. Straightforward Python FastMCP and TypeScript implementations wrapping the core searchAnalytics.query endpoint.*

| Project | What it does |
|---|---|
| <a id="AminForou-mcp-gsc"></a>[**AminForou/mcp-gsc**](https://github.com/AminForou/mcp-gsc) | Provides a straightforward FastMCP Python server exposing Google Search Console searchAnalytics.query with dimension filtering. |
| <a id="every-app-open-seo"></a>[**every-app/open-seo**](https://github.com/every-app/open-seo) | Supplies open-source SEO tools wrapping Search Console API queries for AI coding assistants and automation workflows. |
| <a id="crawlseo-crawlseo"></a>[**crawlseo/crawlseo**](https://github.com/crawlseo/crawlseo) | Wraps Google Search Console performance reporting within an open-source SEO analysis toolkit. |
| <a id="avansaber-seo-monster"></a>[**avansaber/seo-monster**](https://github.com/avansaber/seo-monster) | Provides Python-based Search Console query tools with basic multi-dimension filtering and position tracking. |
| <a id="popiliadam-platinum-seo-engine"></a>[**popiliadam/platinum-seo-engine**](https://github.com/popiliadam/platinum-seo-engine) | Provides Search Console analytics tools within an enterprise SEO automation engine with 538 git commits. |
| <a id="Draivix-aidvertaiser"></a>[**Draivix/aidvertaiser**](https://github.com/Draivix/aidvertaiser) | Exposes Search Console tools alongside 180+ digital advertising tools within a large multi-platform MCP suite. |

### Remote HTTP and cloud-hosted MCP servers

*2 projects. Cloud-hosted MCP servers accessible over remote HTTP or Server-Sent Events (SSE) without local runtime dependencies.*

| Project | What it does |
|---|---|
| <a id="mintmcp-google-search-console-mcp"></a>[**mintmcp/google-search-console-mcp**](https://github.com/mintmcp/google-search-console-mcp) | Exposes 15+ Search Console tools over a remote streamable HTTP SSE transport. Enables cloud-native agent integrations without local server hosting. |
| <a id="HeyPuter-gsc-mcp"></a>[**HeyPuter/gsc-mcp**](https://github.com/HeyPuter/gsc-mcp) | Runs Search Console MCP tools directly inside the cloud-hosted Puter.com OS environment. Accessible remotely via secure webhooks. |

---

## Resources

- **[Google Search Console API Overview](https://developers.google.com/webmaster-tools)**: Official documentation for searchAnalytics, urlInspection, sitemaps, and sites services.
- **[Model Context Protocol Specification](https://modelcontextprotocol.io/)**: The open protocol connecting AI agents with local and remote data tools.
- **[Search Console Bulk Data Export Guide](https://support.google.com/webmasters/answer/12970322)**: Complete schema guide for streaming GSC impression data into Google Cloud BigQuery.
- **[Google Indexing API Quickstart](https://developers.google.com/search/apis/indexing-api/v3/quickstart)**: Documentation for automated real-time URL notification submission.
- **[Google Search Central Developer Documentation](https://developers.google.com/search/docs)**: Technical guidelines covering crawling, indexing, canonicalization, and rich results.

## Reference

- **Property Formats:** Google Search Console supports URL-prefix properties (`https://example.com/`) and Domain properties (`sc-domain:example.com`). API calls targeting domain properties must include the `sc-domain:` prefix to prevent `HTTP 400 Bad Request` errors.
- **Search Analytics API Constraints:** Maximum 25,000 rows per query response. Standard data features a 2–3 day reporting lag; the Fresh Data API provides preliminary metrics for the last 24 hours.
- **URL Inspection API Limits:** Hard quota limit of 2,000 queries per day (QPD) and 600 queries per minute (QPM). Inspects crawl timestamps, Google-selected canonicals, mobile friendliness, and rich results.
- **Authentication Models:** User OAuth 2.0 PKCE enables frictionless browser authentication without Google Cloud Console setup; Service Account JSON keys provide automated headless access for servers and pipelines.
- **Token Economics:** Raw API JSON payloads consume 15,000 to 45,000 tokens per multi-dimension query; compact Markdown tables and CSV serializations reduce context window footprint to 1,000 to 5,000 tokens.
