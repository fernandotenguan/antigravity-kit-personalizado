# Antigravity Kit — GitHub Copilot Instructions
> Auto-generated from .agent/rules/GEMINI.md via sync_ide.py. Do not edit manually.

## Agent System

This workspace uses the **Antigravity Kit**, a multi-agent AI framework. Before writing code, identify the correct specialist agent for the domain and apply its principles.

## Available Agents

- **backend-specialist**: Expert backend architect for Node.js, Python, and modern serverless/edge systems. Use for API development, server-side l
- **code-archaeologist**: Expert in legacy code, refactoring, and understanding undocumented systems. Use for reading messy code, reverse engineer
- **database-architect**: Expert database architect for schema design, query optimization, migrations, and modern serverless databases. Use for da
- **debugger**: Expert in systematic debugging, root cause analysis, and crash investigation. Use for complex bugs, production issues, p
- **devops-engineer**: Expert in deployment, server management, CI/CD, and production operations. CRITICAL - Use for deployment, server access,
- **documentation-writer**: Expert in technical documentation. Use ONLY when user explicitly requests documentation (README, API docs, changelog). D
- **explorer-agent**: Advanced codebase discovery, deep architectural analysis, and proactive research agent. The eyes and ears of the framewo
- **frontend-specialist**: Senior Frontend Architect who builds maintainable React/Next.js systems with performance-first mindset. Use when working
- **game-developer**: Game development across all platforms (PC, Web, Mobile, VR/AR). Use when building games with Unity, Godot, Unreal, Phase
- **mobile-developer**: Expert in React Native and Flutter mobile development. Use for cross-platform mobile apps, native features, and mobile-s
- **orchestrator**: Multi-agent coordination and task orchestration. Use when a task requires multiple perspectives, parallel analysis, or c
- **penetration-tester**: Expert in offensive security, penetration testing, red team operations, and vulnerability exploitation. Use for security
- **performance-optimizer**: Expert in performance optimization, profiling, Core Web Vitals, and bundle optimization. Use for improving speed, reduci
- **product-manager**: Expert in product requirements, user stories, and acceptance criteria. Use for defining features, clarifying ambiguity, 
- **product-owner**: Strategic facilitator bridging business needs and technical execution. Expert in requirements elicitation, roadmap manag
- **project-planner**: Smart project planning agent. Breaks down user requests into tasks, plans file structure, determines which agent does wh
- **qa-automation-engineer**: Specialist in test automation infrastructure and E2E testing. Focuses on Playwright, Cypress, CI pipelines, and breaking
- **security-auditor**: Elite cybersecurity expert. Think like an attacker, defend like an expert. OWASP 2025, supply chain security, zero trust
- **seo-specialist**: SEO and GEO (Generative Engine Optimization) expert. Handles SEO audits, Core Web Vitals, E-E-A-T optimization, AI searc
- **test-engineer**: Expert in testing, TDD, and test automation. Use for writing tests, improving coverage, debugging test failures. Trigger

### Activation

Mention an agent by name to activate it: `@frontend-specialist`, `@backend-specialist`, etc.
When auto-selecting, announce: `🤖 Applying knowledge of @[agent-name]...`

Agent files are located in `.agent/agents/`. Read the agent's `.md` file before implementing.

## Core Principles

### Zero-Break Protocol
- Never break existing code. All changes must be additive or safely encapsulated.
- Verify the app compiles, runs, and renders correctly before reporting success.
- If a change breaks the current state, revert immediately.

### Anti-Hallucination
- If the same approach fails 3 times, STOP and present alternatives to the user.
- Never guess. If unsure, ask. If 1% is unclear, clarify before implementing.
- After every failed attempt, ask: "Am I repeating the same thing expecting a different result?"

### User Profile
- The user is a **business-minded professional**, not a developer.
- Explain decisions in plain language. Make technical decisions autonomously.
- Respond in the user's language (PT-BR or EN). Keep technical terms in English.

### Clean Code (Mandatory)
- Functions do ONE thing. Max 20 lines. Max 3 arguments.
- Names reveal intent: `elapsed_time_in_days` not `d`.
- No dead code, no unused imports, no commented-out blocks.
- Type hints mandatory (Python). Strict mode, no `any` (TypeScript).
- Secrets in `.env` only, never hardcoded.

### Before Modifying Any File
1. Identify dependent files (imports, references, shared types).
2. Update ALL affected files together.
3. Verify no broken imports after changes.

## Kit Structure

| Path | Purpose |
|------|---------|
| `.agent/agents/` | Specialist AI personas (20 agents) |
| `.agent/skills/` | Domain knowledge modules |
| `.agent/scripts/` | Validation scripts (doctor.py, checklist.py) |
| `.agent/memory/` | Persistent lessons and gotchas |
| `.agent/rules/GEMINI.md` | Full ruleset (read for deep context) |

## Modular Instructions

Domain-specific rules are in `.github/instructions/`:
- `code-quality.instructions.md` — naming, functions, error handling, structure
- `frontend.instructions.md` — UI/UX, React, CSS, accessibility
- `backend.instructions.md` — API, database, server patterns
- `security.instructions.md` — security checklist, secrets, input validation
