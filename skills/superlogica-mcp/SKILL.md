---
name: superlogica-mcp
description: Consulta e opera o Superlógica Condomínios, o ERP de gestão de condomínios usado por administradoras, via MCP. Em leitura: carteira de condomínios e unidades, cobranças por período, por unidade e por status, posição de inadimplência com valores atualizados, resumo da arrecadação, acordos e processos judiciais, despesas por período e por conta do plano, favorecidos, contas bancárias com saldo e extrato, plano de contas, balancetes e previsão orçamentária, reservas de área comum, ocorrências, comunicados, solicitações e CRM de cobrança. Em escrita: cadastrar e editar cobrança, liquidar, estornar, invalidar e excluir, cadastrar e liquidar despesa, lançar e estornar movimentação bancária, criar acordo e simular parcelas, cadastrar unidade e responsável legal, reservar e cancelar área comum, abrir e editar ocorrência, disparar comunicado e responder solicitação. Use quando o usuário perguntar sobre inadimplência, cobrança, boleto, despesa, prestação de contas, balancete, saldo de conta do condomínio, reserva de área comum, ocorrência ou solicitação no Superlógica. As datas da API são MM/DD/AAAA. A Área do condômino e a 2ª via pública por CPF ficam fora, porque usam o login do morador.
---

# Superlógica Condomínios — REST API skill

Você tem acesso à **Superlógica Condomínios** REST API na MCP.AI.

> Converse com o **Superlógica Condomínios** da sua administradora a partir do Claude, do ChatGPT ou de qualquer cliente MCP. Roda sobre a **API oficial da Superlógica**, com o **par de tokens da sua própria licença**. A cunha é atravessar a **carteira inteira de uma vez**, que é o que hoje vira relatório exportado e colado em planilha: **inadimplência e cobrança** (boletos por período, por unidade, acordos e processos), **despesas e favorecidos**, **contas bancárias e movimentações**, **prestação de contas e balancetes**. Também escreve: cadastra cobrança e despesa, liquida, estorna, cria acordo, reserva área comum, abre ocorrência, dispara comunicado e responde solicitação. **Não afiliado à Superlógica.**

## Base URL

```
https://api.mcp.ai/api/superlogica
```

Todo endpoint é um **POST** na Base URL + o path abaixo. Os parâmetros vão no corpo JSON.

## Autenticação

Inclua em toda request:

```
Authorization: Bearer sk_live_...
Content-Type: application/json
```

> Gere sua chave em **https://app.mcp.ai/settings/api-keys** (workspace API key `sk_live_…`, não expira, revogável). Uma única chave serve pra todos os seus MCPs.

## Formato de resposta

```json
{ "ok": true, "tool": "<tool_id>", "result": <payload> }
```

## Exemplo cURL

```bash
curl -X POST https://api.mcp.ai/api/superlogica/acordos/desfazer \
  -H "Authorization: Bearer sk_live_..." \
  -H "Content-Type: application/json" \
  -d '{}'
```

## Reportar problemas

Se um endpoint retornar erro, vazio ou dado inesperado, reporte (não desista calado): **POST /api/superlogica/report** com `{ "message": "...", "context"?: "...", "conversation"?: [...] }`. Isso notifica o time da MCP.AI.

## Endpoints (114)

#### `superlogica_acordos_desfazer`

Receitas / Acordos: Desfazer acordo (PUT /acordos/desfazer). _(POST /api/superlogica/acordos/desfazer)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas licenças Superlógica conectadas: id ou label da conexão. Veja superlogica_list_accounts. |
| `body` | string | Não | Corpo da requisição como JSON string (enviado como form-urlencoded). Datas em MM/DD/AAAA. Nomes case-sensitive. Parâmetros da doc: ID_ACORDO_ACO. Significado: ID_ACORDO_ACO: ID do acordo. |
| `query` | string | Não | Query params como JSON string. Vários endpoints de escrita da Superlógica leem os campos da query em vez do corpo — a doc indica quais. |

#### `superlogica_acordos_list`

Receitas / Acordos / Obtendo dados para gerar o acordo: Listar acordos existentes (GET /Acordos). _(POST /api/superlogica/acordos/list)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas licenças Superlógica conectadas: id ou label da conexão. Veja superlogica_list_accounts. |
| `query` | string | Não | Query params como JSON string. Datas em MM/DD/AAAA (americano). Nomes são case-sensitive. Parâmetros da doc: idCondominio, dtInicio, dtFim, filtrarpor, exibirDadosDasParcelas, exibirSomenteDadosDosBoletosOrigens, exibirDadosDasComposicoes, itensPorPagina, pagina. |

#### `superlogica_acordos_put`

Receitas / Acordos: Novo acordo (POST /acordos/put). _(POST /api/superlogica/acordos/put)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas licenças Superlógica conectadas: id ou label da conexão. Veja superlogica_list_accounts. |
| `body` | string | Não | Corpo da requisição como JSON string (enviado como form-urlencoded). Datas em MM/DD/AAAA. Nomes case-sensitive. Parâmetros da doc: RECEITA_APROPRIACAO[0][ST_CONTA_CONT], RECEITA_APROPRIACAO[0][ST_DESCRICAO_CONT], RECEITA_APROPRIACAO[0][ST_COMPLEMENTO_REC], RECEITA_APROPRIACAO[0][VL_VALOR_REC], RECEITA_APROPRIACAO[0][APROPRIARPRIMEIRO], RECEITA_APROPRIACAO[1][ST_CONTA_CONT], RECEITA_APROPRIACAO[1][ST_DESCRICAO_CONT], RECEITA_APROPRIACAO[1][ST_COMPLEMENTO_REC], RECEITA_APROPRIACAO[1][VL_VALOR_REC], RECEITA_APROPRIACAO[1][APROPRIARPRIMEIRO], RECEITA_APROPRIACAO[2][ST_CONTA_CONT], RECEITA_APROPRIACAO[2][ST_DESCRICAO_CONT], RECEITA_APROPRIACAO[2][ST_COMPLEMENTO_REC], RECEITA_APROPRIACAO[2][VL_VALOR_REC], RECEITA_APROPRIACAO[2][APROPRIARPRIMEIRO], TOTAL_RECEITAAPRO, PRIORIZARHONORARIOS, SIMULA_TOTAL, SIMULA_ENTRADA, NM_PARCELA_ACO, FL_EMITIR_RECIBO, DT_PRIMEIRA_PARCELA, ENTRADA[0][VALOR], ENTRADA[0][ID_FORMAPAGAMENTO_RECB], ENTRADA[0][VENCIMENTO], PARCELAS[0][VENCIMENTO], PARCELAS[0][VALOR], PARCELAS[0][OBSERVACAO], PARCELAS[1][VENCIMENTO], PARCELAS[1][VALOR], …. Significado: TOTAL_RECEITAAPRO: Somatória do VL_VALOR_REC das RECEITA_APROPRIACAO. Se a natureza da conta (ST_CONTA_CONT) for do tipo 2 (despesa), ao invés de somar, deve ser subtraído o valor. · PRIORIZARHONORARIOS: 1 - Para utilizar o valor APROPRIARPRIMEIRO de cada RECEITA_APROPRIACAO · SIMULA_TOTAL: Somatória do VL_VALOR_REC das RECEITA_APROPRIACAO. Se a natureza da conta (ST_CONTA_CONT) for do tipo 2 (despesa), ao invés de somar, deve ser subtraído o valor. · NM_PARCELA_ACO: Número de parcelas do acordo · ALTERAR_ENCARGOS: Utilize (1) se for usar valores diferentes de taxas para esta cobrança · NM_TXJUROS_COND: Taxa de juros (ex: 1) - Se utilizar um valor diferente do padrão, envie flag 1 no parâmetro ALTERAR_ENCARGOS · NM_TXMULTA_COND: Taxa de multa (ex: 2) - Se utilizar um valor diferente do padrão, envie flag 1 no parâmetro ALTERAR_ENCARGOS · NM_TXDESCONTO_RECB: Taxa de desconto (ex: 0) - Se utilizar um valor diferente do padrão, envie flag 1 no parâmetro ALTERAR_ENCARGOS. |
| `query` | string | Não | Query params como JSON string. Vários endpoints de escrita da Superlógica leem os campos da query em vez do corpo — a doc indica quais. |

#### `superlogica_acordos_simularparcelas`

Receitas / Acordos / Obtendo dados para gerar o acordo: Simulando as parcelas do acordo (GET /acordos/simularparcelas). _(POST /api/superlogica/acordos/simularparcelas)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas licenças Superlógica conectadas: id ou label da conexão. Veja superlogica_list_accounts. |
| `query` | string | Não | Query params como JSON string. Datas em MM/DD/AAAA (americano). Nomes são case-sensitive. Parâmetros da doc: RECEITA_APROPRIACAO[][ST_CONTA_CONT], RECEITA_APROPRIACAO[][ST_DESCRICAO_CONT], RECEITA_APROPRIACAO[][ST_COMPLEMENTO_REC], RECEITA_APROPRIACAO[][VL_VALOR_REC], RECEITA_APROPRIACAO[][APROPRIARPRIMEIRO], TOTAL_RECEITAAPRO, PRIORIZARHONORARIOS, SIMULA_TOTAL, SIMULA_ENTRADA, NM_PARCELA_ACO, FL_EMITIR_RECIBO, DT_PRIMEIRA_PARCELA, ENTRADA[][VALOR], ENTRADA[][ID_FORMAPAGAMENTO_RECB], ENTRADA[][VENCIMENTO], PARCELAS[][VENCIMENTO], PARCELAS[][VALOR], PARCELAS[][OBSERVACAO], ALTERAR_ENCARGOS, NM_TXJUROS_COND, NM_TXMULTA_COND, NM_TXDESCONTO_RECB, ID_FORMA_RECB, ID_CONTABANCO_CB, DT_ACORDO_ACO, ID_IMPRESSAO_FIMP, TIPO_ACORDO, ID_UNIDADE_UNI, ID_CONDOMINIO_COND. |

#### `superlogica_arquivos_adicionaretiqueta`

Despesas / Etiquetas: Adicionar etiquetas (PUT /arquivos/adicionaretiqueta). _(POST /api/superlogica/arquivos/adicionaretiqueta)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas licenças Superlógica conectadas: id ou label da conexão. Veja superlogica_list_accounts. |
| `body` | string | Não | Corpo da requisição como JSON string (enviado como form-urlencoded). Datas em MM/DD/AAAA. Nomes case-sensitive. Parâmetros da doc: idDocumento, idEtiqueta. Significado: idDocumento: Id do arquivo · idEtiqueta: Id da etiqueta. |
| `query` | string | Não | Query params como JSON string. Vários endpoints de escrita da Superlógica leem os campos da query em vez do corpo — a doc indica quais. |

#### `superlogica_arquivos_create`

Documentos e Arquivos: Salvar novo arquivo (POST /arquivos). _(POST /api/superlogica/arquivos/create)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas licenças Superlógica conectadas: id ou label da conexão. Veja superlogica_list_accounts. |
| `body` | string | Não | Corpo da requisição como JSON string (enviado como form-urlencoded). Datas em MM/DD/AAAA. Nomes case-sensitive. Parâmetros da doc: ID_RESPONSAVEL_ARQ, FL_TIPO_ARQ, ARQUIVO. Significado: ID_RESPONSAVEL_ARQ: ID do contato responsável por este arquivo · FL_TIPO_ARQ: Define para qual funcionalidade o arquivo está vinculado 1 -> Cliente | 2 -> Unidade | 3 -> Fornecedor | 4 -> Usuário | 5 -> Movimentação direta | 6 -> Processo | 7 -> Conta digital | 8 -> Pessoa física | 9 -> Despesas anexo | 10 -> Solicitação | 11 -> Medição consumo · ARQUIVO: *Arquivo que deseja subir (Tamanho max 15MB). |
| `query` | string | Não | Query params como JSON string. Vários endpoints de escrita da Superlógica leem os campos da query em vez do corpo — a doc indica quais. |

#### `superlogica_arquivos_etiquetas`

Despesas / Etiquetas: Listar etiquetas (GET /arquivos/etiquetas). _(POST /api/superlogica/arquivos/etiquetas)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas licenças Superlógica conectadas: id ou label da conexão. Veja superlogica_list_accounts. |
| `query` | string | Não | Query params como JSON string. Datas em MM/DD/AAAA (americano). Nomes são case-sensitive. Parâmetros da doc: idArquivo, tipoEtiqueta. |

#### `superlogica_arquivos_list`

Unidades: Listar arquivos (GET /arquivos/index). _(POST /api/superlogica/arquivos/list)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas licenças Superlógica conectadas: id ou label da conexão. Veja superlogica_list_accounts. |
| `query` | string | Não | Query params como JSON string. Datas em MM/DD/AAAA (americano). Nomes são case-sensitive. |

#### `superlogica_arquivos_put`

Unidades: Adicionar arquivo (POST /arquivos/put). _(POST /api/superlogica/arquivos/put)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas licenças Superlógica conectadas: id ou label da conexão. Veja superlogica_list_accounts. |
| `body` | string | Não | Corpo da requisição como JSON string (enviado como form-urlencoded). Datas em MM/DD/AAAA. Nomes case-sensitive. Parâmetros da doc: ID_RESPONSAVEL_ARQ, FL_TIPO_ARQ, ARQUIVO. Significado: ID_RESPONSAVEL_ARQ: ID da unidade · FL_TIPO_ARQ: Tipo de arquivo (2 = Tipo unidade) · ARQUIVO: *Arquivo (Tamanho max 15MB). |
| `query` | string | Não | Query params como JSON string. Vários endpoints de escrita da Superlógica leem os campos da query em vez do corpo — a doc indica quais. |

#### `superlogica_arquivos_removeetiqueta`

Despesas / Etiquetas: Remover etiquetas (PUT /arquivos/removeetiqueta). _(POST /api/superlogica/arquivos/removeetiqueta)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas licenças Superlógica conectadas: id ou label da conexão. Veja superlogica_list_accounts. |
| `body` | string | Não | Corpo da requisição como JSON string (enviado como form-urlencoded). Datas em MM/DD/AAAA. Nomes case-sensitive. Parâmetros da doc: idDocumento, idEtiqueta. Significado: idDocumento: Id do arquivo · idEtiqueta: Id da etiqueta. |
| `query` | string | Não | Query params como JSON string. Vários endpoints de escrita da Superlógica leem os campos da query em vez do corpo — a doc indica quais. |

#### `superlogica_arrecadacoes_resumo`

Receitas: Resumo da arrecadação (GET /arrecadacoes/resumo). _(POST /api/superlogica/arrecadacoes/resumo)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas licenças Superlógica conectadas: id ou label da conexão. Veja superlogica_list_accounts. |
| `query` | string | Não | Query params como JSON string. Datas em MM/DD/AAAA (americano). Nomes são case-sensitive. Parâmetros da doc: dtInicio, idCondominio, verificarProcessamento, tipoCobranca, agruparPorTipoDeCobranca, pagina. |

