# PLAN: AIOS Integration — Antigravity Kit Power-Up

> **Objetivo:** Integrar as melhores práticas de infraestrutura do Synkra AIOS-Core no antigravity-kit-personalizado, sem quebrar nenhuma funcionalidade existente. O `.agent/` passará a funcionar como um produto de software profissional — com testes, validação automática, diagnóstico e pipeline autônomo.

---

## 📋 Overview

### O que muda

| Antes | Depois |
|-------|--------|
| Kit de arquivos `.md` sem validação | Kit com testes automáticos que garantem integridade |
| Verificação manual de qualidade | Pre-commit que roda `checklist.py` antes de cada commit |
| Sem CI/CD | GitHub Actions bloqueia merge se kit estiver quebrado |
| Sem diagnóstico | `doctor.py` verifica saúde completa do kit |
| Workflow manual por agente | `/ade` pipeline autônomo: req → spec → impl → qa |
| Só Gemini CLI | Sync scripts para Claude, Codex, Cursor (multi-IDE) |

### Por que isso importa

O AIOS-Core trata o próprio framework como um produto de software. O Antigravity tem mais skills e agentes que o AIOS, mas sem a infraestrutura de automação, qualquer atualização pode quebrar silenciosamente referências, frontmatter ou fluxos. Essas melhorias **blindam** o kit.

---

## ✅ Success Criteria

- [ ] `python .agent/tests/test_kit_integrity.py` → 100% pass
- [ ] `python .agent/scripts/doctor.py` → All checks green
- [ ] Pre-commit hook ativo e funcional (testar com commit intencional com erro)
- [ ] GitHub Actions CI rodando em PR aberto
- [ ] `/ade` workflow invocável e documentado
- [ ] Nenhum arquivo existente quebrado (zero-break)

---

## 🛠️ Tech Stack

| Componente | Tecnologia | Motivo |
|---|---|---|
| **Testes do Kit** | Python `pytest` + módulo `pathlib` | Já usamos Python nos scripts existentes |
| **Git Hooks** | `.husky/` via `npm` + script Python | Compatível com Windows (PowerShell) |
| **CI/CD** | GitHub Actions (`.github/workflows/`) | Já existe repositório GitHub |
| **Diagnóstico** | Python `doctor.py` | Consistente com os outros scripts |
| **ADE Pipeline** | `.agent/workflows/ade.md` (slash command) | Sem nova dependência |
| **Multi-IDE Sync** | Python `sync_ide.py` | Script simples, zero dependência |

---

## 📁 File Structure — Novos Arquivos

```
antigravity-kit-personalizado/
├── .github/
│   └── workflows/
│       └── ci.yml                        # [NEW] GitHub Actions CI
├── .husky/
│   └── pre-commit                        # [NEW] Git hook pre-commit
├── .agent/
│   ├── scripts/
│   │   ├── doctor.py                     # [NEW] Diagnóstico do kit
│   │   ├── sync_ide.py                   # [NEW] Multi-IDE sync
│   │   ├── checklist.py                  # [EXISTENTE] — não modificar
│   │   └── verify_all.py                 # [EXISTENTE] — não modificar
│   ├── tests/
│   │   └── test_kit_integrity.py         # [NEW] Testes automáticos do kit
│   └── workflows/
│       ├── ade.md                        # [NEW] ADE autonomous pipeline workflow
│       └── [11 existentes]               # [EXISTENTE] — não modificar
├── aios-integration.md                   # Este plano
└── package.json                          # [MODIFY] Adicionar scripts npm para hooks
```

---

## 📊 Task Breakdown

### FASE 1 — Fundação: Testes + Diagnóstico (P0)

> **Objetivo:** Criar a base que valida o kit automaticamente. Sem isso, nenhuma outra melhoria tem garantia de funcionar.

---

#### TASK 1.1 — Criar `test_kit_integrity.py`

**Agent:** `test-engineer`
**Skill:** `testing-patterns`
**Priority:** P0 (blocker para tudo)
**Dependencies:** Nenhuma

**INPUT:** Estrutura atual do `.agent/` (20 agentes, 36 skills, 11 workflows)

**OUTPUT:** `.agent/tests/test_kit_integrity.py` que valida:
- Todo agente em `.agent/agents/` tem frontmatter com `name:` e `skills:` válidos
- Todo skill referenciado em um agente existe em `.agent/skills/`
- Todo skill tem `SKILL.md` com conteúdo mínimo (>100 chars)
- Todo workflow em `.agent/workflows/` tem frontmatter com `description:`
- Nenhum skill referenciado é um ghost (arquivo inexistente)

**VERIFY:**
```bash
python -m pytest .agent/tests/test_kit_integrity.py -v
# Expected: X passed, 0 failed
```

**Rollback:** Deletar o arquivo — não afeta nada existente.

---

#### TASK 1.2 — Criar `doctor.py`

**Agent:** `backend-specialist`
**Skill:** `python-patterns`
**Priority:** P0
**Dependencies:** TASK 1.1 (usa mesma lógica de validação)

**INPUT:** Kit completo em `.agent/`

