# Orchestration patterns

The recurring shapes multi-agent workflows take, with pointers to entries in this directory that implement each one. See the [glossary](glossary.md) for term definitions.

## Sequential pipeline

Agents run in a fixed order; each consumes the previous agent's output. The simplest pattern and the easiest to debug.

- Researcher → writer → editor → publisher chains.
- Implemented by: CrewAI (Crews, sequential processes), MetaGPT's SOP pipelines, LangGraph linear graphs, or any [workflow engine](../README.md#workflow--orchestration-infrastructure) with ordered steps.

**Watch out:** errors compound down the chain — a bad early output poisons everything after it. Add validation agents or checkpoints between stages.

## Supervisor / orchestrator-worker

One orchestrator agent plans, decomposes the task, delegates subtasks to specialist workers, and synthesizes results.

- The dominant enterprise pattern: Bedrock's supervisor/collaborator, Databricks Mosaic supervisor agent, watsonx Orchestrate, Agentforce's primary/secondary agents, Magentic-One's lead Orchestrator.
- Framework support: OpenAI Agents SDK handoffs, LangGraph supervisor nodes, CrewAI hierarchical processes.

**Watch out:** the supervisor is a single point of failure and a cost multiplier (it sees everything). Give workers narrow tools and tight output schemas.

## Hierarchical teams

Supervisors manage sub-teams, each with their own local coordinator — supervisors all the way down.

- ChatDev's CEO/CTO/programmer/tester company, MetaGPT's role hierarchy, Microsoft Foundry's nested workflows.

**Watch out:** coordination overhead grows fast; keep the tree shallow (2–3 levels) unless tasks genuinely decompose that way.

## Swarm / decentralized

No central coordinator — agents broadcast, negotiate, or vote. Emergent but harder to control.

- CAMEL role-play societies, AgentVerse dynamic teams, Generative Agents' Smallville, NANDA's decentralized vision.

**Watch out:** nondeterministic and expensive. Best for exploration, simulation, and research — not for the invoice pipeline.

## Debate / adversarial

Multiple agents argue toward a better answer: proposer vs. critic, or N-way debate with a judge.

- The Multiagent Debate paper (factuality gains), ChatDev's communicative dehallucination, reviewer agents in MetaGPT.

**Watch out:** 2–3 rounds usually capture most of the gain; more rounds mostly burn tokens.

## Blackboard / shared-state

Agents read and write a shared workspace instead of messaging each other directly.

- MetaGPT's shared message pool, LangGraph's shared state + checkpointing, [memory layers](../README.md#coordination-memory--state) like Mem0/Graphiti/Redis Agent Memory as the blackboard.

**Watch out:** concurrent writes need conventions (namespaces, locks, or append-only logs) or agents will clobber each other's work.

## Human-in-the-loop

A human approves, corrects, or takes over at defined gates.

- Needs durable execution (the workflow must *wait* for days, not hold a socket open): Temporal, Restate, Trigger.dev, and Inngest all have first-class human-approval primitives. AutoGen's conversable agents support human proxies in the loop.

**Watch out:** put the gates where mistakes are expensive (spending money, sending messages, deleting data), not everywhere.

## A2A vs. MCP: which protocol?

They solve different problems and are frequently used together:

- **MCP (Model Context Protocol)** — agent ↔ tool/data. How an agent calls your APIs, databases, and services with a standard schema.
- **A2A (Agent2Agent Protocol)** — agent ↔ agent. How your agent discovers, delegates to, and receives results from *another organization's* agent.

Rule of thumb: MCP inside your trust boundary, A2A across it. See [protocols](../README.md#agent-to-agent-protocols--standards).
