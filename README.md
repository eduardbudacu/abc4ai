# The ABC Method for Agentic Software Development

---

## Abstract

Agentic AI systems can now generate working software, yet most frameworks treat the human as a reviewer bolted onto an automated pipeline rather than as a first-class participant in a designed collaboration. This paper introduces the **ABC method**, a lightweight socio-technical methodology for agentic software development structured around three actors — **A**lice (the engineer), **B**ob (the customer), and the **C**hatbot (the conversational interface to an agentic execution layer) — connected by six explicit conversational feedback loops: (1) inquiring dialogue, (2) requirements and constraints, (3) prompting, (4) clarifications, (5) artifacts and increments, and (6) acceptance and feedback. The method makes two claims. First, that the unit of progress in agentic development is not the code commit but the *conversational loop*, and that naming and instrumenting these six loops turns an ad-hoc chat with an AI tool into a repeatable engineering process. Second, that human roles remain differentiated and complementary: the engineer contributes system thinking, statistics and probability, and architecture and design, while the customer contributes domain knowledge, impact metrics, and intuition — neither is replaceable by the agentic layer. Beneath the conversational surface, the method assumes a layered runtime in which the chatbot orchestrates parallel agents (A₁…Aₙ), each capable of spawning subagents, executing on a shared operating system. The ABC method extends agile collaboration patterns such as the Three Amigos into the agentic era, replacing the tester's seat at the table with an orchestrated machine counterpart while preserving conversation as the primary medium of shared understanding.

---

## 1. The core idea

Agentic software development succeeds or fails on the quality of its **conversational feedback loops**, not on the raw capability of the underlying models. The ABC method structures development as a triadic conversation:

- **A — Alice**, the engineer
- **B — Bob**, the customer
- **C — Chatbot**, the conversational front-end of an agentic execution layer

Each edge of the triangle carries a specific, named kind of conversation. Making these loops explicit is what turns "chatting with an AI" into a method.

## 2. The six conversational feedback loops

| # | Loop | Direction | Content |
|---|------|-----------|---------|
| 1 | Inquiring dialogue | Alice → Bob | The engineer probes the problem space with open questions |
| 2 | Requirements & constraints | Bob → Alice | The customer articulates needs, boundaries, and non-negotiables |
| 3 | Prompt | Alice → Chatbot | The engineer translates shared understanding into precise instructions |
| 4 | Clarifications | Chatbot → Alice | The agentic system surfaces ambiguity back to the engineer before and during execution |
| 5 | Artifacts & increments | Chatbot → Bob | Working increments flow *directly* to the customer |
| 6 | Acceptance & feedback | Bob → Chatbot | The customer evaluates increments and feeds acceptance signals *directly* back into the agentic system |

Two structural choices are deliberate and distinctive:

**Loops 1–2 precede loops 3–4.** The human-to-human conversation is upstream of the human-to-machine conversation. Prompting (loop 3) is a *translation act*: it presupposes that inquiring dialogue and requirements elicitation have already produced shared understanding. Prompt quality is therefore a lagging indicator of conversation quality between Alice and Bob.

**Loops 5–6 bypass the engineer.** The customer receives increments from, and gives acceptance feedback to, the agentic system directly. The engineer is not a bottleneck in the delivery loop; she is the architect of the conversation itself. This shortens the acceptance cycle dramatically compared to traditional demo-at-sprint-review cadences, while keeping the engineer in control of loops 3–4 where technical judgment matters.

## 3. Complementary human competencies

The method asserts that both human roles remain essential and *differently skilled*:

| Engineer (Alice) | Customer (Bob) |
|---|---|
| System thinking | Domain knowledge |
| Statistics & probability | Impact metrics |
| Architecture & design | Intuition |

The engineer's column is notable for including **statistics and probability**: working with stochastic, non-deterministic generators requires reasoning about distributions of outputs, confidence, and failure rates — a competency traditional software methods rarely name. The customer's column pairs measurable **impact metrics** with **intuition**, acknowledging that acceptance in loop 6 is partly tacit and cannot be fully specified upfront.

## 4. The execution architecture

Beneath the conversational surface sits a layered runtime:

```
┌─────────────────────────────────┐
│            Chatbot              │  ← conversational interface / orchestrator
├─────────────────────────────────┤
│         Agentic Layer           │
│   A₁    A₂    …    Aₙ           │  ← parallel specialized agents
│   /|\                           │
│  subagents                      │  ← each agent may spawn subagents
├─────────────────────────────────┤
│        Operating System         │  ← shared execution substrate
└─────────────────────────────────┘
```

The chatbot is not the intelligence; it is the *membrane* between the human conversation and a hierarchy of orchestrated agents. Humans converse with one interface; the interface delegates to n agents; agents delegate to subagents. Loops 3–6 all pass through this membrane, which keeps the human-facing surface simple regardless of internal execution complexity.

## 5. Method summary

1. Alice and Bob converse (loops 1–2) until shared understanding is sufficient to act.
2. Alice translates understanding into prompts (loop 3); the system pushes ambiguity back (loop 4) rather than guessing.
3. The agentic layer decomposes work across agents and subagents and produces increments.
4. Increments flow directly to Bob (loop 5); Bob's acceptance and feedback flow directly back (loop 6).
5. Rejected or partially accepted increments re-enter the triangle: feedback may trigger new inquiring dialogue (loop 1) or refined prompts (loop 3).

