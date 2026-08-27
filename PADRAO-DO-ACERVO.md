# Padrão de Organização do Acervo

## Finalidade

Este documento estabelece como classificar, nomear, versionar e catalogar as documentações do sistema. O objetivo é manter uma única fonte confiável de regras e preparar o acervo para consulta humana e por inteligência artificial.

## Hierarquia das pastas

Os documentos devem seguir a hierarquia:

```text
domínio do produto / módulo ou integração / ID-e-título-da-funcionalidade / documentos
```

Cada funcionalidade deve possuir um dossiê próprio. PRD, REQ, MIG e outros documentos referentes à mesma entrega ficam juntos nesse dossiê e compartilham o código da funcionalidade.

## Nome dos arquivos

Formato obrigatório:

```text
TIPO-DOMINIO-NNN - titulo-descritivo - vNN - STATUS.ext
```

Exemplo:

```text
REQ-INT-001 - integracao-com-maximus-pdv - v01 - IMPLEMENTADO.pdf
```

Regras:

- Usar hífen comum (`-`) como separador.
- Usar o título em letras minúsculas, sem acentos, aspas, parênteses ou sublinhados.
- Separar as palavras do título com hífen.
- Manter o título curto, específico e sem termos redundantes.
- Não colocar datas no nome do arquivo.
- Não alterar nem reutilizar o ID permanente.
- Manter o mesmo ID no nome, no conteúdo e no índice.
- PRD e REQ da mesma funcionalidade devem compartilhar domínio e número, diferenciando-se pelo tipo: `PRD-INT-001` e `REQ-INT-001`.

## Tipos de documento

| Código | Uso |
|---|---|
| PRD | Objetivo, problema, solução, escopo e decisões de produto |
| REQ | Requisitos, regras, fluxos, limitações e critérios de aceitação |
| SCR | Security Change Request para demandas e alterações relacionadas à segurança |
| MIG | Migração, regularização ou execução pontual |
| DEC | Decisão de negócio que precisa de rastreabilidade própria |
| GUIA | Orientação operacional ou explicativa |

## Códigos de domínio

| Código | Domínio |
|---|---|
| ATD | Atendimento |
| CRM | CRM e Administração de Empresas |
| IA | Inteligência Artificial |
| MSG | Mensagens e Canais |
| INT | Integrações |
| CIG | Crescer Instagram |
| ENF | Encarte Farma |
| INF | Infraestrutura |
| ADM | Administração do Sistema |
| DSH | Relatórios e Dashboards |

Um novo código de domínio deve ser registrado neste documento antes de ser utilizado.

## Numeração

- A numeração possui três dígitos e é sequencial dentro de cada domínio.
- O número pertence permanentemente à funcionalidade e é compartilhado pelos documentos do mesmo dossiê.
- Um número removido, cancelado ou substituído não pode ser reutilizado.
- O prefixo de tipo diferencia os documentos do dossiê, por exemplo `PRD-MSG-001` e `REQ-MSG-001`.

## Versões

- `v01`: primeira versão catalogada.
- Incrementar a versão quando houver mudança aprovada no comportamento, escopo, regra, requisito ou limitação.
- Correções apenas ortográficas podem manter a versão, desde que não alterem o significado.
- A versão anterior deve ser preservada no histórico quando a mudança modificar regras aplicadas.

### Atualizações incrementais de documentos existentes

Quando um PRD, REQ, MIG ou outro documento existente receber uma atualização ou mudança incremental, o conteúdo e a estrutura da versão anterior não devem ser reescritos, resumidos ou reorganizados.

A nova versão deve ser produzida da seguinte forma:

1. Copiar integralmente o arquivo vigente, preservando conteúdo, estrutura, paginação e referências.
2. Acrescentar uma ou mais páginas de atualização ao final do documento, conforme a quantidade de conteúdo necessária.
3. Registrar nesse bloco final somente as regras adicionadas, alteradas ou removidas pela atualização.
4. Incrementar o número da versão do novo arquivo.
5. Manter a nova versão no dossiê como vigente.
6. Mover a versão anterior para a subpasta `historico/`, alterando seu status para `SUBSTITUIDO`.
7. Atualizar o índice do acervo na mesma operação.

Assim, em uma atualização de `v01` para `v02`, a única diferença entre os arquivos deve ser o bloco de atualização adicionado ao final da `v02`. Esse bloco pode ocupar uma ou mais páginas. Em uma atualização posterior, a nova versão deve preservar integralmente a versão imediatamente anterior e acrescentar um novo bloco ao final.

### Estrutura do bloco de atualização

O bloco acrescentado ao final deve conter:

- título `Atualização da versão vNN`;
- data da decisão;
- origem ou motivo da atualização;
- descrição objetiva da alteração;
- regras adicionadas;
- regras modificadas;
- regras removidas ou desconsideradas;
- impacto nos fluxos e critérios de aceitação;
- indicação de que as demais regras permanecem inalteradas;
- regra de prevalência informando que a atualização mais recente deve ser considerada em caso de divergência com páginas anteriores.

Quando o conteúdo exigir mais de uma página, todas elas devem apresentar identificação da versão e permanecer agrupadas sequencialmente no final do documento. A divisão entre páginas deve respeitar a continuidade das seções, sem cortar tabelas, listas ou regras de forma confusa.

Itens sem alteração devem ser identificados como `Não se aplica`, evitando seções ambíguas ou vazias.

### Relação entre PRD e REQ durante uma atualização

- Antes de versionar, verificar se a mudança afeta o PRD, o REQ ou ambos.
- Quando a decisão alterar comportamento, regra, fluxo ou critério descrito nos dois documentos, os dois devem receber seus respectivos blocos de atualização.
- O bloco do PRD deve registrar a decisão de produto e o impacto no escopo ou experiência.
- O bloco do REQ deve registrar o impacto nos requisitos, regras, fluxos, campos, mensagens e critérios aplicáveis.
- O bloco de atualização não deve criar regras que não tenham sido confirmadas.

