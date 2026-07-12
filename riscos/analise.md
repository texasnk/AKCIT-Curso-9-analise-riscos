# Etapa 2 - Analise Qualitativa dos Riscos

Documento gerado para analisar qualitativamente os riscos previamente identificados em `riscos/identificacao.md`, descrevendo impactos, fatores condicionantes e posicionamento em matriz de probabilidade versus impacto. A analise considera apenas as informacoes fornecidas sobre o projeto; quando houver incerteza, ela esta indicada explicitamente.

**Timestamp de geracao:** 2026-07-12 19:29:04 -03:00

## Criterios Utilizados

- **Probabilidade qualitativa:** Baixa, Media ou Alta.
- **Impacto qualitativo:** Baixo, Medio ou Alto.
- Nao foram atribuidos valores numericos de probabilidade, impacto ou severidade.
- A classificacao considera evidencias do contexto informado, como instabilidade ja observada, criticidade da integracao externa, mudancas de requisitos e carga de trabalho da equipe.

## Resumo da Analise Estruturada

| ID | Risco | Impactos principais | Fatores condicionantes | Probabilidade | Impacto |
| --- | --- | --- | --- | --- | --- |
| R-01 | Instabilidade na integracao com o prontuario externo | Atrasos, retrabalho tecnico, falhas em testes integrados e risco de bloqueio de funcionalidades dependentes. | Falta de documentacao clara da API, mudancas recentes no sistema externo e criticidade da integracao. | Alta | Alto |
| R-02 | Dependencia critica de sistema externo para a entrega | Bloqueio de entrega, dificuldade de aceite e dependencia de resolucoes fora do controle direto da equipe. | Integracao externa declarada como critica e ausencia de informacao sobre plano de contingencia. | Alta | Alto |
| R-03 | Retrabalho por mudancas no fluxo de agendamento | Reestimativa de prazo, aumento de esforco, alteracao de codigo ja implementado e necessidade de regressao. | Alteracoes solicitadas por stakeholders em validacoes e regras de negocio durante fase intermediaria. | Alta | Alto |
| R-04 | Ambiguidade nas novas regras de negocio | Implementacao incorreta, desalinhamento com stakeholders e retrabalho durante homologacao. | Novas regras de agendamento ainda exigem validacao quanto a criterios de aceite e exemplos de negocio. | Media | Medio |
| R-05 | Atraso por sobrecarga da equipe | Descumprimento de prazos, reducao de previsibilidade e possivel acumulacao de atividades em progresso. | Equipe relatou aumento da carga de trabalho e dificuldade para cumprir estimativas iniciais. | Alta | Alto |
| R-06 | Gargalo de testes | Atraso na validacao, menor cobertura de regressao e maior chance de defeitos chegarem a homologacao. | Apenas 1 tester para funcionalidades implementadas, em progresso, mudancas no agendamento e integracao critica. | Alta | Alto |
| R-07 | Defeitos de regressao em funcionalidades ja implementadas | Perda de qualidade em fluxos existentes, retrabalho e instabilidade em funcionalidades antes consideradas prontas. | Mudancas no agendamento e ajustes de integracao podem afetar partes ja implementadas. | Media | Alto |
| R-08 | Inconsistencia de dados entre sistema e prontuario | Divergencia de informacoes, falhas operacionais e dificuldade de confiabilidade no fluxo integrado. | Instabilidade da integracao e dependencia de sincronizacao com o sistema externo de prontuario. | Media | Alto |
| R-09 | Notificacoes inconsistentes apos mudancas no agendamento | Comunicacoes incorretas, ausentes ou disparadas no momento inadequado, afetando a experiencia do usuario. | Notificacoes podem depender de eventos e status alterados pelas novas regras de agendamento. | Media | Medio |

## Analise Estruturada dos Riscos

### R-01 - Instabilidade na integracao com o prontuario externo

**Risco:** Instabilidade na integracao com o prontuario externo.

**Descricao:** A integracao com o sistema externo pode continuar apresentando falhas ou comportamento inconsistente devido a documentacao insuficiente da API e mudancas recentes no sistema de prontuario.

**Possiveis impactos no projeto:** Pode gerar atraso em desenvolvimento e testes integrados, aumento de esforco para diagnostico, retrabalho tecnico e dificuldade para concluir funcionalidades dependentes da integracao.

**Fatores que influenciam a ocorrencia:** Falta de documentacao clara, mudancas recentes no sistema externo, dependencia de fornecedor ou equipe externa e criticidade da integracao para a entrega.

**Probabilidade qualitativa:** Alta.

**Impacto qualitativo:** Alto.

**Justificativa da classificacao:** A instabilidade ja foi observada no contexto informado, e a integracao e critica para a entrega. Portanto, a chance de recorrencia e alta e o impacto potencial tambem e alto.

### R-02 - Dependencia critica de sistema externo para a entrega

**Risco:** Dependencia critica de sistema externo para a entrega.

**Descricao:** A entrega do projeto pode depender de disponibilidade, estabilidade, regras e suporte de um sistema externo que nao esta sob controle direto da equipe do projeto.

