# Status do Projeto para Stakeholders

Documento de comunicacao objetiva sobre a situacao atual do projeto, principais riscos revisados, acoes recomendadas e decisoes necessarias para apoiar a continuidade do trabalho.

**Timestamp de geracao:** 2026-07-12 20:08:51 -03:00

**Ultima atualizacao:** 2026-07-12 21:32:23 -03:00

## Contexto Atual do Projeto

O projeto esta em fase intermediaria de desenvolvimento. Parte das funcionalidades ja foi implementada e outras seguem em andamento, incluindo cadastro de usuarios, agenda medica, agendamento de consultas, notificacoes e integracao com um sistema externo de prontuario.

Neste momento, a situacao exige decisoes de gestao para manter a entrega viavel e preservar a qualidade. Os pontos mais relevantes sao:

- A integracao com o prontuario externo e critica para a entrega e ja apresentou instabilidade.
- Novas regras foram solicitadas para o fluxo de agendamento, mas precisam ser avaliadas sem comprometer o funcionamento principal do sistema.
- A equipe relatou aumento de carga de trabalho e dificuldade para cumprir os prazos inicialmente estimados.
- A capacidade de testes e limitada, pois ha 1 tester para validar funcionalidades, mudancas, integracao e regressao.
- Foram identificados riscos adicionais relacionados a dados sensiveis, controle de acesso, concorrencia em agendamentos, indisponibilidade da API externa e estresse da equipe.

Ja esta em andamento:

- Identificacao e revisao dos riscos do projeto.
- Analise qualitativa de probabilidade e impacto.
- Definicao de estrategias possiveis de resposta aos riscos.
- Recalibragem do impacto das notificacoes, considerado menor quando comparado aos riscos de integracao, dados, agenda, seguranca e capacidade da equipe.

## Principais Pontos de Atencao

### 1. Integracao com o prontuario externo

A integracao continua sendo o principal ponto de dependencia externa. A instabilidade, a falta de documentacao clara, possiveis indisponibilidades da API e desalinhamentos de regras podem afetar diretamente a entrega.

**Impacto possivel:** atraso, bloqueio de funcionalidades dependentes, retrabalho, falhas em homologacao e necessidade de alinhamento com o responsavel pelo sistema externo.

**Direcao recomendada:** transferir parte desse risco por meio de SLA, contrato ou acordo formal, exigindo melhor documentacao, cronograma de manutencao, comunicacao previa de mudancas, canal de suporte e regras claras da API.

### 2. Mudancas no fluxo de agendamento e controle de escopo

As novas validacoes e regras solicitadas podem ser importantes, mas introduzi-las agora pode gerar retrabalho e pressionar ainda mais a equipe. O risco de crescimento nao controlado de escopo deve ser tratado de forma explicita.

**Impacto possivel:** atraso, perda de foco na entrega principal, aumento de testes, retrabalho e dificuldade de previsibilidade.

**Direcao recomendada:** evitar momentaneamente o novo escopo que nao seja essencial para o funcionamento principal do sistema. As novas demandas devem ser avaliadas e, quando possivel, planejadas para uma versao futura.

### 3. Sobrecarga da equipe e qualidade final

A equipe e composta por 4 desenvolvedores e 1 tester. Como ja houve relato de aumento de carga de trabalho e dificuldade com os prazos, existe risco de estresse da equipe e reducao da qualidade final.

**Impacto possivel:** mais defeitos, retrabalho, queda de produtividade, reducao de foco e menor previsibilidade da entrega.

**Direcao recomendada:** negociar uma nova data final, priorizar o escopo essencial, limitar novas demandas e reservar tempo realista para testes, correcao e estabilizacao.

### 4. Capacidade de testes

O gargalo de testes e um risco relevante. Como ha apenas 1 tester, a cobertura completa pode nao ser possivel dentro do prazo original.

**Impacto possivel:** validacao mais lenta, menor cobertura de regressao e maior chance de defeitos residuais.

**Direcao recomendada:** aceitar formalmente esse risco residual, pois a capacidade de testes deveria ter sido considerada desde o inicio do projeto. Ainda assim, recomenda-se priorizar testes dos fluxos mais criticos e mitigar regressao com testes automatizados sempre que viavel.

### 5. Qualidade, seguranca e confiabilidade dos dados

O sistema pode lidar com dados pessoais e dados relacionados a saude. Tambem ha risco de inconsistencias entre o sistema e o prontuario externo, acesso indevido por perfis mal definidos e falta de rastreabilidade para diagnosticar falhas.

**Impacto possivel:** exposicao indevida de dados, dificuldade de suporte, perda de confianca, retrabalho e problemas no aceite da entrega.

**Direcao recomendada:** validar controles de acesso, protecao de dados sensiveis, logs sem exposicao indevida, rastreabilidade de operacoes e mecanismos de reconciliacao com o prontuario.

### 6. Concorrencia em agendamentos