The method is iterative by construction: every loop is a feedback loop, and the triangle has no terminal state other than sustained acceptance.

---

## 6. Supporting literature

### 6.1 Human-in-the-loop agentic development (supports loops 3–6)

- **Takerngsaksiri et al., "Human-In-the-Loop Software Development Agents" (HULA)**, arXiv:2411.12924. Atlassian/Monash framework deployed in Jira allowing engineers to refine and guide LLM agents when generating plans and code. Empirically validates that human guidance at each stage — rather than end-of-pipeline review — reduces development time and effort. Directly supports the ABC claim that iterative human refinement loops (3–4) outperform fire-and-forget automation. https://arxiv.org/pdf/2411.12924

- **"Agentic Software Engineering: Foundational Pillars and a Research Roadmap"**, arXiv:2509.06216. Proposes "Agentic Loop Engineering" with explicit human-in-the-loop control: mechanisms for a human coach to pause workflows, redirect branches, and add context without restarting. Independently converges on the ABC intuition that the *loops themselves* are the engineering object. https://arxiv.org/pdf/2509.06216

- **"iReDev: A Knowledge-Driven Multi-Agent Framework for Intelligent Requirements Development"**, arXiv:2507.13081. Weaves human confirmation into every artifact hand-off, forming a closed loop of "machine generation → human adjudication → machine correction" involving both engineers and clients — a two-human-role structure closely paralleling Alice/Bob, and direct support for loops 5–6. https://arxiv.org/pdf/2507.13081

### 6.2 Conversational requirements elicitation (supports loops 1–2)

- **"LLMREI: Automating Requirements Elicitation Interviews with LLMs"**, arXiv:2507.02564. Shows LLMs can conduct context-adaptive elicitation interviews, transitioning between probing and follow-up questions — evidence that "inquiring dialogue" (loop 1) is a distinct, studiable conversational skill, and that parts of it can be shared with the agentic layer. https://arxiv.org/html/2507.02564v1

- **"From Real-Time Conversation to User Story: Leveraging Agile Requirements through LLM"** (2025/2026). Conceptual framework generating high-quality user stories from live conversations with end users, with automated and manual validation to mitigate hallucination — supporting the ABC premise that conversation, not documentation, is the primary requirements medium. https://www.researchgate.net/publication/396391255

### 6.3 Agile collaboration triads (methodological lineage)

- **Three Amigos (George Dinwiddie, BDD tradition)**. The established agile practice of bringing business, development, and testing perspectives into a time-boxed conversation before development, producing shared understanding and acceptance criteria. The ABC method is a direct structural descendant: it preserves the triad and the conversational medium, but replaces the third human perspective with an orchestrated agentic system — and adds explicit typed loops where Three Amigos leaves the conversation unstructured. See e.g. https://www.alci.dev/en/que-es/three-amigos and https://www.techtarget.com/searchsoftwarequality/tip/How-to-hold-Three-Amigos-meetings-in-Agile-development

### 6.4 Layered agentic runtimes (supports §4)

- **Multi-agent orchestration architecture guides** (e.g., Augment Code, 2026). Document the now-consistent production pattern: an orchestrator layer for coordination and delegation, with subagents in scoped context windows — precisely the Chatbot → Agentic Layer → Subagents stack. https://www.augmentcode.com/guides/multi-agent-orchestration-architecture-guide

- **"Coordination as an Architectural Layer for LLM-Based Multi-Agent Systems"**, arXiv:2605.03310. Argues coordination should be a configurable architectural layer separable from agent logic, noting that most production multi-agent failures are coordination defects rather than model-capability defects — strong support for ABC's emphasis on structuring the interaction layer rather than relying on raw model capability. https://arxiv.org/pdf/2605.03310

- **Spring AI subagent pattern** (2026). Hierarchical agent architectures where an orchestrator delegates to specialized subagents in isolated context windows, mirroring the A₁…Aₙ + subagents sketch. https://spring.io/blog/2026/01/27/spring-ai-agentic-patterns-4-task-subagents/

### 6.5 What the ABC method adds beyond the literature

1. **A typed taxonomy of loops.** Existing HITL work says "keep the human in the loop"; ABC says *which* loops exist, who owns each, and in which direction each flows.
2. **The direct customer–agent channel (loops 5–6).** HULA and iReDev keep the engineer as intermediary for delivery; ABC deliberately routes increments and acceptance around the engineer.
3. **Named complementary competency sets**, including statistics & probability as a core engineering skill for stochastic systems and intuition as a legitimate acceptance input.
4. **Continuity with agile practice.** ABC is positioned as an evolution of Three Amigos rather than a replacement of agile — adoptable by existing teams as a conversational discipline, not a new toolchain.

---

*Document generated from original notebook sketch; diagram elements: Alice–Bob–Chatbot triangle with numbered loops ①–⑥, Eng/Cust competency columns, and the Agentic Layer / Subagents / Operating System stack.*