**Possiveis impactos no projeto:** Pode bloquear funcionalidades essenciais, dificultar aceite, comprometer o cronograma e exigir negociacao com partes externas.

**Fatores que influenciam a ocorrencia:** A integracao foi definida como critica para a entrega, e nao foram fornecidas informacoes sobre plano de contingencia, ambiente estavel de testes ou acordo formal de suporte.

**Probabilidade qualitativa:** Alta.

**Impacto qualitativo:** Alto.

**Justificativa da classificacao:** A dependencia ja existe e afeta uma parte critica do projeto. Como ha instabilidade associada ao sistema externo, a exposicao ao risco e elevada.

### R-03 - Retrabalho por mudancas no fluxo de agendamento

**Risco:** Retrabalho por mudancas no fluxo de agendamento.

**Descricao:** Alteracoes solicitadas por stakeholders em validacoes e regras de negocio podem afetar funcionalidades ja desenvolvidas ou parcialmente implementadas.

**Possiveis impactos no projeto:** Pode aumentar esforco de desenvolvimento, exigir replanejamento, ampliar testes de regressao e provocar atraso em entregas planejadas.

**Fatores que influenciam a ocorrencia:** O projeto esta em fase intermediaria, parte das funcionalidades ja foi implementada e as mudancas foram solicitadas apos o inicio do desenvolvimento.

**Probabilidade qualitativa:** Alta.

**Impacto qualitativo:** Alto.

**Justificativa da classificacao:** As mudancas ja foram solicitadas e atingem o fluxo de agendamento, que e uma funcionalidade central do sistema descrito. O impacto tende a ser alto por envolver codigo, testes e validacao de negocio.

### R-04 - Ambiguidade nas novas regras de negocio

**Risco:** Ambiguidade nas novas regras de negocio.

**Descricao:** As novas validacoes e regras de negocio do agendamento podem ser interpretadas de maneira diferente por desenvolvedores, tester e stakeholders.

**Possiveis impactos no projeto:** Pode causar implementacao divergente da expectativa dos stakeholders, defeitos funcionais, retrabalho e demora na homologacao.

**Fatores que influenciam a ocorrencia:** Nao foram informados criterios de aceite, exemplos de cenarios, responsavel por decisao de regra ou documentacao detalhada das alteracoes.

**Probabilidade qualitativa:** Media.

**Impacto qualitativo:** Medio.

**Justificativa da classificacao:** Ha incerteza sobre o nivel de detalhamento das regras. O risco e relevante, mas sua ocorrencia depende da qualidade da documentacao e da validacao feita com stakeholders.

### R-05 - Atraso por sobrecarga da equipe

**Risco:** Atraso por sobrecarga da equipe.

**Descricao:** A equipe pode nao conseguir cumprir os prazos inicialmente estimados devido ao aumento de carga de trabalho relatado.

**Possiveis impactos no projeto:** Pode gerar atraso no cronograma, acumulacao de tarefas, reducao de previsibilidade e pressao sobre qualidade ou escopo.

**Fatores que influenciam a ocorrencia:** Equipe composta por 4 desenvolvedores e 1 tester, mudancas de requisitos em andamento, necessidade de estabilizar integracao critica e dificuldade ja relatada para cumprir estimativas.

**Probabilidade qualitativa:** Alta.

**Impacto qualitativo:** Alto.

**Justificativa da classificacao:** O aumento de carga e a dificuldade de prazo ja foram reportados. Como ainda ha funcionalidades em progresso e retrabalho potencial, a probabilidade e o impacto sao altos.

### R-06 - Gargalo de testes

**Risco:** Gargalo de testes.

**Descricao:** A capacidade de testes pode ser insuficiente para validar funcionalidades implementadas, funcionalidades em progresso, novas regras de agendamento e integracao externa critica.

**Possiveis impactos no projeto:** Pode atrasar validacoes, reduzir cobertura de regressao, aumentar defeitos nao detectados e comprometer a qualidade percebida na homologacao.

**Fatores que influenciam a ocorrencia:** Existe apenas 1 tester informado para cobrir multiplos fluxos funcionais e uma integracao instavel. Nao ha informacao sobre automacao de testes ou apoio adicional.

**Probabilidade qualitativa:** Alta.

**Impacto qualitativo:** Alto.

**Justificativa da classificacao:** A combinacao de escopo funcional, mudancas de regras e integracao critica torna provavel o gargalo de validacao. O impacto e alto porque testes insuficientes podem afetar prazo e qualidade.

### R-07 - Defeitos de regressao em funcionalidades ja implementadas

**Risco:** Defeitos de regressao em funcionalidades ja implementadas.

**Descricao:** Alteracoes no fluxo de agendamento ou ajustes na integracao podem introduzir defeitos em funcionalidades ja construidas.

**Possiveis impactos no projeto:** Pode reduzir qualidade, gerar retrabalho, atrasar homologacao e comprometer a confianca em funcionalidades anteriormente consideradas estaveis.

