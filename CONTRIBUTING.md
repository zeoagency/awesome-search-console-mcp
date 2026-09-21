# Contributing to Awesome Search Console MCP

Thank you for your interest in contributing to **Awesome Search Console MCP**!

This project is a curated, developer-focused index and technical capability benchmark of Model Context Protocol (MCP) servers and agent-facing tooling built for **[Google Search Console](https://search.google.com/search-console)**.

To maintain high architectural fidelity, signal-to-noise ratio, and evidentiary rigor, all submissions must comply with the guidelines below.

---

## Scope & Inclusion Boundaries

### What Belongs

- **Direct Google Search Console MCP Servers**: Servers exposing `searchAnalytics`, `urlInspection`, `sitemaps`, or `sites` API methods over Model Context Protocol (stdio, SSE, Streamable HTTP).
- **Embedded Relational Analytics Engines**: MCP servers that ingest GSC performance data into local SQLite, DuckDB, or embedded data warehouses for LLM SQL querying.
- **Enterprise Data Lake Bridges**: Tools connecting GSC BigQuery Bulk Exports to AI agent reasoning loops.
- **Automated Lifecycle & Indexing Engines**: Tools managing Google Indexing API submission queues and sitemap feed audits.
- **Unified Marketing Stacks**: Multi-service tools (GSC + GA4 / Google Ads) with substantive, documented Search Console tool surfaces.
- **Native Binaries & CLI Runtimes**: Zero-runtime or CLI-based agent tools exposing Search Console capabilities.

### What Does NOT Belong (Quarantine Triggers)

To protect developers and agent operators, submissions meeting any of the following triggers are rejected or quarantined:

1. **Third-Party Commercial SEO / Rank-Tracker Directories**: Tools primarily interfacing with commercial third-party SEO platforms (Ahrefs, Semrush, Moz) without substantive, documented Google Search Console functionality.
2. **Paywalled SaaS Shells**: Hosted commercial services with proprietary, paywalled backends and no open-source MCP implementation.
3. **Binary-Only or Obfuscated Repositories**: Repositories shipping compiled binaries without corresponding source code.
4. **Synthetic Slop / Bot-Farm Forks**: Automated forks created without substantial differentiation, documentation, or maintenance.
5. **Non-MCP Scripts**: General standalone scripts or tutorials that do not implement the Model Context Protocol or an agent tool specification.

---

## Submission Guidelines

When proposing a new Search Console MCP server or updating an existing listing, please adhere to our editorial standards:

### 1. Two-Stage Linking Requirement

Every project listed in the repository exists in two places:

1. **Developer Comparison Matrix**: Row entry featuring technical capability columns, with the project name linking internally to `#slug` (e.g. `[owner/repo](#owner-repo)`).
2. **Categorized Detailed Table**: Row entry under the appropriate job category/subcategory featuring an anchor target `<a id="slug"></a>`, the bold project link to upstream GitHub `[**owner/repo**](https://github.com/owner/repo)`, and a curated description.

### 2. Differentiated Prose Standard

- **Length**: Strictly 1 to 3 sentences.
- **Voice**: Active, verb-first framing (e.g., *"Synchronizes historical search performance into a local SQLite data warehouse with automated 25k pagination..."*).
- **Substance**: State concrete architectural facts (runtime, auth method, persistence mechanism, token ergonomics) rather than marketing buzzwords (*"best"*, *"blazing fast"*, *"revolutionary"*).
- **Prohibited**: Do not leave empty stubs, placeholder strings (`TODO`, `TBD`), or repetitive template descriptions.

### 3. Granularity & Anti-Lumping Rule

- Our taxonomy is organized into **Job Categories** and **Granular Subcategories**.
- Each subcategory must contain between **1 and 8 projects**. If a subcategory grows beyond 8 projects, it must be subdivided by architectural paradigm (e.g., token format, authentication mechanism, or transport model).

---

## Step-by-Step Submission Process

1. **Fork the repository** to your personal or organization account.
2. **Add your project to `README.md`**:
   - Add a row to the **Developer Comparison Matrix** under Section 9 (sorted alphabetically by repository name), using an internal anchor link `[owner/repo](#owner-repo)`.
   - Add a row to the appropriate **Subcategory Table** under Sections 1–8 with `<a id="owner-repo"></a>[**owner/repo**](https://github.com/owner/repo)` and your 1–3 sentence verb-first description.
   - Update the numeric count in the Table of Contents, Section Header, and Subcategory Header to maintain exact arithmetic parity.
3. **Run local markdown validation**:

   ```bash
   npx markdownlint-cli2 "**/*.md"
   ```

   All checks must pass with zero errors.
4. **Submit a Pull Request** with a clear title (e.g., `Add owner/repo under Local Persistence`). In the PR description, summarize:
   - Repository URL and author.
   - Key architectural features (runtime, transport, auth method, local database, token format).
   - Confirmation that the submission does not trigger any quarantine rules.

---

## Code of Conduct

We are committed to providing a friendly, safe, and welcoming environment for all contributors. Please refer to [`CODE_OF_CONDUCT.md`](CODE_OF_CONDUCT.md) for community guidelines.
