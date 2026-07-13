# Etapa 3 - Estrategias de Resposta aos Riscos

Documento gerado para sugerir possiveis estrategias de resposta aos riscos previamente identificados e analisados em `riscos/analise.md`. As estrategias apresentadas sao propostas para avaliacao humana e podem ser ajustadas conforme validacao dos stakeholders, acordos contratuais e capacidade real da equipe.

**Timestamp de geracao:** 2026-07-12 19:40:19 -03:00

**Ultima atualizacao:** 2026-07-12 21:39:48 -03:00

## Premissas e Limites da Analise

- Foram considerados os riscos mapeados nas etapas anteriores, incluindo os riscos adicionais R-10 a R-17.
- As estrategias seguem categorias classicas de resposta a riscos: evitar, mitigar, transferir e aceitar.
- Algumas respostas foram ajustadas conforme diretrizes recebidas na revisao, especialmente para integracao externa, novo escopo, sobrecarga, testes e regressao.
- Quando houver dependencia de informacoes nao fornecidas, o ponto esta indicado como necessidade de validacao.

## Resumo das Estrategias Propostas

| ID | Risco | Estrategia primaria proposta para avaliacao | Alternativas viaveis | Implicacoes principais |
| --- | --- | --- | --- | --- |
| R-01 | Instabilidade na integracao com o prontuario externo | Transferir | Mitigar tecnicamente com resiliencia; aceitar risco residual documentado | Exige acionar SLA/contrato, cobrar melhoria de documentacao, cronograma de manutencao, alinhamento de regras e implementar protecoes como circuit breaker, timeout e retry controlado. |
| R-02 | Dependencia critica de sistema externo para a entrega | Transferir e mitigar | Aceitar com contingencia aprovada; evitar escopo dependente se necessario | Exige acordo formal com responsaveis externos, plano de continuidade, modo degradado e comunicacao clara ao usuario quando a integracao nao estiver disponivel. |
| R-03 | Retrabalho por mudancas no fluxo de agendamento | Evitar momentaneamente | Mitigar por refinamento; aceitar replanejamento | Permite proteger o funcionamento do sistema principal e avaliar novo escopo para versao futura. |
| R-04 | Ambiguidade nas novas regras de negocio | Mitigar | Evitar implementacao ate esclarecimento; aceitar risco residual em regras menores | Exige criterios de aceite e exemplos validados antes da implementacao. |
| R-05 | Atraso por sobrecarga da equipe | Mitigar e evitar agravamento | Aceitar nova data formalmente; reduzir escopo | Exige negociacao de prazo e priorizacao para reduzir pressao sobre a equipe. |
| R-06 | Gargalo de testes | Aceitar com registro formal | Mitigar parcialmente com priorizacao; transferir apoio de QA | Assume risco residual porque a capacidade de testes deveria ter sido planejada desde o inicio. |
| R-07 | Defeitos de regressao em funcionalidades ja implementadas | Mitigar | Aceitar risco residual em fluxos nao criticos | Exige testes automatizados, regressao priorizada e execucao recorrente em mudancas relevantes. |
| R-08 | Inconsistencia de dados entre sistema e prontuario | Mitigar e transferir | Aceitar com reconciliacao manual documentada | Exige logs, reconciliacao e alinhamento de responsabilidades com o sistema externo. |
| R-09 | Notificacoes inconsistentes apos mudancas no agendamento | Aceitar ou mitigar levemente | Evitar mudancas sem mapear eventos | Impacto menor que os demais riscos; requer apenas validacao proporcional ao seu peso no aceite. |
| R-10 | Vazamento ou exposicao indevida de dados sensiveis | Mitigar | Transferir parte por requisitos contratuais/fornecedor; evitar exposicao desnecessaria | Exige revisao de acesso, logs, criptografia, mascaramento e politicas de dados. |
| R-11 | Indisponibilidade da API externa de prontuario | Transferir | Mitigar com contingencia e resiliencia tecnica; aceitar indisponibilidade residual via criterio de aceite | Exige SLA, cronograma de manutencao, canal de suporte, comportamento esperado em falhas, circuit breaker, cache controlado, fila de reprocessamento e mensagens amigaveis ao usuario. |
| R-12 | Concorrencia em agendamentos | Mitigar | Aceitar risco residual se baixo volume for validado | Exige controle transacional, bloqueio, idempotencia ou verificacao final de disponibilidade. |
| R-13 | Falha de controle de acesso e perfis de usuario | Mitigar | Evitar liberar perfis sem validacao; aceitar apenas riscos residuais documentados | Exige matriz de permissoes e testes de autorizacao. |
| R-14 | Falta de rastreabilidade para diagnosticar falhas | Mitigar | Aceitar lacunas temporarias com ciencia dos stakeholders | Exige logs, trilha de auditoria, metricas, alertas e correlacao sem expor dados sensiveis. |
| R-15 | Crescimento nao controlado de escopo por novas solicitacoes | Evitar | Mitigar por processo de mudanca; aceitar apenas com replanejamento | Exige congelamento temporario, backlog futuro e decisao clara sobre escopo principal. |
| R-16 | Falhas de compatibilidade entre regras locais e regras do prontuario externo | Transferir e mitigar | Aceitar risco residual com criterios de rejeicao documentados | Exige alinhamento de contrato/API, regras externas, cenarios de rejeicao, validacao antecipada e mensagens compreensiveis quando uma regra externa bloquear a operacao. |
| R-17 | Estresse da equipe e reducao da qualidade final | Mitigar e evitar agravamento | Aceitar nova data; reduzir escopo | Exige renegociacao de prazo, limite de trabalho em progresso e protecao da qualidade. |

