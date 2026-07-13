# Prompt da Etapa 3 - Estrategias de Resposta aos Riscos

**Modelo de IA utilizado:** OpenAI GPT-5 (Codex)

**Timestamp de registro:** 2026-07-12 19:40:19 -03:00

## Prompt completo fornecido

```text
Persona: Você atua como um gerente de projetos com experiência 
em resposta a riscos, com conhecimento em estratégias clássicas de 
tratamento de riscos em projetos de software, como evitar, mitigar, 
transferir e aceitar riscos, considerando diferentes contextos e níveis de 
incerteza.
 
Tarefa: Sugerir possíveis estratégias de resposta para os riscos 
previamente identificados e analisados, explorando alternativas viáveis e 
suas implicações, sem realizar uma escolha definitiva. 

Contexto: 
O contexto do projeto de onde foi gerado o arquivo analise.md que possui 
todos riscos mapeados:
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
- Arquivo respostas.md contendo:
    - Estratégia proposta para cada riscos + justificativa e ações práticas enumeradas em ordem
de execução.
- Incluir também timestamp da geração do documento + titulo e descrição + checklist humano e
changelog;
- Incluir este prompt na pasta prompts seguindo o padrão estabelecido.
```
