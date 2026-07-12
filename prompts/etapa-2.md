# Prompt da Etapa 2 - Analise Qualitativa de Riscos

**Modelo de IA utilizado:** OpenAI GPT-5 (Codex)

**Timestamp de registro:** 2026-07-12 19:31:50 -03:00

## Prompt completo fornecido

```text
Persona: Você atua como um analista de riscos em projetos de 
software, com experiência na análise qualitativa de riscos e aplicação de 
matrizes de probabilidade e impacto.  

Tarefa: Realizar uma análise estruturada dos riscos previamente 
identificados, descrevendo seus impactos e fatores associados, e 
posteriormente organizá-los em uma matriz qualitativa de probabilidade 
vs. impacto, para apoiar a compreensão dos riscos. 

Contexto:
O contexto do projeto de onde foi gerado o arquivo identificacao.md que possui 
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
Apresente o resultado em formato estruturado, conforme o modelo 
abaixo: 
- Tabela simples um resumo da análise estruturada dos riscos, 
explicação dos impactos e identificação de fatores condicionantes;
- Também incluir checklist + changelog de mudanças;
- De maneira mais detalhada:
1.
Análise estruturada dos riscos  
Para cada risco:  
○ Risco: nome ou descrição breve; 
○ Descrição: detalhamento do risco;  
○ Possíveis impactos no projeto: impactos potenciais em 
prazo, esforço, qualidade ou coordenação;  
○ Fatores que influenciam a ocorrência: condições, 
dependências ou características do projeto que aumentam 
ou reduzem a probabilidade de ocorrência  
○ Probabilidade (qualitativa): Baixa / Média / Alta 
○ Impacto (qualitativo): Baixo / Médio / Alto   
○ Justificativa da classificação  

2. Matriz Qualitativa de Riscos  
| Probabilidade\Impacto | Baixo | Médio | Alto | 
| ----------------------- | ----- | ----- | ---- | 
| **Alta**                
| **Média**               
| **Baixa**               
|       
|       
|       
|       
Restrições e diretrizes:  
|      
|       
|       
| 
|      
|      
| 
| 
● Não atribuir valores numéricos de probabilidade ou impacto. 
● Indicar incertezas quando necessário.
```