## Status permitidos

| Status | Significado |
|---|---|
| RASCUNHO | Documento ainda em elaboração |
| EM-VALIDACAO | Conteúdo aguardando decisão ou aprovação |
| APROVADO | Conteúdo aprovado, mas ainda não confirmado como aplicado |
| IMPLEMENTADO | Regra vigente e aplicada no sistema |
| SUBSTITUIDO | Documento que deixou de ser a fonte vigente |
| CANCELADO | Demanda ou regra cancelada |

Somente documentos `IMPLEMENTADO` representam automaticamente o comportamento atual. Os demais exigem interpretação conforme seu status.

Uma funcionalidade pode possuir PRD e REQ sem estar implementada. A existência dos documentos não define o status da entrega.

## Índice do acervo

Todo documento deve possuir uma entrada em `INDICE-DO-ACERVO.md` contendo, no mínimo:

- ID permanente;
- título legível;
- caminho para o arquivo;
- versão;
- status;
- relações e observações relevantes.
- indicação explícita quando o PRD ou o REQ estiver ausente.

O índice deve ser atualizado na mesma alteração que criar, mover, renomear, versionar, substituir ou cancelar um documento.

## Documentos relacionados e conflitos

- Relações entre documentos devem ser registradas no índice.
- Uma regra mais nova não substitui silenciosamente uma regra anterior.
- O documento novo deve informar qual documento ou regra substitui.
- Documentos conflitantes ficam em `99-Em-Analise-e-Historico/` até a decisão.
- Documentos substituídos permanecem disponíveis para rastreabilidade, mas deixam de ser fontes vigentes.

## Fluxo para novas documentações

1. Consultar o índice e os documentos relacionados.
2. Verificar duplicidade, sobreposição e possíveis conflitos.
3. Definir tipo, domínio e próximo número disponível.
4. Produzir o documento marcando dúvidas como pendências, sem inventar regras.
5. Validar o conteúdo com as pessoas responsáveis.
6. Salvar com versão e status corretos.
7. Atualizar o índice e registrar as relações.
8. Preservar no histórico qualquer versão substituída.

## Modo Analista de Requisitos

O comando `Modo Analista de Requisitos`, independentemente do uso de letras maiúsculas ou minúsculas, identifica o fluxo colaborativo utilizado para elaborar PRDs, REQs e SCRs deste acervo.

Esse modo pode ser iniciado mesmo quando a tarefa não estiver aberta dentro da pasta do projeto. Ao ser ativado, deve consultar diretamente este padrão, o índice do acervo e os documentos relacionados na pasta canônica `C:\Users\symbo\Documents\Requisitos do sistema`.

Aplicam-se ao modo as seguintes regras:

- trabalhar em uma documentação por vez;
- utilizar o acervo vigente para prevenir duplicidades e contradições;
- não inventar regras ou preencher lacunas por inferência;
- conduzir as decisões pendentes com a Analista;
- apresentar a documentação como texto integral na conversa;
- não criar nem inserir automaticamente o arquivo oficial;
- permitir que a Analista produza e coloque o arquivo no acervo;
- organizar, nomear e catalogar o arquivo somente depois de sua inserção e quando solicitado.

PRD, REQ e SCR possuem modelos obrigatórios definidos neste documento.

## Processo de análise antes da documentação

Na maioria das demandas, a documentação não deve ser redigida imediatamente após o recebimento da ideia inicial.

Antes de criar um PRD ou REQ, a Analista e o assistente devem, conforme aplicável:

1. compreender a necessidade e o comportamento atual;
2. consultar o acervo e identificar documentos relacionados;
3. analisar, construir, melhorar ou discutir a implementação sob a perspectiva do produto;
4. mapear usuários, empresas, conexões, estados, permissões, impactos e limitações;
5. identificar contradições, lacunas e cenários ainda não decididos;
6. conduzir as decisões necessárias com a Analista, uma por vez;
7. confirmar que o comportamento pretendido está definido e sem brechas identificadas;
8. somente então redigir o documento completo no modelo correspondente.

O PRD ou REQ final não deve apresentar como definição um comportamento ainda incerto. Dúvidas levantadas durante a análise permanecem na conversa de elaboração até serem resolvidas. Quando uma decisão necessária não puder ser tomada, o documento não deve ser tratado como concluído.

### Escolha e sequência dos documentos

A necessidade documental deve ser decidida para cada demanda. Pode ser produzido somente um PRD, somente um REQ, somente um SCR ou mais de um tipo relacionado.

Quando PRD e REQ forem necessários para a mesma funcionalidade, eles podem ser elaborados em sequência para reduzir lacunas documentais:

1. concluir e revisar o PRD;
2. manter o contexto e as decisões confirmadas da funcionalidade;
3. iniciar o REQ como um novo documento do mesmo dossiê;
4. detalhar no REQ os requisitos, regras, fluxos e exceções sem contradizer o PRD;
5. verificar o alinhamento entre os dois documentos antes da conclusão.

Esse fluxo continua respeitando a regra de uma documentação por vez: o REQ somente começa depois que o PRD estiver concluído. A criação de um documento não torna automaticamente o outro obrigatório.

## Padrão geral de linguagem documental

Todos os tipos de documentação devem utilizar linguagem simples, direta e compreensível para pessoas com diferentes níveis de conhecimento sobre o assunto.

Aplicam-se as seguintes regras:

- escrever considerando que o leitor pode não conhecer a funcionalidade, o módulo ou o histórico da demanda;
- explicar termos próprios do sistema na primeira ocorrência, quando não forem evidentes;
- fornecer contexto suficiente para que o documento seja compreendido sem depender de reunião, conversa, card ou conhecimento anterior;
- utilizar frases objetivas, mas sem reduzir explicações necessárias;
- preferir uma explicação completa a um texto curto que permita interpretações diferentes;
- organizar assuntos extensos em parágrafos, listas ou subtópicos coerentes;
- evitar linguagem excessivamente técnica ou elaborada quando uma expressão simples transmitir o mesmo significado;
- evitar termos vagos, ambiguidades, repetições e informações sem relação com a demanda;
- manter o nível de detalhamento compatível com os documentos vigentes do acervo;
- preservar consistência entre objetivo, contexto, problema, solução, escopo e formas de validação;
- não criar informações apenas para preencher uma seção do modelo.

Clareza não significa reduzir o documento ao mínimo. O texto deve ter o tamanho necessário para explicar o comportamento sem brechas, respeitando o limite aplicável ao local onde será utilizado.

## Modelo obrigatório de PRD

Todo novo PRD deve seguir esta ordem:

1. Objetivo.
2. Contexto.
3. Problema.
4. Solução Proposta.
5. Usuários Impactados.
6. Escopo da Entrega.
7. Benefícios Esperados.
8. Critérios de Aceite.
9. Especificação da Interface, quando aplicável.

O modelo possui orientações internas de elaboração. Expressões como `Finalidade`, `Deve responder`, `Deve conter`, `Não deve conter`, `Nível de detalhamento esperado` e `Evitar` orientam a redação, mas não devem aparecer no PRD final. O documento final deve apresentar somente o título do PRD, as seções aplicáveis e o conteúdo específico da demanda.

O PRD descreve o que se pretende implementar, por que a implementação é necessária, como a solução deve funcionar em nível de produto e qual resultado se espera alcançar. Ele não deve apresentar requisitos funcionais identificados, regras de negócio formalizadas, arquitetura, banco de dados, endpoints, classes, bibliotecas, algoritmos, estratégia técnica ou casos de teste completos.

### 1. Objetivo

O Objetivo deve apresentar o propósito da entrega, a parte do produto envolvida, a mudança principal e o resultado esperado.

Deve permitir que uma pessoa sem conhecimento prévio compreenda rapidamente:

- o que será criado, alterado, removido ou melhorado;
- em qual parte do produto a mudança ocorrerá;
- qual é a finalidade da implementação;
- qual será a principal diferença após a entrega.

O Objetivo é uma das partes mais importantes do PRD e não deve ser reduzido a frases genéricas como `melhorar o sistema`, `otimizar a funcionalidade` ou `corrigir o fluxo atual` sem explicar a mudança pretendida.

Não deve conter a descrição completa do problema, o detalhamento dos fluxos, critérios de aceite ou detalhes técnicos.

### 2. Contexto

O Contexto deve explicar o cenário atual como se o documento fosse apresentado a uma pessoa que nunca teve contato com o assunto.

Conforme aplicável, deve apresentar:

- como o sistema ou processo funciona atualmente;
- onde a funcionalidade está inserida;
- quem utiliza o comportamento atual;
- qual situação originou a demanda;
- conceitos próprios do sistema necessários à compreensão;
- histórico relevante;
- módulos, integrações ou funcionalidades relacionados;
- limitações e características do cenário atual;
- comportamentos existentes que precisam ser preservados.

Não basta afirmar que um módulo, integração, configuração ou feature flag existe. Deve-se explicar o que ele faz, por que existe e qual relação possui com a demanda.

Quando houver mais de um assunto relevante, utilizar subtópicos coerentes, como cenário atual, funcionamento existente, origem da necessidade ou relação com outras funcionalidades. Os nomes devem refletir o conteúdo real do PRD.

O Contexto não deve apresentar a solução como se já estivesse implementada nem incluir detalhes técnicos desnecessários.

### 3. Problema

O Problema deve identificar claramente a dificuldade, limitação, risco ou necessidade que justifica a entrega. Enquanto o Contexto explica o cenário, o Problema explica o que nesse cenário precisa ser resolvido.

Deve apresentar, conforme aplicável:

- o que acontece atualmente;
- em quais situações acontece;
- quem é impactado;
- quais consequências são geradas;
- por que o comportamento atual é inadequado;
- o que poderá continuar acontecendo se nada for alterado;
- por que a implementação é necessária.

Quando existirem diferentes problemas ou impactos, utilizar subtópicos. Evitar afirmações vagas como `o comportamento não é ideal`, `o usuário tem dificuldades` ou `o processo precisa ser melhorado` sem explicar a situação e suas consequências.

O Problema não deve conter a descrição completa da solução, regras formalizadas ou alternativas técnicas.

### 4. Solução Proposta

A Solução Proposta deve explicar como o problema será resolvido sob a perspectiva do produto.

Deve apresentar, conforme aplicável:

- a visão geral da solução;
- o funcionamento esperado;
- o fluxo funcional principal;
- as mudanças em relação ao cenário atual;
- os principais comportamentos oferecidos;
- o tratamento de empresas, usuários ou configurações existentes;
- comportamentos que devem permanecer inalterados;
- diferenças relevantes por perfil, empresa, conexão ou canal;
- condições importantes para utilização;
- o resultado esperado ao final do fluxo.

A seção deve ser dividida em subtópicos quando a funcionalidade possuir diferentes comportamentos. Os subtópicos são definidos conforme a demanda e podem tratar, por exemplo, de disponibilidade, configuração inicial, empresas existentes, novas empresas, conexões, continuidade de dados ou indisponibilidade.