#### `superlogica_balancetes_list`

Relatórios: W011A - Demonstrativo de receitas e despesas anual (GET /balancetes/index). _(POST /api/superlogica/balancetes/list)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas licenças Superlógica conectadas: id ou label da conexão. Veja superlogica_list_accounts. |
| `query` | string | Não | Query params como JSON string. Datas em MM/DD/AAAA (americano). Nomes são case-sensitive. Parâmetros da doc: idCondominio, dtInicio, dtFim, agrupadoPorMes. |

#### `superlogica_caixa_list`

Condomínios / Contas bancárias: Listar movimentações bancárias (GET /caixa). _(POST /api/superlogica/caixa/list)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas licenças Superlógica conectadas: id ou label da conexão. Veja superlogica_list_accounts. |
| `query` | string | Não | Query params como JSON string. Datas em MM/DD/AAAA (americano). Nomes são case-sensitive. Parâmetros da doc: idCondominio, dtInicio, dtFim, tipoFiltroData, idContaBancaria, semSaldoInicial. |

#### `superlogica_caixa_saldo`

Condomínios / Contas bancárias: Obter saldo de conta bancária (GET /caixa/saldo). _(POST /api/superlogica/caixa/saldo)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas licenças Superlógica conectadas: id ou label da conexão. Veja superlogica_list_accounts. |
| `query` | string | Não | Query params como JSON string. Datas em MM/DD/AAAA (americano). Nomes são case-sensitive. Parâmetros da doc: idConta, idEmpresa, dtInicio, ateAData. |

#### `superlogica_cobranca_create`

Receitas: Cadastrar nova cobrança (POST /cobranca). _(POST /api/superlogica/cobranca/create)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas licenças Superlógica conectadas: id ou label da conexão. Veja superlogica_list_accounts. |
| `body` | string | Não | Corpo da requisição como JSON string (enviado como form-urlencoded). Datas em MM/DD/AAAA. Nomes case-sensitive. Parâmetros da doc: ID_CONDOMINIO_COND, ID_UNIDADE_UNI, DT_VENCIMENTO_RECB, RECEITA_APROPRIACAO[0][ST_CONTA_CONT], RECEITA_APROPRIACAO[0][ST_DESCRICAO_CONT], RECEITA_APROPRIACAO[0][VL_VALOR_REC], RECEITA_APROPRIACAO[0][ST_COMPLEMENTO_REC], RECEITA_APROPRIACAO[0][APROPRIARPRIMEIRO], VALOR_TOTAL, NUMERO_PERCELAS, ALTERAR_ENCARGOS, NM_TXJUROS_COND, NM_TXMULTA_COND, NM_TXDESCONTO_COND, FL_TIPOCOB_COT, ID_CONTABANCO_CB, ID_FORMAPAGAMENTO_RECB, DT_COMPETENCIA. Significado: ID_CONDOMINIO_COND: *ID do condomínio (Para conseguir esse valor use o endpoint do Condominios->Listar todos os condomínios) · ID_UNIDADE_UNI: *ID da unidade(Para conseguir esse valor use o endpoint do Unidades->Listar unidades de um condomínio) · DT_VENCIMENTO_RECB: *Data de vencimento · RECEITA_APROPRIACAO[0][ST_CONTA_CONT]: *ID da conta categoria (ex: 1.9) · RECEITA_APROPRIACAO[0][ST_DESCRICAO_CONT]: (Opcional) Deixe em branco para usar automaticamente a descrição da conta categoria passado no ID do parâmetro ST_CONTA_CONT · RECEITA_APROPRIACAO[0][VL_VALOR_REC]: *Valor do serviço · RECEITA_APROPRIACAO[0][ST_COMPLEMENTO_REC]: (Opcional) Complemento da conta categoria selecionada · VALOR_TOTAL: *Total de todas as apropriações. |
| `query` | string | Não | Query params como JSON string. Vários endpoints de escrita da Superlógica leem os campos da query em vez do corpo — a doc indica quais. |

#### `superlogica_cobranca_desinvalidar`

Receitas: Cancelar invalidação de uma cobrança (PUT /cobranca/desinvalidar). _(POST /api/superlogica/cobranca/desinvalidar)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas licenças Superlógica conectadas: id ou label da conexão. Veja superlogica_list_accounts. |
| `body` | string | Não | Corpo da requisição como JSON string (enviado como form-urlencoded). Datas em MM/DD/AAAA. Nomes case-sensitive. Parâmetros da doc: id, ID_CONDOMINIO. Significado: id: *ID da cobrança (ID_RECEBIMENTO_RECB) · ID_CONDOMINIO: *ID do condomínio (Para conseguir esse valor use o endpoint do Condominios->Listar todos os condomínios). |
| `query` | string | Não | Query params como JSON string. Vários endpoints de escrita da Superlógica leem os campos da query em vez do corpo — a doc indica quais. |

#### `superlogica_cobranca_estornar`

Receitas: Estornar uma cobrança (PUT /cobranca/estornar). _(POST /api/superlogica/cobranca/estornar)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas licenças Superlógica conectadas: id ou label da conexão. Veja superlogica_list_accounts. |
| `body` | string | Não | Corpo da requisição como JSON string (enviado como form-urlencoded). Datas em MM/DD/AAAA. Nomes case-sensitive. Parâmetros da doc: id, ID_CONDOMINIO. Significado: id: *ID da cobrança (Para conseguir essa informação use os endpoint para Listar as cobranças e use o campo ID_RECEBIMENTO_RECB) · ID_CONDOMINIO: *ID do condomínio (Para conseguir esse valor use o endpoint do Condominios->Listar todos os condomínios). |
| `query` | string | Não | Query params como JSON string. Vários endpoints de escrita da Superlógica leem os campos da query em vez do corpo — a doc indica quais. |

#### `superlogica_cobranca_excluir`

Receitas: Excluir uma cobrança (PUT /cobranca/excluir). _(POST /api/superlogica/cobranca/excluir)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas licenças Superlógica conectadas: id ou label da conexão. Veja superlogica_list_accounts. |
| `body` | string | Não | Corpo da requisição como JSON string (enviado como form-urlencoded). Datas em MM/DD/AAAA. Nomes case-sensitive. Parâmetros da doc: id, ID_CONDOMINIO, CANCELAR_RESERVA, EXCLUIR_RECEITA. Significado: id: *ID da cobrança (ID_RECEBIMENTO_RECB) · ID_CONDOMINIO: *ID do condomínio (Para conseguir esse valor use o endpoint do Condominios->Listar todos os condomínios) · CANCELAR_RESERVA: 1 - Para cancelar a reserva vinculada (opcional). |
| `query` | string | Não | Query params como JSON string. Vários endpoints de escrita da Superlógica leem os campos da query em vez do corpo — a doc indica quais. |

#### `superlogica_cobranca_gerarlinksegundavia`

2a via: Gerar link para download de 2a via de boleto (GET /cobranca/gerarlinksegundavia). _(POST /api/superlogica/cobranca/gerarlinksegundavia)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas licenças Superlógica conectadas: id ou label da conexão. Veja superlogica_list_accounts. |
| `query` | string | Não | Query params como JSON string. Datas em MM/DD/AAAA (americano). Nomes são case-sensitive. Parâmetros da doc: ID_CONDOMINIO_COND, ID_RECEBIMENTO_RECB, DT_VENCIMENTO_RECB, DT_ATUALIZACAO_VENCIMENTO. |

#### `superlogica_cobranca_liquidar`

Receitas: Liquidar uma cobrança (PUT /cobranca/liquidar). _(POST /api/superlogica/cobranca/liquidar)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas licenças Superlógica conectadas: id ou label da conexão. Veja superlogica_list_accounts. |
| `body` | string | Não | Corpo da requisição como JSON string (enviado como form-urlencoded). Datas em MM/DD/AAAA. Nomes case-sensitive. Parâmetros da doc: DT_LIQUIDACAO_RECB, DT_RECEBIMENTO_RECB, VL_PAGO, VL_DESCONTO, ID_FORMAPAGAMENTO_RECB, ID_CONDOMINIO_COND, ID_RECEBIMENTO_RECB, ID_CONTABANCO_CB, VL_EMITIDO_RECB, VL_DEVIDO, DT_VENCIMENTO, TX_BANCARIA, EMITIR_RECIBO, VL_JUROS, VL_MULTA, VL_ATUALIZACAOMOMETARIA, ST_OBSERVACAO_RECB, DEBITAR_TX_BANCARIA. Significado: DT_LIQUIDACAO_RECB: *Data de liquidação (m/d/Y) · DT_RECEBIMENTO_RECB: *Data de recebimento (m/d/Y) · VL_PAGO: *Valor total pago · VL_DESCONTO: Desconto(opcional) · ID_CONDOMINIO_COND: *ID do condomínio (Para conseguir esse valor use o endpoint do Condominios->Listar todos os condomínios) · ID_RECEBIMENTO_RECB: *ID da cobrança · ID_CONTABANCO_CB: *ID da conta bancária (Para conseguir essa informação use o endPoint "Condominios->Contas Bancárias->Lista contas bancárias") · VL_EMITIDO_RECB: Valor emitido. |
| `query` | string | Não | Query params como JSON string. Vários endpoints de escrita da Superlógica leem os campos da query em vez do corpo — a doc indica quais. |

#### `superlogica_cobranca_list`

Receitas / Acordos / Obtendo dados para gerar o acordo: Listando composições do acordo (GET /cobranca/index). _(POST /api/superlogica/cobranca/list)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas licenças Superlógica conectadas: id ou label da conexão. Veja superlogica_list_accounts. |
| `query` | string | Não | Query params como JSON string. Datas em MM/DD/AAAA (americano). Nomes são case-sensitive. Parâmetros da doc: apenasColunasPrincipais, semProcesso, comValoresAtualizados, status, ordenacao[], id, comHonorarios, somenteComposicoesAcordo, comDadosDasContasEReceitas, comComposicoes, dtAtualizacao, ids[], idCondominio, exibirPgtoComDiferenca, comContatosDaUnidade, filtrarpor, dtInicio, dtFim, itensPorPagina, pagina, comDadosDasUnidades, exibirDadosDoContato, comDadosDasApropriacoes, getEncargosRaw, UNIDADES[]. |

#### `superlogica_cobranca_update`

Receitas: Editar uma cobrança (PUT /cobranca/update). _(POST /api/superlogica/cobranca/update)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas licenças Superlógica conectadas: id ou label da conexão. Veja superlogica_list_accounts. |
| `body` | string | Não | Corpo da requisição como JSON string (enviado como form-urlencoded). Datas em MM/DD/AAAA. Nomes case-sensitive. Parâmetros da doc: ID_RECEBIMENTO_RECB, FL_STATUS_RECB, DT_VENCIMENTO_RECB, RECEITA_APROPRIACAO[0][ID_RECEITA_REC], RECEITA_APROPRIACAO[0][ST_CONTA_CONT], RECEITA_APROPRIACAO[0][ST_DESCRICAO_CONT], RECEITA_APROPRIACAO[0][ST_COMPLEMENTO_REC], RECEITA_APROPRIACAO[0][VL_VALOR_REC], RECEITA_APROPRIACAO[0][VL_VALOR_RECA], RECEITA_APROPRIACAO[0][VL_VALOR_RECA_CLEAN], RECEITA_APROPRIACAO[0][ID_RETORNOITEMDUPLICADO_RETI], RECEITA_APROPRIACAO[0][FL_PGMTINDEVIDO_REC], RECEITA_APROPRIACAO[0][VL_SALDO_REC], RECEITA_APROPRIACAO[0][DT_RECEITA_REC], RECEITA_APROPRIACAO[0][ST_LABEL_REC], RECEITA_APROPRIACAO[0][TX_ANOTACAO_REC], RECEITA_APROPRIACAO[1][ID_RECEITA_REC], RECEITA_APROPRIACAO[1][ST_CONTA_CONT], RECEITA_APROPRIACAO[1][ST_DESCRICAO_CONT], RECEITA_APROPRIACAO[1][ST_COMPLEMENTO_REC], RECEITA_APROPRIACAO[1][VL_VALOR_REC], RECEITA_APROPRIACAO[1][VL_VALOR_RECA], RECEITA_APROPRIACAO[1][VL_VALOR_RECA_CLEAN], RECEITA_APROPRIACAO[1][ID_RETORNOITEMDUPLICADO_RETI], RECEITA_APROPRIACAO[1][FL_PGMTINDEVIDO_REC], RECEITA_APROPRIACAO[1][VL_SALDO_REC], RECEITA_APROPRIACAO[1][DT_RECEITA_REC], RECEITA_APROPRIACAO[1][ST_LABEL_REC], RECEITA_APROPRIACAO[1][TX_ANOTACAO_REC], FL_DESCONTOVALORFIXO_COND, …. Significado: ID_RECEBIMENTO_RECB: *ID da cobrança · DT_VENCIMENTO_RECB: Data de vencimento · alterarTxJuros: Utilize 1 para valores padrões (ignora NM_TXJUROS_COND) e 0 para utiizar o valor definido no campo NM_TXJUROS_COND · alterarTxMulta: Utilize 1 para valores padrões (ignora NM_TXMULTA_COND) e 0 para utiizar o valor definido no campo NM_TXMULTA_COND · alterarTxDesconto: Utilize 1 para valores padrões (ignora NM_TXDESCONTO_RECB) e 0 para utiizar o valor definido no campo NM_TXDESCONTO_RECB · ID_CONDOMINIO_COND: *ID do condomínio (Para conseguir esse valor use o endpoint do Condominios->Listar todos os condomínios) · id: *ID da cobrança (ID_RECEBIMENTO_RECB) · ID_CONDOMINIO: *ID do condomínio (Para conseguir esse valor use o endpoint do Condominios->Listar todos os condomínios). |
| `query` | string | Não | Query params como JSON string. Vários endpoints de escrita da Superlógica leem os campos da query em vez do corpo — a doc indica quais. |

#### `superlogica_comunicados_create`

Comunicados: Criar novo comunicado (POST /comunicados). _(POST /api/superlogica/comunicados/create)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas licenças Superlógica conectadas: id ou label da conexão. Veja superlogica_list_accounts. |
| `body` | string | Não | Corpo da requisição como JSON string (enviado como form-urlencoded). Datas em MM/DD/AAAA. Nomes case-sensitive. Parâmetros da doc: ST_TITULO_COM, ST_TEXTO_COM, ID_CONDOMINIO_COND, FL_DESTINATARIO_COM, FL_CANALCOMUNICACAO_COM, FL_NOTIFICAR_COM. Significado: ST_TITULO_COM: *Título do Comunicado · ST_TEXTO_COM: *Texto do comunicado (HTML) · ID_CONDOMINIO_COND: *ID do condomínio (Para conseguir esse valor use o endpoint do Condominios->Listar todos os condomínios) · FL_DESTINATARIO_COM: 1 = 'para unidades deste condomínio' | 2 = 'para responsáveis legais deste condomínio' | 3 = 'para todos deste condomínio' | 4 = 'para unidades de todos os condomínios' | 5 = 'para responsáveis legais de todos os condomínios' | 6 = 'para todos de todos os condomínios' · FL_CANALCOMUNICACAO_COM: 1 = VIA AREA CONDOMINO | 2 = CARTA | 3 = VIA CARTA E AREA | 4 = EMAIL E AREA | 5 = EMAIL,CARTA E AREA · FL_NOTIFICAR_COM: *Importante se não enviar 1 não vai notificar!. |
| `query` | string | Não | Query params como JSON string. Vários endpoints de escrita da Superlógica leem os campos da query em vez do corpo — a doc indica quais. |