## Respostas Propostas por Risco

### R-01 - Instabilidade na integracao com o prontuario externo

**Estrategia primaria proposta para avaliacao:** Transferir.

**Justificativa:** Como a instabilidade esta associada a um sistema externo critico, parte relevante do risco pode ser transferida por meio de SLA, contrato, compromisso formal de suporte e exigencia de melhor documentacao. A equipe interna ainda pode mitigar tecnicamente, mas nao controla sozinha a qualidade, disponibilidade e mudancas do sistema externo.

**Alternativas viaveis e implicacoes:**
- **Mitigar:** criar tratamento de falhas, testes integrados, monitoramento e padroes de resiliencia. Reduz impacto, mas nao elimina dependencia externa.
- **Aceitar:** seguir com instabilidade residual documentada. Exige aceite formal dos stakeholders.

**Acoes praticas em ordem de execucao:**
1. Consolidar evidencias das falhas de integracao, incluindo cenarios, respostas da API e impacto observado.
2. Acionar responsaveis pelo sistema externo com base no SLA ou contrato existente.
3. Solicitar melhoria da documentacao da API, exemplos de uso, regras de negocio e cenarios de erro.
4. Solicitar cronograma de manutencoes, mudancas previstas e janelas de indisponibilidade.
5. Definir timeouts para evitar que o usuario fique aguardando indefinidamente.
6. Implementar circuit breaker para suspender temporariamente chamadas a API externa quando houver falhas repetidas.
7. Usar retry controlado com backoff para falhas transitorias, evitando sobrecarregar a API externa.
8. Definir mensagens amigaveis e orientadas a acao para o usuario quando a integracao estiver indisponivel.
9. Definir canal formal de suporte e prazos de resposta para incidentes da integracao.
10. Revalidar os fluxos integrados apos retorno do responsavel externo.

### R-02 - Dependencia critica de sistema externo para a entrega

**Estrategia primaria proposta para avaliacao:** Transferir e mitigar.

**Justificativa:** A entrega depende de um sistema externo. A parte relacionada a disponibilidade, documentacao, mudancas e suporte deve ser transferida para o responsavel externo por acordo formal; a equipe do projeto deve mitigar com contingencia e criterios de aceite.

**Alternativas viaveis e implicacoes:**
- **Aceitar:** reconhecer a dependencia como condicao da entrega. Exige decisao explicita dos stakeholders.
- **Evitar:** adiar funcionalidades dependentes da integracao. Pode reduzir escopo da entrega principal.

**Acoes praticas em ordem de execucao:**
1. Identificar quais funcionalidades dependem obrigatoriamente do prontuario externo.
2. Formalizar responsabilidades do sistema externo quanto a disponibilidade, suporte e comunicacao de mudancas.
3. Definir criterios de aceite para cenarios em que o sistema externo esteja indisponivel ou instavel.
4. Definir modo degradado para manter o sistema utilizavel quando a integracao externa falhar, quando isso for aceitavel para o negocio.
5. Avaliar cache temporario ou leitura de dados previamente sincronizados, respeitando seguranca e consistencia.
6. Avaliar simulacao controlada para testes ou adiamento de escopo dependente.
7. Submeter alternativas aos stakeholders para decisao.
8. Atualizar planejamento e comunicacao do projeto conforme a decisao.