Quando a funcionalidade puder variar por conexão, avaliar API Oficial, API Baileys, API Híbrida, Instagram e Facebook. O PRD deve explicar somente as diferenças relevantes e pode declarar de forma resumida as conexões sem alteração ou não aplicáveis.

O texto deve explicar o que deve acontecer, em qual situação, para quem e qual resultado é esperado. Não deve definir como o código será construído nem apresentar requisitos ou regras de negócio formalmente identificados.

### 5. Usuários Impactados

Esta seção deve identificar quem utiliza, configura, visualiza, administra, recebe benefícios ou é afetado indiretamente pela funcionalidade.

Pode incluir:

- usuários finais;
- empresas clientes;
- administradores;
- usuários internos;
- equipes de suporte ou operação;
- áreas de negócio;
- clientes internos ou externos.

Para cada grupo, deve ser explicado brevemente como será impactado. Não basta listar perfis sem descrever a relação deles com a entrega.

### 6. Escopo da Entrega

O Escopo deve delimitar claramente o que faz e o que não faz parte da implementação.

#### Inclui

Deve listar, conforme aplicável:

- funcionalidades e alterações contempladas;
- comportamentos previstos;
- telas, perfis ou conexões afetados;
- tratamento de empresas, dados ou configurações existentes;
- validações incluídas;
- comportamentos existentes que devem ser preservados.

#### Não inclui

Deve listar, conforme aplicável:

- evoluções futuras;
- módulos e mudanças não relacionados;
- integrações não afetadas;
- comportamentos que permanecerão inalterados;
- configurações ou processos que não serão criados;
- melhorias consideradas, mas não aprovadas para a entrega.

Os itens devem ser específicos. O escopo não pode contradizer a Solução Proposta, e um comportamento essencial não deve aparecer somente nesta seção.

### 7. Benefícios Esperados

Esta seção deve apresentar o valor gerado para o produto, usuários ou operação e relacioná-lo diretamente ao Problema e à Solução Proposta.

Pode tratar de:

- melhoria da experiência;
- redução de erros ou trabalho manual;
- padronização;
- produtividade e eficiência operacional;
- segurança;
- continuidade do serviço;
- simplificação de processos;
- maior disponibilidade;
- redução de dependências.

Evitar benefícios genéricos como `melhor experiência`, `maior eficiência` ou `melhoria do sistema` sem explicar concretamente o ganho esperado. Esta seção normalmente deve ser curta.

### 8. Critérios de Aceite

Os Critérios de Aceite devem definir os comportamentos mínimos necessários para considerar a entrega concluída sob a perspectiva do produto.

Devem verificar, conforme aplicável:

- o fluxo principal;
- os comportamentos importantes descritos na solução;
- o resultado esperado;
- empresas novas e existentes;
- preservação de dados ou configurações;
- diferenças relevantes por perfil ou conexão;
- limites definidos no escopo;
- comportamentos existentes que não devem ser alterados.

Os critérios devem ser objetivos, claros, verificáveis e independentes quando validarem comportamentos diferentes. Podem começar com `O sistema deve`, `O sistema não deve`, `O usuário deve poder`, `Deve ser possível` ou `A funcionalidade deve`.

Não devem introduzir comportamentos que não apareçam nas seções anteriores, repetir integralmente a Solução Proposta, apresentar detalhes técnicos ou se transformar em casos de teste completos.

### 9. Especificação da Interface

Esta seção é opcional e deve ser utilizada quando a entrega criar ou alterar telas, campos, componentes, mensagens ou navegação. Pode ser omitida em integrações sem alteração visual, processos internos ou demandas exclusivamente de processamento.

Quando aplicável, pode conter:

#### 9.1 Ponto de Entrada

- tela de origem;
- menu, seção, botão ou ação inicial;
- condições e perfis necessários para acesso.

#### 9.2 Estrutura da Interface

- campos, botões, abas, listas, cards, modais, tabelas, seletores, switches, indicadores e mensagens visíveis.

Esta subseção descreve o que existe na interface. O funcionamento das interações deve ser descrito em Comportamentos da Interface.

#### 9.3 Fluxo da Interface

- onde o usuário inicia;
- quais ações executa;
- o que o sistema apresenta;
- como o fluxo continua;
- qual é o resultado da interação.

#### 9.4 Comportamentos da Interface

- cliques, seleções, preenchimento, salvamento, cancelamento e confirmação;
- campos obrigatórios, habilitados ou desabilitados;
- atualização da tela;
- retorno de sucesso ou erro;
- manutenção ou descarte de valores.

#### 9.5 Estados da Interface

Subseção opcional para estados relevantes, como inicial, carregando, vazio, preenchido, sucesso, erro, indisponível, sem resultados ou sem permissão.

Não devem ser criados estados que não se apliquem à funcionalidade.

### Consistência do PRD

As seções devem formar uma sequência coerente:

- o Objetivo apresenta a entrega;
- o Contexto explica o cenário;
- o Problema justifica a necessidade;
- a Solução Proposta resolve o problema;
- o Escopo delimita a solução;
- os Benefícios representam o valor esperado;
- os Critérios de Aceite validam o que foi proposto.

Um comportamento não deve aparecer pela primeira vez somente nos Critérios de Aceite. O PRD final não deve possuir decisões funcionais pendentes ou depender de informações não registradas para ser compreendido.

### Extensão do PRD

Com base no acervo atual:

- a faixa recomendada é de 8 mil a 15 mil caracteres;
- demandas complexas podem chegar a aproximadamente 20 mil caracteres;
- o limite máximo adotado é de aproximadamente 25 mil caracteres.

Antes de reduzir conteúdo necessário, devem ser eliminadas repetições entre Contexto e Problema, Solução Proposta e Critérios de Aceite, benefícios genéricos, explicações duplicadas no Escopo e orientações internas do modelo. Informações necessárias para compreender a demanda não devem ser removidas apenas para encurtar o documento.

