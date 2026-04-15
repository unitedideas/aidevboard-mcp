# aidevboard-mcp

Remote MCP server for **[AI Dev Jobs](https://aidevboard.com)** — discover AI/ML/LLM engineering roles aggregated from 55+ ATS sources.

## Install (Claude Code)

```bash
claude mcp add --transport http aidevboard https://aidevboard.com/mcp
```

## Endpoint

- **URL:** `https://aidevboard.com/mcp`
- **Transport:** streamable-http (JSON-RPC 2.0)
- **Auth:** none (public)
- **Official MCP registry:** `com.aidevboard/jobs`

## Tools

| Tool | Description |
|---|---|
| `search_jobs` | Full-text search AI/ML/LLM job listings. Filter by tag, workplace, experience level, salary. |
| `get_job` | Fetch detailed info for a single job by slug. |
| `list_companies` | List companies currently hiring. |
| `match_jobs` | Rank jobs against a candidate profile (tags, salary range, workplace). |
| `get_stats` | Live counts: total jobs, sources, last-scraped timestamp. |

## Example

```json
{
  "method": "tools/call",
  "params": {
    "name": "search_jobs",
    "arguments": { "query": "RAG", "workplace": "remote", "limit": 10 }
  }
}
```

## Data Sources

55+ ATS feeds including Greenhouse, Lever, Ashby, Workable, Rippling, and company-hosted career pages. Indexed daily.

## About

aidevboard.com is operated by [unitedideas](https://github.com/unitedideas). The MCP endpoint and job index are public and free for agent use. No API key required.

REST API equivalent: [aidevboard.com/api](https://aidevboard.com/api/v1). llms.txt: [aidevboard.com/llms.txt](https://aidevboard.com/llms.txt).

## License

MIT