### R-03 - Retrabalho por mudancas no fluxo de agendamento

**Estrategia primaria proposta para avaliacao:** Evitar momentaneamente.

**Justificativa:** O novo escopo pode ser evitado neste momento para proteger a entrega do sistema principal. As novas demandas devem ser avaliadas, refinadas e possivelmente planejadas para uma versao futura, evitando retrabalho imediato e perda de foco.

**Alternativas viaveis e implicacoes:**
- **Mitigar:** aceitar parte das mudancas apos avaliacao de impacto e priorizacao.
- **Aceitar:** absorver o retrabalho agora. Pode gerar atraso e pressao adicional sobre a equipe.

**Acoes praticas em ordem de execucao:**
1. Separar escopo original do fluxo de agendamento e novo escopo solicitado.
2. Avaliar impacto das novas regras em prazo, testes, integracao e funcionalidades ja implementadas.
3. Classificar cada mudanca como essencial para a entrega principal ou candidata a versao futura.
4. Propor congelamento temporario do novo escopo que nao seja essencial.
5. Registrar itens adiados em backlog futuro com justificativa.
6. Obter aprovacao dos stakeholders para manter foco no funcionamento principal do sistema.

### R-04 - Ambiguidade nas novas regras de negocio

**Estrategia primaria proposta para avaliacao:** Mitigar.

**Justificativa:** A ambiguidade pode ser reduzida com criterios de aceite, exemplos e validacao antes da implementacao. Sem esse alinhamento, o risco de retrabalho aumenta.

**Alternativas viaveis e implicacoes:**
- **Evitar:** nao implementar regras ambiguas ate esclarecimento.
- **Aceitar:** implementar com entendimento atual, assumindo maior chance de ajuste posterior.

**Acoes praticas em ordem de execucao:**
1. Mapear regras de agendamento ainda indefinidas ou com interpretacao incerta.
2. Criar exemplos de cenarios aceitos, rejeitados e excecoes.
3. Validar exemplos com stakeholders responsaveis pela regra.
4. Converter exemplos aprovados em criterios de aceite.
5. Revisar criterios com desenvolvimento e teste.
6. Registrar decisoes para consulta futura.

### R-05 - Atraso por sobrecarga da equipe

**Estrategia primaria proposta para avaliacao:** Mitigar e evitar agravamento.

**Justificativa:** A sobrecarga pode ser reduzida com renegociacao de uma nova data final, repriorizacao e reducao de trabalho paralelo. Isso evita que a pressao continue aumentando e protege qualidade e previsibilidade.

**Alternativas viaveis e implicacoes:**
- **Aceitar:** formalizar nova data ou atraso como decisao do projeto.
- **Evitar:** congelar novas demandas e reduzir escopo nao essencial.
- **Transferir:** buscar apoio temporario, se houver disponibilidade.

**Acoes praticas em ordem de execucao:**
1. Levantar atividades pendentes, em progresso e bloqueadas.
2. Reestimar esforco considerando mudancas, integracao externa e capacidade real da equipe.
3. Propor nova data final baseada em capacidade realista.
4. Priorizar o escopo indispensavel para a entrega principal.
5. Reduzir trabalho paralelo e limitar novas entradas de escopo.
6. Formalizar com stakeholders a nova data, escopo e criterios de aceite.

### R-06 - Gargalo de testes

**Estrategia primaria proposta para avaliacao:** Aceitar com registro formal.

**Justificativa:** A equipe possui apenas 1 tester, e essa capacidade deveria ter sido considerada no planejamento inicial do projeto. Neste momento, o risco pode ser aceito formalmente, com ciencia dos stakeholders sobre possiveis impactos em cobertura, prazo de validacao e defeitos residuais.

**Alternativas viaveis e implicacoes:**
- **Mitigar:** priorizar testes criticos e automatizar verificacoes repetitivas quando viavel.
- **Transferir:** obter apoio temporario de QA externo ou de outra equipe.

**Acoes praticas em ordem de execucao:**
1. Registrar formalmente a limitacao de capacidade de testes.
2. Definir cobertura minima obrigatoria para fluxos criticos.
3. Priorizar testes de agendamento, integracao com prontuario, controle de acesso e regressao.
4. Documentar cenarios que ficarao fora da cobertura por restricao de capacidade.
5. Obter ciencia e aceite dos stakeholders sobre o risco residual.
6. Reavaliar a necessidade de apoio adicional caso a cobertura minima nao seja suficiente.