**OUTPUT:** `.agent/scripts/doctor.py` com relatório de saúde:
```
🏥 Antigravity Kit — System Diagnostics
✔ Python version: 3.x.x (OK)
✔ .agent/ directory: found
✔ Agents: 20 found, 0 broken frontmatter
✔ Skills: 36 found, 0 missing SKILL.md
✔ Workflows: 11 found, 0 broken
✔ Scripts: checklist.py ✅ | verify_all.py ✅
✔ Cross-references: 0 ghost skills detected

✅ All checks passed! Kit is healthy.
```

**VERIFY:**
```bash
python .agent/scripts/doctor.py
# Expected: "All checks passed" com exit code 0
```

**Rollback:** Deletar o arquivo.

---

### FASE 2 — Automação: Git Hooks + CI/CD (P1)

> **Objetivo:** Tornar a validação automática e obrigatória. Nenhum commit quebra o kit; nenhum PR sem CI.

---

#### TASK 2.1 — Git Hook pre-commit

**Agent:** `devops-engineer`
**Skill:** `deployment-procedures`
**Priority:** P1
**Dependencies:** TASK 1.1

**INPUT:** `checklist.py` existente + `test_kit_integrity.py` (TASK 1.1)

**OUTPUT:** `.husky/pre-commit` que executa antes de cada `git commit`:
```bash
#!/bin/sh
echo "🔍 Antigravity pre-commit check..."
python .agent/tests/test_kit_integrity.py
if [ $? -ne 0 ]; then
  echo "❌ Kit integrity check failed. Fix errors before committing."
  exit 1
fi
echo "✅ Pre-commit check passed."
```
+ modificação de `package.json` para adicionar `"prepare": "husky install"`.

**VERIFY:**
1. Fazer uma edição intencional inválida em um agent `.md` (ex: remover `skills:` do frontmatter)
2. Tentar `git commit` → deve ser BLOQUEADO com mensagem de erro
3. Reverter edição → `git commit` deve funcionar normalmente

**Rollback:** Remover `.husky/` e reverter `package.json`.

---

#### TASK 2.2 — GitHub Actions CI

**Agent:** `devops-engineer`
**Skill:** `deployment-procedures`
**Priority:** P1
**Dependencies:** TASK 1.1 + TASK 1.2

**INPUT:** `test_kit_integrity.py` e `doctor.py`

**OUTPUT:** `.github/workflows/ci.yml` que roda em cada PR:
```yaml
name: Antigravity Kit CI
on: [push, pull_request]
jobs:
  validate:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-python@v5
        with: { python-version: '3.12' }
      - name: Kit Integrity Tests
        run: python -m pytest .agent/tests/ -v
      - name: Doctor Check
        run: python .agent/scripts/doctor.py
```

**VERIFY:**
1. Abrir um PR qualquer no repositório GitHub
2. Verificar que o check "Antigravity Kit CI" aparece e passa
3. (Opcional) Fazer um PR com erro intencional → CI deve falhar

**Rollback:** Deletar `.github/workflows/ci.yml`.

---

### FASE 3 — ADE Pipeline: Workflow Autônomo (P2)

> **Objetivo:** Implementar o padrão ADE (Autonomous Development Engine) do AIOS como um workflow `/ade` do Antigravity Kit. Transforma requisitos vagos em código funcional com pipeline multi-agente supervisado.

---

#### TASK 3.1 — Criar workflow `/ade`

**Agent:** `orchestrator`
**Skill:** `behavioral-modes` + `brainstorming`
**Priority:** P2
**Dependencies:** Nenhuma (independente das fases 1 e 2)

**INPUT:** Análise do ADE do AIOS-Core (7 Epics) + workflows existentes do kit

**OUTPUT:** `.agent/workflows/ade.md` com pipeline de 6 fases:

```
Fase 1: Discovery (@project-planner — Socratic Gate mínimo)
Fase 2: Spec (@backend-specialist ou @frontend-specialist — cria spec técnica)
Fase 3: Critique (@qa-automation-engineer — revisa spec)
Fase 4: Execution (@orchestrator — divide em subtasks paralelas)
Fase 5: QA Review (@test-engineer — valida output)
Fase 6: Memory (@project-planner — documenta padrões aprendidos em .agent/memory/)
```

**VERIFY:**
```
/ade "adicionar uma nova skill chamada exemplo ao kit"
# Expected: Fluxo completo executado, skill criada seguindo estrutura correta
```

**Rollback:** Deletar `.agent/workflows/ade.md`. Workflows são aditivos.

---

#### TASK 3.2 — Criar `.agent/memory/` — Memory Layer simples

**Agent:** `project-planner`
**Skill:** `plan-writing`
**Priority:** P2 (pode ser paralelo com 3.1)
**Dependencies:** TASK 3.1 (referenciado no Fase 6)

**INPUT:** Conceito do ADE Epic 7 (Memory Layer)

**OUTPUT:**
- `.agent/memory/lessons.md` — arquivo onde o agente registra padrões e aprendizados
- `.agent/memory/gotchas.md` — erros comuns encontrados no projeto

