# Etapa 3 - Estrategias de Resposta aos Riscos

Documento gerado para sugerir possiveis estrategias de resposta aos riscos previamente identificados e analisados em `riscos/analise.md`. As estrategias apresentadas sao propostas para avaliacao humana e nao representam uma decisao definitiva de tratamento.

**Timestamp de geracao:** 2026-07-12 19:40:19 -03:00

## Premissas e Limites da Analise

- Foram considerados apenas os riscos ja mapeados nas etapas anteriores.
- As estrategias seguem categorias classicas de resposta a riscos: evitar, mitigar, transferir e aceitar.
- Nao ha escolha final de estrategia neste documento; a decisao deve ser feita por responsaveis do projeto apos revisao.
- Quando houver dependencia de informacoes nao fornecidas, o ponto esta indicado como necessidade de validacao.

## Resumo das Estrategias Propostas

| ID | Risco | Estrategia primaria proposta para avaliacao | Alternativas viaveis | Implicacoes principais |
| --- | --- | --- | --- | --- |
| R-01 | Instabilidade na integracao com o prontuario externo | Mitigar | Transferir parte do risco ao fornecedor externo; aceitar instabilidades residuais controladas | Exige diagnostico tecnico, alinhamento externo e testes integrados mais frequentes. |
| R-02 | Dependencia critica de sistema externo para a entrega | Mitigar | Transferir por acordo formal de suporte; aceitar mediante contingencia aprovada | Pode demandar plano de contingencia, criterios de aceite especificos e decisao dos stakeholders. |
| R-03 | Retrabalho por mudancas no fluxo de agendamento | Mitigar | Evitar novas mudancas por congelamento temporario de escopo; aceitar replanejamento | Pode alterar prazo, escopo ou prioridade de entregas. |
| R-04 | Ambiguidade nas novas regras de negocio | Mitigar | Evitar implementacao ate esclarecimento; aceitar risco residual em regras de menor impacto | Exige refinamento, criterios de aceite e validacao formal. |
| R-05 | Atraso por sobrecarga da equipe | Mitigar | Aceitar atraso formalmente; reduzir escopo para evitar sobrecarga adicional | Pode requerer replanejamento, priorizacao e ajuste de expectativa com stakeholders. |
| R-06 | Gargalo de testes | Mitigar | Transferir parte da validacao para apoio temporario; aceitar cobertura reduzida com ciencia dos stakeholders | Pode afetar prazo de validacao, qualidade e confianca na entrega. |
| R-07 | Defeitos de regressao em funcionalidades ja implementadas | Mitigar | Aceitar risco residual em fluxos de baixa criticidade | Exige priorizacao de regressao e controle de mudancas em funcionalidades ja prontas. |
| R-08 | Inconsistencia de dados entre sistema e prontuario | Mitigar | Transferir responsabilidades de contrato/API ao fornecedor; aceitar apenas com processo de reconciliacao | Pode exigir logs, reconciliacao, tratamento de falhas e definicao de responsabilidades. |
| R-09 | Notificacoes inconsistentes apos mudancas no agendamento | Mitigar | Aceitar se notificacoes nao forem criticas para aceite; evitar mudancas sem mapear eventos | Exige validacao da dependencia entre agendamento e notificacoes. |

## Respostas Propostas por Risco

### R-01 - Instabilidade na integracao com o prontuario externo

**Estrategia primaria proposta para avaliacao:** Mitigar.

**Justificativa:** A instabilidade ja foi observada e a integracao e critica para a entrega. Mitigar permite reduzir recorrencia e impacto sem depender de uma eliminacao completa do risco, que pode nao estar sob controle direto da equipe.

**Alternativas viaveis e implicacoes:**
- **Transferir:** formalizar suporte, prazos de resposta ou esclarecimentos com o responsavel pelo sistema externo. Implica dependencia de acordo externo.
- **Aceitar:** seguir com instabilidade residual documentada. Implica risco de falhas em homologacao ou entrega, exigindo ciencia formal dos stakeholders.