### R-07 - Defeitos de regressao em funcionalidades ja implementadas

**Estrategia primaria proposta para avaliacao:** Mitigar.

**Justificativa:** Defeitos de regressao podem ser reduzidos com ferramentas de testes automatizados, execucao recorrente de regressao e criterios claros para validar fluxos ja implementados.

**Alternativas viaveis e implicacoes:**
- **Aceitar:** limitar regressao em fluxos de menor criticidade, com risco residual documentado.
- **Evitar:** restringir mudancas em modulos estaveis sem avaliacao de impacto.

**Acoes praticas em ordem de execucao:**
1. Identificar fluxos implementados que podem ser afetados por mudancas no agendamento ou integracao.
2. Definir testes de regressao prioritarios.
3. Selecionar ferramentas ou estrutura existente para automatizar cenarios repetitivos.
4. Automatizar inicialmente os fluxos mais criticos e mais propensos a regressao.
5. Executar regressao automatizada a cada mudanca relevante.
6. Monitorar defeitos encontrados e ampliar cobertura conforme necessidade.

### R-08 - Inconsistencia de dados entre sistema e prontuario

**Estrategia primaria proposta para avaliacao:** Mitigar e transferir.

**Justificativa:** A equipe pode mitigar com logs, reconciliacao e tratamento de falhas, mas parte da responsabilidade deve ser alinhada com o sistema externo, principalmente contrato da API, respostas esperadas e mudancas de comportamento.

**Alternativas viaveis e implicacoes:**
- **Aceitar:** permitir inconsistencia residual com procedimento manual de reconciliacao.
- **Transferir:** formalizar responsabilidades do sistema externo sobre contratos, mudancas e disponibilidade.

**Acoes praticas em ordem de execucao:**
1. Mapear dados sincronizados com o prontuario.
2. Definir criterios de divergencia entre os sistemas.
3. Implementar ou validar logs de integracao e correlacao de operacoes.
4. Definir procedimento de reconciliacao para falhas.
5. Avaliar fila de reprocessamento para operacoes que falharem por indisponibilidade temporaria.
6. Indicar status claro ao usuario quando uma operacao estiver pendente de sincronizacao.
7. Alinhar com o responsavel externo o comportamento esperado da API.
8. Validar com stakeholders se o tratamento e aceitavel para entrega.

### R-09 - Notificacoes inconsistentes apos mudancas no agendamento

**Estrategia primaria proposta para avaliacao:** Aceitar ou mitigar levemente.

**Justificativa:** O impacto das notificacoes foi classificado como baixo em relacao aos demais riscos. O risco pode ser aceito se as notificacoes nao forem criterio central de aceite, mantendo apenas validacoes proporcionais para evitar comunicacoes incorretas relevantes.

**Alternativas viaveis e implicacoes:**
- **Mitigar:** revisar eventos e mensagens afetadas pelas mudancas no agendamento.
- **Evitar:** nao alterar eventos de notificacao sem mapear impactos.

**Acoes praticas em ordem de execucao:**
1. Confirmar se notificacoes sao criterio obrigatorio de aceite.
2. Mapear eventos do agendamento que disparam notificacoes.
3. Validar apenas os cenarios de maior visibilidade para o usuario.
4. Registrar comportamento esperado das mensagens.
5. Aceitar risco residual caso notificacoes nao sejam criticas.
6. Corrigir apenas inconsistencias que afetem comunicacao essencial.

### R-10 - Vazamento ou exposicao indevida de dados sensiveis

**Estrategia primaria proposta para avaliacao:** Mitigar.

**Justificativa:** O sistema pode envolver dados pessoais e de saude. Esse risco deve ser reduzido por controles de seguranca, revisao de acesso, protecao de logs e boas praticas de armazenamento e trafego.

**Alternativas viaveis e implicacoes:**
- **Transferir:** exigir controles equivalentes de fornecedores ou sistemas externos por contrato.
- **Evitar:** remover exposicao desnecessaria de dados em telas, logs e notificacoes.