## Modelo obrigatório de SCR

O Security Change Request documenta uma alteração necessária para corrigir, reduzir ou prevenir um problema de segurança. Deve explicar o problema, o comportamento identificado, o comportamento seguro esperado, o alcance conhecido, os impactos, as garantias necessárias e a forma de validação.

Todo novo SCR deve seguir esta ordem:

1. Resumo do problema.
2. Contexto.
3. Comportamento identificado.
4. Comportamento esperado.
5. Escopo afetado.
6. Impacto potencial.
7. Requisitos de Segurança.
8. Critérios de aceite.
9. Fora do escopo.

O modelo possui orientações internas de elaboração. Expressões como `Deve responder`, `Deve conter`, `Não deve conter`, `Nível de detalhamento`, `Classificação das informações` e `Evitar` não devem aparecer no SCR final. O documento final deve apresentar somente o título, as nove seções e o conteúdo específico da demanda.

O SCR pode utilizar termos técnicos quando necessários para descrever o problema com precisão, mas deve manter linguagem simples e direta. Não deve ensinar como explorar a falha nem determinar a solução técnica. A pessoa responsável pela implementação possui autonomia técnica para escolher a correção, desde que atenda às garantias documentadas.

O SCR não deve conter classificação de prioridade, código de exploração, credenciais, senhas, tokens, dados pessoais, informações sensíveis, instruções desnecessárias de ataque, soluções técnicas não confirmadas ou impactos apresentados como fatos sem evidência.

### 1. Resumo do problema

Deve apresentar de forma curta e objetiva:

- qual problema de segurança foi identificado;
- o que o sistema está permitindo, deixando de impedir ou deixando de proteger;
- qual proteção esperada não está sendo respeitada;
- por que o comportamento representa um problema de segurança;
- em qual área ou funcionalidade ele foi identificado.

O resumo não deve explicar toda a investigação, apresentar código, arquitetura, causa técnica detalhada, passo a passo de exploração ou definição da correção.

### 2. Contexto

Deve explicar como a área afetada funciona e qual proteção deveria fazer parte do fluxo normal.

Conforme aplicável, deve apresentar:

- a função da área, operação ou recurso afetado;
- quem utiliza e quem deveria ter acesso;
- as condições normais de acesso;
- o tipo de informação ou operação envolvida;
- a proteção esperada;
- a relação com autenticação, autorização, isolamento entre empresas ou outra proteção;
- dependências necessárias para compreender o problema.

Como o leitor principal possui conhecimento técnico do sistema, o Contexto não precisa repetir arquitetura ou informações amplamente conhecidas que não influenciem a análise. Termos técnicos devem ser explicados quando não forem evidentes para outros possíveis leitores.

### 3. Comportamento identificado

Deve registrar objetivamente o que o sistema está permitindo indevidamente, sem transformar o documento em um guia de exploração.

Deve conter, conforme aplicável:

- a condição em que o problema ocorre;
- o comportamento observado;
- o resultado indevido;
- a proteção que deveria ter impedido o resultado;
- o grau de confirmação;
- a indicação de áreas relacionadas que utilizem a mesma proteção.

Quando necessário, classificar a informação como:

- `Comportamento confirmado`: reproduzido ou demonstrado;
- `Comportamento potencial`: compatível com a falha, mas ainda não comprovado;
- `Área não verificada`: relacionada à mesma proteção e que precisa ser considerada na validação.

Uma possibilidade nunca deve ser apresentada como fato confirmado.

Evidências não sensíveis podem ser resumidas. Evidências com credenciais, tokens, dados pessoais, informações de clientes ou instruções detalhadas de exploração devem permanecer em local controlado e ser apenas referenciadas no SCR.

### 4. Comportamento esperado

Deve definir como o sistema deve se comportar depois da alteração, independentemente da solução técnica adotada.

Deve apresentar, conforme aplicável:

- o que deve ser permitido;
- o que deve ser impedido;
- quem pode acessar a informação ou executar a operação;
- qual condição de segurança precisa ser atendida;
- como o sistema deve responder quando a condição não for atendida;
- quais fluxos legítimos devem continuar funcionando;
- como a proteção deve permanecer consistente no escopo abrangido.

O texto deve definir o resultado de segurança esperado, não middleware, função, método, biblioteca ou alteração de código.

### 5. Escopo afetado

Deve identificar as partes do produto em que o problema foi confirmado e as áreas relacionadas que precisam ser consideradas.

O foco deve estar em funcionalidades, informações e operações, podendo incluir:

- funcionalidade em que a falha foi confirmada;
- tipos de informação envolvidos;
- operações afetadas;
- perfis, empresas ou clientes potencialmente impactados;
- integrações relacionadas;
- fluxos que compartilham a mesma proteção;
- áreas que precisam ser verificadas durante a validação.

Quando necessário, separar:

- `Escopo confirmado`: áreas em que o comportamento foi demonstrado;
- `Escopo relacionado`: áreas que compartilham a mesma proteção;
- `Escopo não verificado`: áreas relacionadas ainda não avaliadas.

O uso de `não verificado` não confirma a existência da falha. Indica somente que a verificação faz parte da segurança da alteração.

Evitar expressões abertas como `verificar todo o sistema`, `corrigir todas as rotas` ou `validar tudo relacionado à segurança` sem identificar a proteção, funcionalidade ou grupo de operações considerado.

### 6. Impacto potencial

Deve descrever as consequências que o problema pode gerar para usuários, empresas, dados, operação ou produto.

Considerar, quando aplicável:

- acesso indevido ou exposição de informações;
- alteração ou exclusão de dados;
- execução de ações sem autorização;
- acesso a informações de outro usuário ou empresa;
- elevação indevida de permissão;
- indisponibilidade ou interrupção de processos;
- impactos operacionais, financeiros, reputacionais, de privacidade ou conformidade.

