# Rota SCR

SCR significa **Security Change Request** e documenta uma alteração necessária para corrigir, reduzir ou prevenir um problema de segurança.

Antes de trabalhar em um SCR, ler integralmente em `PADRAO-DO-ACERVO.md` as seções `Processo de análise antes da documentação`, `Padrão geral de linguagem documental` e `Modelo obrigatório de SCR`. O padrão vivo prevalece sobre este resumo.

## Estrutura oficial

1. Resumo do problema
2. Contexto
3. Comportamento identificado
4. Comportamento esperado
5. Escopo afetado
6. Impacto potencial
7. Requisitos de Segurança
8. Critérios de aceite
9. Fora do escopo

As orientações internas do modelo não devem aparecer no SCR final.

## Conduta específica

- Manter a linguagem simples e direta, utilizando termos técnicos somente quando necessários para precisão.
- Não incluir prioridade.
- Diferenciar comportamento, escopo e impacto confirmados dos potenciais ou ainda não verificados.
- Não apresentar uma possibilidade como fato.
- Não ensinar como explorar a falha nem determinar a solução técnica.
- Não registrar credenciais, tokens, dados pessoais, informações de clientes ou outras evidências sensíveis.
- Referenciar evidências sensíveis mantidas em local controlado quando necessário.
- Preservar os fluxos legítimos na definição do comportamento esperado e nos critérios.
- Identificar Requisitos de Segurança como `RS-01`, `RS-02`, `RS-03` e manter os identificadores estáveis.
- Identificar critérios como `CA-01`, `CA-02`, `CA-03` e relacioná-los aos RS sempre que possível.
- Não inventar gravidade, exploração, obrigação legal, prazo, CVE, classificação de dados, impacto ou controle técnico.

O SCR pode existir sozinho ou se relacionar a PRD e REQ quando a alteração de segurança também afetar o comportamento do produto. A existência do SCR não torna os outros documentos obrigatórios.

Entregar o SCR completo em texto para revisão; não salvar o arquivo oficial.