**Acoes praticas em ordem de execucao:**
1. Mapear dados sensiveis armazenados, trafegados e exibidos.
2. Revisar permissoes de acesso a dados de agenda e prontuario.
3. Validar criptografia em transito e em repouso, quando aplicavel.
4. Remover ou mascarar dados sensiveis de logs e mensagens.
5. Testar cenarios de acesso indevido.
6. Registrar pendencias de seguranca para decisao antes da entrega.

### R-11 - Indisponibilidade da API externa de prontuario

**Estrategia primaria proposta para avaliacao:** Transferir.

**Justificativa:** A disponibilidade da API externa depende do responsavel pelo sistema de prontuario. Por SLA e contrato, e possivel exigir informacoes de manutencao, tempos de resposta, janelas de indisponibilidade, suporte e qualidade da documentacao.

**Alternativas viaveis e implicacoes:**
- **Mitigar:** implementar contingencia local, mensagens controladas e reprocessamento.
- **Aceitar:** documentar indisponibilidade residual como risco assumido.

**Acoes praticas em ordem de execucao:**
1. Confirmar SLA, disponibilidade esperada e responsabilidades do sistema externo.
2. Solicitar cronograma de manutencoes e comunicacao previa de mudancas.
3. Definir procedimento de incidente para indisponibilidade da API.
4. Implementar circuit breaker para evitar repeticao de chamadas durante falhas persistentes.
5. Configurar timeouts curtos e mensagens de retorno claras para evitar espera indefinida.
6. Implementar retry com backoff apenas para falhas transitorias.
7. Avaliar cache controlado para dados que possam ser exibidos temporariamente sem comprometer seguranca ou consistencia.
8. Avaliar fila de reprocessamento para operacoes que possam ser concluidas depois.
9. Exibir estado claro ao usuario, como "servico temporariamente indisponivel" ou "sincronizacao pendente", quando aplicavel.
10. Testar comportamento do sistema quando a API externa falhar.
11. Registrar criterios de aceite para indisponibilidade externa.

### R-12 - Concorrencia em agendamentos

**Estrategia primaria proposta para avaliacao:** Mitigar.

**Justificativa:** Conflitos de agenda podem afetar diretamente a confiabilidade do sistema. A mitigacao deve focar em controle de concorrencia, validacao final de disponibilidade e operacoes idempotentes quando necessario.

**Alternativas viaveis e implicacoes:**
- **Aceitar:** apenas se o volume de uso simultaneo for validado como baixo e o risco residual for aprovado.

**Acoes praticas em ordem de execucao:**
1. Mapear operacoes concorrentes possiveis no agendamento.
2. Definir regra de bloqueio ou reserva temporaria de horario.
3. Implementar verificacao final de disponibilidade antes da confirmacao.
4. Avaliar idempotencia para evitar duplicidade em repeticoes de chamada.
5. Testar cenarios de agendamento simultaneo.
6. Registrar comportamento esperado em caso de conflito.

### R-13 - Falha de controle de acesso e perfis de usuario

**Estrategia primaria proposta para avaliacao:** Mitigar.

**Justificativa:** Como o sistema possui usuarios e pode expor agenda ou dados de prontuario, controles de autorizacao precisam ser revisados e testados antes da entrega.

**Alternativas viaveis e implicacoes:**
- **Evitar:** nao liberar perfis ou funcionalidades sem matriz de permissao validada.
- **Aceitar:** apenas riscos residuais de baixo impacto, documentados e aprovados.

**Acoes praticas em ordem de execucao:**
1. Definir perfis de usuario existentes e suas permissoes.
2. Criar matriz de acesso por funcionalidade e tipo de dado.
3. Validar regras de autorizacao com stakeholders.
4. Testar acessos permitidos e negados.
5. Corrigir inconsistencias de permissao encontradas.
6. Registrar perfis aprovados como criterio de aceite.

### R-14 - Falta de rastreabilidade para diagnosticar falhas

**Estrategia primaria proposta para avaliacao:** Mitigar.

**Justificativa:** Logs, trilhas de auditoria e correlacao ajudam a diagnosticar instabilidades, indisponibilidade e divergencias entre sistemas, reduzindo tempo de investigacao.

**Alternativas viaveis e implicacoes:**
- **Aceitar:** manter lacunas temporarias se nao houver tempo para ampliar observabilidade, com ciencia dos stakeholders.

