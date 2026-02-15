# 🤖 Project Bootstrap — The AI Agent Operating System for Software Projects

> **Ship entire projects, not just prompts.**
>
> A battle-tested instruction framework that turns AI coding agents into disciplined software engineers — complete with project management, quality gates, sub-agent delegation, and session continuity.

---

## The Problem

You've seen it before. You paste a prompt into an AI coding agent, it starts strong, builds half a feature, then the session ends. The next session? It has no memory of what happened. It re-invents decisions, overwrites working code, or simply starts from scratch. By the third session, you're debugging the debugger.

AI coding agents are powerful — but **without structure, they're chaotic.** They lack:

- **Memory** across sessions
- **Project management** discipline
- A clear **definition of done**
- **Quality assurance** separation (the same agent writes AND verifies code)
- A way to **hand off** cleanly when context windows fill up
- Guardrails against **repeating the same mistakes**

**Project Bootstrap** solves all of this.

It's a single `AGENT.md` file — a comprehensive instruction set that transforms any AI coding agent into a structured, self-managing software engineering team. Think of it as an operating system for AI-driven development.

---

## What It Does

At its core, Project Bootstrap is an **agent instruction framework** that enforces a phased, disciplined approach to building software. Drop the `AGENT.md` file into any project, point your AI agent at it, and it will:

### 📋 Gather Requirements Before Writing Code
No more "just start coding." The agent conducts a proper requirements gathering session, asks clarifying questions, and produces a formal specification document — complete with MoSCoW prioritization, data models, and non-functional requirements.

### 🏗️ Plan Before Building
The agent proposes a tech stack, defines the project structure, documents architecture decisions, establishes coding conventions, and creates a risk register. Every decision is logged. Nothing is left to vibes.

### 📦 Break Work Into Trackable Tasks
Features are decomposed into small, verifiable tasks grouped into milestones. Each task has a unique ID (`M2-T3`), a clear verification method, and a definition of done. The first milestone is always environment setup — because a project that doesn't run is a project that doesn't ship.

### 🔄 Implement One Task at a Time
During implementation, the agent follows a strict loop: pick a task → implement → test → commit → update progress → repeat. No batch implementations. No half-finished features. Every commit is atomic and tagged with its task ID.

### 🧪 Enforce Quality Through Sub-Agents
Here's where it gets interesting. The framework introduces **specialist sub-agents** — separate AI personas for testing, code review, security auditing, documentation, and DevOps. The agent that writes the code is **never** the sole verifier. This separation of concerns catches bugs that self-review misses.

### 🧠 Remember Everything Across Sessions
A suite of living documents (`progress.md`, `decisions.md`, `lessons.md`, `risks.md`) ensures that every session picks up exactly where the last one left off. Failed approaches are recorded so they're never repeated. Decisions are logged so they're never re-litigated.

### 🏁 Close Projects Properly
When all milestones are complete, the agent runs a final review checklist: full test suite, security audit, code review, documentation completeness, production hardening, and deployment. No loose ends.

---

## How It Works — The Five Phases

Project Bootstrap guides the agent through five sequential phases, with explicit user approval gates between each one.

```
Phase 0          Phase 1          Phase 2          Phase 3          Phase 4          Phase 5
Orientation  →  Requirements  →  Planning  →  Backlog  →  Implementation  →  Closure
   │               │               │            │              │               │
   │  Read docs,   │  Gather       │  Tech      │  Break into  │  Build, test,  │  Final review,
   │  detect env,  │  requirements,│  stack,    │  tasks &     │  commit, demo  │  deploy,
   │  resume if    │  produce      │  arch,     │  milestones  │  per milestone │  handoff
   │  continuing   │  spec.md      │  plan.md   │  backlog.md  │               │
   │               │               │            │              │               │
   └── auto ──────►└── 🚫 gate ──►└── 🚫 ────►└── 🚫 ──────►└── 🚫 ────────►└── done
```

### Phase 0 — Orientation

The agent reads everything first. If resuming a previous session, it checks `docs/progress.md` and picks up where the last agent left off. If starting fresh, it scans for existing code, detects the tech stack, and asks about any design assets or reference materials you have.

### Phase 1 — Requirements Gathering

