# Antigravity Kit

**Custom Fork by FernandoTenguan**

> A collection of AI agent templatescomplete with Skills, Agents, and Workflows
> optimized for web developers, designers and teams.
>
> **This fork adds:** Vercel & Claude enhancements, React performance guidelines,
> and other communitydriven skills.

---

## Project Overview

The Antigravity Kit is a starting point for building powerful AIassisted
development workflows. You can plug it into any JavaScript/TypeScript project to
get:

- **Agents** specialized AI personas (frontend dev, backend dev, security
  auditor, etc.).
- **Skills** domain knowledge modules that teach agents how to perform tasks.
- **Workflows** slashcommand procedures that orchestrate agents in common
  scenarios.

This custom fork extends the original with:

- Extra community skills (`@rmyndharis/antigravity-skills`)
- Vercelapproved React/Next.js best practices and web design guidelines
- Claudepowered frontend design reasoning
- Prebundled `skills_guide.md` for immediate reference

---

## What's Included

| Component     | Count | Description                                                        |
| ------------- | ----- | ------------------------------------------------------------------ |
| **Agents**    | 20    | Specialist AI personas (frontend, backend, security, PM, QA, etc.) |
| **Skills**    | 40+   | Domainspecific knowledge modules (including Vercel & Claude)       |
| **Workflows** | 11    | Slashcommand procedures for common tasks                           |

---

## Installation

This fork must be installed manually, since the official CLI defaults to the
upstream repository.

### Option 1 NPX (recommended)

```bash
npx giget@latest github:fernandotenguan/antigravity-kit-personalizado/.agent .agent --force
```

> `giget` downloads and extracts only the `.agent` folder into your project.

### Option 2 Git clone

```bash
git clone https://github.com/fernandotenguan/antigravity-kit-personalizado.git
# then copy the .agent directory into your project
```

### Option 3 Modify the global CLI

1. `npm install -g @vudovn/ag-kit`
2. Open the installed binary (e.g. `.../node_modules/@vudovn/ag-kit/bin/index.js`)
3. Change
    ```js
    const REPO = "github:vudovn/antigravity-kit";
    ```
    to
    ```js
    const REPO = "github:fernandotenguan/antigravity-kit-personalizado";
    ```
4. Use `ag-kit init` as usual.

> **Note:** the `.agent` folder should **not** be added to your projects
> `.gitignore` if you want AIpowered editors like Cursor or Windsurf to index
> workflows. Instead, add it to `.git/info/exclude` so it remains local but
> accessible.

---

## Usage

### Agents

Describe your need and the system:

1. Analyzes your request
2. Detects relevant domain(s)
3. Selects the best agent(s)
4. Reports which specialist(s) are at work

```
You: "Add JWT authentication"
AI:  Applying @security-auditor + @backend-specialist...

You: "Fix the dark mode button"
AI:  Using @frontend-specialist...

You: "Login returns 500 error"
AI:  Using @debugger for systematic analysis...
```

**Benefits:**

- Zero learning curve
- Expertlevel responses
- Transparent agent selection
- Manual override via `@agent-name`

### Workflows

Invoke slash commands for structured procedures:

| Command          | Purpose                             |
| ---------------- | ----------------------------------- |
| `/brainstorm`    | Explore options before implementing |
| `/create`        | Scaffold features or applications   |
| `/debug`         | Systematic debugging                |
| `/deploy`        | Deploy the app                      |
| `/enhance`       | Improve existing code               |
| `/orchestrate`   | Coordinate multiple agents          |
| `/plan`          | Break tasks into actionable steps   |
| `/preview`       | Preview changes locally             |
| `/status`        | Check project health                |
| `/test`          | Generate and run tests              |
| `/ui-ux-pro-max` | Produce UI/UX designs in 50 styles  |

_Example:_

```
/brainstorm authentication system
/create landing page with hero section
/debug why login fails
```

### Skills

Skills load automatically based on context; the AI reads each description and
applies relevant knowledge.

### CLI Tools

| Command         | Description                   |
| --------------- | ----------------------------- |
| `ag-kit init`   | Install the `.agent` folder   |
| `ag-kit update` | Refresh to the latest version |
| `ag-kit status` | Display installation status   |

**Options:**

```bash
ag-kit init --force        # overwrite existing .agent
ag-kit init --path ./app   # install to a specific directory
ag-kit init --quiet        # minimal output (useful for CI)
ag-kit init --dry-run      # show actions without executing
```

---

## Support the Project

> **Buy me a coffee**

<p align="center">
  <!-- INSTRUCTIONS FOR PIX QR CODE: -->
  <!-- 1. Generate a PIX QR code using sites like geradordepix.com or your banking app -->
  <!-- 2. Save the image in the repo (e.g. pix-fernando.png) -->
  <!-- 3. Upload it to GitHub or use a direct URL here -->
  <img src="pix-fernando.png" alt="Apoie com PIX" width="200" />
</p>

**Ou copie a chave PIX:** fernando.tenguan@gmail.com

---

## License

MIT FernandoTenguan  
(Forked from Vudovns original project)

---

> _Thank you for exploring this custom Antigravity Kit build smarter, faster, and with confidence!_
