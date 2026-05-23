# Curriculum Bible — Agentic AI: From Zero to Frontier

## Voice & Tone
- Direct, confident, practitioner-to-practitioner
- Mixed technical/non-technical audience: never condescending, never hand-wavy
- "Here's what actually happens, here's why it matters, here's what breaks"
- No hype. Name the limitations honestly. Credibility comes from calling out what doesn't work.
- Short sentences preferred. Use analogies to de-abstract concepts, but always ground them back in the technical reality.
- Second person ("you") for exercises; first-person plural ("we") for narrative explanation.

## Core Vocabulary (use these exact terms, consistently)

| Term | Definition (use exactly this framing) |
|------|---------------------------------------|
| **agent** | A system that perceives its environment, reasons about a goal, takes actions via tools, and uses the results to decide what to do next. The loop is the thing. |
| **agentic loop** | The core execution cycle: Perceive → Reason → Act → Observe → (repeat until goal met or stop condition) |
| **tool** | Any capability an agent can invoke that has a real-world effect or returns information from outside the model: web search, code execution, database read/write, API calls, file I/O |
| **orchestrator** | An agent whose job is to decompose tasks, delegate to subagents, and synthesize results. Doesn't execute leaf tasks itself. |
| **subagent** | An agent that receives a scoped task from an orchestrator and executes it. May use tools; may not spawn further agents. |
| **context window** | The finite "working memory" of the model — everything the model sees at inference time. The primary resource to be managed. |
| **context engineering** | The practice of deciding what goes into the context window: what to include, what to compress, what to retrieve, what to discard. |
| **guardrail** | A control layer — upstream or downstream of the model — that constrains or filters agent behavior. |
| **HITL** | Human-in-the-loop: a design pattern where certain decisions or actions require human approval before execution. |
| **MCP** | Model Context Protocol — Anthropic's open standard for agent-to-tool communication. |
| **A2A** | Agent-to-Agent protocol — Google's open standard for agent-to-agent communication and interoperability. |
| **eval** | An evaluation: a structured test that measures agent quality on a defined task with defined success criteria. |
| **ReAct** | Reason + Act — the foundational agent loop pattern where the model alternates between reasoning steps and tool calls. |

## Running Examples (thread these through all modules)

### Example A: "Aria" — the customer success agent
- Used in: M1 (what makes it an agent), M2 (tool design), M3 (context engineering), M5 (guardrails, HITL), M6 (framework choice)
- Setup: Aria handles inbound customer support tickets. She can read CRM data, query order history, issue refunds (up to $50), escalate to human agents, and send emails.
- What makes her interesting: the $50 refund limit and escalation logic are perfect for teaching HITL, guardrails, and scope limits.

### Example B: "COMPASS" — the competitive intelligence agent network
- Used in: M2 (orchestrator pattern), M3 (RAG), M4 (multi-agent), M6 (framework comparison), M7 (frontier patterns)
- Setup: A 3-agent system — a Planner that decomposes research questions, Researcher agents that fetch and summarize sources, a Synthesizer that writes the final brief.
- What makes it interesting: teaches parallelism, state management, and why multi-agent adds complexity before it adds value.

## Module Dependency Contract

Each module can assume learners have internalized:

| Module | Can assume from prior |
|--------|-----------------------|
| M1 | Nothing — builds from scratch |
| M2 | M1: definition of "agent", the four pillars (Perceive/Reason/Act/Learn), the spectrum from pipeline to agent |
| M3 | M1+M2: what a tool is, what the ReAct loop looks like, what a context window is |
| M4 | M1+M2+M3: single-agent architecture, context management, tool design, RAG basics |
| M5 | M1-M4: full agent and multi-agent architecture, MCP, orchestration patterns |
| M6 | M1-M5: everything; this module applies all prior knowledge to framework selection |
| M7 | M1-M6: full curriculum; this is synthesis + meta-skill |

## HTML Template Structure

Each module-0X.html file should follow this structure:
1. `<head>` — same fonts and CSS variables as overview, plus module-specific styles
2. Hero section: module number, title, badge, back link to overview
3. Module description (expanded from the overview blurb — 2-3 paragraphs)
4. For each topic in the module:
   - Topic header (h2 or h3)
   - 3-6 paragraphs of explanation
   - At least one concrete example (reference Aria or COMPASS where applicable)
   - Where relevant: a callout box for "common mistake" or "key insight"
   - Code snippet if the topic has implementation content
5. Hands-on exercise (expanded from the lab block)
6. Module summary / "what you should now be able to do"
7. "Next: Module X →" link footer

## Design Conventions
- Same CSS variables as overview: --bg, --surface, --surface2, --border, --accent, --accent2, --accent3, --text, --muted, --danger
- Same fonts: Syne (headings), DM Sans (body), IBM Plex Mono (labels/code/meta)
- Dark theme throughout
- Code blocks: IBM Plex Mono, surface2 background, accent-colored border-left
- Callout boxes for "Key Insight", "Common Mistake", "Real-World Example"
- Module badge color matches the tier: foundation=muted, core=accent(purple), advanced=accent2(gold), frontier=accent3(teal)
- Navigation: sticky top bar with "← Back to Curriculum" + sibling module links
- Target length per module: enough to genuinely teach the topic. Estimate 2,000–4,000 words of body text per module, more for heavier modules (M2, M4, M5).

## Cross-Module Callbacks
- When M2 introduces the ReAct loop, it should say "this is the loop Aria runs"
- When M3 talks about context pruning, reference the COMPASS Synthesizer's challenge
- When M4 introduces orchestrator/subagent, name COMPASS explicitly as the example
- When M5 introduces the $50 refund limit, call back to Aria from M1/M2
- M6 should ask: "which framework would you use for Aria? For COMPASS? Why?"
- M7 should reference both as "systems you can now evaluate new frameworks against"