Separar obrigatoriamente:

- `Impacto confirmado`: consequência efetivamente demonstrada;
- `Impacto potencial`: consequência possível, mas ainda não comprovada.

Se nenhum impacto tiver sido comprovado, isso deve ser informado. A ausência de impacto confirmado não elimina o risco potencial.

Não devem ser inventadas classificações de prioridade ou gravidade, obrigações legais, CVEs, estimativas financeiras ou impactos sem evidência.

### 7. Requisitos de Segurança

Devem definir as condições de segurança que obrigatoriamente precisam ser atendidas após a alteração, sem determinar a implementação.

Os requisitos devem utilizar identificadores estáveis e sequenciais:

- `RS-01`;
- `RS-02`;
- `RS-03`.

Cada requisito deve preferencialmente representar uma única condição, ser objetivo, compreensível, verificável e permanecer válido independentemente da solução escolhida.

Podem tratar, conforme aplicável, de:

- quem pode e quem não pode executar uma ação;
- acessos que devem ser impedidos;
- autenticação e autorização;
- isolamento entre usuários ou empresas;
- condições anteriores à disponibilização de informações ou operações;
- preservação de fluxos legítimos;
- consistência da proteção no escopo afetado;
- impedimento da repetição do problema em áreas relacionadas.

Não devem conter alterações de middleware, nomes de funções, métodos, bibliotecas, estruturas de código, soluções técnicas não confirmadas ou melhorias funcionais sem relação com a proteção.

### 8. Critérios de aceite

Devem definir como confirmar que os Requisitos de Segurança foram atendidos, o comportamento indevido deixou de ocorrer e os fluxos legítimos continuam funcionando.

Os critérios devem utilizar identificadores sequenciais:

- `CA-01`;
- `CA-02`;
- `CA-03`.

Sempre que possível, cada critério deve indicar os Requisitos de Segurança relacionados.

Devem validar, conforme aplicável:

- resultados observáveis;
- comportamentos que não podem mais ocorrer;
- áreas confirmadas e relacionadas;
- isolamento entre usuários ou empresas;
- tratamento de solicitações inválidas;
- continuidade dos fluxos autorizados;
- ausência do comportamento indevido descrito no SCR.

Não devem apresentar regras novas, soluções técnicas, casos de teste excessivamente detalhados, critérios subjetivos ou garantias absolutas que não possam ser verificadas.

### 9. Fora do escopo

Deve definir o que não será tratado pelo SCR, evitando a inclusão de mudanças funcionais ou melhorias desnecessárias à correção.

Pode conter:

- funcionalidades relacionadas que não serão alteradas;
- problemas diferentes que exigem outro SCR;
- melhorias não relacionadas à correção;
- mudanças de produto não necessárias aos Requisitos de Segurança;
- novas permissões ou comportamentos funcionais não contemplados;
- áreas avaliadas e confirmadas como não relacionadas.

Quando não houver exclusão relevante, registrar `Não aplicável`.

Um item necessário para atender aos Requisitos de Segurança não pode ser colocado fora do escopo. Um problema diferente pode ser encaminhado para outro SCR.

### Padrão de linguagem do SCR

- utilizar linguagem simples e direta;
- empregar termos técnicos somente quando contribuírem para a precisão;
- explicar termos que possam não ser conhecidos fora da área de segurança;
- evitar linguagem excessivamente jurídica, técnica ou elaborada;
- separar assuntos em parágrafos, listas ou subtópicos;
- não apresentar possibilidades como fatos;
- não afirmar exploração sem confirmação;
- não ampliar artificialmente o impacto;
- distinguir autenticação de autorização quando relevante;
- distinguir acesso legítimo de acesso indevido.

### Segurança da própria documentação

- não registrar segredos, credenciais ou tokens;
- não incluir dados pessoais ou informações de clientes sem necessidade;
- não fornecer detalhes de exploração além do necessário;
- referenciar evidências sensíveis armazenadas em local controlado;
- considerar quem terá acesso ao SCR antes de inserir informações técnicas sensíveis.

### Momento de elaboração do SCR

O SCR não precisa ser redigido imediatamente após a identificação inicial. Antes de concluí-lo, devem ser analisados o comportamento, o grau de confirmação, o escopo conhecido, os impactos, o comportamento esperado, as garantias necessárias e as formas de validação.

O documento deve ser produzido quando houver informação suficiente para orientar a correção. Áreas relacionadas ainda não verificadas podem fazer parte da validação, desde que sejam identificadas objetivamente e não apresentadas como falhas confirmadas.

## Rota Validação de Bug

A rota `Validação de Bug` é utilizada para formular cards de bugs já validados pela Analista e que devem ser corrigidos.

Apesar do nome da rota, o processo de rastreio, reprodução, investigação e validação inicial é realizado pela própria Analista antes do início da elaboração. Ao acionar a rota, considera-se que:

- o comportamento já foi validado como bug;
- a necessidade de correção já foi confirmada;
- a Analista fornecerá as informações necessárias;
- o trabalho colaborativo será somente organizar, esclarecer e redigir o card.

O assistente não deve refazer a validação, tentar rastrear o problema, exigir classificação de confirmação ou iniciar investigação técnica. Quando faltar uma informação necessária à redação, deve formular uma pergunta por vez para a Analista.

O card de bug não é um tipo documental do acervo, não recebe código documental, não precisa ser inserido em dossiê e não deve ser catalogado no índice. O resultado deve ser apresentado como texto na conversa, pronto para a Analista copiar para o card. Não deve ser criado ou publicado automaticamente.

### Estrutura oficial do card

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

