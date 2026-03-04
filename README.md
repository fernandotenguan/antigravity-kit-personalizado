# Antigravity Kit — Personalized by FernandoTenguan

> A production-grade AI agent framework for building software with professional quality —
> without needing to know how to code.

[![Kit Version](https://img.shields.io/badge/Kit-v2.0.0-blue)](https://github.com/fernandotenguan/antigravity-kit-personalizado)
[![Agents](https://img.shields.io/badge/Agents-20-green)](https://github.com/fernandotenguan/antigravity-kit-personalizado)
[![Skills](https://img.shields.io/badge/Skills-47-orange)](https://github.com/fernandotenguan/antigravity-kit-personalizado)
[![Tests](https://img.shields.io/badge/Tests-Automated-brightgreen)](https://github.com/fernandotenguan/antigravity-kit-personalizado)

---

## What's Included

| Component         | Count | Description                                                        |
| ----------------- | ----- | ------------------------------------------------------------------ |
| **Agents**        | 20    | Specialist AI personas (frontend, backend, security, game dev, etc.) |
| **Skills**        | 47    | Domain-specific knowledge modules with automated scripts           |
| **Workflows**     | 13    | Slash-command procedures including the autonomous `/ade` pipeline  |
| **Master Scripts**| 4     | `doctor.py`, `checklist.py`, `verify_all.py`, `sync_ide.py`        |
| **Kit Tests**     | ✅     | Automated pytest suite — runs before every commit                  |
| **Memory Layer**  | ✅     | Persistent lessons and gotchas across sessions                     |

---

## Features

### 🤖 Intelligent Auto-Routing
Describe what you need in plain English. The kit detects the domain and applies the right specialist automatically — no commands required.

```
You: "The login button is not working"       → @debugger
You: "Make the UI look more modern"           → @frontend-specialist
You: "Is the app safe to deploy?"             → @security-auditor
You: "check kit" / "diagnose"                 → Health check (doctor.py)
```

### 🚀 Autonomous Development Pipeline (`/ade`)
The most powerful mode. You describe a feature, the kit plans it, shows you the spec, and waits for approval before writing any code.

```
/ade add email notification system
/ade create a sales dashboard with charts
/ade implement Google OAuth login
```

**6-phase pipeline:** Discovery → Spec → ✋ Your Approval → Code → QA → Memory

### 🏥 Kit Health Diagnostics
```bash
python .agent/scripts/doctor.py
```
Validates all 20 agents, 47 skills, 13 workflows, and master scripts in seconds.

### 🔒 Automated Pre-Commit Guard
Tests run automatically before every `git commit`. If anything breaks, the commit is blocked until fixed.

### 🧠 Persistent Memory Layer
The kit remembers patterns and lessons learned across sessions, stored in `.agent/memory/`.

### 🔄 Multi-IDE Sync
Export the kit configuration to Claude Code, Cursor, and Codex CLI:
```bash
python .agent/scripts/sync_ide.py --target all
```

## 🚀 Como Iniciar um Novo Projeto (Sua Fábrica)

Este repositório é seu **Cérebro de Desenvolvimento**. Para criar um novo projeto (ex: Lotofácil, E-commerce, App Mobile) usando esta inteligência:

1.  **Crie sua nova pasta** no computador.
2.  **No chat do seu agente**, digite: 
    ```
    /new-project
    ```
3.  O agente vai te guiar na cópia do `.agent/` (a "alma" do kit) e na configuração inicial da sua nova aplicação.

---

## 📜 Regras de Manutenção
Se você é um desenvolvedor ou quer que o agente atualize este kit base (fork), ele deve SEMPRE seguir as:
[Regras de Manutenção e Evolução (KIT_MASTER_RULES.md)](file:///c:/Users/ferna/Desktop/IA%20Project/antigravity-kit-personalizado/KIT_MASTER_RULES.md)

---

## What's Included

> **Requirements:** Python 3.9+ and Git

### Option 1 — NPX (Recommended, fastest)

Copy only the `.agent` folder into your existing project:

```bash
npx giget@latest github:fernandotenguan/antigravity-kit-personalizado/.agent .agent --force
```

Then install the pre-commit hook so tests run automatically:

```bash
python .agent/scripts/install_hooks.py
```

### Option 2 — Git Clone

Clone the full repository and copy `.agent` into your project:

```bash
git clone https://github.com/fernandotenguan/antigravity-kit-personalizado.git
cd antigravity-kit-personalizado
# Copy .agent/ into your own project:
xcopy .agent "C:\path\to\your-project\.agent" /E /I    # Windows
# cp -r .agent /path/to/your-project/                  # Linux/macOS
```

### Verify Installation

```bash
python .agent/scripts/doctor.py
```

Expected output: `✅ All checks passed! Kit is healthy.`

---

## Setup in VSCode (with GitHub Copilot or Gemini Code Assist)

The kit works with any AI assistant in VSCode that can read workspace files. Here's how to get the best experience:

### Step 1 — Open the Project in VSCode

```bash
code .
```

Make sure your project has the `.agent/` folder at the root level.

### Step 2 — Configure the AI to Read the Kit

The kit's rules are stored in `.agent/rules/GEMINI.md`. For the AI to follow them automatically:

**For GitHub Copilot (VSCode):**

1. Open the Command Palette: `Ctrl+Shift+P` (Win) or `Cmd+Shift+P` (Mac)
2. Search for: `GitHub Copilot: Open Chat`
3. At the start of a session, type:
   ```
   Read and apply the rules in .agent/rules/GEMINI.md
   ```

**For Gemini Code Assist (VSCode):**

The `GEMINI.md` rules are loaded automatically if the file is present in the workspace.

**For Cursor:**

Run the sync script to generate Cursor-specific rules:
```bash
python .agent/scripts/sync_ide.py --target cursor
```
This creates `.cursor/rules.md` with the full kit configuration.

**For Claude Code:**
```bash
python .agent/scripts/sync_ide.py --target claude
```
This creates `.claude/CLAUDE.md`.

### Step 3 — Install Recommended VSCode Extensions

For the best development experience:

| Extension | Purpose |
|-----------|---------|
| `esbenp.prettier-vscode` | Code formatting |
| `dbaeumer.vscode-eslint` | Linting |
| `ms-python.python` | Run `.agent/scripts/*.py` directly |
| `ms-vscode.vscode-github-copilot` | AI coding assistant |
| `github.copilot-chat` | Chat interface for agent commands |

### Step 4 — Run the Kit Health Check from VSCode

1. Open the integrated terminal: `` Ctrl+` ``
2. Run:
```bash
python .agent/scripts/doctor.py
```

### Step 5 — Using Slash Commands in VSCode Chat

In the Copilot chat panel, type any slash command:

```
/ade add a dark mode toggle to the app
/debug why does the form not submit
/build-saas subscription platform for freelancers
```

---

## Slash Commands Reference

| Command          | Purpose                                            |
| ---------------- | -------------------------------------------------- |
| `/ade`           | **Autonomous pipeline** — full feature end-to-end  |
| `/build-saas`    | Plan a complete SaaS in 7 guided steps             |
| `/plan`          | Create a detailed plan without writing code yet    |
| `/create`        | Scaffold a new feature or application              |
| `/brainstorm`    | Explore options with strategic questions           |
| `/enhance`       | Improve an existing feature                        |
| `/debug`         | Systematic bug investigation                       |
| `/test`          | Generate and run tests                             |
| `/deploy`        | Pre-flight checks + guided deployment              |
| `/preview`       | Start local dev server                             |
| `/status`        | Check project progress                             |
| `/ui-ux-pro-max` | Premium UI/UX design in 50 styles                 |
| `/orchestrate`   | Coordinate multiple agents for complex tasks        |

---

## Validation & Quality Scripts

```bash
# Kit health check (run first, always)
python .agent/scripts/doctor.py

# Run automated kit integrity tests
python -m pytest .agent/tests/test_kit_integrity.py -v

# Full project audit (security, lint, UX, SEO)
python .agent/scripts/checklist.py .

# Full verification before deployment
python .agent/scripts/verify_all.py . --url http://localhost:3000

# Sync kit to other IDEs
python .agent/scripts/sync_ide.py --target all
```

---

## How It Works

```
User request
    │
    ▼
[GEMINI.md Rules]         ← P0: global rules, anti-hallucination, clean code
    │
    ▼
[Intelligent Routing]     ← auto-detects domain from request
    │
    ▼
[Agent Selected]          ← @frontend-specialist, @debugger, @security-auditor...
    │
    ▼
[Skills Loaded]           ← domain knowledge specific to the task
    │
    ▼
[Output + Verification]   ← zero-break protocol, tests run
    │
    ▼
[Memory Updated]          ← lessons.md + gotchas.md
```

---

## Project Structure

```
project-root/
├── .agent/
│   ├── agents/          # 20 specialist AI personas
│   ├── skills/          # 47 knowledge modules
│   ├── workflows/       # 13 slash-command procedures
│   ├── scripts/         # master validation scripts
│   │   ├── doctor.py          # kit health check
│   │   ├── checklist.py       # priority-based audit
│   │   ├── verify_all.py      # full verification suite
│   │   ├── sync_ide.py        # multi-IDE export
│   │   └── install_hooks.py   # git hook installer
│   ├── tests/
│   │   └── test_kit_integrity.py  # automated pytest suite
│   ├── memory/
│   │   ├── lessons.md   # patterns that worked well
│   │   └── gotchas.md   # common pitfalls to avoid
│   └── rules/
│       └── GEMINI.md    # master rules file (P0)
└── README.md
```

---

## Support the Project

If this kit saves you time, consider supporting:

<p align="center">
  <img src="pix-fernando.png" alt="PIX QR Code" width="180" />
</p>

**PIX key:** `fernando.tenguan@gmail.com`

---

## License

MIT — FernandoTenguan
(Forked from Vudovn's original Antigravity Kit project)

---

> *Build smarter. Ship faster. With confidence.*