#### `superlogica_comunicados_notificarcomunicado`

Comunicados: Disparar comunicados pendentes (POST /comunicados/notificarcomunicado). _(POST /api/superlogica/comunicados/notificarcomunicado)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas licenças Superlógica conectadas: id ou label da conexão. Veja superlogica_list_accounts. |
| `body` | string | Não | Corpo da requisição como JSON string (enviado como form-urlencoded). Datas em MM/DD/AAAA. Nomes case-sensitive. |
| `query` | string | Não | Query params como JSON string. Vários endpoints de escrita da Superlógica leem os campos da query em vez do corpo — a doc indica quais. |

#### `superlogica_condominiogrupos_list`

Condomínios: Listar grupos de condominios (GET /condominiogrupos/index). _(POST /api/superlogica/condominiogrupos/list)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas licenças Superlógica conectadas: id ou label da conexão. Veja superlogica_list_accounts. |
| `query` | string | Não | Query params como JSON string. Datas em MM/DD/AAAA (americano). Nomes são case-sensitive. Parâmetros da doc: somenteGruposComCondominios. |

#### `superlogica_condominios_create`

Condomínios: Cadastrar novo condomínio (POST /condominios). _(POST /api/superlogica/condominios/create)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas licenças Superlógica conectadas: id ou label da conexão. Veja superlogica_list_accounts. |
| `body` | string | Não | Corpo da requisição como JSON string (enviado como form-urlencoded). Datas em MM/DD/AAAA. Nomes case-sensitive. Parâmetros da doc: ST_NOME_COND, ST_FANTASIA_COND, ST_CPF_COND, ST_LABEL_COND, ST_ENDERECO_COND, ST_NUMEROENDERECO_COND, ST_BAIRRO_COND, ST_CEP_COND, ST_CIDADE_COND, ST_ESTADO_COND, ID_PLANOCONTA_PLC, DT_DIAVENCIMENTO_COND, ID_TIPOCOBRANCA_TCO, DT_DATAABERTURA_CB, CONTASBANCARIAS[0][ID_BANCO_BANC], CONTASBANCARIAS[0][ST_NOME_BANC], CONTASBANCARIAS[0][ST_CONTA_CB], CONTASBANCARIAS[0][ST_NUMERO_AGB], CONTASBANCARIAS[0][ST_DESCRICAO_CB], CONTASBANCARIAS[0][VL_SALDO_CB], CONTASBANCARIAS[0][FL_PRINCIPAL_CB], ST_COMPLEMENTO_COND, ST_TELEFONE_COND. Significado: ST_NOME_COND: *Nome Condomínio · ST_FANTASIA_COND: *Nome Fantasia · ST_CPF_COND: *CNPJ · ST_LABEL_COND: Label · ST_ENDERECO_COND: Endereço · ST_NUMEROENDERECO_COND: Número · ST_BAIRRO_COND: Bairro · ST_CEP_COND: CEP. |
| `query` | string | Não | Query params como JSON string. Vários endpoints de escrita da Superlógica leem os campos da query em vez do corpo — a doc indica quais. |

#### `superlogica_condominios_get`

Condomínios: Listar todos os condomínios (GET /condominios/get). _(POST /api/superlogica/condominios/get)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas licenças Superlógica conectadas: id ou label da conexão. Veja superlogica_list_accounts. |
| `query` | string | Não | Query params como JSON string. Datas em MM/DD/AAAA (americano). Nomes são case-sensitive. Parâmetros da doc: id, somenteCondominiosAtivos, ignorarCondominioModelo, apenasColunasPrincipais, apenasDadosDoPlanoDeContas, comDataFechamento, itensPorPagina, pagina. |

#### `superlogica_condominios_update`

Condomínios: Editar dados condomínio (PUT /condominios). _(POST /api/superlogica/condominios/update)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas licenças Superlógica conectadas: id ou label da conexão. Veja superlogica_list_accounts. |
| `body` | string | Não | Corpo da requisição como JSON string (enviado como form-urlencoded). Datas em MM/DD/AAAA. Nomes case-sensitive. Parâmetros da doc: ID_CONDOMINIO_COND, ST_NOME_COND, ST_FANTASIA_COND, ST_CPF_COND, ST_LABEL_COND, ST_ENDERECO_COND, ST_NUMEROENDERECO_COND, ST_BAIRRO_COND, ST_CEP_COND, ST_CIDADE_COND, ST_ESTADO_COND, ID_PLANOCONTA_PLC, DT_DIAVENCIMENTO_COND, FL_ATIVO_COND, DT_DATAABERTURA_CB, ST_COMPLEMENTO_COND, ST_TELEFONE_COND, ST_FAX_COND, ST_INSCRMUNICIPAL_COND, ST_INSCRESTADUAL_COND. Significado: ID_CONDOMINIO_COND: Id do condominio que vai ser editado · ST_NOME_COND: Nome Condomínio · ST_FANTASIA_COND: Nome Fantasia · ST_CPF_COND: CNPJ · ST_LABEL_COND: Label · ST_ENDERECO_COND: Endereço · ST_NUMEROENDERECO_COND: Número · ST_BAIRRO_COND: Bairro. |
| `query` | string | Não | Query params como JSON string. Vários endpoints de escrita da Superlógica leem os campos da query em vez do corpo — a doc indica quais. |

#### `superlogica_configuracoes_create`

Condomínios: Alterar valor de uma configuração específica de um condomínio (POST /configuracoes). _(POST /api/superlogica/configuracoes/create)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas licenças Superlógica conectadas: id ou label da conexão. Veja superlogica_list_accounts. |
| `body` | string | Não | Corpo da requisição como JSON string (enviado como JSON). Datas em MM/DD/AAAA. Nomes case-sensitive. Parâmetros da doc: idCondominio, NOME_CONFIG. |
| `query` | string | Não | Query params como JSON string. Vários endpoints de escrita da Superlógica leem os campos da query em vez do corpo — a doc indica quais. |

#### `superlogica_configuracoes_list`

Condomínios: Listar configurações específicas de um condomínio (GET /configuracoes). _(POST /api/superlogica/configuracoes/list)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas licenças Superlógica conectadas: id ou label da conexão. Veja superlogica_list_accounts. |
| `query` | string | Não | Query params como JSON string. Datas em MM/DD/AAAA (americano). Nomes são case-sensitive. Parâmetros da doc: idCondominio. |

#### `superlogica_configuracoes_list_get`

Receitas: Configurações de boletos em um condomínio (GET /configuracoes/index). _(POST /api/superlogica/configuracoes/list/get)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas licenças Superlógica conectadas: id ou label da conexão. Veja superlogica_list_accounts. |
| `query` | string | Não | Query params como JSON string. Datas em MM/DD/AAAA (americano). Nomes são case-sensitive. Parâmetros da doc: idCondominio. |

#### `superlogica_consumo_list`

Consumo: Consulta de consumo (GET /consumo/index). _(POST /api/superlogica/consumo/list)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas licenças Superlógica conectadas: id ou label da conexão. Veja superlogica_list_accounts. |
| `query` | string | Não | Query params como JSON string. Datas em MM/DD/AAAA (americano). Nomes são case-sensitive. Parâmetros da doc: tipoLeitura, idCondominio, posicaoEm. |

#### `superlogica_consumo_put_create`

Consumo: Inserir consumo (POST /consumo/put). _(POST /api/superlogica/consumo/put/create)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas licenças Superlógica conectadas: id ou label da conexão. Veja superlogica_list_accounts. |
| `body` | string | Não | Corpo da requisição como JSON string (enviado como JSON). Datas em MM/DD/AAAA. Nomes case-sensitive. Parâmetros da doc: tipoLeitura, id_condominio_cond, id_unidade_uni, posicaoEm, leituras[mes_atual][nm_ano_rsp], leituras[mes_atual][nm_mes_rsp], leituras[mes_atual][id_tipo_rec], leituras[apenas_editar_medidor], leituras[mes_atual][diadaleitura], novaleitura_mes_atual. |
| `query` | string | Não | Query params como JSON string. Vários endpoints de escrita da Superlógica leem os campos da query em vez do corpo — a doc indica quais. |

#### `superlogica_consumo_put_update`

Consumo: Edição de consumo (PUT /consumo/put). _(POST /api/superlogica/consumo/put/update)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas licenças Superlógica conectadas: id ou label da conexão. Veja superlogica_list_accounts. |
| `body` | string | Não | Corpo da requisição como JSON string (enviado como JSON). Datas em MM/DD/AAAA. Nomes case-sensitive. Parâmetros da doc: tipoLeitura, id_condominio_cond, id_unidade_uni, posicaoEm, leituras[mes_atual][nm_ano_rsp], leituras[mes_atual][nm_mes_rsp], leituras[mes_atual][id_tipo_rec], leituras[apenas_editar_medidor], leituras[mes_atual][diadaleitura], leituras[mes_anterior][vl_valor_rsp], leituras[mes_atual][vl_valor_rsp], novaleitura_mes_atual, id_arquivo_arq. |
| `query` | string | Não | Query params como JSON string. Vários endpoints de escrita da Superlógica leem os campos da query em vez do corpo — a doc indica quais. |

#### `superlogica_contabancos_list`

Condomínios / Contas bancárias: Listar contas bancárias (GET /contabancos/index). _(POST /api/superlogica/contabancos/list)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas licenças Superlógica conectadas: id ou label da conexão. Veja superlogica_list_accounts. |
| `query` | string | Não | Query params como JSON string. Datas em MM/DD/AAAA (americano). Nomes são case-sensitive. Parâmetros da doc: exibirDadosAgencia, exibirContasFechadas, exibirDadosBanco, exibirContasAtivas, idCondominio. |

#### `superlogica_contatofavorecido_create`

Despesas: Cadastrar dados de pagamento favorecido (POST /contatofavorecido). _(POST /api/superlogica/contatofavorecido/create)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas licenças Superlógica conectadas: id ou label da conexão. Veja superlogica_list_accounts. |
| `body` | string | Não | Corpo da requisição como JSON string (enviado como form-urlencoded). Datas em MM/DD/AAAA. Nomes case-sensitive. Parâmetros da doc: ST_NOMERECEBEDOR_FAV, FL_PRINCIPAL_FAV, FL_TIPOCONTA_FAV, ST_BANCO_FAV, ST_NOME_BANC, ST_AGENCIA_FAV, ST_CONTABANCARIA_FAV, ID_FORMA_PAG, ID_CONTATO_CON, FL_CPFCNPJTERCEIRO, ST_CPFCNPJRECEBEDOR_FAV. Significado: ST_NOMERECEBEDOR_FAV: Nome referência · FL_PRINCIPAL_FAV: Método principal (0 | 1) · FL_TIPOCONTA_FAV: Tipo da conta (0 - Conta corrente | 1 - Poupança) · ST_BANCO_FAV: Banco (Para conseguir esse valor use o endpoint do Despesas ->Listar favorecidos) · ST_NOME_BANC: Banco · ST_AGENCIA_FAV: Agência (com dígito) · ST_CONTABANCARIA_FAV: Conta ( Informe o dígito da conta separado por um traço, por exemplo: 1234-5) · ID_FORMA_PAG: Forma de pagamento (0 Boleto | 1 Cheque | 2 Dinheiro | 3 Cartão de crédito | 4 Cartão de débito | 7 Débito automático | 8 Trans. bancária | 9 Doc/Ted | 10 Outros | 12 Pix | 13 DCTFWeb). |
| `query` | string | Não | Query params como JSON string. Vários endpoints de escrita da Superlógica leem os campos da query em vez do corpo — a doc indica quais. |

#### `superlogica_contatofavorecido_list`

Despesas: Listar dados pagamento favorecido (GET /contatofavorecido/index). _(POST /api/superlogica/contatofavorecido/list)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas licenças Superlógica conectadas: id ou label da conexão. Veja superlogica_list_accounts. |
| `query` | string | Não | Query params como JSON string. Datas em MM/DD/AAAA (americano). Nomes são case-sensitive. Parâmetros da doc: comStatus, idFornecedor. |

#### `superlogica_contatos_delete`

Unidades: Excluir um contato (POST /contatos/delete). _(POST /api/superlogica/contatos/delete)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas licenças Superlógica conectadas: id ou label da conexão. Veja superlogica_list_accounts. |
| `body` | string | Não | Corpo da requisição como JSON string (enviado como form-urlencoded). Datas em MM/DD/AAAA. Nomes case-sensitive. Parâmetros da doc: idUnidade, idCondominio, idContato. |
| `query` | string | Não | Query params como JSON string. Vários endpoints de escrita da Superlógica leem os campos da query em vez do corpo — a doc indica quais. |

#### `superlogica_despesas_anexar`

Despesas: Anexar arquivos (POST /despesas/anexar). _(POST /api/superlogica/despesas/anexar)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas licenças Superlógica conectadas: id ou label da conexão. Veja superlogica_list_accounts. |
| `body` | string | Não | Corpo da requisição como JSON string (enviado como form-urlencoded). Datas em MM/DD/AAAA. Nomes case-sensitive. Parâmetros da doc: ID_DESPESA_DES, ID_PARCELA_PDES, ARQUIVOS[][ID_ARQUIVO_ARQ]. |
| `query` | string | Não | Query params como JSON string. Vários endpoints de escrita da Superlógica leem os campos da query em vez do corpo — a doc indica quais. |

#### `superlogica_despesas_create`