**Acoes praticas em ordem de execucao:**
1. Listar os pontos da integracao que apresentam falha ou comportamento instavel.
2. Registrar evidencias tecnicas das falhas, incluindo cenarios, payloads, respostas e horarios, se disponiveis.
3. Solicitar esclarecimento formal sobre API, mudancas recentes e comportamento esperado ao responsavel pelo sistema externo.
4. Priorizar testes integrados dos fluxos que dependem do prontuario.
5. Definir tratamento para falhas transitorias, como retentativa, mensagem de erro controlada ou fila de reprocessamento, caso aplicavel.
6. Reavaliar o risco apos nova rodada de testes integrados.

### R-02 - Dependencia critica de sistema externo para a entrega

**Estrategia primaria proposta para avaliacao:** Mitigar.

**Justificativa:** A dependencia externa nao pode ser eliminada com as informacoes atuais, mas pode ser reduzida por planejamento de contingencia, criterios claros de aceite e alinhamento com responsaveis externos.

**Alternativas viaveis e implicacoes:**
- **Transferir:** estabelecer acordo de suporte ou compromisso formal com o fornecedor/responsavel externo. Implica negociacao fora da equipe de desenvolvimento.
- **Aceitar:** manter a dependencia como condicao conhecida de entrega. Implica necessidade de aceite explicito dos stakeholders.
- **Evitar:** remover ou adiar funcionalidades dependentes da integracao. Implica possivel reducao de escopo e precisa de aprovacao.

**Acoes praticas em ordem de execucao:**
1. Identificar quais requisitos de entrega dependem obrigatoriamente do prontuario externo.
2. Separar funcionalidades bloqueadas, parcialmente dependentes e independentes da integracao.
3. Definir criterios de aceite especificos para cenarios com indisponibilidade ou instabilidade externa.
4. Avaliar alternativas de contingencia, como modo degradado, simulacao controlada para testes ou adiamento de escopo dependente.
5. Submeter as alternativas aos stakeholders para decisao.
6. Registrar a decisao e atualizar o planejamento do projeto.

### R-03 - Retrabalho por mudancas no fluxo de agendamento

**Estrategia primaria proposta para avaliacao:** Mitigar.

**Justificativa:** As mudancas ja foram solicitadas e atingem funcionalidade central. Mitigar permite controlar impacto por priorizacao, refinamento e replanejamento antes da implementacao.

**Alternativas viaveis e implicacoes:**
- **Evitar:** congelar temporariamente novas mudancas no fluxo de agendamento. Implica negociacao com stakeholders.
- **Aceitar:** absorver o retrabalho no planejamento. Implica possivel atraso ou reducao de escopo em outras frentes.

**Acoes praticas em ordem de execucao:**
1. Consolidar todas as alteracoes solicitadas para o fluxo de agendamento.
2. Validar se cada alteracao possui regra de negocio, criterio de aceite e prioridade.
3. Estimar impacto em codigo ja implementado, testes e documentacao.
4. Separar alteracoes obrigatorias para entrega de alteracoes que podem ser adiadas.
5. Atualizar planejamento considerando retrabalho e regressao.
6. Obter aprovacao dos stakeholders sobre escopo e prazo revisados.

### R-04 - Ambiguidade nas novas regras de negocio

**Estrategia primaria proposta para avaliacao:** Mitigar.

**Justificativa:** A ambiguidade pode ser reduzida com refinamento, exemplos e criterios de aceite. Implementar regras pouco claras aumentaria retrabalho e divergencia de entendimento.

**Alternativas viaveis e implicacoes:**
- **Evitar:** nao iniciar implementacao das regras ambiguas ate esclarecimento. Implica possivel impacto no prazo.
- **Aceitar:** implementar com base em entendimento atual. Implica maior chance de retrabalho em homologacao.