**Acoes praticas em ordem de execucao:**
1. Definir eventos minimos que precisam ser rastreados.
2. Incluir identificadores de correlacao nas operacoes de integracao, se aplicavel.
3. Registrar falhas de integracao sem expor dados sensiveis.
4. Definir metricas e alertas para falhas repetidas, aumento de latencia e indisponibilidade da API externa.
5. Validar logs para agendamento, integracao e controle de acesso.
6. Definir responsavel por consulta e analise dos registros.
7. Revisar se a rastreabilidade atende aos cenarios criticos.

### R-15 - Crescimento nao controlado de escopo por novas solicitacoes

**Estrategia primaria proposta para avaliacao:** Evitar.

**Justificativa:** O crescimento de escopo, ou scope creep, deve ser evitado momentaneamente para garantir que o sistema principal funcione. Novas solicitacoes devem ser avaliadas e direcionadas para uma entrega futura quando nao forem essenciais.

**Alternativas viaveis e implicacoes:**
- **Mitigar:** adotar processo formal de mudanca com avaliacao de impacto.
- **Aceitar:** incorporar novas demandas apenas com replanejamento aprovado.

**Acoes praticas em ordem de execucao:**
1. Congelar temporariamente novas demandas nao essenciais.
2. Classificar solicitacoes novas por urgencia, valor e dependencia.
3. Avaliar impacto em prazo, qualidade, testes e integracao.
4. Sugerir itens nao essenciais para backlog de versao futura.
5. Aprovar formalmente qualquer excecao ao congelamento.
6. Comunicar aos stakeholders o impacto de aceitar novo escopo agora.

### R-16 - Falhas de compatibilidade entre regras locais e regras do prontuario externo

**Estrategia primaria proposta para avaliacao:** Transferir e mitigar.

**Justificativa:** Parte do risco vem de regras e validacoes do sistema externo, que devem ser esclarecidas pelo responsavel da API. A equipe interna deve mitigar garantindo que regras locais sejam compatibilizadas com contratos e cenarios de rejeicao.

**Alternativas viaveis e implicacoes:**
- **Aceitar:** manter risco residual apenas se rejeicoes forem documentadas e tratadas.

**Acoes praticas em ordem de execucao:**
1. Solicitar documentacao atualizada das regras e validacoes do prontuario.
2. Mapear regras locais de agendamento que dependem do sistema externo.
3. Identificar divergencias entre regras locais e regras externas.
4. Antecipar validacoes no sistema local quando as regras externas forem conhecidas.
5. Ajustar mensagens de erro para orientar o usuario quando a operacao for rejeitada pelo prontuario.
6. Testar cenarios de rejeicao pelo prontuario.
7. Registrar regras alinhadas como criterio de aceite.

## Tecnicas de Resiliencia e Experiencia do Usuario

As tecnicas abaixo podem reduzir o impacto de indisponibilidade, instabilidade ou lentidao do sistema externo. A aplicacao depende de validacao tecnica, requisitos de negocio e limites de consistencia de dados.

| Tecnica | Onde se aplica | Beneficio esperado | Cuidados / validacoes |
| --- | --- | --- | --- |
| Circuit breaker | Chamadas para a API externa de prontuario | Evita chamadas repetidas para um servico instavel e permite resposta mais rapida ao usuario. | Definir criterios para abrir/fechar circuito e mensagem adequada durante indisponibilidade. |
| Timeout controlado | Todas as chamadas externas criticas | Evita que o usuario fique aguardando indefinidamente. | Ajustar tempo limite conforme SLA, criticidade e experiencia esperada. |
| Retry com backoff | Falhas temporarias de rede ou indisponibilidade momentanea | Aumenta chance de sucesso sem exigir nova acao do usuario. | Evitar repeticoes agressivas que sobrecarreguem a API externa. |
| Fila de reprocessamento | Operacoes que podem ser concluidas depois | Permite registrar uma solicitacao e tentar sincronizar novamente mais tarde. | Validar se o negocio aceita operacoes pendentes e como isso sera exibido ao usuario. |
| Modo degradado | Fluxos parcialmente dependentes do prontuario | Mantem partes do sistema utilizaveis mesmo com falha externa. | Definir claramente o que pode funcionar sem o prontuario e o que deve ser bloqueado. |
| Cache controlado | Consultas de dados que podem ser reutilizados temporariamente | Reduz dependencia imediata da API externa e melhora tempo de resposta. | Validar validade dos dados, seguranca, privacidade e risco de informacao desatualizada. |
| Mensagens amigaveis e acionaveis | Falhas, indisponibilidade e rejeicoes de regra | Reduz frustracao e orienta o usuario sobre o que fazer. | Evitar termos tecnicos e nao expor detalhes internos ou dados sensiveis. |
| Status de sincronizacao | Operacoes pendentes com o prontuario | Aumenta transparencia quando uma acao ainda nao foi confirmada externamente. | Definir estados claros, como pendente, confirmado, falhou e requer acao. |
| Idempotencia | Criacao, alteracao e cancelamento de agendamentos | Evita duplicidade quando uma mesma operacao for reenviada. | Definir chaves de idempotencia e comportamento esperado em repeticoes. |
| Observabilidade e alertas | Integracao, agenda, seguranca e acesso | Permite identificar falhas antes que se tornem incidentes maiores. | Garantir logs suficientes sem registrar dados sensiveis em claro. |

