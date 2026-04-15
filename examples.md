# aidevboard-mcp — Example tool calls

## search_jobs

```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "tools/call",
  "params": {
    "name": "search_jobs",
    "arguments": {
      "query": "RAG infrastructure",
      "workplace": "remote",
      "experience_level": "senior",
      "limit": 5
    }
  }
}
```

Returns an array of job listings with fields: `id`, `title`, `company_name`, `location`, `workplace`, `experience_level`, `salary_min`, `salary_max`, `tags`, `apply_url`, `published_at`.

## get_job

```json
{
  "jsonrpc": "2.0",
  "id": 2,
  "method": "tools/call",
  "params": {
    "name": "get_job",
    "arguments": { "slug": "ml-engineer-anthropic-abc123" }
  }
}
```

## list_companies

```json
{
  "jsonrpc": "2.0",
  "id": 3,
  "method": "tools/call",
  "params": { "name": "list_companies", "arguments": { "limit": 20 } }
}
```

## match_jobs

Rank jobs against a candidate profile.

```json
{
  "jsonrpc": "2.0",
  "id": 4,
  "method": "tools/call",
  "params": {
    "name": "match_jobs",
    "arguments": {
      "skills": ["pytorch", "llm", "distributed-systems"],
      "min_salary": 180000,
      "workplace": "remote",
      "limit": 10
    }
  }
}
```

Scoring: +2 per matching tag, +3 if salary in range, +2 if workplace matches, +1 if experience level matches.

## get_stats

```json
{
  "jsonrpc": "2.0",
  "id": 5,
  "method": "tools/call",
  "params": { "name": "get_stats", "arguments": {} }
}
```

Returns `{total_jobs, total_companies, last_scraped_at, top_tags}`.

## Via Claude Code

```bash
claude mcp add --transport http aidevboard https://aidevboard.com/mcp
# then in session:
# "find 5 remote senior RAG engineering roles"
# "show me which companies are hiring for pytorch"
```

## REST API equivalent

If your agent doesn't speak MCP, the equivalent REST endpoints are:

- `GET https://aidevboard.com/api/v1/jobs?q=RAG&workplace=remote`
- `GET https://aidevboard.com/api/v1/jobs/{slug}`
- `GET https://aidevboard.com/api/v1/companies`
- `POST https://aidevboard.com/api/v1/jobs/match`
- `GET https://aidevboard.com/api/v1/stats`

See [openapi.yaml](https://aidevboard.com/openapi.yaml).