Despesas: Cadastrar nova despesa (POST /despesas). _(POST /api/superlogica/despesas/create)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas licenças Superlógica conectadas: id ou label da conexão. Veja superlogica_list_accounts. |
| `body` | string | Não | Corpo da requisição como JSON string (enviado como form-urlencoded). Datas em MM/DD/AAAA. Nomes case-sensitive. Parâmetros da doc: ID_CONDOMINIO_COND, ST_NOME_CON, ID_CONTATO_CON, ST_NOMERECEBEDOR_FAV, ID_FAVORECIDO_CON, DT_VENCIMENTOPRIMEIRAPARCELA, ID_FORMA_PAG, DADOS_PAGAMENTOS, ID_FAVORECIDO_FAV, DT_DESPESA_DES, ID_TIPO_DOC, ST_DOCUMENTO_DES, ST_SERIENOTA_DES, APROPRIACAO[0][ST_CONTA_CONT], APROPRIACAO[0][ST_DESCRICAO_CONT], APROPRIACAO[0][ST_COMPLEMENTO_APRO], APROPRIACAO[0][VL_VALOR_PDES], APROPRIACAO[0][ST_NOMEGRUPOSALDO_GS], APROPRIACAO[0][ID_GRUPOSALDO_GS], RETENCOES[0][ID_RV2_IMPOSTO_DES], RETENCOES[0][DT_VENCIMENTO_PDES], RETENCOES[0][FL_RETERIMPOSTO_DES], RETENCOES[0][ST_COMPLEMENTO_PDES], RETENCOES[0][ST_CODIGOBARRAS_PDES], CHECK_LIQUIDAR_TODOS_CH, DT_LIQUIDACAO_PDES, VL_DESCONTO_PDES, VL_MULTA_PDES, VL_JUROS_PDES, VL_PAGO, …. Significado: ID_CONDOMINIO_COND: *ID do condomínio · ST_NOME_CON: *Nome do Fornecedor · ID_CONTATO_CON: *ID do Fornecedor (Para conseguir esse valor use o endpoint do Despesas ->Listar favorecidos) · ST_NOMERECEBEDOR_FAV: Nome do Favorecido · ID_FAVORECIDO_CON: ID do Favorecido (Para conseguir esse valor use o endpoint do Despesas ->Listar favorecidos) · DT_VENCIMENTOPRIMEIRAPARCELA: *Data de vencimento · ID_FORMA_PAG: *ID Forma pagamento (0 Boleto | 1 Cheque | 2 Dinheiro | 3 Cartão de crédito | 4 Cartão de débito | 7 Débito automático | 8 Trans. bancária | 9 Doc/Ted | 10 Outros | 12 Pix | 13 DCTFWeb)) · DADOS_PAGAMENTOS: Dados Pagamento (Para conseguir esse valor use o endpoint do Despesas -> Listar dados pagamento favorecido " DADOS_PAGAMENTOS = st_nomerecebedor"). |
| `query` | string | Não | Query params como JSON string. Vários endpoints de escrita da Superlógica leem os campos da query em vez do corpo — a doc indica quais. |

#### `superlogica_despesas_delete`

Despesas: Excluir despesa (PUT /despesas/delete). _(POST /api/superlogica/despesas/delete)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas licenças Superlógica conectadas: id ou label da conexão. Veja superlogica_list_accounts. |
| `body` | string | Não | Corpo da requisição como JSON string (enviado como form-urlencoded). Datas em MM/DD/AAAA. Nomes case-sensitive. Parâmetros da doc: ID_PARCELA_PDES. |
| `query` | string | Não | Query params como JSON string. Vários endpoints de escrita da Superlógica leem os campos da query em vez do corpo — a doc indica quais. |

#### `superlogica_despesas_despesasrecorrente`

Despesas: Listar despesas recorrentes não lançadas (GET /despesas/despesasrecorrente). _(POST /api/superlogica/despesas/despesasrecorrente)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas licenças Superlógica conectadas: id ou label da conexão. Veja superlogica_list_accounts. |
| `query` | string | Não | Query params como JSON string. Datas em MM/DD/AAAA (americano). Nomes são case-sensitive. Parâmetros da doc: idCondominio, dtInicio, dtFim, itensPorPagina, pagina. |

#### `superlogica_despesas_estornar`

Despesas: Estornar despesa (PUT /despesas/estornar). _(POST /api/superlogica/despesas/estornar)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas licenças Superlógica conectadas: id ou label da conexão. Veja superlogica_list_accounts. |
| `body` | string | Não | Corpo da requisição como JSON string (enviado como form-urlencoded). Datas em MM/DD/AAAA. Nomes case-sensitive. Parâmetros da doc: ID_PARCELA_PDES. Significado: ID_PARCELA_PDES: ID da parcela. |
| `query` | string | Não | Query params como JSON string. Vários endpoints de escrita da Superlógica leem os campos da query em vez do corpo — a doc indica quais. |

#### `superlogica_despesas_liquidar`

Despesas: Liquidar despesa (PUT /despesas/liquidar). _(POST /api/superlogica/despesas/liquidar)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas licenças Superlógica conectadas: id ou label da conexão. Veja superlogica_list_accounts. |
| `body` | string | Não | Corpo da requisição como JSON string (enviado como form-urlencoded). Datas em MM/DD/AAAA. Nomes case-sensitive. Parâmetros da doc: ID_DESPESA_DES, ID_PARCELA_PDES, ID_CONTATO_CON, ST_NOME_CON, DT_LIQUIDACAO_PDES, ID_FORMA_PAG, ID_CONTABANCO_CB, NM_NUMERO_CH, VL_VALOR_PDES, CHECK_LIQUIDAR_TODOS_CH, EMITIR_RECIBO, VL_DESCONTO_PDES, VL_MULTA_PDES, VL_JUROS_PDES, VL_PAGO, ID_CONDOMINIO_COND, ARQUIVOS[]. |
| `query` | string | Não | Query params como JSON string. Vários endpoints de escrita da Superlógica leem os campos da query em vez do corpo — a doc indica quais. |

#### `superlogica_despesas_list`

Despesas: Listar despesas por período (GET /despesas/index). _(POST /api/superlogica/despesas/list)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas licenças Superlógica conectadas: id ou label da conexão. Veja superlogica_list_accounts. |
| `query` | string | Não | Query params como JSON string. Datas em MM/DD/AAAA (americano). Nomes são case-sensitive. Parâmetros da doc: comStatus, dtInicio, dtFim, filtrarpor, idCondominio, CONTAS[], itensPorPagina, pagina. |

#### `superlogica_despesas_post`

Despesas: Editar despesa (PUT /despesas/post). _(POST /api/superlogica/despesas/post)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas licenças Superlógica conectadas: id ou label da conexão. Veja superlogica_list_accounts. |
| `body` | string | Não | Corpo da requisição como JSON string (enviado como form-urlencoded). Datas em MM/DD/AAAA. Nomes case-sensitive. Parâmetros da doc: ST_NOME_CON, ST_CODIGORECEITA_PDES, ST_NOMECONTRIBUINTE_PDES, FL_TIPOCONTRIBUINTE_PDES, ST_IDENTCONTRIBUINTE_PDES, DT_VENCIMENTO_PDES, ST_TRIBUTONUMEROREF_PDES, DT_TRIBUTOPERIODO_PDES, APROPRIACAO[0][ST_CONTA_CONT], APROPRIACAO[0][ST_DESCRICAO_CONT], APROPRIACAO[0][ID_DESPESA_DES], APROPRIACAO[0][ST_COMPLEMENTO_APRO], APROPRIACAO[0][VL_VALOR_PDES], APROPRIACAO[0][FL_TIPOTRIBUTO_PDES], APROPRIACAO[0][VL_TRIBUTO_PDES], APROPRIACAO[0][VL_OUTRASENTIDADES_PDES], APROPRIACAO[0][VL_TRIBUTOMULTA_PDES], APROPRIACAO[0][VL_TRIBUTOENCARGOS_PDES], VL_TRIBUTORECEITABRUTA_PDES, ST_PORCENTORECEITABRUTA_PDES, DT_DESPESA_DES, ST_DOCUMENTO_DES, ID_FORMA_PAG, DESPESA_FECHADA, RATEIO_FECHADO, ID_RV2_IMPOSTO_DES, VL_TEMP, ID_RV2_ORIGEM_DES, VL_RV2_VALORRETIDO_DES, VL_RV2_SUBEMPREITADA_DES, …. Significado: APROPRIACAO[0][VL_VALOR_PDES]: Valor individual de cada conta categoria · DESPESA_FECHADA: *(opcional) · RATEIO_FECHADO: *(opcional) · DESPESA_PARCELA[0][VL_VALOR_PDES]: (Soma de todas as apropriações / quantidade de parcelas) · RETENCOES[0][DT_VENCIMENTO_PDES]: *(opcional) · ID_TIPO_DOC: Tipo do documento: 1 -> Nota Fiscal | 2 -> Imposto | 3 -> Fatura | 4 -> Recibo | 5 -> Cupom Fiscal | 6 -> Outros · ST_SERIENOTA_DES: Apenas se o tipo do documento for igual a 1 (Nota Fiscal) · ARQUIVOS[0][ID_ARQUIVO_ARQ]: *(Opcional) Vincular um arquivo na despesa. OBS: É importante enviar todos os arquivos previamente vinculados. Caso contrário, apenas o novo arquivo será cadastrado, resultando na remoção de todos os arquivos anteriores.. |
| `query` | string | Não | Query params como JSON string. Vários endpoints de escrita da Superlógica leem os campos da query em vez do corpo — a doc indica quais. |

#### `superlogica_documentos_create`

Documentos e Arquivos: Inserir novo documento (POST /documentos). _(POST /api/superlogica/documentos/create)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas licenças Superlógica conectadas: id ou label da conexão. Veja superlogica_list_accounts. |
| `body` | string | Não | Corpo da requisição como JSON string (enviado como form-urlencoded). Datas em MM/DD/AAAA. Nomes case-sensitive. Parâmetros da doc: arquivo, idEmpresa, publicar. Significado: arquivo: Arquivo que deseja subir. |
| `query` | string | Não | Query params como JSON string. Vários endpoints de escrita da Superlógica leem os campos da query em vez do corpo — a doc indica quais. |

#### `superlogica_formasdepagamento_list`

Condomínios: Listar formas de pagamento (GET /formasdepagamento). _(POST /api/superlogica/formasdepagamento/list)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas licenças Superlógica conectadas: id ou label da conexão. Veja superlogica_list_accounts. |
| `query` | string | Não | Query params como JSON string. Datas em MM/DD/AAAA (americano). Nomes são case-sensitive. Parâmetros da doc: paraCobranca, paraDespesa. |

#### `superlogica_fornecedores_create`

Despesas: Cadastrar favorecido (POST /fornecedores). _(POST /api/superlogica/fornecedores/create)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas licenças Superlógica conectadas: id ou label da conexão. Veja superlogica_list_accounts. |
| `body` | string | Não | Corpo da requisição como JSON string (enviado como form-urlencoded). Datas em MM/DD/AAAA. Nomes case-sensitive. Parâmetros da doc: ID_CONDOMINIO_COND, ID_CONTATO_CON, ST_CPF_CON, ST_NOME_CON, ST_FANTASIA_CON, ST_INSCRICAOMUNICIPAL_CON, ST_RG_CON, ST_ORGAOEMISSOR_CON, ST_TELEFONE_CON, ST_FAX_CON, ST_BAIRRO_CON, ST_EMAIL_CON, ST_CEP_CON, ST_ENDERECO_CON, ST_NUMEROENDERECO_CON, ST_CIDADE_CON, ST_ESTADO_CON, ST_COMPLEMENTO_CON, ST_INSS_CON, NM_RPASEQUENCIAL_CON, ID_TIPOCONTATO_TCON, ID_FORMA_PAG, ST_AGENCIA_CON, ST_BANCO_CON, ST_CONTABANCARIA_CON, FL_TIPOCONTA_CON, ST_OPERACAO_CON, CONTATO_IMPOSTO[][ID_RV2_COD_IMP], CONTATO_IMPOSTO[][ST_RV2_NOME_IMP], CONTATO_IMPOSTO[][VALOR_ALIQUOTA], …. |
| `query` | string | Não | Query params como JSON string. Vários endpoints de escrita da Superlógica leem os campos da query em vez do corpo — a doc indica quais. |

#### `superlogica_fornecedores_list`

Despesas: Listar favorecidos (GET /fornecedores/index). _(POST /api/superlogica/fornecedores/list)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas licenças Superlógica conectadas: id ou label da conexão. Veja superlogica_list_accounts. |
| `query` | string | Não | Query params como JSON string. Datas em MM/DD/AAAA (americano). Nomes são case-sensitive. Parâmetros da doc: contatosDoTipo, itensPorPagina, pagina. |

#### `superlogica_fornecedores_update`

Despesas: Editar favorecido (PUT /fornecedores). _(POST /api/superlogica/fornecedores/update)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas licenças Superlógica conectadas: id ou label da conexão. Veja superlogica_list_accounts. |
| `body` | string | Não | Corpo da requisição como JSON string (enviado como form-urlencoded). Datas em MM/DD/AAAA. Nomes case-sensitive. Parâmetros da doc: ID_CONDOMINIO_COND, ID_CONTATO_CON, ST_CPF_CON, ST_IDENTIFICADOREXTERNO_CON, ST_NOME_CON, ST_FANTASIA_CON, ST_RG_CON, ST_ORGAOEMISSOR_CON, ST_INSCRICAOMUNICIPAL_CON, ST_INSS_CON, NM_RPASEQUENCIAL_CON, ID_TIPOCONTATO_TCON, ST_FAX_CON, ST_TELEFONE_CON, ST_EMAIL_CON, ST_CEP_CON, ST_ENDERECO_CON, ST_NUMEROENDERECO_CON, ST_COMPLEMENTO_CON, ST_BAIRRO_CON, ST_CIDADE_CON, ST_ESTADO_CON, FL_RECEBEDOR_CON, ST_CPFCNPJRECEBEDOR_CON, ST_NOMERECEBEDOR_CON, ST_BANCO_CON, ST_AGENCIA_CON, ST_CONTABANCARIA_CON, ID_FORMA_PAG, FL_TIPOCONTA_CON, …. Significado: ID_CONDOMINIO_COND: *ID do condomínio (Para conseguir esse valor use o endpoint do Condominios->Listar todos os condomínios) · ID_CONTATO_CON: *Obrigatório informar o ID_CONTATO_CON · ST_CPF_CON: CPF/CNPJ do fornecedor · ST_IDENTIFICADOREXTERNO_CON: Identificador · ST_NOME_CON: *Nome do fornecedor ou contato · ST_FANTASIA_CON: Nome fantasia · ST_RG_CON: RG · ST_ORGAOEMISSOR_CON: Orgão Emissor. |
| `query` | string | Não | Query params como JSON string. Vários endpoints de escrita da Superlógica leem os campos da query em vez do corpo — a doc indica quais. |

#### `superlogica_grupousuarios_list`

Solicitações (Tickets): Listar departamentos (GET /grupousuarios/index). _(POST /api/superlogica/grupousuarios/list)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas licenças Superlógica conectadas: id ou label da conexão. Veja superlogica_list_accounts. |
| `query` | string | Não | Query params como JSON string. Datas em MM/DD/AAAA (americano). Nomes são case-sensitive. Parâmetros da doc: ordenacao, itensPorPagina, pagina, semOutrasOpcoes, id, apenasComUsuarios, pesquisa. |

#### `superlogica_historicocobranca_create`