**Fatores que influenciam a ocorrencia:** Parte das funcionalidades ja esta implementada, enquanto requisitos e integracao ainda sofrem alteracoes. Nao foi informado nivel de cobertura de regressao.

**Probabilidade qualitativa:** Media.

**Impacto qualitativo:** Alto.

**Justificativa da classificacao:** A ocorrencia depende da abrangencia das mudancas e da cobertura de testes. O impacto e alto porque regressao em funcionalidades existentes pode atrasar a entrega e afetar a percepcao de qualidade.

### R-08 - Inconsistencia de dados entre sistema e prontuario

**Risco:** Inconsistencia de dados entre sistema e prontuario.

**Descricao:** Falhas de integracao podem causar diferencas entre informacoes registradas no sistema desenvolvido e no prontuario externo.

**Possiveis impactos no projeto:** Pode causar falhas operacionais, necessidade de reconciliacao manual, perda de confianca nos dados e dificuldade de validacao do fluxo integrado.

**Fatores que influenciam a ocorrencia:** A integracao e critica e ja apresenta instabilidade. Nao foram informados mecanismos de reconciliacao, logs de integracao ou tratamento de falhas transitorias.

**Probabilidade qualitativa:** Media.

**Impacto qualitativo:** Alto.

**Justificativa da classificacao:** Nao ha evidencia explicita de inconsistencia ja ocorrida, por isso a probabilidade foi classificada como media. O impacto e alto porque divergencia de dados em prontuario pode afetar diretamente o resultado esperado do sistema.

### R-09 - Notificacoes inconsistentes apos mudancas no agendamento

**Risco:** Notificacoes inconsistentes apos mudancas no agendamento.

**Descricao:** Mudancas no fluxo de agendamento podem alterar eventos, status ou condicoes que disparam notificacoes, resultando em comunicacoes incorretas ou ausentes.

**Possiveis impactos no projeto:** Pode afetar a experiencia do usuario, gerar confusao sobre consultas agendadas, demandar correcoes e ampliar testes funcionais.

**Fatores que influenciam a ocorrencia:** O sistema inclui notificacoes e o fluxo de agendamento esta passando por mudancas. Nao foi confirmado se as notificacoes dependem diretamente dos eventos alterados.

**Probabilidade qualitativa:** Media.

**Impacto qualitativo:** Medio.

**Justificativa da classificacao:** Ha dependencia plausivel entre agendamento e notificacoes, mas ela precisa ser validada. O impacto foi considerado medio porque pode afetar qualidade e uso do sistema, embora o contexto nao indique que notificacoes sejam tao criticas quanto a integracao com prontuario.

## Matriz Qualitativa de Riscos

| Probabilidade\Impacto | Baixo | Medio | Alto |
| --------------------- | ----- | ----- | ---- |
| **Alta** | Nenhum risco classificado | Nenhum risco classificado | R-01, R-02, R-03, R-05, R-06 |
| **Media** | Nenhum risco classificado | R-04, R-09 | R-07, R-08 |
| **Baixa** | Nenhum risco classificado | Nenhum risco classificado | Nenhum risco classificado |

## Incertezas e Pontos para Validacao

- Validar quais funcionalidades dependem diretamente da integracao com o prontuario externo.
- Validar se existe plano de contingencia para falhas ou indisponibilidade do sistema externo.
- Validar se as novas regras de agendamento possuem criterios de aceite, exemplos e aprovacao formal.
- Validar cobertura de testes, existencia de automacao e capacidade real do tester unico informado.
- Validar se notificacoes sao disparadas diretamente por eventos alterados no fluxo de agendamento.
- Validar se existem mecanismos de log, reconciliacao ou reprocessamento para inconsistencias com o prontuario.

## Checklist para Revisao Humana e Assinatura

- [ ] Confirmar se as classificacoes de probabilidade estao aderentes a realidade atual do projeto.
- [ ] Confirmar se as classificacoes de impacto refletem os criterios de prazo, esforco, qualidade e coordenacao.
- [ ] Revisar se algum risco deve mudar de posicao na matriz qualitativa.
- [ ] Validar incertezas registradas e complementar evidencias, quando disponiveis.
- [ ] Confirmar se a matriz deve ser usada como entrada para priorizacao e planejamento de respostas.
- [ ] Registrar aprovacao ou solicitar ajustes no change-log.

**Responsavel pela revisao:** ______________________________

**Data da revisao:** ____ / ____ / ______

**Assinatura:** ____________________________________________

## Change-log de Revisao Humana

Use esta secao para registrar solicitacoes de ajuste feitas durante revisao humana. Alteracoes posteriores devem manter historico de decisao.

| Versao | Data | Solicitante | Alteracao solicitada | Justificativa | Responsavel pela alteracao | Status |
| --- | --- | --- | --- | --- | --- | --- |
| 1.0 | 2026-07-12 | Geracao inicial por IA | Criacao da analise qualitativa e matriz de riscos. | Atender a etapa de analise estruturada dos riscos previamente identificados. | IA | Concluido |
|  |  |  |  |  |  |  |
