# Contributing

Thanks for helping keep this the most current directory of multi-agent workflow tooling!

## Adding an entry

1. **Check it fits:** a framework, platform, protocol, infrastructure component, research paper/system, benchmark, or coordination tool that is genuinely about **multiple AI agents working together in workflows** — not a single-agent framework, not a plain LLM API, not a generic workflow tool with no agent story. A PR must point at a primary source: the project's official docs/repo, the vendor's product page, or the paper's canonical home (arXiv, proceedings, project page).
2. **Add to the right section** of `README.md`:
   - Open-source orchestration frameworks → libraries/frameworks you self-host or embed, where agents collaborate (sequential, hierarchical, supervisor-worker, swarm, debate)
   - Commercial / SaaS multi-agent platforms → hosted products that run multi-agent workflows for you
   - Cloud multi-agent services → first-party multi-agent offerings from cloud providers
   - Agent-to-agent protocols & standards → protocols/specifications for agents to discover, message, and delegate to each other
   - Workflow & orchestration infrastructure → durable-execution / workflow engines with a real multi-agent story
   - Research papers & systems → published papers and their accompanying systems/demos
   - Benchmarks & evals → benchmarks that measure multi-agent collaboration
   - Coordination, memory & state → shared memory, blackboards, checkpointing, and messaging layers used between agents
   - Retired / renamed → projects shut down, merged, or renamed, with the date
3. **One entry = one bullet.** Format:
   `- [Name](https://official-site-or-docs) — ` one-line description of the multi-agent story (what the agents do, how they're coordinated).
   Tag verification honestly: write `✅ verified 2026-09-29` only when you opened the official page/repo yourself; otherwise mark it `⚠️ unverified`. **Never invent capabilities, benchmarks scores, or license terms.**
4. **Add the matching record** to `data/multi-agent-workflows.json` with these exact fields:

| field | type | values |
|---|---|---|
| `name` | string | project / product / paper name |
| `vendor` | string | company, org, or lab |
| `url` | string | official https:// URL (docs page or repo) |
| `description` | string | one sentence on the multi-agent story |
| `license` | string | e.g. `"MIT"`, `"Apache-2.0"`, `"proprietary"`, `"n/a"` (papers / protocol specs), or `"unverified"` |
| `category` | string | `framework` / `platform` / `cloud` / `protocol` / `infra` / `research` / `benchmark` / `coordination` |
| `verified` | bool | `true` only if you opened the official source yourself |
| `source_url` | string | official page where the facts appear, or `""` |
| `status` | string | `active` / `maintenance` / `archived` / `renamed` / `commercial` |
| `gotchas` | string[] | 1–4 caveats (pricing wall, auth model, maturity, lock-in) |

5. **Status changes:** if a project is archived, renamed, or materially pivots, update its README entry *and* add a row (newest-first) to the "Retired / renamed" section.

## Style rules

- Link the **official site** (docs, repo, or paper page), never a blog post or reseller.
- Facts that can change (pricing, model support, benchmarks) get "as of" context in prose or are omitted — link the source instead of hard-coding numbers that rot.
- Vendor claims stay labeled as vendor claims ("vendor claims", "reported by community sources").
- Entries are stamped with their verification date; never guess a number. If the official page is ambiguous, mark it `⚠️ unverified`.
- For papers, link the canonical version (arXiv or proceedings) and note the venue/year inline.