CRM de Cobrança: Criar agendamento (POST /historicocobranca). _(POST /api/superlogica/historicocobranca/create)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas licenças Superlógica conectadas: id ou label da conexão. Veja superlogica_list_accounts. |
| `body` | string | Não | Corpo da requisição como JSON string (enviado como form-urlencoded). Datas em MM/DD/AAAA. Nomes case-sensitive. Parâmetros da doc: ID_CONDOMINIO_COND, ID_UNIDADE_UNI, ST_URLGRAVACAO_HATE, DT_DATA_HATE, DT_HORA_HATE, FL_CANALCOMUNICACAO_HATE, ID_TIPORESULTADO_ATEND, ST_DESCRICAORESULTADO_ATEND, FL_MOTIVOINADIMPLENCIA_HATE, ST_DESCRICAO_HATE, FL_TIPOATENDIMENTO_HATE, FL_AGENDAR_CONTATO, DT_DATA_AGENDAMENTO, DT_HORA_AGENDAMENTO, RESPONSAVEL_AGENDAMENTO, ID_RESPONSAVEL_AGENDAMENTO, ST_IDENTIFICADOREXTERNO_HATE, FL_VIA_API. Significado: ID_CONDOMINIO_COND: Id condominio agendamento · ID_UNIDADE_UNI: Id unidade · ST_URLGRAVACAO_HATE: url gravação de audio · DT_DATA_HATE: Dia do agendamento · DT_HORA_HATE: Hora do agendamento · FL_CANALCOMUNICACAO_HATE: Canal de comunicação: 1 = telefone; 2 = email; 3 = sms; 4 = carta; 5 = presencial; 6 = aplicativo de mensagem; 7 = outros · ID_TIPORESULTADO_ATEND: Tipo de resultado do atendimento: 1 = Efetivo; 2 = Acordo; 3 = Pago; 4 = Promessa; 5 = Não efetivo; 6 = Não concorda; 7 = Retornar contato; 8 = Sem contato; 9 = Telefone errado; 10 = Não atende; 11 = Ocupado; 12 = Outros; · ST_DESCRICAORESULTADO_ATEND: Nome tipo atendimento. |
| `query` | string | Não | Query params como JSON string. Vários endpoints de escrita da Superlógica leem os campos da query em vez do corpo — a doc indica quais. |

#### `superlogica_historicocobranca_list`

CRM de Cobrança: Listar históricos de Cobranças (GET /historicocobranca/index). _(POST /api/superlogica/historicocobranca/list)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas licenças Superlógica conectadas: id ou label da conexão. Veja superlogica_list_accounts. |
| `query` | string | Não | Query params como JSON string. Datas em MM/DD/AAAA (americano). Nomes são case-sensitive. Parâmetros da doc: idEmpresa, dtInicio, dtFim, filtrarpor, UNIDADES[], BLOCOS[], RESPONSAVEL[]. |

#### `superlogica_historicocobranca_update`

CRM de Cobrança: Editar agendamento (PUT /historicocobranca). _(POST /api/superlogica/historicocobranca/update)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas licenças Superlógica conectadas: id ou label da conexão. Veja superlogica_list_accounts. |
| `body` | string | Não | Corpo da requisição como JSON string (enviado como form-urlencoded). Datas em MM/DD/AAAA. Nomes case-sensitive. Parâmetros da doc: ID_HISTORICO_HATE, ID_CONDOMINIO_COND, ID_UNIDADE_UNI, DT_DATA_HATE, DT_HORA_HATE, FL_CANALCOMUNICACAO_HATE, ID_TIPORESULTADO_ATEND, ST_DESCRICAORESULTADO_ATEND, FL_MOTIVOINADIMPLENCIA_HATE, ST_DESCRICAO_HATE, FL_TIPOATENDIMENTO_HATE, FL_AGENDAR_CONTATO, DT_DATA_AGENDAMENTO, DT_HORA_AGENDAMENTO, RESPONSAVEL_AGENDAMENTO, ID_RESPONSAVEL_AGENDAMENTO, ST_IDENTIFICADOREXTERNO_HATE, FL_VIA_API. Significado: ID_HISTORICO_HATE: Id condominio agendamento · ID_CONDOMINIO_COND: Id unidade · ID_UNIDADE_UNI: Dia do agendamento · DT_DATA_HATE: Hora do agendamento · DT_HORA_HATE: Canal de comunicação: 1 = telefone; 2 = email; 3 = sms; 4 = carta; 5 = presencial; 6 = aplicativo de mensagem; 7 = outros · FL_CANALCOMUNICACAO_HATE: Tipo de resultado do atendimento: 1 = Efetivo; 2 = Acordo; 3 = Pago; 4 = Promessa; 5 = Não efetivo; 6 = Não concorda; 7 = Retornar contato; 8 = Sem contato; 9 = Telefone errado; 10 = Não atende; 11 = Ocupado; 12 = Outros; · ID_TIPORESULTADO_ATEND: Nome tipo atendimento · ST_DESCRICAORESULTADO_ATEND: Motivo da inadimplencia: 1 = 'Problema financeiro'; 2 = 'Não recebeu cobrança'; 3 = 'Não concorda com cobrança'; 10 = 'Outros';. |
| `query` | string | Não | Query params como JSON string. Vários endpoints de escrita da Superlógica leem os campos da query em vez do corpo — a doc indica quais. |

#### `superlogica_impostos_list`

Despesas: Listar imposto (GET /impostos). _(POST /api/superlogica/impostos/list)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas licenças Superlógica conectadas: id ou label da conexão. Veja superlogica_list_accounts. |
| `query` | string | Não | Query params como JSON string. Datas em MM/DD/AAAA (americano). Nomes são case-sensitive. |

#### `superlogica_impressoes_list`

Documentos e Arquivos: Listar os documentos de um condomínio (GET /impressoes/index). _(POST /api/superlogica/impressoes/list)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas licenças Superlógica conectadas: id ou label da conexão. Veja superlogica_list_accounts. |
| `query` | string | Não | Query params como JSON string. Datas em MM/DD/AAAA (americano). Nomes são case-sensitive. Parâmetros da doc: idCondominio, publicadoApenasPara, dtInicio, dtFim, itensPorPagina, pagina. |

#### `superlogica_impressoes_post`

Relatórios: Fila de Impressão (GET /impressoes/post). _(POST /api/superlogica/impressoes/post)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas licenças Superlógica conectadas: id ou label da conexão. Veja superlogica_list_accounts. |
| `query` | string | Não | Query params como JSON string. Datas em MM/DD/AAAA (americano). Nomes são case-sensitive. Parâmetros da doc: FL_COMPARTILHAR, ID_IMPRESSAO_FIMP. |

#### `superlogica_inadimplencia_list`

Receitas / Acordos / Obtendo dados para gerar o acordo: Listar inadimplência de uma unidade (GET /inadimplencia). _(POST /api/superlogica/inadimplencia/list)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas licenças Superlógica conectadas: id ou label da conexão. Veja superlogica_list_accounts. |
| `query` | string | Não | Query params como JSON string. Datas em MM/DD/AAAA (americano). Nomes são case-sensitive. Parâmetros da doc: id, semProcesso, comValoresAtualizados, status, idCondominio, apenasColunasPrincipais. |

#### `superlogica_inadimplencia_list_get`

Receitas: Listar inadimplência por período (GET /inadimplencia/index). _(POST /api/superlogica/inadimplencia/list/get)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas licenças Superlógica conectadas: id ou label da conexão. Veja superlogica_list_accounts. |
| `query` | string | Não | Query params como JSON string. Datas em MM/DD/AAAA (americano). Nomes são case-sensitive. Parâmetros da doc: posicaoEm, comValoresAtualizados, comValoresAtualizadosPorComposicao, apenasResumoInad, idCondominio, comDadosDaReceita, itensPorPagina, pagina, cobrancaDoTipo, semAcordo, semProcesso, id. |

#### `superlogica_ini_config`

Condomínios: Listar o valor de uma configuração global do sistema (GET /ini/config). _(POST /api/superlogica/ini/config)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas licenças Superlógica conectadas: id ou label da conexão. Veja superlogica_list_accounts. |
| `query` | string | Não | Query params como JSON string. Datas em MM/DD/AAAA (americano). Nomes são case-sensitive. Parâmetros da doc: sessao, variavel. |

#### `superlogica_ini_postconfig`

Condomínios: Alterar valor de uma configuração global do sistema (POST /ini/postconfig). _(POST /api/superlogica/ini/postconfig)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas licenças Superlógica conectadas: id ou label da conexão. Veja superlogica_list_accounts. |
| `body` | string | Não | Corpo da requisição como JSON string (enviado como JSON). Datas em MM/DD/AAAA. Nomes case-sensitive. Parâmetros da doc: secao, variavel, valor. |
| `query` | string | Não | Query params como JSON string. Vários endpoints de escrita da Superlógica leem os campos da query em vez do corpo — a doc indica quais. |

#### `superlogica_list_accounts`

Lista as conexões (licenças) Superlógica vinculadas a este install — id, label. _(POST /api/superlogica/list/accounts)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas licenças Superlógica conectadas: id ou label da conexão. Veja superlogica_list_accounts. |

#### `superlogica_malotes_delete`

Despesas / Malotes: Excluir malote (POST /malotes/delete). _(POST /api/superlogica/malotes/delete)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas licenças Superlógica conectadas: id ou label da conexão. Veja superlogica_list_accounts. |
| `body` | string | Não | Corpo da requisição como JSON string (enviado como form-urlencoded). Datas em MM/DD/AAAA. Nomes case-sensitive. Parâmetros da doc: ID_MALOTE_MLT. Significado: ID_MALOTE_MLT: ID do malote. |
| `query` | string | Não | Query params como JSON string. Vários endpoints de escrita da Superlógica leem os campos da query em vez do corpo — a doc indica quais. |

#### `superlogica_malotes_list`

Despesas / Malotes: Listar malotes (GET /malotes/index). _(POST /api/superlogica/malotes/list)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas licenças Superlógica conectadas: id ou label da conexão. Veja superlogica_list_accounts. |
| `query` | string | Não | Query params como JSON string. Datas em MM/DD/AAAA (americano). Nomes são case-sensitive. |

#### `superlogica_malotes_post`

Despesas / Malotes: Editar malote (POST /malotes/post). _(POST /api/superlogica/malotes/post)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas licenças Superlógica conectadas: id ou label da conexão. Veja superlogica_list_accounts. |
| `body` | string | Não | Corpo da requisição como JSON string (enviado como form-urlencoded). Datas em MM/DD/AAAA. Nomes case-sensitive. Parâmetros da doc: ID_MALOTE_MLT, salvar, FL_STATUS_MLT, ST_NOME_ENTREGA_CALC, FL_AOSCUIDADOSDE_MLT, ID_RESPONSAVEL_ENTREGA_MLT, ID_CONDOMINIO_COND, NM_LACRE_IDA_MLT, NM_LACRE_VOLTA_MLT, ST_OBSERVACAO_GERACAO_MLT, SalvarDespachar, MALOTE_ITENS[0][ID_ITEM_MTI], MALOTE_ITENS[0][FL_RETORNO_MTI], MALOTE_ITENS[0][FL_TIPO_MTI], MALOTE_ITENS[0][ST_DESCRICAO_MTI]. Significado: ID_MALOTE_MLT: ID do malote · salvar: Salvar malote? 0 - Não 1 - Sim · FL_STATUS_MLT: Status do malote 0 - Não foi despachado 1 - Despachado · ST_NOME_ENTREGA_CALC: Responsável pela entrega · FL_AOSCUIDADOSDE_MLT: 0 - Síndico 1 - Porteiro 2 - Zelador 3 - Todos do Conselho 4 - Síndico e Conselho 5 - Outros · ID_RESPONSAVEL_ENTREGA_MLT: ID do responsável pela entrega (ID_USUARIO_USU) · ID_CONDOMINIO_COND: ID do condomínio · NM_LACRE_IDA_MLT: Número do lacre de ida. |
| `query` | string | Não | Query params como JSON string. Vários endpoints de escrita da Superlógica leem os campos da query em vez do corpo — a doc indica quais. |

#### `superlogica_malotes_put`

Despesas / Malotes: Cadastrar malote (POST /malotes/put). _(POST /api/superlogica/malotes/put)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas licenças Superlógica conectadas: id ou label da conexão. Veja superlogica_list_accounts. |
| `body` | string | Não | Corpo da requisição como JSON string (enviado como form-urlencoded). Datas em MM/DD/AAAA. Nomes case-sensitive. Parâmetros da doc: salvar, FL_STATUS_MLT, ST_NOME_ENTREGA_CALC, FL_AOSCUIDADOSDE_MLT, ID_RESPONSAVEL_ENTREGA_MLT, ID_CONDOMINIO_COND, NM_LACRE_IDA_MLT, NM_LACRE_VOLTA_MLT, ST_OBSERVACAO_GERACAO_MLT, SalvarDespachar, MALOTE_ITENS[0][FL_RETORNO_MTI], MALOTE_ITENS[0][FL_TIPO_MTI], MALOTE_ITENS[0][ST_DESCRICAO_MTI]. Significado: salvar: Salvar malote? 0 - Não 1 - Sim · FL_STATUS_MLT: Status do malote 0 - Não foi despachado 1 - Despachado · ST_NOME_ENTREGA_CALC: Responsável pela entrega · FL_AOSCUIDADOSDE_MLT: 0 - Síndico 1 - Porteiro 2 - Zelador 3 - Todos do Conselho 4 - Síndico e Conselho 5 - Outros · ID_RESPONSAVEL_ENTREGA_MLT: ID do responsável pela entrega (ID_USUARIO_USU) · ID_CONDOMINIO_COND: ID do condomínio · NM_LACRE_IDA_MLT: Número do lacre de ida · NM_LACRE_VOLTA_MLT: Número do lacre de volta. |
| `query` | string | Não | Query params como JSON string. Vários endpoints de escrita da Superlógica leem os campos da query em vez do corpo — a doc indica quais. |

#### `superlogica_movimentacoesdiretas_create`

Condomínios / Contas bancárias: Adicionar nova movimentação bancária (POST /MovimentacoesDiretas). _(POST /api/superlogica/movimentacoesdiretas/create)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas licenças Superlógica conectadas: id ou label da conexão. Veja superlogica_list_accounts. |
| `body` | string | Não | Corpo da requisição como JSON string (enviado como form-urlencoded). Datas em MM/DD/AAAA. Nomes case-sensitive. Parâmetros da doc: DT_ENTRADA_MD, ST_CONTA_CONT, ST_DESCRICAO_CONT, ST_COMPLEMENTO_MD, VL_VALOR_MD, ID_CONTABANCO_CB, ID_PLANOCONTAS_PLC, ID_RATEIO_RAT, MARCAR_PARA_IMPRESSAO, ID_CONDOMINIO_COND, FL_ACAO_IMPRESSAO, NM_NUMERO_CH, ST_FORNECEDOR, TX_DESCRICAO_MD, ARQUIVOS[]. Significado: DT_ENTRADA_MD: *Data de entrada · ST_CONTA_CONT: *Número da conta categoria no plano de contas. Ex: 1.5 · ST_DESCRICAO_CONT: ID no plano de contas e nome da conta categoria. Ex: 1.5 Tarifa bancária · ST_COMPLEMENTO_MD: Complemento da conta categoria (opcional) · VL_VALOR_MD: *Valor da movimentação · ID_CONTABANCO_CB: *ID da conta bancária (Para conseguir essa informação use o endPoint "Condominios->Contas Bancárias->Lista contas bancárias") · MARCAR_PARA_IMPRESSAO: Marcar para impressão · ID_CONDOMINIO_COND: *ID do condomínio (Para conseguir esse valor use o endpoint do Condominios->Listar todos os condomínios). |
| `query` | string | Não | Query params como JSON string. Vários endpoints de escrita da Superlógica leem os campos da query em vez do corpo — a doc indica quais. |

