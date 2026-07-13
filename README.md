# Analise de Riscos em Projeto de Software

Este repositorio contem os artefatos produzidos para um exercicio pratico de identificacao, analise, resposta e comunicacao de riscos em um projeto de software.

## Descricao do Projeto

O cenario utilizado considera o desenvolvimento de um aplicativo para agendamento de consultas medicas. O sistema inclui funcionalidades como:

- cadastro de usuarios;
- gestao de agenda medica;
- agendamento de consultas;
- notificacoes;
- integracao com um sistema externo de prontuario.

O projeto esta em fase intermediaria de desenvolvimento, com parte das funcionalidades ja implementadas e outras ainda em progresso.

Durante o andamento do projeto, foram considerados os seguintes desafios:

- instabilidade na integracao com o sistema externo de prontuario, causada por falta de documentacao clara da API e mudancas recentes no sistema externo;
- solicitacoes de alteracao em requisitos do fluxo de agendamento, incluindo novas validacoes e regras de negocio;
- aumento da carga de trabalho da equipe, com dificuldade para cumprir prazos inicialmente estimados;
- equipe composta por 4 desenvolvedores e 1 tester;
- integracao com o sistema externo considerada critica para a entrega.

## Objetivo do Exercicio

O objetivo do exercicio e utilizar apoio de LLM para estruturar artefatos de gestao de riscos em um projeto de software, cobrindo as seguintes etapas:

1. **Identificacao de riscos**
   - Lista de riscos identificados.
   - Breve descricao de cada risco.
   - Contexto em que cada risco pode ocorrer.

2. **Analise qualitativa dos riscos**
   - Analise estruturada dos riscos.
   - Explicacao dos impactos potenciais.
   - Identificacao de fatores condicionantes.
   - Classificacao qualitativa de probabilidade e impacto.

3. **Definicao de estrategias de resposta**
   - Estrategia proposta para cada risco.
   - Justificativa da estrategia.
   - Acoes praticas associadas.
   - Consideracao de estrategias como evitar, mitigar, transferir e aceitar.

4. **Comunicacao para stakeholders**
   - Texto claro e objetivo para publico nao tecnico.
   - Contexto atual do projeto.
   - Principais riscos e impactos.
   - Acoes recomendadas.
   - Proximos passos para tomada de decisao.

5. **Organizacao dos artefatos**
   - Arquivos em Markdown.
   - Organizacao em pastas.
   - Historico de commits representando a evolucao da atividade.

## Organizacao do Repositorio

```text
.
├── README.md
├── comunicacao/
│   └── status-stakeholders.md
├── prompts-iniciais/
│   ├── etapa-1.md
│   ├── etapa-2.md
│   ├── etapa-3.md
│   └── etapa-4.md
└── riscos/
    ├── identificacao.md
    ├── analise.md
    └── respostas.md
```

## Descricao dos Artefatos

- `riscos/identificacao.md`: documento da etapa 1, contendo a lista de riscos identificados, contexto de ocorrencia, incertezas, termos tecnicos relacionados, checklist de revisao humana e change-log.
- `riscos/analise.md`: documento da etapa 2, contendo a analise qualitativa dos riscos, impactos, fatores condicionantes, matriz de probabilidade versus impacto, checklist e change-log.
- `riscos/respostas.md`: documento da etapa 3, contendo estrategias de resposta aos riscos, justificativas e acoes praticas em ordem de execucao.
- `comunicacao/status-stakeholders.md`: documento da etapa 4, contendo uma comunicacao objetiva para stakeholders, com foco em tomada de decisao.
- `prompts-iniciais/`: pasta com os prompts iniciais utilizados nas etapas do exercicio, mantendo rastreabilidade sobre como os artefatos foram gerados com apoio de IA.

## Observacoes

As informacoes foram tratadas como um cenario de exercicio academico. Quando algum ponto dependia de dados nao fornecidos, os documentos indicaram incertezas ou necessidade de validacao humana.

Os riscos e respostas foram revisados ao longo da atividade para incluir pontos adicionais como seguranca de dados, indisponibilidade da API externa, concorrencia em agendamentos, controle de acesso, rastreabilidade, crescimento de escopo e estresse da equipe.
