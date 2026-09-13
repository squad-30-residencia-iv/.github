# 🚀 Plataforma para Gestão de Campanhas de Voucher Digital

> Sem uma plataforma centralizada, o varejo enfrenta erros e dificuldade para criar, manter e acompanhar campanhas promocionais com regras distintas de cupons e vouchers. Este projeto centraliza a configuração, a concessão, a utilização e a auditoria dessas campanhas digitais, com controle de elegibilidade, alvos, vigência e resultados.

---

## 📌 Visão Geral & Metodologia

Este repositório atua como a **Fonte Única da Verdade** para documentação, governança e alinhamento do projeto. Trabalhamos com uma metodologia ágil inspirada em práticas de **DevOps adaptadas para a era da Inteligência Artificial (AIOps)**, aplicando **Spec-Driven Development (SDD)** para guiar todo o ciclo de desenvolvimento técnico.

### ⚖️ As 3 Regras de Ouro

1. **Integração Semanal Contínua:** Nada de guardar trabalho no computador pessoal até o fim; o progresso é integrado semanalmente.
2. **IA como Copiloto:** A IA acelera a execução e planejamento, mas a responsabilidade técnica e crítica é humana.
3. **Validação Obrigatória:** Se a IA gerou código, requisito ou teste, o responsável deve entender e testar.

---

## 👥 Estrutura do Time & Squads

A equipe é composta por 10 integrantes organizados em 3 squads funcionais e uma liderança de projeto:

| Papel / Squad                                 | Integrantes                                                                                                                                                                                                                                                           | Foco Principal                                                                         | Ferramental de Apoio                               |
| :-------------------------------------------- | :-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :------------------------------------------------------------------------------------- | :------------------------------------------------- |
| **Gestão de Projetos**                        | • [Danilo Araujo](https://github.com/DanAraujo1001)                                                                                                                                                                                                                   | Orquestração do Kanban, remoção de bloqueios e alinhamento com stakeholders            | GitHub Projects, IA para métricas e relatórios     |
| **Squad 1: Negócios & Produto** (2 pessoas)   | • [Bergue Vitor](https://github.com/bergue-vitor) <br>• [Vitor Pádua](https://github.com/vitor-paduaa)                                                                                                                                                                | Mapeamento do problema, alinhamento com cliente, escrita de Histórias de Usuário e BDD | `.github/docs/`, Issues no GitHub                  |
| **Squad 2: Engenharia & Solução** (5 pessoas) | • [Iago Rocha](https://github.com/iagovrocha) <br>• [Lavínia Mota](https://github.com/LaviniaMota07) <br>• [João Paulo](https://github.com/joaopauldsn) <br>• [Gabriel Torres](https://github.com/GabTorres7) <br>• [Victor Rivera](https://github.com/RiveraaVictor) | Arquitetura técnica, redação de Specs (SDD), desenvolvimento do Backend e Frontend     | IDE / Cursor (`.cursor/rules`), Copilot, SDD specs |
| **Squad 3: DevOps, QA & IA** (2 pessoas)      | • [Juliana Ivo](https://github.com/julianaivo) <br>• [Nicole](https://github.com/Nicole5436)                                                                                                                                                                          | Infraestrutura, pipelines de CI/CD, testes automatizados e governança de PromptOps     | GitHub Actions, `PROMPT_GUIDELINES.md`             |

---

## 🗂️ Ecossistema de Repositórios

Toda a solução está centralizada dentro desta organização no GitHub:

- [.github](https://github.com/squad-30-residencia-iv/.github): Governança institucional, regras de negócio gerais e guia de PromptOps.
- [backend-api](https://github.com/squad-30-residencia-iv/backend-api): Serviço de backend, APIs, contratos de dados e regras de negócio.
- [frontend-web](https://github.com/squad-30-residencia-iv/frontend-web): Interface web, componentes visuais e consumo de serviços.
- [ai-services](https://github.com/squad-30-residencia-iv/ai-services): Scripts de inteligência artificial, automações e pipelines de dados.

---

## 🧭 Documentação Central

Navegue pelos documentos estruturais do projeto na pasta `docs/`:

- 📄 [`docs/problematica.md`](docs/problematica.md): Contextualização da empresa parceira e gargalos mapeados.
- 📋 [`docs/requisitos.md`](docs/requisitos.md): Requisitos funcionais, regras de negócio e escopo macro.
- 📐 [`docs/arquitetura.md`](docs/arquitetura.md): Visão de arquitetura de software, tecnologias e infraestrutura.
- 🤖 [`PROMPT_GUIDELINES.md`](PROMPT_GUIDELINES.md): Guia de governança de IA, engenharia de prompts testados e diretrizes anti-alucinação.

---

## 🔄 Fluxo de Gestão (Kanban)

O acompanhamento diário e semanal é realizado via **GitHub Projects**.