As orientações internas de preenchimento não devem aparecer no card final.

### Título

Deve utilizar o formato `Bug: descrição curta e específica do problema` e identificar o comportamento incorreto e, quando útil, a funcionalidade afetada.

Evitar títulos genéricos como `Bug no sistema`, `Erro na tela`, `Funcionalidade não funciona` ou `Problema ao publicar`.

### Contexto

Deve explicar a funcionalidade e o cenário necessário para compreender o bug.

Pode conter, conforme aplicável:

- o que a funcionalidade faz;
- onde ela está localizada;
- como o fluxo funciona normalmente;
- quem utiliza a funcionalidade;
- qual regra ou comportamento existente está relacionado;
- em qual condição o problema foi identificado;
- conexão, navegador, empresa, formato ou tipo de publicação envolvido;
- evidências relevantes fornecidas pela Analista.

O Contexto deve ser compreensível para alguém que não acompanhou a validação. Não deve apresentar uma hipótese técnica como fato nem repetir integralmente o Problema.

### Problema

Deve descrever objetivamente o comportamento incorreto validado pela Analista.

Deve explicar, conforme aplicável:

- o que o sistema está fazendo;
- em qual momento acontece;
- qual resultado incorreto é apresentado;
- se o fluxo fica bloqueado ou pode continuar;
- qual impacto direto o bug causa;
- mensagens, demora, ausência de retorno ou ações indevidamente permitidas ou bloqueadas.

Não deve indicar uma causa técnica que não tenha sido confirmada.

### Fluxo de reprodução

Esta seção é opcional e deve ser utilizada quando a Analista fornecer uma sequência conhecida para reproduzir o problema.

O fluxo deve ser apresentado em lista numerada e pode incluir:

- pré-condições;
- perfil utilizado;
- tipo de conexão;
- navegador;
- formato do arquivo;
- estado anterior do cadastro;
- configuração necessária;
- ações realizadas;
- resultado incorreto observado.

Não devem ser incluídos passos irrelevantes, credenciais, dados pessoais, informações sensíveis ou causas técnicas presumidas.

Quando não houver fluxo conhecido, a seção deve ser omitida. A ausência da seção não impede a criação do card, pois o bug já foi validado pela Analista.

### Comportamento esperado

Deve explicar o resultado correto sob a perspectiva do usuário e do produto.

Pode conter:

- resultado esperado;
- dados que devem ser recuperados ou exibidos;
- continuidade esperada do fluxo;
- comportamento em caso de sucesso;
- comportamento em caso de falha real;
- mensagens definidas;
- bloqueios necessários durante processamento;
- preservação de fluxos válidos;
- rejeição de entradas realmente inválidas;
- limites de tempo fornecidos e confirmados pela Analista.

Não deve determinar a solução técnica, criar mensagens ou limites arbitrários, ampliar o escopo nem introduzir uma regra sem confirmação.

### Requisitos Funcionais

Devem transformar o comportamento esperado em condições objetivas para a correção.

Os identificadores devem seguir `RF01`, `RF02`, `RF03` e permanecer estáveis dentro do card.

Cada requisito deve preferencialmente representar um comportamento, ser claro, verificável, diretamente relacionado ao bug e escrito sob a perspectiva do resultado esperado.

Não deve conter biblioteca, arquitetura, componente técnico, alteração de código, possível solução não confirmada ou melhoria que não seja necessária para corrigir o problema.

A quantidade de requisitos deve ser proporcional ao bug. Não criar requisitos artificiais para aumentar o card.

### Critérios de aceite

Devem definir como confirmar que o bug foi corrigido.

Conforme aplicável, devem verificar:

- o fluxo em que o problema ocorria;
- o comportamento correto esperado;
- a ausência do comportamento incorreto;
- a preservação dos fluxos que já funcionavam;
- entradas válidas e inválidas;
- perfis, conexões, navegadores ou formatos afetados;
- mensagens de sucesso ou erro definidas;
- limites de tempo confirmados;
- situações relacionadas que possam sofrer regressão.

Cada critério deve ser objetivo, verificável, relacionado aos Requisitos Funcionais e escrito em linguagem simples.

Não deve introduzir comportamento novo, determinar a implementação, exigir garantias impossíveis de validar ou utilizar termos vagos sem explicar o resultado.

### Simplicidade do card

A rota não deve transformar um bug simples em um documento extenso. O card deve conter somente o necessário para que o problema, o comportamento esperado, a correção necessária e a forma de validação sejam compreendidos.

Informações de ambiente ou evidências não formam seções obrigatórias. Quando forem relevantes e fornecidas pela Analista, devem ser inseridas no Contexto ou no Fluxo de reprodução.

## Modelo obrigatório da documentação de requisitos

Toda nova documentação de requisitos deve seguir, quando aplicável, esta ordem:

1. Objetivo.
2. Contexto.
3. Escopo.
4. Requisitos Funcionais (RF).
5. Regras de Negócio (RN).
6. Fluxo Principal.
7. Fluxos Alternativos.
8. Exceções.
9. Elementos da Interface.
10. Mensagens do Sistema.
11. Requisitos Não Funcionais (RNF).
12. Critérios de Aceitação (CA).
13. Dependências e Observações.

As seções são condicionais. Quando uma seção não for aplicável, deve ser marcada como `Não se aplica`. Não devem ser criadas informações artificiais apenas para preencher o modelo.

### Classificação das informações

