# ManyPI Docs

Documentation for [ManyPI](https://manypi.com) — the AI sales platform that
finds leads, verifies them, and runs cold-email outreach, built on a web-data
agent.

Published with [Mintlify](https://mintlify.com).

## Structure

| Tab | Directory | Covers |
| --- | --- | --- |
| **Guides** | `leads/`, `outreach/`, `agent/`, `scraping/`, `platform/` | Product documentation, from quickstart to plan limits. |
| **API reference** | `api-reference/` | Every REST endpoint, generated from `api-reference/openapi.json`. |
| **MCP Server** | `mcp/` | Connecting ManyPI to Claude, Cursor, ChatGPT and other MCP clients. |

Navigation lives in [`docs.json`](docs.json). Every page must be listed there to
appear in the sidebar.

## Local development

```bash
npm i -g mint
mint dev
```

Opens a preview at `http://localhost:3000`.

Check for broken links before pushing:

```bash
mint broken-links
```

## Editing the API reference

Endpoint pages are thin MDX stubs — a title plus an `openapi` frontmatter key
pointing at an operation:

```mdx
---
title: "List leads"
openapi: "GET /api/leads"
---
```

All the real content (parameters, schemas, examples, permission notes) lives in
[`api-reference/openapi.json`](api-reference/openapi.json). Edit the spec, not
the stubs.

To add an endpoint:

1. Add the operation to `openapi.json` with a `summary`, a `description` naming
   the required permission, and an example.
2. Create the stub MDX under `api-reference/<group>/<slug>.mdx`.
3. Add the page path to the matching group in `docs.json`.

## Deployment

Changes to the default branch deploy automatically via the Mintlify GitHub app.
