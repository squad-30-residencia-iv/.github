# 🤖 Guia de Governança de IA & PromptOps

> Documento de referência mantido pelo **Squad 3 (DevOps/QA/AIOps)**. Toda estratégia ou comando de IA validado pelo time deve ser registrado aqui para compartilhamento contínuo.

---

## 1. Regras de Ouro no Uso de IA

1. **Regra do "Saber Explicar":** A IA acelera a escrita de código e documentação, mas o responsável humano deve compreender e defender cada linha perante o time ou mentor.
2. **Dupla Checagem Anti-Alucinação:** Proibido subir dados de negócio, métricas da empresa ou códigos sem testes e validação empírica.
3. **Privacidade Estrita:** É estritamente proibido enviar dados sensíveis, credenciais ou segredos da empresa parceira para ferramentas públicas de IA.

---

## 2. Catálogo de Prompts Validados (PromptOps)

### A. Para o Squad 1 (Negócios & Requisitos)

- **Objetivo:** Estruturação de Histórias de Usuário / BDD a partir de notas de reunião.
- **Modelo Sugerido:** Claude 3.7 / ChatGPT-4o
- **Prompt Base:**
  > Atue como Product Owner especialista em BDD. Com base nas seguintes anotações da reunião com o cliente [COLAR NOTAS], estruture 3 Histórias de Usuário completas contendo:
  >
  > - Como / Quero / Para que
  > - Regras de negócio restritivas
  > - Ao menos 2 cenários de aceite no formato Dado / Quando / Então

### B. Para o Squad 2 (Engenharia & Specs SDD)

- **Objetivo:** Geração de contrato de spec técnica a partir de uma História de Usuário.
- **Modelo Sugerido:** Cursor / Claude Code / Copilot Chat
- **Prompt Base:**
  > Com base na História de Usuário [COLAR US], elabore a especificação técnica em formato Markdown contendo:
  >
  > - Schemas de entrada e saída (TypeScript ou Zod)
  > - Definição dos endpoints REST (método, path, status codes de sucesso e erro)
  > - Tratamento de casos de borda e falhas esperadas

### C. Para o Squad 3 (QA, CI/CD & Auditoria)

- **Objetivo:** Geração de casos de teste automatizados para PRs.
- **Modelo Sugerido:** Cursor / ChatGPT-4o
- **Prompt Base:**
  > Atue como QA Engineer. Analise a seguinte função/endpoint [COLAR CÓDIGO] e escreva testes unitários abrangentes cobrindo o caminho feliz, parâmetros inválidos e tratamento de exceções.