| Informação | Seção |
|---|---|
| Finalidade da funcionalidade | Objetivo |
| Situação atual, necessidade e cenário de uso | Contexto |
| Limites do que está e não está incluído | Escopo |
| Comportamento executado pelo sistema | RF |
| Condição, restrição ou decisão de negócio | RN |
| Caminho normal de sucesso | Fluxo Principal |
| Caminho diferente, mas previsto | Fluxo Alternativo |
| Falha ou situação anormal | Exceção |
| Campos, botões, seletores e demais componentes relevantes | Elementos da Interface |
| Texto relevante apresentado ao usuário | Mensagens do Sistema |
| Qualidade, desempenho, segurança, auditoria ou compatibilidade | RNF |
| Forma objetiva de validar o comportamento | Critérios de Aceitação |
| Dependência, limitação ou informação externa relevante | Dependências e Observações |

### Identificadores internos

- Requisitos funcionais: `RF01`, `RF02`, `RF03`.
- Regras de negócio: `RN01`, `RN02`, `RN03`.
- Fluxos alternativos: `FA01`, `FA02`, `FA03`.
- Exceções: `EX01`, `EX02`, `EX03`.
- Mensagens: `MSG01`, `MSG02`, `MSG03`.
- Requisitos não funcionais: `RNF01`, `RNF02`, `RNF03`.
- Critérios de aceitação: `CA01`, `CA02`, `CA03`.

Cada identificador deve ser único e permanecer estável. Um requisito deve representar um comportamento verificável. Comportamentos que possam ser testados ou alterados separadamente devem possuir identificadores separados.

### Regras de redação

- Não inventar comportamentos, regras, campos, mensagens, limitações ou integrações.
- Utilizar linguagem simples, clara, objetiva e verificável.
- Escrever considerando que o leitor pode não conhecer a funcionalidade, o módulo ou o histórico da demanda.
- Explicar termos próprios do sistema na primeira ocorrência, quando não forem evidentes.
- Fornecer contexto suficiente para que o REQ seja compreendido sem depender de reunião, conversa, card ou conhecimento anterior.
- Preferir uma explicação completa a uma formulação curta que permita interpretações diferentes.
- Manter o nível de detalhamento e a organização compatíveis com os REQs vigentes do acervo.
- Evitar linguagem excessivamente técnica ou elaborada quando uma expressão simples transmitir o mesmo significado.
- Preferir a construção `O sistema deve...` nos requisitos.
- Evitar termos vagos como `corretamente`, `rápido`, `intuitivo`, `normalmente`, `quando necessário` e `se possível` sem uma condição objetiva.
- Não repetir a mesma informação integralmente em várias seções.
- Separar comportamento do sistema, regra de negócio, qualidade e forma de validação.
- Documentar o comportamento e a necessidade de negócio, não arquitetura, endpoint, classe, biblioteca, framework ou código.
- Critérios de aceitação devem descrever como verificar o comportamento, sem apenas copiar os requisitos funcionais.
- Manter consistência entre contexto, escopo, requisitos, regras, fluxos, exceções, mensagens e critérios de aceitação.
- Não criar conteúdo artificial para aumentar o nível de detalhe ou preencher uma seção não aplicável.

## Procedimento de colaboração para criar um REQ

### Responsabilidades

- A Analista de Requisitos cria o arquivo oficial e o insere no acervo.
- O assistente ajuda a pesquisar o acervo, mapear comportamentos, identificar conflitos, formular perguntas e redigir o texto da documentação.
- O assistente não deve gerar automaticamente o arquivo final de requisitos.
- O assistente não deve inserir automaticamente o texto nos arquivos do acervo.
- Durante a elaboração, o resultado deve ser apresentado como texto legível na conversa para revisão da Analista.
- Depois que a Analista criar e colocar o arquivo pronto na pasta, o assistente pode nomeá-lo, classificá-lo, movê-lo para o dossiê correto e atualizar o índice, quando solicitado.

### Uma documentação por vez

- Somente uma documentação de requisitos deve permanecer ativa durante a elaboração.
- Não iniciar a documentação seguinte antes de a Analista concluir a atual e emitir o comando para desconsiderar o contexto específico da anterior.
- Ao receber esse comando, manter apenas as regras gerais do acervo e iniciar o levantamento da próxima funcionalidade.
- Informações, decisões e pendências de uma funcionalidade não devem ser transportadas para outra sem relação documental explícita.

### Levantamento obrigatório

Antes de redigir o documento:

1. Ler o PRD da funcionalidade.
2. Consultar o índice do acervo.
3. Ler os PRDs, REQs, MIGs e decisões relacionados.
4. Identificar regras existentes que não podem ser contraditas.
5. Mapear o fluxo principal de ponta a ponta.
6. Mapear todos os caminhos alternativos previstos.
7. Mapear falhas, indisponibilidades e exceções conhecidas.
8. Mapear permissões, configurações, estados, campos, mensagens e limitações aplicáveis.
9. Avaliar separadamente todas as conexões do sistema: API Oficial, API Baileys, API Híbrida, Instagram e Facebook.
10. Registrar cada conexão como `Aplicável`, `Não aplicável`, `Sem alteração` ou `Pendente de definição`, com justificativa baseada nas fontes disponíveis.
11. Transformar lacunas e ambiguidades em perguntas para a Analista, sem assumir respostas.
12. Redigir o documento completo seguindo o modelo obrigatório.

A avaliação de todas as conexões é obrigatória, mas isso não significa que todas devam possuir requisitos. Quando uma conexão não participar da funcionalidade, a documentação deve declarar sua não aplicabilidade ou seu enquadramento em fora de escopo, conforme o contexto.

### Entrega do texto

- O documento deve ser apresentado integralmente como texto na conversa.
- O texto deve permanecer editável e fácil de ler.
- Não criar PDF, DOCX, Markdown ou outro arquivo como parte automática da elaboração.
- Não salvar o texto na pasta do acervo.
- A Analista revisa o documento completo e solicita os ajustes necessários.
- Somente a versão textual aprovada pela Analista deve ser utilizada por ela para criar o arquivo oficial.
