# Prompt da Etapa 1 - Identificacao de Riscos

**Modelo de IA utilizado:** OpenAI GPT-5 (Codex)

**Timestamp de registro:** 2026-07-12 19:16:41 -03:00

## Prompt completo fornecido

```text
Persona: 
Você atua como um especialista em gerenciamento de 
riscos em projetos de software, com experiência na identificação de riscos 
técnicos, organizacionais e de processo, especialmente em contextos de 
alta incerteza e mudanças.

Tarefa:
Identificar possíveis riscos associados ao projeto, com base nas 
informações fornecidas, considerando fatores que podem impactar o 
andamento, a qualidade ou os resultados do projeto. 

Contexto: 
● Trata-se de um projeto de desenvolvimento de software, o
sistema inclui funcionalidades como cadastro de 
usuários, gestão de agenda médica, agendamento de consultas, notificações 
e integração com um sistema externo de prontuário. 
O projeto encontra-se em fase intermediária de desenvolvimento, com 
parte das funcionalidades já implementadas e outras ainda em progresso. 
● A integração com o sistema de prontuário apresentou 
instabilidade, devido à falta de documentação clara de 
Application Programming Interface (API) e mudanças recentes 
no sistema externo; 
● Stakeholders solicitaram alterações em requisitos relacionados ao 
fluxo de agendamento, incluindo novas validações e regras de 
negócio; 
● A equipe de desenvolvimento relatou aumento da carga de 
trabalho, com dificuldades para cumprir prazos inicialmente 
estimados. 

Considere ainda que: 
● a equipe é composta por 4 desenvolvedores e 1 tester 
● a integração com o sistema externo é crítica para a entrega do projeto


Saída:  
Apresente o resultado em um arquivo identificacao.md  dentro da pasta riscos, 
formato estruturado, conforme o modelo abaixo: 
- Tabela com a lista de riscos identificados, descrição breve sobre cada risco,
contexto em que pode ocorrer;
- Incluir titulo claro sobre a etapa e objetivo do documento + descrição breve;
- Timestamp da geração do documento;
- Checklist para um humano revisar e assinar;
- Sessão para preenchimento das alterações do documento, caso a revisão humana
solicite ajustes, tudo deve ser documentado como um "change-log";
- Por fim crie, uma pasta 'prompts' e um arquivo 'etapa-1.md' incluir este prompt completo e modelo de IA
utilizado.

Restrições e diretrizes:  
● Não assumir informações que não foram fornecidas explicitamente.  
● Indicar claramente quando houver incerteza ou necessidade de 
validação. 
● Evitar generalizações excessivas ou riscos genéricos.
```
