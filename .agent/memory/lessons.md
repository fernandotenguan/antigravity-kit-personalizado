# Lessons Learned — Antigravity Kit

> Padrões identificados durante o desenvolvimento. Consulte antes de iniciar uma task complexa.

---

## Formato de entrada

```markdown
## YYYY-MM-DD — [Feature/Task Name]
**Padrão identificado:** O que funcionou bem (reutilizável)
**Pitfall evitado:** O que não fazer / armadilha identificada
**Contexto:** Quando aplicar este padrão
**Arquivos chave:** lista de arquivos relevantes
```

---

## 2026-03-03 — AIOS Integration Planning

**Padrão identificado:** Ao integrar novos scripts/workflows ao kit, atualizar SEMPRE os 4 arquivos de configuração do agente em sequência: GEMINI.md → ARCHITECTURE.md → intelligent-routing → workflow file.
**Pitfall evitado:** Criar novos scripts sem registrá-los no GEMINI.md faz o agente não saber que existem.
**Contexto:** Toda vez que um novo script master, workflow ou skill for adicionado ao kit.
**Arquivos chave:** `.agent/rules/GEMINI.md`, `.agent/ARCHITECTURE.md`, `.agent/skills/intelligent-routing/SKILL.md`