Como o sistema possui agenda medica e agendamento de consultas, pode haver risco de dois usuarios ou processos tentarem reservar ou alterar o mesmo horario ao mesmo tempo.

**Impacto possivel:** duplicidade de agendamentos, conflito de horarios, perda de atualizacao e retrabalho operacional.

**Direcao recomendada:** mitigar com validacao final de disponibilidade, regras de bloqueio, controle transacional ou outro mecanismo tecnico equivalente, conforme arquitetura do sistema.

### 7. Notificacoes

As notificacoes podem ser afetadas pelas mudancas no agendamento, mas o impacto foi considerado menor em comparacao aos demais riscos.

**Impacto possivel:** mensagens incorretas, ausentes ou disparadas no momento errado.

**Direcao recomendada:** tratar de forma proporcional. Validar notificacoes essenciais, mas sem deslocar foco dos riscos mais criticos.

## Acoes em Andamento ou Recomendadas

1. **Acionar o responsavel pelo prontuario externo com base em SLA ou contrato.**
   Solicitar documentacao atualizada da API, cronograma de manutencao, regras de negocio, cenarios de erro e canal formal de suporte.

2. **Separar escopo principal de novas solicitacoes.**
   Identificar o que e indispensavel para a entrega atual e o que pode ser planejado para uma versao futura.

3. **Negociar uma nova data final.**
   Replanejar considerando a integracao externa, mudancas de escopo, capacidade da equipe, capacidade de testes e tempo de estabilizacao.

4. **Aceitar formalmente o gargalo de testes ou decidir por reforco de capacidade.**
   Caso nao haja reforco, registrar quais cenarios serao priorizados e quais riscos residuais serao aceitos.

5. **Mitigar regressao com testes automatizados.**
   Priorizar automacao para fluxos criticos ja implementados, especialmente agendamento, integracao, controle de acesso e regras principais.

6. **Validar seguranca e acesso a dados sensiveis.**
   Confirmar perfis, permissoes, dados expostos em telas, logs, notificacoes e trafego com o sistema externo.

7. **Definir tratamento para indisponibilidade e falhas de integracao.**
   Avaliar mensagens controladas, reprocessamento, reconciliacao, logs e criterios de aceite para falhas externas.

8. **Validar concorrencia no agendamento.**
   Confirmar como o sistema evita duplicidade ou conflito em reservas simultaneas.

## Proximos Passos para Decisao

Os stakeholders precisam validar ou decidir os seguintes pontos:

1. **Escopo da entrega atual.**
   Confirmar quais funcionalidades devem permanecer na entrega principal e quais novas solicitacoes devem ir para backlog futuro.

2. **Nova data final ou aceite de risco de prazo.**
   Decidir se o prazo sera renegociado para refletir a realidade atual de escopo, integracao e capacidade da equipe.

3. **Acionamento formal do responsavel pelo sistema externo.**
   Confirmar quem fara a comunicacao e quais pontos serao cobrados via SLA, contrato ou acordo: documentacao, manutencao, suporte, disponibilidade e regras da API.

4. **Criterios de aceite da integracao.**
   Definir o que sera considerado aceitavel quando a API externa estiver instavel, indisponivel ou retornando regras divergentes.

5. **Criterios de aceite das regras de agendamento.**
   Aprovar regras, exemplos e excecoes antes de implementar mudancas adicionais.

6. **Nivel minimo de testes.**
   Confirmar a cobertura minima obrigatoria e aceitar formalmente as lacunas que nao puderem ser cobertas com a capacidade atual.

7. **Nivel minimo de seguranca e rastreabilidade.**
   Validar controles de acesso, tratamento de dados sensiveis, logs, auditoria e reconciliacao antes da entrega.

## Pontos que Exigem Validacao

- Quais funcionalidades dependem obrigatoriamente do prontuario externo.
- Se existe SLA, contrato ou acordo formal aplicavel ao sistema externo.
- Quais manutencoes, mudancas e indisponibilidades da API externa estao previstas.
- Quais novas regras de agendamento sao essenciais para a entrega atual.
- Se o prazo atual ainda e realista considerando escopo, equipe, testes e integracao.
- Se existem controles suficientes para dados sensiveis e perfis de usuario.
- Se ha mecanismos de controle de concorrencia para evitar conflitos de agenda.
- Se existem logs e rastreabilidade suficientes sem expor dados sensiveis.
- Quais lacunas de teste serao aceitas pelos stakeholders.

## Mensagem Final

O projeto continua viavel, mas a situacao atual exige decisao clara sobre escopo, prazo, integracao externa, testes e qualidade. O maior risco nao esta em um unico ponto isolado, mas na combinacao entre dependencia externa critica, novas mudancas de escopo, capacidade limitada de validacao e sobrecarga da equipe.

A recomendacao e proteger a entrega principal, formalizar responsabilidades do sistema externo, renegociar prazo quando necessario e aceitar conscientemente os riscos residuais. Essa abordagem ajuda a manter a qualidade, reduzir retrabalho e apoiar decisoes mais realistas e transparentes.
