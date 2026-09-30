# Choosing a multi-agent framework

A decision guide for picking from the [frameworks](../README.md#open-source-orchestration-frameworks), [platforms](../README.md#commercial--saas-multi-agent-platforms), and [cloud services](../README.md#cloud-multi-agent-services) in this directory. All facts below are as of September 2026; entries marked ⚠️ unverified in the README need a second look at the official source.

## First question: build, buy, or rent cloud?

- **You want to own the code and self-host** → start with the [open-source frameworks](../README.md#open-source-orchestration-frameworks). MIT/Apache-2.0 options: CrewAI, LangGraph, CAMEL, MetaGPT, OpenAI Agents SDK, Agno, Google ADK, AgentScope, PraisonAI, SmythOS SRE.
- **You want a managed product with a UI** → [SaaS platforms](../README.md#commercial--saas-multi-agent-platforms): CrewAI AMP, Relevance AI, Lindy, Gumloop, Dust, Beam AI, SmythOS, Flowise, Bardeen, LangSmith Deployment. Expect per-seat or per-run pricing and less control over the model layer.
- **You're already on a cloud and want the managed path** → [cloud services](../README.md#cloud-multi-agent-services): Bedrock multi-agent collaboration (AWS), Gemini Enterprise Agent Platform (Google Cloud), Microsoft Foundry workflows or Copilot Studio (Microsoft), Agentforce (Salesforce), watsonx Orchestrate (IBM).

## If you're building: which framework shape fits?

- **Role-based crews with sequential or hierarchical task flow** (research → write → review pipelines): CrewAI (Crews + Flows), PraisonAI.
- **Explicit state machines and graphs** (you want to see and control every transition, branch, and retry): LangGraph — pairs with LangGraph checkpointing and LangMem for shared state.
- **Conversation-first teams** (agents talk to each other in group chats, humans can jump in): AutoGen's AgentChat pattern — but note AutoGen is in **maintenance mode**; Microsoft directs new users to the Microsoft Agent Framework, and Magentic-One shows the orchestrator-led pattern that replaced it.
- **Role-play / SOP-driven collaboration** (software-team simulations, structured artifacts passed between specialists): MetaGPT (SOP-encoded roles, shared message pool), CAMEL (inception-prompted role-play), ChatDev-style chat chains.
- **Lightweight, model-agnostic agents with tool use** (OpenAI-centric but swappable): OpenAI Agents SDK (MIT, with a first-party Temporal integration), Agno, Google ADK (if you're deploying on Google's managed runtime).
- **.NET shop**: Semantic Kernel (Microsoft, MIT).

## Cross-cutting constraints

- **Durability matters more than you think.** Agent teams run long, call flaky tools, and need human-in-the-loop approvals that survive restarts. If your workflow is more than a demo, put it on [durable infrastructure](../README.md#workflow--orchestration-infrastructure): Temporal, Trigger.dev, DBOS, Restate, or Hatchet — not a bare script with sleeps.
- **Agents need shared memory.** Pick the [coordination layer](../README.md#coordination-memory--state) early: Mem0 or Graphiti for long-term memory, LangGraph checkpointing for resumable runs, AgentMail or a message bus for agent-to-agent messaging.
- **If agents cross trust boundaries** (yours talking to a partner's), you need a protocol, not just a framework: [A2A](../README.md#agent-to-agent-protocols--standards) for agent-to-agent delegation, MCP for agent-to-tool access.
- **License check before you commit:** Inngest (SSPL), Windmill (AGPL-3.0), n8n (fair-code), and Restate's runtime (BSL-1.1) are *not* OSI open source. Fine for SaaS use in most cases, but get legal to look if you're embedding or redistributing.

## Suggested shortlists

| Situation | Look at first |
|---|---|
| Startup, Python, ship this quarter | CrewAI or LangGraph + Temporal or Trigger.dev + Mem0 |
| Enterprise, Microsoft stack | Microsoft Foundry workflows or Copilot Studio; Semantic Kernel for .NET |
| Enterprise, AWS stack | Bedrock multi-agent collaboration (supervisor pattern) |
| Enterprise, Google Cloud | ADK + Gemini Enterprise Agent Platform |
| Research / novel collaboration patterns | CAMEL, MetaGPT, AgentScope + the [research papers](../README.md#research-papers--systems) |
| Cross-org agent delegation | A2A; MCP for tool access |
