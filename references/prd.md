# Rota PRD

O PRD registra o que se pretende implementar, por que a implementação é necessária, como a solução deve funcionar em nível de produto e qual resultado se espera alcançar.

Antes de trabalhar em um PRD, ler integralmente em `PADRAO-DO-ACERVO.md` as seções `Processo de análise antes da documentação`, `Padrão geral de linguagem documental` e `Modelo obrigatório de PRD`. O padrão vivo prevalece sobre este resumo.

## Momento de elaboração

Na maioria das demandas, não redigir o PRD imediatamente. Primeiro analisar, construir, melhorar, criar ou discutir a implementação em conjunto com a Analista. Identificar lacunas e conduzir as decisões necessárias, uma por vez.

Somente produzir o PRD completo quando o comportamento pretendido estiver bem definido e sem brechas identificadas. O PRD final não deve conter decisões funcionais pendentes.

## Estrutura oficial

1. Objetivo
2. Contexto
3. Problema
4. Solução Proposta
5. Usuários Impactados
6. Escopo da Entrega
7. Benefícios Esperados
8. Critérios de Aceite
9. Especificação da Interface, quando aplicável

As orientações internas usadas para explicar o modelo, incluindo `Finalidade`, `Deve responder`, `Deve conter`, `Não deve conter`, `Nível de detalhamento esperado` e `Evitar`, não devem aparecer no PRD final.

Objetivo, Contexto e Problema são partes centrais e devem ser explicados como para uma pessoa que ainda não conhece o assunto. Utilizar linguagem simples, direta e autossuficiente, mantendo o nível de detalhamento dos PRDs vigentes do acervo.

O PRD não deve conter requisitos funcionais ou regras de negócio formalmente identificados. Também não deve definir arquitetura, banco de dados, endpoints, classes, bibliotecas, algoritmos, estratégia técnica ou casos de teste completos.

## Extensão

- Faixa recomendada: 8 mil a 15 mil caracteres.
- Demandas complexas: até aproximadamente 20 mil caracteres.
- Limite máximo: aproximadamente 25 mil caracteres.

Remover repetições antes de reduzir explicações necessárias. Entregar o PRD completo em texto para revisão; não salvar o arquivo oficial.
