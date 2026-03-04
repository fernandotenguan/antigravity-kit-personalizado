# Changelog

All notable changes to the Antigravity Kit will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/2.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]


### [2.2.0] - 2026-03-04
- **ADD**: Importação de 9 novas skills estratégicas do repositório `antigravity-awesome-skills`.
- **ADD**: Pacote "Estratégia e Memória": `00-andruia-consultant`, `agent-memory-mcp`, `agent-evaluation`, `agent-orchestration-multi-agent-optimize`.
- **ADD**: Pacote "IA Preditiva Pro": `ai-engineer`, `machine-learning-ops-ml-pipeline`.
- **ADD**: Pacote "SaaS & Business": `micro-saas-launcher`, `startup-analyst`, `20-andruia-niche-intelligence`.
- **IMPROVE**: Tradução bilingue (PT-BR/EN) para a série de agentes Andruia.
- **DOC**: Atualização do `README.md` e `GUIA_DO_USUARIO.md` refletindo o novo total de 47 skills.

### [2.1.0] - 2026-03-04
- **ADD**: Novo documento de governança de IA: `KIT_MASTER_RULES.md`.
- **ADD**: Novo workflow interativo `/new-project` para guiar a criação de novos sistemas.
- **DOC**: Atualização completa do `README.md` e `GUIA_DO_USUARIO.md` com foco em usuários de negócio.
- **CLEAN**: Remoção de subpasta redundante `antigravity-kit-personalizado` que causava confusão de nomes.
- **IMPROVE**: Refinamento do script `doctor.py` e validação de saúde do kit.

### [2.0.0] - 2026-03-01
- **New Skills**:
    - `rust-pro` - Master Rust 1.75+ 
- **Agent Workflows**:
    - Updated `orchestrate.md` fix output turkish


## [2.0.1] - 2026-01-26

### Added

- **Agent Flow Documentation**: New comprehensive workflow documentation
    - Added `.agent/AGENT_FLOW.md` - Complete agent flow architecture guide
    - Documented Agent Routing Checklist (mandatory steps before code/design work)
    - Documented Socratic Gate Protocol for requirement clarification
    - Added Cross-Skill References pattern documentation
- **New Skills**:
    - `react-best-practices` - Consolidated Next.js and React expertise
    - `web-design-guidelines` - Professional web design standards and patterns

### Changed

- **Skill Consolidation**: Merged `nextjs-best-practices` and `react-patterns` into unified `react-best-practices` skill
- **Architecture Updates**:
    - Enhanced `.agent/ARCHITECTURE.md` with improved flow diagrams
    - Updated `.agent/rules/GEMINI.md` with Agent Routing Checklist
- **Agent Updates**:
    - Updated `frontend-specialist.md` with new skill references
    - Updated `qa-automation-engineer.md` with enhanced testing workflows
- **Frontend Design Skill**: Enhanced `frontend-design/SKILL.md` with cross-references to `web-design-guidelines`

### Removed

- Deprecated `nextjs-best-practices` skill (consolidated into `react-best-practices`)
- Deprecated `react-patterns` skill (consolidated into `react-best-practices`)

### Fixed

- **Agent Flow Accuracy**: Corrected misleading terminology in AGENT_FLOW.md
    - Changed "Parallel Execution" → "Sequential Multi-Domain Execution"
    - Changed "Integration Layer" → "Code Coherence" with accurate description
    - Added reality notes about AI's sequential processing vs. simulated multi-agent behavior
    - Clarified that scripts require user approval (not auto-executed)

## [2.0.0] - Unreleased

### Initial Release

- Initial release of Antigravity Kit
- 20 specialized AI agents
- 37 domain-specific skills
- 11 workflow slash commands
- CLI tool for easy installation and updates
- Comprehensive documentation and architecture guide

[Unreleased]: https://github.com/vudovn/antigravity-kit/compare/v2.0.0...HEAD
[2.0.0]: https://github.com/vudovn/antigravity-kit/releases/tag/v2.0.0