#### `superlogica_movimentacoesdiretas_estornar`

Condomínios / Contas bancárias: Estornar movimentação bancária (PUT /movimentacoesDiretas/estornar). _(POST /api/superlogica/movimentacoesdiretas/estornar)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas licenças Superlógica conectadas: id ou label da conexão. Veja superlogica_list_accounts. |
| `body` | string | Não | Corpo da requisição como JSON string (enviado como JSON). Datas em MM/DD/AAAA. Nomes case-sensitive. Parâmetros da doc: ID_CONTABANCO_MOV. |
| `query` | string | Não | Query params como JSON string. Vários endpoints de escrita da Superlógica leem os campos da query em vez do corpo — a doc indica quais. |

#### `superlogica_movimentacoesdiretas_post`

Condomínios / Contas bancárias: Editar movimentação bancária (PUT /MovimentacoesDiretas/post). _(POST /api/superlogica/movimentacoesdiretas/post)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas licenças Superlógica conectadas: id ou label da conexão. Veja superlogica_list_accounts. |
| `body` | string | Não | Corpo da requisição como JSON string (enviado como form-urlencoded). Datas em MM/DD/AAAA. Nomes case-sensitive. Parâmetros da doc: DT_ENTRADA_MD, ST_CONTA_CONT, ST_DESCRICAO_CONT, ST_COMPLEMENTO_MD, VL_VALOR_MD, ID_CONTABANCO_CB, ID_PLANOCONTAS_PLC, ID_RATEIO_RAT, MARCAR_PARA_IMPRESSAO, ID_CONDOMINIO_COND, FL_ACAO_IMPRESSAO, NM_NUMERO_CH, ST_FORNECEDOR, TX_DESCRICAO_MD, ARQUIVOS[], DT_ENTRADA_MD, ST_CONTA_CONT, ST_COMPLEMENTO_MD, VL_VALOR_MD, ID_CONTABANCO_CB, MARCAR_PARA_IMPRESSAO, ID_CONDOMINIO_COND, FL_ACAO_IMPRESSAO, NM_NUMERO_CH, ST_FORNECEDOR, TX_DESCRICAO_MD, ARQUIVOS[], ID_CONTABANCO_MOV, ID_MOVIMENTACAODIRETA_MD. Significado: DT_ENTRADA_MD: Data de entrada · ST_CONTA_CONT: ID no plano de contas. Ex: 1.5 · ST_DESCRICAO_CONT: ID no plano de contas e nome da conta categoria. Ex: 1.5 Tarifa bancária · ST_COMPLEMENTO_MD: Complemento da conta categoria (opcional) · VL_VALOR_MD: Valor da movimentação · ID_CONTABANCO_CB: ID da conta bancária · ID_CONDOMINIO_COND: ID do condomínio · TX_DESCRICAO_MD: Deixe em branco para preenchimento automático: "Conta - Categoria". |
| `query` | string | Não | Query params como JSON string. Vários endpoints de escrita da Superlógica leem os campos da query em vez do corpo — a doc indica quais. |

#### `superlogica_ocorrencias_adicionarsugestao`

Ocorrências: Criar sugestão (POST /ocorrencias/adicionarsugestao). _(POST /api/superlogica/ocorrencias/adicionarsugestao)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas licenças Superlógica conectadas: id ou label da conexão. Veja superlogica_list_accounts. |
| `body` | string | Não | Corpo da requisição como JSON string (enviado como form-urlencoded). Datas em MM/DD/AAAA. Nomes case-sensitive. Parâmetros da doc: ID_TIPO_UOS, ST_SUGESTAO_UOS, NM_CONTADOR_UOS. Significado: ID_TIPO_UOS: 1 = Outras infrações da convenção sem multa, 2 = Notificação financeira 3 = Outras infrações da convenção com multa 4 = Convivência: Infração da convenção sem multa · ST_SUGESTAO_UOS: Descrição da sugestão · NM_CONTADOR_UOS: Ordem da sugestão. |
| `query` | string | Não | Query params como JSON string. Vários endpoints de escrita da Superlógica leem os campos da query em vez do corpo — a doc indica quais. |

#### `superlogica_ocorrencias_create`

Ocorrências: Criar ocorrência (POST /ocorrencias). _(POST /api/superlogica/ocorrencias/create)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas licenças Superlógica conectadas: id ou label da conexão. Veja superlogica_list_accounts. |
| `body` | string | Não | Corpo da requisição como JSON string (enviado como form-urlencoded). Datas em MM/DD/AAAA. Nomes case-sensitive. Parâmetros da doc: ID_CONDOMINIO_COND, ID_UNIDADE_UNI, DT_OCORRENCIA_UOC, FL_TIPO_UOC, TX_OBS_UOC, FL_NOTIFICAR_UOC, ST_TITULO_UOC, NOTIFICAR_EMAIL, TX_TEXTO_UOC. Significado: ID_CONDOMINIO_COND: *Id do condominio · ID_UNIDADE_UNI: *Id da unidade (Usar o ID_UNIDADE_UNI do Unidades -> Listar Unidades) · DT_OCORRENCIA_UOC: *Data ocorrência MM/DD/YYYY · FL_TIPO_UOC: 1 = Outra sem multa, 2 = Notificação Financeira, 3 = Outra com multa, 4 = Convivência sem multa,5 = Convivencia com multa, 6= Obra sem multa, 7 = Obra com multa · TX_OBS_UOC: Motivo da ocorrência (sugestões retornadas no endpoint GET ocorrencias/sugestoes ) · FL_NOTIFICAR_UOC: 1 = Não notificar, 2 = Inquilino, 3 = Proprietário · ST_TITULO_UOC: Titulo da ocorrência · NOTIFICAR_EMAIL: 1 = notificar, 0 = não notificar. |
| `query` | string | Não | Query params como JSON string. Vários endpoints de escrita da Superlógica leem os campos da query em vez do corpo — a doc indica quais. |

#### `superlogica_ocorrencias_delete`

Ocorrências: Deletar ocorrência (POST /ocorrencias/delete). _(POST /api/superlogica/ocorrencias/delete)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas licenças Superlógica conectadas: id ou label da conexão. Veja superlogica_list_accounts. |
| `body` | string | Não | Corpo da requisição como JSON string (enviado como form-urlencoded). Datas em MM/DD/AAAA. Nomes case-sensitive. Parâmetros da doc: ID_OCORRENCIA_UOC. Significado: ID_OCORRENCIA_UOC: *Id da ocorrência (fornecido no endpoint Ocorrência -> Listar ocorrências). |
| `query` | string | Não | Query params como JSON string. Vários endpoints de escrita da Superlógica leem os campos da query em vez do corpo — a doc indica quais. |

#### `superlogica_ocorrencias_imprimircarta`

Ocorrências: Imprimir carta (POST /ocorrencias/imprimircarta). _(POST /api/superlogica/ocorrencias/imprimircarta)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas licenças Superlógica conectadas: id ou label da conexão. Veja superlogica_list_accounts. |
| `body` | string | Não | Corpo da requisição como JSON string (enviado como form-urlencoded). Datas em MM/DD/AAAA. Nomes case-sensitive. Parâmetros da doc: ID_IMPRESSORA_IMPR, ID_OCORRENCIA_UOC, ID_UNIDADE_UNI, FL_NOTIFICAR_UOC, ST_TITULO_UOC, TX_TEXTO_UOC. Significado: ID_IMPRESSORA_IMPR: Padrão pdf · ID_OCORRENCIA_UOC: *Id da ocorrência (fornecido no endpoint Ocorrência -> Listar ocorrências) · ID_UNIDADE_UNI: *ID da unidade · FL_NOTIFICAR_UOC: 1 - Não notificar | 2 - Notificar inquilino | 3 - Notificar proprietário · ST_TITULO_UOC: Título da ocorrência (sugestões retornadas no endpoint GET ocorrencias/sugestoes ) · TX_TEXTO_UOC: Texto da ocorrência. |
| `query` | string | Não | Query params como JSON string. Vários endpoints de escrita da Superlógica leem os campos da query em vez do corpo — a doc indica quais. |

#### `superlogica_ocorrencias_list`

Ocorrências: Listar ocorrências (GET /ocorrencias). _(POST /api/superlogica/ocorrencias/list)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas licenças Superlógica conectadas: id ou label da conexão. Veja superlogica_list_accounts. |
| `query` | string | Não | Query params como JSON string. Datas em MM/DD/AAAA (americano). Nomes são case-sensitive. |

#### `superlogica_ocorrencias_susgestoes`

Ocorrências: Listar sugestões (GET /ocorrencias/susgestoes). _(POST /api/superlogica/ocorrencias/susgestoes)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas licenças Superlógica conectadas: id ou label da conexão. Veja superlogica_list_accounts. |
| `query` | string | Não | Query params como JSON string. Datas em MM/DD/AAAA (americano). Nomes são case-sensitive. |

#### `superlogica_ocorrencias_update`

Ocorrências: Editar ocorrência (PUT /ocorrencias). _(POST /api/superlogica/ocorrencias/update)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas licenças Superlógica conectadas: id ou label da conexão. Veja superlogica_list_accounts. |
| `body` | string | Não | Corpo da requisição como JSON string (enviado como form-urlencoded). Datas em MM/DD/AAAA. Nomes case-sensitive. Parâmetros da doc: ID_OCORRENCIA_UOC, ID_CONDOMINIO_COND, ID_UNIDADE_UNI, DT_OCORRENCIA_UOC, FL_TIPO_UOC, TX_OBS_UOC, FL_NOTIFICAR_UOC, ST_TITULO_UOC, NOTIFICAR_EMAIL, TX_TEXTO_UOC. Significado: ID_OCORRENCIA_UOC: Id da ocorrência (usar endpoint Ocorrência -> Listar ocorrências) · ID_CONDOMINIO_COND: *Id do condominio · ID_UNIDADE_UNI: *Id da unidade (Usar o ID_UNIDADE_UNI do Unidades -> Listar Unidades) · DT_OCORRENCIA_UOC: *Data ocorrência MM/DD/YYYY · FL_TIPO_UOC: 1 = Outra sem multa, 2 = Notificação Financeira, 3 = Outra com multa, 4 = Convivência sem multa,5 = Convivencia com multa, 6= Obra sem multa, 7 = Obra com multa · TX_OBS_UOC: Motivo da ocorrência (sugestões retornadas no endpoint GET ocorrencias/sugestoes ) · FL_NOTIFICAR_UOC: 1 = Não notificar, 2 = Inquilino, 3 = Proprietário · ST_TITULO_UOC: Titulo da ocorrência. |
| `query` | string | Não | Query params como JSON string. Vários endpoints de escrita da Superlógica leem os campos da query em vez do corpo — a doc indica quais. |

#### `superlogica_planocontas_deleteconta`

Condomínios / Plano de contas: Excluindo conta num plano de contas (PUT /planocontas/deleteconta). _(POST /api/superlogica/planocontas/deleteconta)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas licenças Superlógica conectadas: id ou label da conexão. Veja superlogica_list_accounts. |
| `body` | string | Não | Corpo da requisição como JSON string (enviado como form-urlencoded). Datas em MM/DD/AAAA. Nomes case-sensitive. Parâmetros da doc: ST_CONTA_CONT, ID_PLANOCONTA_PLC. Significado: ST_CONTA_CONT: Índice da natureza da conta · ID_PLANOCONTA_PLC: ID do plano de contas. |
| `query` | string | Não | Query params como JSON string. Vários endpoints de escrita da Superlógica leem os campos da query em vez do corpo — a doc indica quais. |

#### `superlogica_planocontas_list`

Condomínios / Plano de contas: Listar IDs dos planos de contas (GET /planocontas/index). _(POST /api/superlogica/planocontas/list)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas licenças Superlógica conectadas: id ou label da conexão. Veja superlogica_list_accounts. |
| `query` | string | Não | Query params como JSON string. Datas em MM/DD/AAAA (americano). Nomes são case-sensitive. Parâmetros da doc: ID_CONDOMINIO_COND. |

#### `superlogica_planocontas_list_get`

Condomínios / Plano de contas: Listar contas de um plano de contas específico (GET /planocontas). _(POST /api/superlogica/planocontas/list/get)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas licenças Superlógica conectadas: id ou label da conexão. Veja superlogica_list_accounts. |
| `query` | string | Não | Query params como JSON string. Datas em MM/DD/AAAA (americano). Nomes são case-sensitive. Parâmetros da doc: id. |

#### `superlogica_planocontas_postconta`

