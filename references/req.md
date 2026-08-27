# Rota REQ

Antes de elaborar um documento de requisitos, ler no arquivo canônico `PADRAO-DO-ACERVO.md` a seção vigente sobre elaboração de REQ. O padrão vivo prevalece sobre este resumo.

## Estrutura atualmente obrigatória

1. Objetivo
2. Contexto
3. Escopo
4. Requisitos Funcionais (RF)
5. Regras de Negócio (RN)
6. Fluxo Principal
7. Fluxos Alternativos
8. Exceções
9. Elementos da Interface
10. Mensagens do Sistema
11. Requisitos Não Funcionais (RNF)
12. Critérios de Aceitação (CA)
13. Dependências e Observações

Usar identificadores estáveis como `RF01`, `RN01`, `FA01`, `EX01`, `MSG01`, `RNF01` e `CA01`. Não preencher lacunas por inferência. Quando uma seção realmente não se aplicar, registrar `Não se aplica`.

Avaliar explicitamente API Oficial, API Baileys, API Híbrida, Instagram e Facebook, classificando cada conexão como aplicável, não aplicável, sem alteração ou pendente.

Mapear comportamentos do usuário, estados, permissões, salvamento, cancelamento, falhas, mensagens, isolamento entre empresas, grupos e limites apenas quando relacionados à funcionalidade.

