# Multi-Account Routing & OAuth Authentication Patterns

Architectural guide to handling authentication, token refreshing, and dynamic multi-property switching in Google Search Console Model Context Protocol (MCP) servers.

---

## 1. Authentication Models: Trade-offs & Use Cases

Google Search Console APIs require authorized Google identity. Two primary authentication models exist in the MCP ecosystem:

| Dimension | User OAuth 2.0 PKCE | Service Account JSON |
|---|---|---|
| **Primary Audience** | Desktop IDEs, Cursor, Claude Desktop | Headless servers, CI/CD, batch workers |
| **User Friction** | Zero-friction browser consent flow | Requires Google Cloud Console project creation |
| **GSC Verification** | Automatically inherits user's permissions | Must add service account email as GSC user |
| **Token Storage** | Local OS keychain or secure tokens directory | Static `.json` credential keyfile |
| **Dynamic Switching** | Supports multi-user profile switching | Single identity per service account key |

---

## 2. Frictionless User OAuth 2.0 PKCE Flow

For desktop agent environments (Cursor, Claude Code, Windsurf), requiring users to create a Google Cloud project and download a JSON key generates immense friction.

Modern servers implement OAuth 2.0 with Proof Key for Code Exchange (PKCE) and a local loopback server:

```text
┌────────┐               ┌────────────┐               ┌──────────────┐
│ Agent  │               │ MCP Server │               │ Google OAuth │
└───┬────┘               └─────┬──────┘               └──────┬───────┘
    │                          │                             │
    │ Start MCP Server         │                             │
    ├─────────────────────────>│                             │
    │                          │ Start localhost:8085 server │
    │                          │ Opens browser auth URL      │
    │                          ├────────────────────────────>│
    │                          │                             │
    │                          │ User grants GSC scope       │
    │                          │ Redirect to localhost:8085  │
    │                          │<────────────────────────────┤
    │                          │ Exchanges code for tokens   │
    │                          │ Stores refresh token locally│
    │ Ready for tool calls     │                             │
    │<─────────────────────────┤                             │
```

---

## 3. Dynamic Multi-Account & Multi-Property Routing

In agency, enterprise, and multi-brand workflows, an agent frequently needs to inspect multiple properties across different Google accounts in a single session.

### 3.1. Explicit `account` Parameter

Servers like `bakissation/mcp-google-multi` and `MattiooFR/mcp-gsc-multi-account` store credentials under named profiles (`client_a`, `client_b`):

```json
{
  "name": "query_search_analytics",
  "arguments": {
    "account": "client_alpha",
    "siteUrl": "sc-domain:example.com",
    "startDate": "2026-08-01",
    "endDate": "2026-08-31"
  }
}
```

### 3.2. Automatic Domain Matching

Advanced servers maintain an in-memory index of verified properties across all connected accounts. When the agent passes `siteUrl: "sc-domain:example.com"`, the MCP server automatically routes the request through the specific account holding verification for that domain, completely abstracting credential management from the LLM.
