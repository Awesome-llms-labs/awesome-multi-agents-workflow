# Glossary

The working vocabulary of multi-agent systems, as used in this directory.

- **Agent** — an LLM-powered software entity that perceives, reasons, and acts through tools toward a goal.
- **Orchestrator / supervisor** — the agent (or component) that plans, decomposes tasks, and delegates to worker agents. See [orchestration patterns](orchestration-patterns.md).
- **Worker / specialist agent** — an agent with a narrow role and toolset, directed by an orchestrator or a pipeline.
- **Crew** — CrewAI's term for a team of role-based agents collaborating on a task.
- **Swarm** — a decentralized multi-agent pattern with no central coordinator; agents coordinate through broadcast, negotiation, or stigmergy.
- **Handoff** — transferring control (and conversation context) from one agent to another, e.g. OpenAI Agents SDK handoffs.
- **A2A** — Agent2Agent Protocol: the Linux Foundation standard for agent-to-agent discovery, delegation, and messaging (v1.0.0, March 2026).
- **MCP** — Model Context Protocol: the standard for agent-to-tool/data connections. Complementary to A2A, not a competitor.
- **ACP** — IBM/BeeAI's Agent Communication Protocol; merged into A2A (Aug 2025). Legacy — build on A2A.
- **Durable execution** — workflow infrastructure (Temporal, Restate, Trigger.dev, DBOS, Inngest) that persists workflow state so long-running agent runs survive restarts, retries, and human-approval waits.
- **Checkpointing** — persisting an agent run's state at intervals so it can resume after failure; e.g. LangGraph checkpointing.
- **Blackboard** — a shared workspace (message pool, shared state, memory store) that agents read from and write to instead of messaging each other directly.
- **Inception prompting** — CAMEL's technique: two agents are given complementary role prompts ("AI user" / "AI assistant") so they autonomously cooperate without further instruction.
- **SOP agents** — MetaGPT's approach: human Standard Operating Procedures encoded as agent roles that exchange structured artifacts.
- **Role-play** — agents assigned personas/roles (CEO, programmer, reviewer) whose interactions produce collaborative behavior.
- **Multiagent debate** — a pattern where several agent instances propose, critique, and converge on an answer to improve factuality and reasoning.
- **Emergent behavior** — group-level behavior (cooperation, norms, deception) that arises from agent interactions and wasn't explicitly programmed; studied in Generative Agents, AgentVerse, SOTopia.
- **Human-in-the-loop (HITL)** — defined gates where a human approves or intervenes before the workflow continues.
- **Agent Card** — A2A's discovery document describing what an agent can do (compare ACP's Agent Manifest).
- **Trajectory** — the recorded sequence of an agent's thoughts, tool calls, and observations; used for debugging and evals.
- **FIPA-ACL / KQML** — the 1990s agent communication languages (speech-act performatives); historically important, superseded in practice.
