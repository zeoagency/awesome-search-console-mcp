# AGENTS.md

Working rules and language guidelines for anyone — human or agent — editing this repository. It is a curated, plain-English index of the Google Search Console Model Context Protocol (MCP) and agent tooling ecosystem. Keep it lean, minimalist, and immediately useful.

---

## 1. Project Philosophy & Minimalist Structure

- **No Onboarding Essays:** Do not add introductory installation tutorials or "getting started" walkthroughs to the catalog root. Keep the README strictly minimalist: title with awesome badge, positioning quote, official API links, Table of Contents with counts, direct jump links into the tables, and the developer decision matrix.
- **Fast Jump Navigation:** Developers should jump straight to the relevant problem domain from the Table of Contents in one click.

---

## 2. Project Language & Voice Values

The language of this catalog must be simple, direct, and developer-friendly:

### 2.1. Plain-English, Verb-First Prose

- Lead with active verbs (*Synchronizes*, *Queries*, *Inspects*, *Persists*, *Exposes*, *Routes*, *Authenticates*, *Audits*).
- Avoid passive constructions, convoluted phrasing, and marketing buzzwords (*"ultimate"*, *"blazing fast"*, *"revolutionary"*).
- State clearly what an agent or developer can *do* with the tool, not a laundry list of generic features.

### 2.2. The 1–3 Sentence Rule

Every project entry must be strictly 1 to 3 concise sentences:

- **Sentence 1:** What the tool specifically does for a developer or agent.
- **Sentence 2:** Architectural specifics (e.g., embedded SQLite, OAuth PKCE, 25k pagination auto-loop, token format).
- **Sentence 3 (Optional):** Key differentiation or unique tool capabilities (e.g., Indexing API lifecycle, cannibalization detection, BigQuery export).

### 2.3. Subcategory Header & Table Standards

Every subcategory begins with an exact project count and a 1-sentence summary, followed by a clean 2-column markdown table:

```markdown
### Embedded SQLite data warehouses with sandboxed SQL

*4 projects. Syncs historical search performance into local SQLite tables, exposing sandboxed SQL tools to LLMs for sub-second queries.*

| Project | What it does |
|---|---|
| <a id="owner-repo"></a>[**owner/repo**](https://github.com/owner/repo) | Plain-English explanation of what the tool does and who it is for. |
```

---

## 3. Strict Exclusion Criteria (What NEVER Belongs Here)

To maintain a high-signal catalog, the following must **never** be added:

1. **NO Generic SEO Directories or Third-Party Rank-Trackers:** Only tools explicitly interfacing with Google Search Console, Google Indexing API, or GSC BigQuery bulk export qualify.
2. **NO Empty Scaffolds or Incomplete Stubs:** Repositories without functional MCP tool definitions or broken builds.
3. **NO Commercial Paywalled Shells:** Closed-source commercial products with no public open-source MCP implementation.
4. **NO Binary-Only Distributions:** Precompiled binaries without accompanying source code.
5. **NO Marketing Hype or AI Filler:** Descriptions must remain factual, concise, and neutral.

---

## 4. Two-Stage Linking Requirement

Every project in the repository must follow the two-stage linking pattern:

1. **Quick Comparison Matrix (Stage 1):** Internal jump link to `#owner-repo` (`[owner/repo](#owner-repo)`).
2. **Subcategory Table (Stage 2):** Target anchor `<a id="owner-repo"></a>` followed by the bold link to the upstream repository `[**owner/repo**](https://github.com/owner/repo)`.

---

## 5. Before Committing

1. Run `npx markdownlint-cli2 "**/*.md"` — it must exit clean with **0 issues**.
2. Verify count arithmetic: ensure the count in the Table of Contents, Section Header, and Subcategory Header match the exact number of table rows.
3. Commit with the conventional commit format: `docs(awesome-gsc): <summary>`.
