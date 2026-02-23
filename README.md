# Antigravity Kit (Custom Fork by Fernando Tenguan)

> AI Agent templates with Skills, Agents, and Workflows
> **Custom Version:** Enhanced with Vercel, Claude, and React optimizations.

## 🚀 What's New in this Fork?

This version has been customized and loaded with powerful external skills to supercharge your development workflow:

- **@rmyndharis/antigravity-skills**: Additional community-driven agent skills.
- **vercel-labs/agent-skills**:
  - `vercel-react-best-practices`: React and Next.js performance optimizations based on Vercel Engineering standards.
  - `web-design-guidelines`: Web interface guidelines compliance, accessibility checks, and UX audits.
- **anthropics/claude-code**:
  - `frontend-design`: Advanced design thinking, UI/UX decision making, and aesthetic configurations.
- **Included Files**: The `skills_guide.md` is now shipped by default when initiating this kit.

---

## Quick Install

To use this customized fork instead of the original, you need to point the CLI tool to this repository. *(See instructions below on how to do this or use this repository locally).*

## Quick Install

Como este é um repositório customizado (fork), o comando oficial `npx @vudovn/ag-kit init` fará o download da versão original. Para baixar a **sua versão personalizada**, você tem algumas alternativas mais dinâmicas:

### Opção 1: Via NPX (Recomendado)
Você pode usar a ferramenta `giget` (a mesma que o criador original usa por trás dos panos) para baixar e extrair apenas a pasta `.agent` diretamente do seu repositório para o seu projeto atual:

```bash
npx giget@latest github:fernandotenguan/antigravity-kit-personalizado/.agent .agent --force
```

### Opção 2: Via Git Clone
Se preferir, clone o repositório em uma pasta temporária e mova a pasta `.agent` para onde precisar:

```bash
git clone https://github.com/fernandotenguan/antigravity-kit-personalizado.git
# Depois, basta copiar a pasta .agent para o seu projeto
```

### Opção 3: Modificando a CLI Global
Se você usa o `ag-kit` frequentemente, pode manter a instalação global e editá-la conforme ensinado.
1. Instale globalmente: `npm install -g @vudovn/ag-kit`
2. Abra o arquivo instalado (ex: `C:\Users\ferna\AppData\Roaming\npm\node_modules\@vudovn\ag-kit\bin\index.js`)
3. Altere a linha `const REPO = 'github:vudovn/antigravity-kit';` para `const REPO = 'github:fernandotenguan/antigravity-kit-personalizado';`.
4. Em qualquer projeto novo, basta rodar `ag-kit init`.

This installs the `.agent` folder containing all templates into your project.

### ⚠️ Important Note on `.gitignore`
If you are using AI-powered editors like **Cursor** or **Windsurf**, adding the `.agent/` folder to your `.gitignore` may prevent the IDE from indexing the workflows. This results in slash commands (like `/plan`, `/debug`) not appearing in the chat suggestion dropdown.

**Recommended Solution:**
To keep the `.agent/` folder local (not tracked by Git) while maintaining AI functionality:
1. Ensure `.agent/` is **NOT** in your project's `.gitignore`.
2. Instead, add it to your local exclude file: `.git/info/exclude`

## What's Included

| Component     | Count | Description                                                        |
| ------------- | ----- | ------------------------------------------------------------------ |
| **Agents**    | 20    | Specialist AI personas (frontend, backend, security, PM, QA, etc.) |
| **Skills**    | 40+   | Domain-specific knowledge modules (Including Vercel & Claude)      |
| **Workflows** | 11    | Slash command procedures                                           |

## Usage

### Using Agents

**No need to mention agents explicitly!** The system automatically detects and applies the right specialist(s):

```
You: "Add JWT authentication"
AI: 🤖 Applying @security-auditor + @backend-specialist...

You: "Fix the dark mode button"
AI: 🤖 Using @frontend-specialist...

You: "Login returns 500 error"
AI: 🤖 Using @debugger for systematic analysis...
```

**How it works:**
- Analyzes your request silently
- Detects domain(s) automatically (frontend, backend, security, etc.)
- Selects the best specialist(s)
- Informs you which expertise is being applied
- You get specialist-level responses without needing to know the system architecture

**Benefits:**
- ✅ Zero learning curve - just describe what you need
- ✅ Always get expert responses
- ✅ Transparent - shows which agent is being used
- ✅ Can still override by mentioning agent explicitly

### Using Workflows

Invoke workflows with slash commands:

| Command          | Description                           |
| ---------------- | ------------------------------------- |
| `/brainstorm`    | Explore options before implementation |
| `/create`        | Create new features or apps           |
| `/debug`         | Systematic debugging                  |
| `/deploy`        | Deploy application                    |
| `/enhance`       | Improve existing code                 |
| `/orchestrate`   | Multi-agent coordination              |
| `/plan`          | Create task breakdown                 |
| `/preview`       | Preview changes locally               |
| `/status`        | Check project status                  |
| `/test`          | Generate and run tests                |
| `/ui-ux-pro-max` | Design with 50 styles                 |

Example:
```
/brainstorm authentication system
/create landing page with hero section
/debug why login fails
```

### Using Skills

Skills are loaded automatically based on task context. The AI reads skill descriptions and applies relevant knowledge.

## CLI Tool

| Command         | Description                               |
| --------------- | ----------------------------------------- |
| `ag-kit init`   | Install `.agent` folder into your project |
| `ag-kit update` | Update to the latest version              |
| `ag-kit status` | Check installation status                 |

### Options

```bash
ag-kit init --force        # Overwrite existing .agent folder
ag-kit init --path ./myapp # Install in specific directory
ag-kit init --quiet        # Suppress output (for CI/CD)
ag-kit init --dry-run      # Preview actions without executing
```

---

## Apoie este projeto (Buy me a coffee)

<p align="center">
  <!-- INSTRUÇÕES PARA O QR CODE PIX: -->
  <!-- 1. Gere seu QR Code Pix em sites como geradordepix.com ou no seu app do banco -->
  <!-- 2. Salve a imagem na pasta do repositório (ex: pix-fernando.png) -->
  <!-- 3. Faça o upload dessa imagem para o GitHub (ou coloque a URL direta da imagem aqui) -->
  <!-- 4. Substitua "COLOQUE_O_LINK_DA_IMAGEM_DO_SEU_QR_CODE_AQUI" pelo link da imagem -->
  <img src="pix-fernando.png" alt="Apoie com PIX" width="200" />
</p>

## License

MIT © Fernando Tenguan (Forked from Vudovn)
