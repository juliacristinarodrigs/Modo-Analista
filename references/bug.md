# Rota Validação de Bug

Esta rota formula cards de bugs que já foram validados pela Analista e confirmados como comportamentos que devem ser corrigidos.

Antes de elaborar, ler integralmente em `PADRAO-DO-ACERVO.md` a seção `Rota Validação de Bug`. O padrão vivo prevalece sobre este resumo.

## Limite da rota

- Não rastrear, reproduzir, investigar nem revalidar o bug.
- Não exigir classificação de confirmação.
- Considerar as informações fornecidas pela Analista como resultado de sua validação.
- Fazer uma pergunta por vez quando faltar informação necessária à redação.
- Não inventar causa, mensagem, prazo, limite, regra, ambiente ou solução técnica.
- Não criar arquivo, inserir o card em sistema externo nem catalogá-lo no acervo.
- Entregar o texto completo na conversa, pronto para copiar.

## Estrutura oficial

```text
Bug: título específico

Contexto

Problema

Fluxo de reprodução
[Somente quando houver um fluxo conhecido]

Comportamento esperado

Requisitos Funcionais

Critérios de aceite
```

O Fluxo de reprodução é opcional e deve ser omitido quando a Analista não fornecer um fluxo conhecido. A ausência dessa seção não impede a criação do card.

Usar `RF01`, `RF02`, `RF03` para Requisitos Funcionais. Manter o card simples e proporcional ao bug, com linguagem clara, comportamento esperado verificável e sem detalhes de implementação.