Condomínios / Plano de contas: Editar conta num plano de contas (PUT /planocontas/postconta). _(POST /api/superlogica/planocontas/postconta)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas licenças Superlógica conectadas: id ou label da conexão. Veja superlogica_list_accounts. |
| `body` | string | Não | Corpo da requisição como JSON string (enviado como form-urlencoded). Datas em MM/DD/AAAA. Nomes case-sensitive. Parâmetros da doc: ST_CONTA_CONT, ST_DESCRICAO_CONT, FL_NATUREZA_CONT, CONTA_OLD, ID_PLANOCONTA_PLC. Significado: ST_CONTA_CONT: Índice da natureza da conta · ST_DESCRICAO_CONT: Descrição da nova conta · FL_NATUREZA_CONT: Natureza da conta · CONTA_OLD: ST_CONTA_CONT anterior (Somente use caso esteja alterando o índice da natureza da conta · ID_PLANOCONTA_PLC: ID do plano de contas. |
| `query` | string | Não | Query params como JSON string. Vários endpoints de escrita da Superlógica leem os campos da query em vez do corpo — a doc indica quais. |

#### `superlogica_planocontas_putconta`

Condomínios / Plano de contas: Nova conta num plano de contas (POST /planocontas/putconta). _(POST /api/superlogica/planocontas/putconta)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas licenças Superlógica conectadas: id ou label da conexão. Veja superlogica_list_accounts. |
| `body` | string | Não | Corpo da requisição como JSON string (enviado como form-urlencoded). Datas em MM/DD/AAAA. Nomes case-sensitive. Parâmetros da doc: ST_CONTA_CONT, ST_DESCRICAO_CONT, FL_NATUREZA_CONT, ID_PLANOCONTA_PLC. Significado: ST_CONTA_CONT: Índice da natureza da conta · ST_DESCRICAO_CONT: Descrição da nova conta · FL_NATUREZA_CONT: Natureza da conta · ID_PLANOCONTA_PLC: ID do plano de contas. |
| `query` | string | Não | Query params como JSON string. Vários endpoints de escrita da Superlógica leem os campos da query em vez do corpo — a doc indica quais. |

#### `superlogica_processos_alterarstatus`

Receitas / Processos Judiciais: Alterar status de um processo (PUT /processos/alterarstatus). _(POST /api/superlogica/processos/alterarstatus)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas licenças Superlógica conectadas: id ou label da conexão. Veja superlogica_list_accounts. |
| `body` | string | Não | Corpo da requisição como JSON string (enviado como form-urlencoded). Datas em MM/DD/AAAA. Nomes case-sensitive. Parâmetros da doc: NOVO_STATUS_PROCESSO, ID_PROCESSO_PROC, ID_CONDOMINIO, FL_STATUS_PROC. Significado: NOVO_STATUS_PROCESSO: Novo status do processo · ID_PROCESSO_PROC: ID do processo · ID_CONDOMINIO: ID do condomínio · FL_STATUS_PROC: Status anterior. |
| `query` | string | Não | Query params como JSON string. Vários endpoints de escrita da Superlógica leem os campos da query em vez do corpo — a doc indica quais. |

#### `superlogica_processos_create`

Receitas / Processos Judiciais: Novo processo (POST /processos). _(POST /api/superlogica/processos/create)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas licenças Superlógica conectadas: id ou label da conexão. Veja superlogica_list_accounts. |
| `body` | string | Não | Corpo da requisição como JSON string (enviado como form-urlencoded). Datas em MM/DD/AAAA. Nomes case-sensitive. Parâmetros da doc: NM_PROCESSO_PROC, ID_UNIDADE_UNI, ID_CONDOMINIO_COND, DT_ABERTURA_PROC, FL_STATUS_PROC, COBRANCAS[0][ID_CONDOMINIO_COND], COBRANCAS[0][ID_RECEBIMENTO_RECB], COBRANCAS[0][DT_VENCIMENTO_RECB], COBRANCAS[0][VL_EMITIDO_RECB]. Significado: NM_PROCESSO_PROC: Número do processo · ID_UNIDADE_UNI: ID da unidade · ID_CONDOMINIO_COND: ID do condomínio · DT_ABERTURA_PROC: Data de abertura · FL_STATUS_PROC: Fase do processo · COBRANCAS[0][ID_CONDOMINIO_COND]: ID do condomínio da cobrança · COBRANCAS[0][ID_RECEBIMENTO_RECB]: ID da cobrança · COBRANCAS[0][DT_VENCIMENTO_RECB]: Data de vencimento da cobrança. |
| `query` | string | Não | Query params como JSON string. Vários endpoints de escrita da Superlógica leem os campos da query em vez do corpo — a doc indica quais. |

#### `superlogica_processos_delete`

Receitas / Processos Judiciais: Excluir processo (PUT /processos/delete). _(POST /api/superlogica/processos/delete)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas licenças Superlógica conectadas: id ou label da conexão. Veja superlogica_list_accounts. |
| `body` | string | Não | Corpo da requisição como JSON string (enviado como form-urlencoded). Datas em MM/DD/AAAA. Nomes case-sensitive. Parâmetros da doc: ID_PROCESSO_PROC. Significado: ID_PROCESSO_PROC: ID do processo. |
| `query` | string | Não | Query params como JSON string. Vários endpoints de escrita da Superlógica leem os campos da query em vez do corpo — a doc indica quais. |

#### `superlogica_processos_list`

Receitas / Processos Judiciais: Listar processos judiciais (GET /processos). _(POST /api/superlogica/processos/list)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas licenças Superlógica conectadas: id ou label da conexão. Veja superlogica_list_accounts. |
| `query` | string | Não | Query params como JSON string. Datas em MM/DD/AAAA (americano). Nomes são case-sensitive. Parâmetros da doc: idCondominio, itensPorPagina, pagina. |

#### `superlogica_publico_downloadarquivo`

Documentos e Arquivos: Download arquivo (GET /publico/downloadarquivo). _(POST /api/superlogica/publico/downloadarquivo)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas licenças Superlógica conectadas: id ou label da conexão. Veja superlogica_list_accounts. |
| `query` | string | Não | Query params como JSON string. Datas em MM/DD/AAAA (americano). Nomes são case-sensitive. Parâmetros da doc: id, hash. |

#### `superlogica_relatorios_id_025a`

Relatórios: W025A - Previsão orçamentária mensal (GET /relatorios/id/025A). _(POST /api/superlogica/relatorios/id/025a)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas licenças Superlógica conectadas: id ou label da conexão. Veja superlogica_list_accounts. |
| `query` | string | Não | Query params como JSON string. Datas em MM/DD/AAAA (americano). Nomes são case-sensitive. Parâmetros da doc: ID_CONDOMINIO_COND, MES_INICIAL, MES_INICIAL_INICIO, COM_SALDO, COM_COMPLEMENTO, render, getId. |

#### `superlogica_relatorios_id_046a`

Relatórios: W046A - Previsão orçamentária (GET /relatorios/id/046A). _(POST /api/superlogica/relatorios/id/046a)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas licenças Superlógica conectadas: id ou label da conexão. Veja superlogica_list_accounts. |
| `query` | string | Não | Query params como JSON string. Datas em MM/DD/AAAA (americano). Nomes são case-sensitive. Parâmetros da doc: ID_CONDOMINIO_COND, MES_INICIAL, MES_INICIAL_INICIO, MAIS_COLUNAS, OUTRAS_COLUNAS, OUTRAS_COLUNAS_QDT_MESES_ACOMPARAR, OUTRAS_COLUNAS_INICIO, COM_FRACOES, FL_CONSIDERAR_FRACAO_IGUAL_CEM_POR_CENTO, COM_MEDIA, COM_FRACOES_DETALHADOS_UNIDADE, AGRUPAR_VALORES, render, getId. |

#### `superlogica_relatorios_list`

Prestação de contas: Listar relatórios (GET /relatorios). _(POST /api/superlogica/relatorios/list)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas licenças Superlógica conectadas: id ou label da conexão. Veja superlogica_list_accounts. |
| `query` | string | Não | Query params como JSON string. Datas em MM/DD/AAAA (americano). Nomes são case-sensitive. Parâmetros da doc: id, getId. |

#### `superlogica_relatoriosselecao_list`

Prestação de contas: Listar relatórios configurados nas prestações de contas (GET /relatoriosselecao/index). _(POST /api/superlogica/relatoriosselecao/list)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas licenças Superlógica conectadas: id ou label da conexão. Veja superlogica_list_accounts. |
| `query` | string | Não | Query params como JSON string. Datas em MM/DD/AAAA (americano). Nomes são case-sensitive. Parâmetros da doc: ID_EMPRESA_RLS, ID_SELECAO_RLS. |

#### `superlogica_relatoriosselecao_put_create`

Prestação de contas: Adicionar relatórios numa prestação de contas (POST /relatoriosselecao/put). _(POST /api/superlogica/relatoriosselecao/put/create)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas licenças Superlógica conectadas: id ou label da conexão. Veja superlogica_list_accounts. |
| `body` | string | Não | Corpo da requisição como JSON string (enviado como form-urlencoded). Datas em MM/DD/AAAA. Nomes case-sensitive. Parâmetros da doc: SELECAO[0][ID_SELECAO_RLS], SELECAO[0][ST_URL_RLS], SELECAO[0][ID_EMPRESA_RLS], SELECAO[0][NM_ORDENACAO_RLS], SELECAO[0][ST_TITULOTEXTO_RLS], SELECAO[0][ST_SUBTITULOTEXTO_RLS], SELECAO[0][ST_TEXTO_RLS], SELECAO[0][ID_MODELOORIGEM_RLS], ID_EMPRESA_RLS, ID_SELECAO_RLS. Significado: SELECAO[0][ID_SELECAO_RLS]: ID do tipo de prestação de contas · SELECAO[0][ST_URL_RLS]: URL do relatório · SELECAO[0][ID_EMPRESA_RLS]: ID do condomínio · SELECAO[0][NM_ORDENACAO_RLS]: Posição na ordenação da prestação · ID_EMPRESA_RLS: ID do condomínio (use o mesmo do array SELECAO) · ID_SELECAO_RLS: ID do tipo de prestação (use o memso do array SELECAO). |
| `query` | string | Não | Query params como JSON string. Vários endpoints de escrita da Superlógica leem os campos da query em vez do corpo — a doc indica quais. |

#### `superlogica_relatoriosselecao_put_update`

Prestação de contas: Excluir relatórios da prestação de contas (PUT /relatoriosselecao/put). _(POST /api/superlogica/relatoriosselecao/put/update)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas licenças Superlógica conectadas: id ou label da conexão. Veja superlogica_list_accounts. |
| `body` | string | Não | Corpo da requisição como JSON string (enviado como JSON). Datas em MM/DD/AAAA. Nomes case-sensitive. Parâmetros da doc: ID_EMPRESA_RLS, ID_SELECAO_RLS. |
| `query` | string | Não | Query params como JSON string. Vários endpoints de escrita da Superlógica leem os campos da query em vez do corpo — a doc indica quais. |

#### `superlogica_reservas_areas`

Reservas: Listar áreas comuns (GET /reservas/areas). _(POST /api/superlogica/reservas/areas)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas licenças Superlógica conectadas: id ou label da conexão. Veja superlogica_list_accounts. |
| `query` | string | Não | Query params como JSON string. Datas em MM/DD/AAAA (americano). Nomes são case-sensitive. Parâmetros da doc: idCondominio. |

#### `superlogica_reservas_areasreservas`

Reservas: Listar reservas das áreas comuns (GET /reservas/areasreservas). _(POST /api/superlogica/reservas/areasreservas)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas licenças Superlógica conectadas: id ou label da conexão. Veja superlogica_list_accounts. |
| `query` | string | Não | Query params como JSON string. Datas em MM/DD/AAAA (americano). Nomes são case-sensitive. Parâmetros da doc: idCondominio, idArea, status. |

#### `superlogica_reservas_cancelar`

Reservas: Cancelar reserva (PUT /reservas/cancelar). _(POST /api/superlogica/reservas/cancelar)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas licenças Superlógica conectadas: id ou label da conexão. Veja superlogica_list_accounts. |
| `body` | string | Não | Corpo da requisição como JSON string (enviado como form-urlencoded). Datas em MM/DD/AAAA. Nomes case-sensitive. Parâmetros da doc: ID_AREA_ARE, ID_RESERVA_RES, ID_CONDOMINIO_COND, ST_MOTIVOCANCELAMENTO_RES, FL_NAO_NOTIFICAR_CONDOMINO. Significado: ID_AREA_ARE: ID da área · ID_RESERVA_RES: ID da reserva · ID_CONDOMINIO_COND: ID do condomínio · ST_MOTIVOCANCELAMENTO_RES: (Obrigatório) Mensagem com o motivo do cancelamento · FL_NAO_NOTIFICAR_CONDOMINO: 1 para não notificar o condômino sobre o cancelamento. |
| `query` | string | Não | Query params como JSON string. Vários endpoints de escrita da Superlógica leem os campos da query em vez do corpo — a doc indica quais. |

#### `superlogica_reservas_create`

Reservas: Reservar para uma unidade (POST /reservas). _(POST /api/superlogica/reservas/create)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas licenças Superlógica conectadas: id ou label da conexão. Veja superlogica_list_accounts. |
| `body` | string | Não | Corpo da requisição como JSON string (enviado como form-urlencoded). Datas em MM/DD/AAAA. Nomes case-sensitive. Parâmetros da doc: ID_CONDOMINIO_COND, ID_UNIDADE_UNI, ID_AREA_ARE, DT_RESERVA_RES, FL_NAO_NOTIFICAR_CONDOMINO, FL_RESERVA_JA_CONFIRMADA, VL_ADMVALORRESERVA_RES. Significado: ID_CONDOMINIO_COND: ID do condomínio · ID_UNIDADE_UNI: ID da unidade · ID_AREA_ARE: ID da área · DT_RESERVA_RES: Data da reserva · FL_NAO_NOTIFICAR_CONDOMINO: 1 para não notificar condômino sobre a reserva · FL_RESERVA_JA_CONFIRMADA: 1 para marcar reserva como já confirmada · VL_ADMVALORRESERVA_RES: Valor a ser cobrado pela administradora pela reserva. Por padrão, utiliza o valor registrado na área.. |
| `query` | string | Não | Query params como JSON string. Vários endpoints de escrita da Superlógica leem os campos da query em vez do corpo — a doc indica quais. |

#### `superlogica_reservas_reserva`

Reservas: Confirmar reserva (PUT /reservas/reserva). _(POST /api/superlogica/reservas/reserva)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas licenças Superlógica conectadas: id ou label da conexão. Veja superlogica_list_accounts. |
| `body` | string | Não | Corpo da requisição como JSON string (enviado como form-urlencoded). Datas em MM/DD/AAAA. Nomes case-sensitive. Parâmetros da doc: ID_RESERVA_RES, FL_STATUS_RES, ID_CONDOMINIO_COND. Significado: ID_RESERVA_RES: ID da reserva · FL_STATUS_RES: 1 para confirmar a reserva · ID_CONDOMINIO_COND: ID do condomínio. |
| `query` | string | Não | Query params como JSON string. Vários endpoints de escrita da Superlógica leem os campos da query em vez do corpo — a doc indica quais. |

#### `superlogica_responsaveis_list`

Solicitações (Tickets): Listar condôminos (GET /responsaveis/index). _(POST /api/superlogica/responsaveis/list)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas licenças Superlógica conectadas: id ou label da conexão. Veja superlogica_list_accounts. |
| `query` | string | Não | Query params como JSON string. Datas em MM/DD/AAAA (americano). Nomes são case-sensitive. Parâmetros da doc: idCondominio, ordenacao, itensPorPagina, pagina. |

#### `superlogica_retorno_put`

Receitas / Retorno: Processar arquivo retorno (POST /retorno/put). _(POST /api/superlogica/retorno/put)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas licenças Superlógica conectadas: id ou label da conexão. Veja superlogica_list_accounts. |
| `body` | string | Não | Corpo da requisição como JSON string (enviado como form-urlencoded). Datas em MM/DD/AAAA. Nomes case-sensitive. Parâmetros da doc: ARQUIVO. |
| `query` | string | Não | Query params como JSON string. Vários endpoints de escrita da Superlógica leem os campos da query em vez do corpo — a doc indica quais. |

#### `superlogica_sindicos_cargos`

Responsáveis Legais: Listagem de cargos de Responsável Legal (GET /sindicos/cargos). _(POST /api/superlogica/sindicos/cargos)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas licenças Superlógica conectadas: id ou label da conexão. Veja superlogica_list_accounts. |
| `query` | string | Não | Query params como JSON string. Datas em MM/DD/AAAA (americano). Nomes são case-sensitive. Parâmetros da doc: itensPorPagina, pagina. |

#### `superlogica_sindicos_delete`

Responsáveis Legais: Excluir Responsável Legal (PUT /Sindicos/delete). _(POST /api/superlogica/sindicos/delete)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas licenças Superlógica conectadas: id ou label da conexão. Veja superlogica_list_accounts. |
| `body` | string | Não | Corpo da requisição como JSON string (enviado como form-urlencoded). Datas em MM/DD/AAAA. Nomes case-sensitive. Parâmetros da doc: ID_SINDICO_SIN. Significado: ID_SINDICO_SIN: ID do responsável legal. |
| `query` | string | Não | Query params como JSON string. Vários endpoints de escrita da Superlógica leem os campos da query em vez do corpo — a doc indica quais. |

#### `superlogica_sindicos_list`

Responsáveis Legais: Listar os responsáveis legais (GET /sindicos). _(POST /api/superlogica/sindicos/list)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas licenças Superlógica conectadas: id ou label da conexão. Veja superlogica_list_accounts. |
| `query` | string | Não | Query params como JSON string. Datas em MM/DD/AAAA (americano). Nomes são case-sensitive. Parâmetros da doc: idCondominio, comStatus, itensPorPagina, pagina. |

#### `superlogica_sindicos_list_get`

Solicitações (Tickets): Listar Síndico/Presidente ou Conselheiro (GET /sindicos/index). _(POST /api/superlogica/sindicos/list/get)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas licenças Superlógica conectadas: id ou label da conexão. Veja superlogica_list_accounts. |
| `query` | string | Não | Query params como JSON string. Datas em MM/DD/AAAA (americano). Nomes são case-sensitive. Parâmetros da doc: idCondominio, cargo[], excetoComCargo. |

#### `superlogica_sindicos_post`

Responsáveis Legais: Editar Responsável Legal (PUT /Sindicos/post). _(POST /api/superlogica/sindicos/post)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas licenças Superlógica conectadas: id ou label da conexão. Veja superlogica_list_accounts. |
| `body` | string | Não | Corpo da requisição como JSON string (enviado como form-urlencoded). Datas em MM/DD/AAAA. Nomes case-sensitive. Parâmetros da doc: ID_SINDICO_SIN, ST_NOME_SIN, ID_CONDOMINIO_COND, ST_CARGO_SIN, DT_ENTRADA_SIN, ST_CGC_SIN, ST_CPF_SIN, ST_TELEFONE_SIN, ST_CELULAR_SIN, ST_EMAIL_SIN, ST_CEP_SIN, ST_ENDERECO_SIN, ST_COMPLEMENTO_SIN, ST_BAIRRO_SIN, ST_CIDADE_SIN, ST_ESTADO_SIN, ST_OBSERVACAO_SIN, FL_NOTIFICARRESERVAS_SIN, DT_NASCIMENTO_SIN, DT_SAIDA_SIN. Significado: ID_SINDICO_SIN: ID do responsável legal · ST_NOME_SIN: Nome do responsável legal · ID_CONDOMINIO_COND: ID do condomínio · ST_CARGO_SIN: Cargo · DT_ENTRADA_SIN: Data de entrada · ST_CPF_SIN: CPF · ST_TELEFONE_SIN: Telefone · ST_CELULAR_SIN: Celular. |
| `query` | string | Não | Query params como JSON string. Vários endpoints de escrita da Superlógica leem os campos da query em vez do corpo — a doc indica quais. |

#### `superlogica_sindicos_put`

Responsáveis Legais: Cadastrar novo Responsável Legal (POST /Sindicos/put). _(POST /api/superlogica/sindicos/put)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas licenças Superlógica conectadas: id ou label da conexão. Veja superlogica_list_accounts. |
| `body` | string | Não | Corpo da requisição como JSON string (enviado como form-urlencoded). Datas em MM/DD/AAAA. Nomes case-sensitive. Parâmetros da doc: ST_NOME_SIN, ID_CONDOMINIO_COND, ST_CARGO_SIN, DT_ENTRADA_SIN, ST_CGC_SIN, ST_CPF_SIN, ST_TELEFONE_SIN, ST_CELULAR_SIN, ST_EMAIL_SIN, ST_CEP_SIN, ST_ENDERECO_SIN, ST_COMPLEMENTO_SIN, ST_BAIRRO_SIN, ST_CIDADE_SIN, ST_ESTADO_SIN, ST_OBSERVACAO_SIN, FL_NOTIFICARRESERVAS_SIN, DT_NASCIMENTO_SIN, DT_SAIDA_SIN. Significado: ST_NOME_SIN: Nome do responsável legal · ID_CONDOMINIO_COND: ID do condomínio · ST_CARGO_SIN: Cargo · DT_ENTRADA_SIN: Data de entrada · ST_CPF_SIN: CPF · ST_TELEFONE_SIN: Telefone · ST_CELULAR_SIN: Celular · ST_EMAIL_SIN: Email. |
| `query` | string | Não | Query params como JSON string. Vários endpoints de escrita da Superlógica leem os campos da query em vez do corpo — a doc indica quais. |

#### `superlogica_tickets_create`

Solicitações (Tickets): Nova solicitação (POST /tickets). _(POST /api/superlogica/tickets/create)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas licenças Superlógica conectadas: id ou label da conexão. Veja superlogica_list_accounts. |
| `body` | string | Não | Corpo da requisição como JSON string (enviado como form-urlencoded). Datas em MM/DD/AAAA. Nomes case-sensitive. Parâmetros da doc: FL_TIPOSOLICITANTE_TIC, ST_COPIA_TIC, ST_HISTORICO_TIH, ID_SOLICITANTE_TIC, ID_FAVORECIDO_FAV, ID_CONDOMINIO_COND, ID_RESPONSAVEL_TIC, FL_STATUS_TIC, FL_FORCAR_INTERNO_TIC, FL_INTERNO_TIC, ID_GRUPO_TIC, ID_CLIENTE_TIC. Significado: FL_TIPOSOLICITANTE_TIC: ID do tipo de solicitante · ST_COPIA_TIC: Email de cópia. Somente usado para caso o solicitante for do tipo "Outro" · ST_HISTORICO_TIH: Mensagem (texto) da solicitação · ID_SOLICITANTE_TIC: ID do solicitante. Se o tipo de solicitante for Síndico/Presidente, o ID será do Síndico/Presidente. Se o tipo de solicitante for Conselheiro, o ID será do Conselheiro. Se o tipo de solicitante for Condômino, o ID será do Condômino. Se o tipo de solicitante for Outro, não preencha este campo · ID_CONDOMINIO_COND: ID do condomínio · ID_RESPONSAVEL_TIC: ID do responsável · FL_STATUS_TIC: Status do ticket · FL_FORCAR_INTERNO_TIC: 0 - para abrir como ticket interno. 1 - para abrir como ticket visível para o cliente. |
| `query` | string | Não | Query params como JSON string. Vários endpoints de escrita da Superlógica leem os campos da query em vez do corpo — a doc indica quais. |

#### `superlogica_tickets_list`

Solicitações (Tickets): Listar solicitações (GET /tickets). _(POST /api/superlogica/tickets/list)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas licenças Superlógica conectadas: id ou label da conexão. Veja superlogica_list_accounts. |
| `query` | string | Não | Query params como JSON string. Datas em MM/DD/AAAA (americano). Nomes são case-sensitive. Parâmetros da doc: itensPorPagina, pagina, idCondominio, condominioAtual, id, status, solicitante, tipoSolicitante. |

#### `superlogica_tickets_puthistorico`

Solicitações (Tickets): Adicionar uma resposta ou anotação a um ticket (POST /tickets/puthistorico). _(POST /api/superlogica/tickets/puthistorico)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas licenças Superlógica conectadas: id ou label da conexão. Veja superlogica_list_accounts. |
| `body` | string | Não | Corpo da requisição como JSON string (enviado como form-urlencoded). Datas em MM/DD/AAAA. Nomes case-sensitive. Parâmetros da doc: ST_COPIA_TIC, ST_HISTORICO_TIH, ID_CONTATO_TIH, FL_TIPOCONTATO_TIH, FL_INTERNO_TIH, ID_TICKET_TIC, FL_RESPONDER_ENCERRAR_TIC. Significado: ST_HISTORICO_TIH: Mensagem (texto) da resposta · ID_CONTATO_TIH: ID do contato · FL_TIPOCONTATO_TIH: Flag do tipo de contato · FL_INTERNO_TIH: 1 - Flag para caso o ticket seja interno · ID_TICKET_TIC: ID da solicitação · FL_RESPONDER_ENCERRAR_TIC: 1 - Para responder o ticket marcando-o como finalizado. |
| `query` | string | Não | Query params como JSON string. Vários endpoints de escrita da Superlógica leem os campos da query em vez do corpo — a doc indica quais. |

#### `superlogica_unidades_delete`

Unidades: Excluir uma unidade (POST /unidades/delete). _(POST /api/superlogica/unidades/delete)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas licenças Superlógica conectadas: id ou label da conexão. Veja superlogica_list_accounts. |
| `body` | string | Não | Corpo da requisição como JSON string (enviado como form-urlencoded). Datas em MM/DD/AAAA. Nomes case-sensitive. Parâmetros da doc: ID_UNIDADE_UNI, ID_CONDOMINIO_COND. Significado: ID_UNIDADE_UNI: *ID da unidade(Para conseguir esse valor use o endpoint do Unidades->Listar unidades de um condomínio) · ID_CONDOMINIO_COND: *ID do condomínio (Para conseguir esse valor use o endpoint do Condominios->Listar todos os condomínios). |
| `query` | string | Não | Query params como JSON string. Vários endpoints de escrita da Superlógica leem os campos da query em vez do corpo — a doc indica quais. |

#### `superlogica_unidades_list`

Unidades: Listar unidades de um condomínio (GET /unidades/index). _(POST /api/superlogica/unidades/list)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas licenças Superlógica conectadas: id ou label da conexão. Veja superlogica_list_accounts. |
| `query` | string | Não | Query params como JSON string. Datas em MM/DD/AAAA (americano). Nomes são case-sensitive. Parâmetros da doc: idCondominio, exibirGruposDasUnidades, itensPorPagina, pagina, exibirDadosDosContatos, pesquisa. |

#### `superlogica_unidades_post_create`

Unidades: Cadastrar nova unidade (POST /unidades/post). _(POST /api/superlogica/unidades/post/create)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas licenças Superlógica conectadas: id ou label da conexão. Veja superlogica_list_accounts. |
| `body` | string | Não | Corpo da requisição como JSON string (enviado como form-urlencoded). Datas em MM/DD/AAAA. Nomes case-sensitive. Parâmetros da doc: ST_UNIDADE_UNI, ID_CONDOMINIO_COND, ST_BLOCO_UNI, ST_METRAGEM_UNI, NM_FRACAO_UNI, NM_ABATIMENTO_UNI. Significado: ST_UNIDADE_UNI: *Nome da unidade · ID_CONDOMINIO_COND: *ID do condomínio (Para conseguir esse valor use o endpoint do Condominios->Listar todos os condomínios) · ST_BLOCO_UNI: Bloco · ST_METRAGEM_UNI: Área (M²) · NM_FRACAO_UNI: Fração (%) · NM_ABATIMENTO_UNI: Abatimento (%). |
| `query` | string | Não | Query params como JSON string. Vários endpoints de escrita da Superlógica leem os campos da query em vez do corpo — a doc indica quais. |

#### `superlogica_unidades_post_update`

Unidades: Editar uma unidade (PUT /unidades/post). _(POST /api/superlogica/unidades/post/update)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas licenças Superlógica conectadas: id ou label da conexão. Veja superlogica_list_accounts. |
| `body` | string | Não | Corpo da requisição como JSON string (enviado como form-urlencoded). Datas em MM/DD/AAAA. Nomes case-sensitive. Parâmetros da doc: ID_CONDOMINIO_COND, ID_UNIDADE_UNI, ST_UNIDADE_UNI, ST_BLOCO_UNI, ST_METRAGEM_UNI, NM_ABATIMENTO_UNI, NM_VENCIMENTO_UNI, contatos[0][ID_CONTATO_CON], contatos[0][ST_NOME_CON], contatos[0][DT_ENTRADA_RES], contatos[0][ID_TIPORESP_TRES], contatos[0][ID_LABEL_TRES], contatos[0][ID_TIPOCONTATO_TCON], contatos[0][FL_ENTREGACOBRANCA_RESP], contatos[0][DT_NASCIMENTO_CON], contatos[0][ST_EMAIL_CON], contatos[0][ST_TELEFONE_CON], contatos[0][ST_BAIRRO_CON], contatos[0][ST_CEP_CON], contatos[0][ST_CIDADE_CON], contatos[0][ST_COMPLEMENTO_CON], contatos[0][ST_ENDERECO_CON], contatos[0][ST_ESTADO_CON], contatos[0][ST_FAX_CON], contatos[0][ST_CPF_CON], contatos[0][ST_CGC_CON]. Significado: ID_CONDOMINIO_COND: *ID do condomínio (Para conseguir esse valor use o endpoint do Condominios->Listar todos os condomínios) · ID_UNIDADE_UNI: *ID da unidade(Para conseguir esse valor use o endpoint do Unidades->Listar unidades de um condomínio) · ST_UNIDADE_UNI: Nome da unidade · ST_BLOCO_UNI: Bloco · ST_METRAGEM_UNI: Área (M²) · NM_ABATIMENTO_UNI: Área (M²) · NM_VENCIMENTO_UNI: Data de vencimento da unidade · contatos[0][ID_CONTATO_CON]: Caso queira utilizar o contato de outra unidade, informe o [0][ID_CONTATO_CON] (Consultar no endpoint Unidades->Listar Unidades de um condominio), se utilizar esse campo, os campos abaixo serão desconsiderados!!!. |
| `query` | string | Não | Query params como JSON string. Vários endpoints de escrita da Superlógica leem os campos da query em vez do corpo — a doc indica quais. |

#### `superlogica_usuario_list`

Solicitações (Tickets): Listar responsáveis (GET /usuario/index). _(POST /api/superlogica/usuario/list)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `account` | string | Não | Quando há múltiplas licenças Superlógica conectadas: id ou label da conexão. Veja superlogica_list_accounts. |
| `query` | string | Não | Query params como JSON string. Datas em MM/DD/AAAA (americano). Nomes são case-sensitive. Parâmetros da doc: ID_CONDOMINIO_COND. |

---

Este MCP também funciona via **conexão MCP** (Claude / Cursor) em `https://api.mcp.ai/p_superlogica` — veja o [README](../../README.md). A skill acima é pra consumir a **REST API** direto (agente próprio / código).