**Acoes praticas em ordem de execucao:**
1. Mapear regras de agendamento que ainda possuem interpretacao incerta.
2. Criar exemplos de cenarios aceitos, rejeitados e excecoes.
3. Validar os exemplos com stakeholders responsaveis pela regra.
4. Transformar os exemplos validados em criterios de aceite.
5. Revisar os criterios com desenvolvimento e teste antes da implementacao.
6. Registrar decisoes de regra para consulta futura.

### R-05 - Atraso por sobrecarga da equipe

**Estrategia primaria proposta para avaliacao:** Mitigar.

**Justificativa:** A sobrecarga ja foi relatada e ha dificuldade para cumprir prazos estimados. Mitigar permite reduzir impacto por priorizacao, replanejamento e controle de trabalho em progresso.

**Alternativas viaveis e implicacoes:**
- **Aceitar:** reconhecer o atraso e comunicar nova previsao. Implica ajuste formal de expectativa.
- **Evitar:** reduzir escopo ou congelar novas demandas. Implica decisao de produto/projeto.
- **Transferir:** buscar apoio temporario externo ou de outra equipe. Implica disponibilidade e tempo de alinhamento.

**Acoes praticas em ordem de execucao:**
1. Levantar atividades pendentes, em progresso e bloqueadas.
2. Identificar itens diretamente ligados a entrega critica.
3. Reestimar esforco considerando mudancas de requisitos e instabilidade da integracao.
4. Priorizar o trabalho por criticidade e dependencia.
5. Reduzir trabalho paralelo quando houver disputa pela mesma capacidade da equipe.
6. Comunicar aos stakeholders o impacto em prazo, escopo ou qualidade para decisao.

### R-06 - Gargalo de testes

**Estrategia primaria proposta para avaliacao:** Mitigar.

**Justificativa:** A existencia de apenas 1 tester para cobrir mudancas, regressao e integracao critica aumenta risco de atraso e defeitos nao detectados. Mitigar ajuda a proteger qualidade e previsibilidade.

**Alternativas viaveis e implicacoes:**
- **Transferir:** obter apoio temporario de teste de outra equipe ou fornecedor. Implica necessidade de alinhamento rapido sobre contexto.
- **Aceitar:** reduzir cobertura de testes com aprovacao formal. Implica maior risco de defeitos em homologacao ou producao.

**Acoes praticas em ordem de execucao:**
1. Priorizar cenarios de teste por criticidade, com foco em agendamento e integracao com prontuario.
2. Identificar cenarios minimos de regressao para funcionalidades ja implementadas.
3. Separar testes que podem ser executados por desenvolvedores sob orientacao do tester.
4. Avaliar possibilidade de automatizar verificacoes repetitivas, se houver estrutura disponivel.
5. Solicitar apoio temporario para testes se a cobertura minima nao couber na capacidade atual.
6. Registrar cobertura executada e lacunas aceitas para revisao dos stakeholders.

### R-07 - Defeitos de regressao em funcionalidades ja implementadas

**Estrategia primaria proposta para avaliacao:** Mitigar.

**Justificativa:** Alteracoes em funcionalidades centrais e ajustes de integracao podem afetar partes ja prontas. Mitigar por regressao dirigida reduz risco de perda de qualidade.

**Alternativas viaveis e implicacoes:**
- **Aceitar:** limitar regressao em fluxos considerados menos criticos. Implica risco residual documentado.
- **Evitar:** bloquear mudancas em modulos estaveis sem aprovacao. Implica menor flexibilidade para ajustes de negocio.

**Acoes praticas em ordem de execucao:**
1. Identificar funcionalidades ja implementadas que se relacionam com agendamento, notificacoes ou prontuario.
2. Definir conjunto minimo de testes de regressao para esses fluxos.
3. Executar regressao apos cada mudanca relevante no agendamento ou integracao.
4. Registrar defeitos encontrados e associar cada um a mudanca correspondente, quando possivel.
5. Priorizar correcao de regressao que afete fluxos criticos.
6. Atualizar a lista de regressao conforme novas regras forem estabilizadas.