Formato de entrada em `lessons.md`:
```markdown
## 2026-MM-DD — [Feature Name]
**Padrão identificado:** [O que funcionou bem]
**Pitfall evitado:** [O que não fazer]
**Contexto:** [Quando aplicar]
```

**VERIFY:** Arquivo criado, formatado corretamente, legível pelo agente em contexto futuro.

**Rollback:** Deletar pasta `.agent/memory/`.

---

### FASE 4 — Multi-IDE Sync (P3)

> **Objetivo:** Gerar configurações sincronizadas do kit para outros IDEs (Claude, Codex, Cursor), como o AIOS faz com `npm run sync:ide:*`.

---

#### TASK 4.1 — Criar `sync_ide.py`

**Agent:** `backend-specialist`
**Skill:** `python-patterns`
**Priority:** P3
**Dependencies:** TASK 1.2 (doctor.py valida antes do sync)

**INPUT:** Arquivos `.agent/agents/`, `.agent/skills/`, `GEMINI.md`

**OUTPUT:** `.agent/scripts/sync_ide.py` com suporte a:
```bash
python .agent/scripts/sync_ide.py --target claude
# Gera .claude/CLAUDE.md com regras do GEMINI.md

python .agent/scripts/sync_ide.py --target cursor
# Gera .cursor/rules.md

python .agent/scripts/sync_ide.py --target all
# Gera todos os targets
```

**VERIFY:**
```bash
python .agent/scripts/sync_ide.py --target claude
# Expected: .claude/CLAUDE.md criado com seções do GEMINI.md
python .agent/scripts/sync_ide.py --target cursor
# Expected: .cursor/rules.md criado
```

**Rollback:** Deletar `.claude/` e `.cursor/rules.md` gerados.

---

## ⚠️ Riscos e Mitigações

| Risco | Mitigação |
|-------|-----------|
| Testes falsos negativos (um agent tem skill name diferente do folder) | Normalização de slug no test (lowercase, strip) |
| Pre-commit lento no Windows | Timeout de 10s; se falhar por timeout, warning (não block) |
| CI Actions bloqueando PRs urgentes | Adicionar `[skip ci]` como opção no commit message |
| `sync_ide.py` sobrescrever configs manuais | Adicionar flag `--dry-run` antes de qualquer escrita |

---

## 🔗 Dependências Entre Fases

```
TASK 1.1 (test_kit_integrity.py)
    ├─── TASK 1.2 (doctor.py)
    │        └─── TASK 2.2 (GitHub Actions CI)
    └─── TASK 2.1 (Git Hook pre-commit)

TASK 3.1 (workflow /ade)
    └─── TASK 3.2 (Memory Layer)

TASK 1.2 (doctor.py)
    └─── TASK 4.1 (sync_ide.py)
```

**Ordem de implementação segura:**
1. → TASK 1.1 (blocker de tudo)
2. → TASK 1.2 + TASK 2.1 (paralelo)
3. → TASK 2.2
4. → TASK 3.1 + TASK 3.2 (paralelo)
5. → TASK 4.1

---

## 🔍 Phase X: Verificação Final

> Executar APÓS implementação completa de todas as fases.

### Checklist de Conclusão

```bash
# 1. Testes do Kit
python -m pytest .agent/tests/test_kit_integrity.py -v
# Expected: All PASS

# 2. Diagnóstico
python .agent/scripts/doctor.py
# Expected: All checks green

# 3. Pre-commit (teste manual)
# Quebrar frontmatter de um agent → git commit → deve falhar → reverter → git commit → deve passar

# 4. CI/CD
# Abrir PR no GitHub → verificar check "Antigravity Kit CI" passou

# 5. ADE Workflow
# /ade "descrição de task simples" → pipeline deve executar

# 6. Sync Multi-IDE
python .agent/scripts/sync_ide.py --dry-run --target all
# Expected: Lista de arquivos que seriam gerados, sem errar

# 7. Zero-Break Audit
python .agent/scripts/checklist.py .
# Expected: Sem regressões nos checks existentes

# 8. verify_all.py
python .agent/scripts/verify_all.py .
# Expected: Sem novas falhas
```

### Rule Compliance

- [ ] Nenhum arquivo existente foi modificado sem necessidade
- [ ] Todos os novos arquivos seguem `clean-code` (Python: type hints, funções <20 linhas)
- [ ] GEMINI.md não foi alterado (é P0 e deve permanecer intocado)
- [ ] README.md atualizado com seção `## Features` para cada nova feature

---

## ✅ PHASE X COMPLETE

> _(Preencher após implementação)_

- Tests: ⬜ Pending
- Doctor: ⬜ Pending
- Pre-commit: ⬜ Pending
- CI/CD: ⬜ Pending
- ADE Workflow: ⬜ Pending
- Memory Layer: ⬜ Pending
- Multi-IDE Sync: ⬜ Pending
- Zero-Break: ⬜ Pending

---

*Plano criado em: 2026-03-03 | Projeto: antigravity-kit-personalizado | Versão: 1.0*