No assumptions. The agent asks you about your project goals, target users, core features, integrations, and constraints. It uses MoSCoW prioritization (Must Have, Should Have, Could Have, Won't Have) to structure the spec. The output is a formal `docs/spec.md` that serves as the source of truth.

### Phase 2 — Implementation Planning

With an approved spec in hand, the agent proposes the tech stack, project structure, architecture pattern, and testing strategy. It creates `docs/plan.md`, `docs/conventions.md` (coding standards), and `docs/risks.md` (a risk register with mitigations). Every significant choice is surfaced to you for approval.

### Phase 3 — Backlog Creation

The plan is broken into granular, independently verifiable tasks. Each task is sized to fit within a single agent session. Tasks are grouped into milestones, and Milestone 1 is always "Project Setup & Foundation" — ensuring the project is runnable, testable, and linted before any features are built.

### Phase 4 — Implementation

The core loop. One task at a time. The agent implements, delegates verification to a Tester sub-agent, commits with a structured message, and updates progress. At the end of each milestone, the agent demos what was built and collects your feedback before moving on.

### Phase 5 — Closure & Deployment

A comprehensive checklist: all tests pass, linting is clean, security audit is done, documentation is complete, no hardcoded secrets remain, and the app is deployed and verified in production.

---

## The Sub-Agent System

One of the most powerful ideas in Project Bootstrap is **role-based sub-agent delegation**. Instead of one agent doing everything (and checking its own homework), the framework defines seven specialist roles:

| Role | Responsibility | When Triggered |
|------|---------------|----------------|
| 🏗️ **Architect** | Design decisions, schema design, API contracts | Complex design tasks |
| 💻 **Implementer** | Focused code implementation | Complex feature tasks |
| 🧪 **Tester** | Write & run tests, report failures | **After every task** (mandatory) |
| 🔍 **Code Reviewer** | Review code for quality, patterns, bugs | After each milestone |
| 🔒 **Security Auditor** | Audit for vulnerabilities | Auth, payments, data handling |
| 📖 **Documentation Writer** | README, API docs, user guides | After milestones |
| ⚙️ **DevOps** | CI/CD, Docker, deployment configs | Infrastructure tasks |

The key insight: **the agent that writes code should never be the only one that verifies it.** The Tester sub-agent is mandatory after every single task — it writes tests independently based on the spec, not just confirming the implementation "works."

Each sub-agent receives only the context it needs (scoped files, relevant conventions, applicable lessons learned) and reports back to the Orchestrator, which integrates the results and decides next steps.

> **No native sub-agent support?** No problem. The framework includes instructions for simulating sub-agents by explicitly switching roles, maintaining separation between writing and testing.

---

## Session Continuity — The Memory Problem, Solved

AI agents forget everything between sessions. Project Bootstrap solves this with a structured document system that acts as **persistent memory**:

| Document | What It Remembers |
|----------|-------------------|
| `docs/progress.md` | Where we are, what's done, what's next, session log |
| `docs/decisions.md` | Every choice made and why — prevents re-litigation |
| `docs/lessons.md` | Every failed approach — prevents repeating mistakes |
| `docs/risks.md` | Known risks, their status, and mitigations |
| `docs/backlog.md` | The full task list with completion status |
| `docs/spec.md` | The approved requirements — the source of truth |
| `docs/plan.md` | Architecture, tech stack, and conventions |
| `CHANGELOG.md` | User-facing summary of what was built |

When a new session starts, the **first thing** the agent does is read all of these documents. It knows what was built, what failed, what decisions were made, and exactly where to resume.

The **Session Handoff Protocol** ensures clean transitions: finish or revert any in-progress work, update all documents, and provide a clear summary for the next agent.

---

## Built-In Quality Standards

Project Bootstrap doesn't just manage tasks — it enforces a baseline of code quality that applies to every project:

### Code Quality
- Small, focused functions. Meaningful names. No dead code.
- Proper error handling — never silently swallowed.
- Input validation at every boundary using schema libraries.
- Security basics: no hardcoded secrets, parameterized queries, output sanitization.
- Performance awareness: pagination, caching, no N+1 queries.

### UI/UX Quality
- Responsive by default (mobile, tablet, desktop).
- Semantic HTML and WCAG AA accessibility.
- All four UI states handled: loading, success, error, empty.
- Consistent typography, spacing, and navigation patterns.

### API Quality
- RESTful conventions with consistent error response formats.
- Pagination on all list endpoints.
- Appropriate HTTP methods and status codes.

These aren't opinions about tooling — they're **universal minimums** that prevent the most common quality failures.

---

## The Safety Net

Things go wrong during implementation. Project Bootstrap has protocols for that too:

### Rollback Protocol
If a task breaks existing functionality: stop, revert to the last working state, analyze the root cause, record the lesson, and only then re-attempt with a corrected approach.

### Debugging Protocol
A structured six-step process: Reproduce → Isolate → Hypothesize → Verify → Fix → Confirm. No shotgun debugging. No rewriting large sections and hoping.

### Context Budget Awareness
The agent monitors its own context window usage. If it's running low, it starts the handoff protocol early rather than rushing to a broken finish. Better to hand off cleanly after five tasks than get cut off mid-task on the sixth.

### Lessons Learned Database
Every rollback, every surprising behavior, every wrong approach gets documented with tags. Before starting any task, the agent checks for relevant lessons. The goal: **no mistake is ever made twice.**

---

## Getting Started

### Prerequisites

- An AI coding agent that accepts custom instructions (GitHub Copilot, Cursor, Cline, Windsurf, Aider, etc.)
- A project idea

### Usage

1. **Copy `AGENT.md` into your project root**

   ```
   your-project/
   ├── AGENT.md      ← drop it here
   └── (your code)
   ```

2. **Point your AI agent at it**

   In your agent's system prompt or instructions, tell it:
   > Read and follow the instructions in `AGENT.md` before doing anything else.

   Or, if your platform supports custom instruction files (like `.cursorrules`, `.github/copilot-instructions.md`, etc.), reference or include `AGENT.md` in that configuration.

3. **Start a conversation**

   Tell your agent what you want to build. It will walk you through the phases — gathering requirements, planning, creating a backlog, and then building task by task.

4. **Approve at each gate**

   The agent will pause at phase boundaries and milestone demos to get your approval. You stay in control of direction; the agent handles execution.

5. **Resume anytime**

   If your session ends, start a new one. The agent reads `docs/progress.md` and picks up exactly where it left off. No context loss. No starting over.

### Approval Modes

At the start of every project, the agent asks which level of oversight you want:

| Mode | You approve... | Best for |
|------|---------------|----------|
| 🔒 **Strict** | Every single task | Learning, critical projects |
| 🔓 **Milestone** | At milestone boundaries | Most projects (default) |
| 🚀 **Auto** | Only when decisions are needed | Experienced users, well-defined specs |

---

## Document Map

Here's the complete set of documents the framework creates and maintains:

```
your-project/
├── AGENT.md              ← The instruction framework (this file)
├── CHANGELOG.md          ← User-facing history of what was built
└── docs/
    ├── spec.md           ← Project requirements & specification
    ├── plan.md           ← Tech stack, architecture, project structure
    ├── conventions.md    ← Code style, naming, patterns
    ├── risks.md          ← Risk register with mitigations
    ├── backlog.md        ← Task backlog grouped by milestone
    ├── progress.md       ← Progress tracker & session log
    ├── decisions.md      ← Decision log for all choices
    └── lessons.md        ← Pitfalls and failed approaches
```

---

## Design Principles

The framework is built on a few core beliefs:

1. **Structure beats talent.** A mediocre agent with great process outperforms a brilliant agent winging it.

2. **The writer shouldn't grade their own test.** Separating implementation from verification catches real bugs, not just the ones you expect.

3. **Memory is infrastructure.** Without persistent context, every session is a cold start. The document system is the agent's long-term memory.

4. **Small batches, always.** One task at a time. One commit per task. Atomic progress that's easy to verify and easy to roll back.

5. **Fail forward.** Every failure becomes a lesson. Every lesson prevents a future failure. The system gets smarter over time.

6. **Humans decide, agents execute.** The framework keeps the user in the loop at every meaningful decision point while automating the execution.

---

## FAQ

### Does this work with [my AI agent]?

If your agent can read a markdown file and follow instructions, yes. The framework is **agent-agnostic** — it works with GitHub Copilot (agent mode), Cursor, Cline, Windsurf, Aider, and any other AI coding assistant that supports custom instructions.

### Is this only for new projects?

No. Phase 0 includes auto-detection of existing codebases — the agent scans for manifest files, config files, test setups, and existing conventions. It adapts to what's already there rather than imposing new patterns.

### What if my agent doesn't support sub-agents?

The framework includes a fallback: simulate sub-agent behavior by explicitly switching roles. The agent finishes all implementation, then switches to "Tester mode" with a fresh perspective. It's not as robust as true delegation, but it's significantly better than no separation at all.

### Can I customize the phases?

Absolutely. The `AGENT.md` file is plain markdown — edit it to match your workflow. Skip phases, add phases, change the quality gates, adjust the document templates. It's your operating system; configure it how you like.

### How does this handle long projects?

Through session continuity. The `docs/progress.md` file and Session Handoff Protocol ensure that sessions chain together seamlessly. The lessons learned database means the project gets smarter over time. There's no practical limit to project duration.

### What about the Definition of Done?

Every task must satisfy a checklist before it's marked complete: code implemented, tests passing, no linter errors, edge cases handled, existing tests still green, progress updated, changelog updated, and any failed approaches documented. No shortcuts.

---

## Rules at a Glance

| Rule | Why It Matters |
|------|---------------|
| 🚫 No skipping phases | Structure prevents chaos |
| ☝️ One task at a time | Atomic progress, clean rollbacks |
| 🧪 Separate write from test | Catches real bugs |
| 🔄 Always update progress | Session continuity |
| ❓ Ask, don't assume | User stays in control |
| ⏪ Rollback, don't pile on | Clean state over spaghetti fixes |
| 🚧 Record every failure | No mistake made twice |
| 🏗️ Environment first | Runnable project before features |
| 🔀 Commit after every task | Git as safety net |
| 🎯 Demo at milestones | Course-correct early, not late |
| ⏳ Watch your context | Clean handoff over rushed finish |
| 📦 Evaluate dependencies | No bloat, no risk |

---

## Contributing

Found a gap in the framework? Have an improvement? The `AGENT.md` file is a living document — fork it, adapt it, and share what works.

---

## License

This project is open source. Use it, modify it, share it — just build something great with it.

---

<p align="center">
  <strong>Stop prompting. Start shipping.</strong>
  <br>
  Drop <code>AGENT.md</code> into your project and let the agent do the rest.
</p>