### R-08 - Inconsistencia de dados entre sistema e prontuario

**Estrategia primaria proposta para avaliacao:** Mitigar.

**Justificativa:** A inconsistencia de dados pode comprometer confianca no fluxo integrado. Como nao ha evidencia de mecanismos de reconciliacao, a mitigacao deve focar rastreabilidade e tratamento de falhas.

**Alternativas viaveis e implicacoes:**
- **Transferir:** formalizar responsabilidades do sistema externo sobre respostas, contratos e mudancas de API. Implica dependencia de acordo externo.
- **Aceitar:** permitir inconsistencia residual com procedimento manual de reconciliacao. Implica custo operacional e risco de erro humano.

**Acoes praticas em ordem de execucao:**
1. Mapear quais dados sao enviados, recebidos ou sincronizados com o prontuario.
2. Definir criterios para identificar divergencia entre os sistemas.
3. Implementar ou validar registros de log para operacoes de integracao, se aplicavel.
4. Definir procedimento de reconciliacao para falhas ou divergencias.
5. Testar cenarios de falha, repeticao e indisponibilidade do sistema externo.
6. Validar com stakeholders se o tratamento proposto e aceitavel para entrega.

### R-09 - Notificacoes inconsistentes apos mudancas no agendamento

**Estrategia primaria proposta para avaliacao:** Mitigar.

**Justificativa:** As notificacoes podem depender de eventos e status alterados pelo novo fluxo de agendamento. A mitigacao reduz risco de comunicacoes incorretas sem exigir decisao imediata de escopo.

**Alternativas viaveis e implicacoes:**
- **Aceitar:** manter notificacoes com comportamento atual se nao forem criticas para aceite. Implica ciencia formal sobre possiveis inconsistencias.
- **Evitar:** impedir mudancas no agendamento sem mapear impacto em notificacoes. Implica maior controle, mas pode atrasar ajustes.

**Acoes praticas em ordem de execucao:**
1. Mapear eventos do fluxo de agendamento que disparam notificacoes.
2. Comparar eventos atuais com as novas regras e validacoes solicitadas.
3. Identificar notificacoes que podem ficar incorretas, duplicadas ou ausentes.
4. Atualizar criterios de teste para cobrir notificacoes afetadas.
5. Validar mensagens e momentos de disparo com stakeholders, se aplicavel.
6. Executar teste funcional dos cenarios alterados antes de homologacao.

## Checklist para Revisao Humana e Assinatura

- [ ] Confirmar se todos os riscos analisados em `riscos/analise.md` foram contemplados.
- [ ] Validar se as estrategias propostas sao viaveis para o contexto real do projeto.
- [ ] Selecionar a estrategia definitiva para cada risco ou solicitar ajustes.
- [ ] Confirmar responsaveis pelas acoes praticas escolhidas.
- [ ] Validar impactos de prazo, escopo, qualidade e coordenacao antes de aprovar respostas.
- [ ] Registrar decisoes e alteracoes no change-log.

**Responsavel pela revisao:** ______________________________

**Data da revisao:** ____ / ____ / ______

**Assinatura:** ____________________________________________

## Change-log de Revisao Humana

Use esta secao para registrar ajustes solicitados, decisoes tomadas e mudancas nas estrategias de resposta. Este documento deve preservar o historico de decisao.

| Versao | Data | Solicitante | Alteracao solicitada | Justificativa | Responsavel pela alteracao | Status |
| --- | --- | --- | --- | --- | --- | --- |
| 1.0 | 2026-07-12 | Geracao inicial por IA | Criacao das estrategias de resposta aos riscos. | Atender a etapa de sugestao de respostas sem escolha definitiva. | IA | Concluido |
|  |  |  |  |  |  |  |