### R-17 - Estresse da equipe e reducao da qualidade final

**Estrategia primaria proposta para avaliacao:** Mitigar e evitar agravamento.

**Justificativa:** A sobrecarga ja foi relatada e pode reduzir a qualidade final. Renegociar uma nova data final, limitar trabalho em progresso e proteger tempo de validacao ajuda a reduzir estresse e defeitos.

**Alternativas viaveis e implicacoes:**
- **Aceitar:** reconhecer formalmente que a data atual aumenta risco de qualidade.
- **Evitar:** reduzir escopo nao essencial e congelar novas demandas.
- **Transferir:** buscar apoio temporario, se houver disponibilidade.

**Acoes praticas em ordem de execucao:**
1. Avaliar sinais de sobrecarga, volume de trabalho em progresso e horas extras.
2. Identificar atividades que mais pressionam a equipe.
3. Negociar nova data final com base em capacidade real.
4. Reduzir ou adiar escopo nao essencial.
5. Reservar tempo explicito para testes, correcao e estabilizacao.
6. Acompanhar defeitos e retrabalho como indicadores de qualidade.

## Checklist para Revisao Humana e Assinatura

- [ ] Confirmar se todos os riscos analisados em `riscos/analise.md` foram contemplados.
- [ ] Validar se a transferencia de riscos externos pode ser sustentada por SLA, contrato ou acordo formal.
- [ ] Confirmar se o novo escopo deve ser evitado momentaneamente e planejado para versao futura.
- [ ] Validar se a nova data final sera negociada para reduzir sobrecarga.
- [ ] Confirmar aceite formal do gargalo de testes e seus riscos residuais.
- [ ] Validar estrategia de testes automatizados para regressao.
- [ ] Validar tecnicas de resiliencia para indisponibilidade da API externa, como circuit breaker, timeout, retry, cache, fila e modo degradado.
- [ ] Validar melhorias de experiencia do usuario para mensagens de erro, status de sincronizacao e operacoes pendentes.
- [ ] Confirmar responsaveis pelas acoes praticas escolhidas.
- [ ] Registrar decisoes e alteracoes no change-log.

**Responsavel pela revisao:** ______________________________

**Data da revisao:** ____ / ____ / ______

**Assinatura:** ____________________________________________

## Change-log de Revisao Humana

Use esta secao para registrar ajustes solicitados, decisoes tomadas e mudancas nas estrategias de resposta. Este documento deve preservar o historico de decisao.

| Versao | Data | Solicitante | Alteracao solicitada | Justificativa | Responsavel pela alteracao | Status |
| --- | --- | --- | --- | --- | --- | --- |
| 1.0 | 2026-07-12 | Geracao inicial por IA | Criacao das estrategias de resposta aos riscos. | Atender a etapa de sugestao de respostas sem escolha definitiva. | IA | Concluido |
| 1.1 | 2026-07-12 | Solicitacao do usuario | Ajuste das estrategias para riscos existentes e inclusao de respostas para R-10 a R-17. | Incorporar revisao humana sobre transferencia via SLA, controle de escopo, renegociacao de prazo, aceite do gargalo de testes, mitigacao por testes automatizados e respostas aos novos riscos. | IA | Concluido |
| 1.2 | 2026-07-12 | Solicitacao do usuario | Inclusao de tecnicas avancadas de resiliencia e melhorias de experiencia do usuario. | Reduzir impacto de indisponibilidade do sistema externo e orientar respostas mais claras ao usuario final. | IA | Concluido |
|  |  |  |  |  |  |  |
