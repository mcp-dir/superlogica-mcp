# Superlógica Condomínios

### Superlógica Condomínios MCP, your whole condo portfolio in plain language

Talk to your property manager's **Superlógica Condomínios** from Claude, ChatGPT or any MCP client. It runs on the **official Superlógica API**, with **your own license's token pair**. The wedge is crossing the **entire portfolio at once**, which today means exporting a report and pasting it into a spreadsheet: **delinquency and billing** (invoices by period and by unit, settlements and lawsuits), **expenses and payees**, **bank accounts and transactions**, **financial statements and trial balances**. It also writes: create charges and expenses, settle, reverse, open a settlement, book an amenity, file an incident, send an announcement and answer a ticket. **Not affiliated with Superlógica.**

- 📉 **Delinquency across the whole portfolio** — invoices by period or by unit, delinquency position with updated amounts, settlements and lawsuits, revenue summary
- 💸 **Expenses and payees** — expenses by period and by chart-of-accounts entry, recurring ones not yet posted, payee registration and payment details, settlement and reversal
- 🏦 **Bank accounts and transactions** — balance per account and per date, cash statement by period, direct entry, edit and reverse
- 📊 **Financial statements** — monthly income and expense trial balance, statement reports, budget forecast and the print queue
- 🏠 **The condo's day to day** — units and residents, legal representatives, amenity bookings, incidents, announcements, tickets and the collections CRM
- 💬 **Works with any MCP client**: Claude Desktop, ChatGPT, Cursor, VS Code, Cline, Continue

[Versão em português](README.md) · [Full docs (PT-BR)](docs/) · [Agent skill](skills/)

---

## One-click install

### Claude (Web and Desktop)

Anthropic unified MCP installation at `claude.ai/customize/connectors`. **The same link works for Claude Web and Claude Desktop** (just be logged in):

[➕ Open in Claude and connect](https://claude.ai/new?modal=add-custom-connector#settings/customize-connectors)

**Manual** (if the deeplink does not open): [claude.ai/customize/connectors](https://claude.ai/customize/connectors?surface=cowork) → **+** → **Add custom connector** → paste **Name** `Superlógica Condomínios` and **URL** `https://api.mcp.ai/p_superlogica`.

### Cursor

[➕ Install Superlógica Condomínios in Cursor](cursor://anysphere.cursor-deeplink/mcp/install?name=superlogica&config=eyJ1cmwiOiJodHRwczovL2FwaS5tY3AuYWkvcF9zdXBlcmxvZ2ljYSJ9)

### VS Code (Copilot Chat)

[➕ Install Superlógica Condomínios in VS Code](vscode:mcp/install?name=superlogica&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A%2F%2Fapi.mcp.ai%2Fp_superlogica%22%7D)

### ChatGPT, Manus, OpenClaw and 40+ other clients

Works with any MCP client that speaks **MCP over HTTP**. The server URL is always:

```
https://api.mcp.ai/p_superlogica
```

Per-client details: [INSTALL.md](INSTALL.md).

---

## Example prompts

```
What is the total delinquency across my portfolio today, by condo?
List the charges falling due in the next 7 days for condo 32
Which expenses are pending payment this month?
Show the balance of every bank account for condo 2
Generate last year's income and expense trial balance, month by month
Which units have been delinquent for more than 90 days?
```

---

## 114 tools available

| Tool | Description |
|---|---|
| `superlogica_list_accounts` | Lista as conexões (licenças) Superlógica vinculadas a este install — id, label. |
| `superlogica_acordos_desfazer` | Receitas / Acordos: Desfazer acordo (PUT /acordos/desfazer). |
| `superlogica_acordos_list` | Receitas / Acordos / Obtendo dados para gerar o acordo: Listar acordos existentes (GET /Acordos). |
| `superlogica_acordos_put` | Receitas / Acordos: Novo acordo (POST /acordos/put). |
| `superlogica_acordos_simularparcelas` | Receitas / Acordos / Obtendo dados para gerar o acordo: Simulando as parcelas do acordo (GET /acordos/simularparcelas). |
| `superlogica_arquivos_adicionaretiqueta` | Despesas / Etiquetas: Adicionar etiquetas (PUT /arquivos/adicionaretiqueta). |
| `superlogica_arquivos_create` | Documentos e Arquivos: Salvar novo arquivo (POST /arquivos). |
| `superlogica_arquivos_etiquetas` | Despesas / Etiquetas: Listar etiquetas (GET /arquivos/etiquetas). |
| `superlogica_arquivos_list` | Unidades: Listar arquivos (GET /arquivos/index). |
| `superlogica_arquivos_put` | Unidades: Adicionar arquivo (POST /arquivos/put). |
| `superlogica_arquivos_removeetiqueta` | Despesas / Etiquetas: Remover etiquetas (PUT /arquivos/removeetiqueta). |
| `superlogica_arrecadacoes_resumo` | Receitas: Resumo da arrecadação (GET /arrecadacoes/resumo). |
| `superlogica_balancetes_list` | Relatórios: W011A - Demonstrativo de receitas e despesas anual (GET /balancetes/index). |
| `superlogica_caixa_list` | Condomínios / Contas bancárias: Listar movimentações bancárias (GET /caixa). |
| `superlogica_caixa_saldo` | Condomínios / Contas bancárias: Obter saldo de conta bancária (GET /caixa/saldo). |
| `superlogica_cobranca_create` | Receitas: Cadastrar nova cobrança (POST /cobranca). |
| `superlogica_cobranca_desinvalidar` | Receitas: Cancelar invalidação de uma cobrança (PUT /cobranca/desinvalidar). |
| `superlogica_cobranca_estornar` | Receitas: Estornar uma cobrança (PUT /cobranca/estornar). |
| `superlogica_cobranca_excluir` | Receitas: Excluir uma cobrança (PUT /cobranca/excluir). |
| `superlogica_cobranca_gerarlinksegundavia` | 2a via: Gerar link para download de 2a via de boleto (GET /cobranca/gerarlinksegundavia). |
| `superlogica_cobranca_liquidar` | Receitas: Liquidar uma cobrança (PUT /cobranca/liquidar). |
| `superlogica_cobranca_list` | Receitas / Acordos / Obtendo dados para gerar o acordo: Listando composições do acordo (GET /cobranca/index). |
| `superlogica_cobranca_update` | Receitas: Editar uma cobrança (PUT /cobranca/update). |
| `superlogica_comunicados_create` | Comunicados: Criar novo comunicado (POST /comunicados). |
| `superlogica_comunicados_notificarcomunicado` | Comunicados: Disparar comunicados pendentes (POST /comunicados/notificarcomunicado). |
| `superlogica_condominiogrupos_list` | Condomínios: Listar grupos de condominios (GET /condominiogrupos/index). |
| `superlogica_condominios_create` | Condomínios: Cadastrar novo condomínio (POST /condominios). |
| `superlogica_condominios_get` | Condomínios: Listar todos os condomínios (GET /condominios/get). |
| `superlogica_condominios_update` | Condomínios: Editar dados condomínio (PUT /condominios). |
| `superlogica_configuracoes_create` | Condomínios: Alterar valor de uma configuração específica de um condomínio (POST /configuracoes). |
| `superlogica_configuracoes_list` | Condomínios: Listar configurações específicas de um condomínio (GET /configuracoes). |
| `superlogica_configuracoes_list_get` | Receitas: Configurações de boletos em um condomínio (GET /configuracoes/index). |
| `superlogica_consumo_list` | Consumo: Consulta de consumo (GET /consumo/index). |
| `superlogica_consumo_put_create` | Consumo: Inserir consumo (POST /consumo/put). |
| `superlogica_consumo_put_update` | Consumo: Edição de consumo (PUT /consumo/put). |
| `superlogica_contabancos_list` | Condomínios / Contas bancárias: Listar contas bancárias (GET /contabancos/index). |
| `superlogica_contatofavorecido_create` | Despesas: Cadastrar dados de pagamento favorecido (POST /contatofavorecido). |
| `superlogica_contatofavorecido_list` | Despesas: Listar dados pagamento favorecido (GET /contatofavorecido/index). |
| `superlogica_contatos_delete` | Unidades: Excluir um contato (POST /contatos/delete). |
| `superlogica_despesas_anexar` | Despesas: Anexar arquivos (POST /despesas/anexar). |
| `superlogica_despesas_create` | Despesas: Cadastrar nova despesa (POST /despesas). |
| `superlogica_despesas_delete` | Despesas: Excluir despesa (PUT /despesas/delete). |
| `superlogica_despesas_despesasrecorrente` | Despesas: Listar despesas recorrentes não lançadas (GET /despesas/despesasrecorrente). |
| `superlogica_despesas_estornar` | Despesas: Estornar despesa (PUT /despesas/estornar). |
| `superlogica_despesas_liquidar` | Despesas: Liquidar despesa (PUT /despesas/liquidar). |
| `superlogica_despesas_list` | Despesas: Listar despesas por período (GET /despesas/index). |
| `superlogica_despesas_post` | Despesas: Editar despesa (PUT /despesas/post). |
| `superlogica_documentos_create` | Documentos e Arquivos: Inserir novo documento (POST /documentos). |
| `superlogica_formasdepagamento_list` | Condomínios: Listar formas de pagamento (GET /formasdepagamento). |
| `superlogica_fornecedores_create` | Despesas: Cadastrar favorecido (POST /fornecedores). |
| `superlogica_fornecedores_list` | Despesas: Listar favorecidos (GET /fornecedores/index). |
| `superlogica_fornecedores_update` | Despesas: Editar favorecido (PUT /fornecedores). |
| `superlogica_grupousuarios_list` | Solicitações (Tickets): Listar departamentos (GET /grupousuarios/index). |
| `superlogica_historicocobranca_create` | CRM de Cobrança: Criar agendamento (POST /historicocobranca). |
| `superlogica_historicocobranca_list` | CRM de Cobrança: Listar históricos de Cobranças (GET /historicocobranca/index). |
| `superlogica_historicocobranca_update` | CRM de Cobrança: Editar agendamento (PUT /historicocobranca). |
| `superlogica_impostos_list` | Despesas: Listar imposto (GET /impostos). |
| `superlogica_impressoes_list` | Documentos e Arquivos: Listar os documentos de um condomínio (GET /impressoes/index). |
| `superlogica_impressoes_post` | Relatórios: Fila de Impressão (GET /impressoes/post). |
| `superlogica_inadimplencia_list` | Receitas / Acordos / Obtendo dados para gerar o acordo: Listar inadimplência de uma unidade (GET /inadimplencia). |
| `superlogica_inadimplencia_list_get` | Receitas: Listar inadimplência por período (GET /inadimplencia/index). |
| `superlogica_ini_config` | Condomínios: Listar o valor de uma configuração global do sistema (GET /ini/config). |
| `superlogica_ini_postconfig` | Condomínios: Alterar valor de uma configuração global do sistema (POST /ini/postconfig). |
| `superlogica_malotes_delete` | Despesas / Malotes: Excluir malote (POST /malotes/delete). |
| `superlogica_malotes_list` | Despesas / Malotes: Listar malotes (GET /malotes/index). |
| `superlogica_malotes_post` | Despesas / Malotes: Editar malote (POST /malotes/post). |
| `superlogica_malotes_put` | Despesas / Malotes: Cadastrar malote (POST /malotes/put). |
| `superlogica_movimentacoesdiretas_create` | Condomínios / Contas bancárias: Adicionar nova movimentação bancária (POST /MovimentacoesDiretas). |
| `superlogica_movimentacoesdiretas_estornar` | Condomínios / Contas bancárias: Estornar movimentação bancária (PUT /movimentacoesDiretas/estornar). |
| `superlogica_movimentacoesdiretas_post` | Condomínios / Contas bancárias: Editar movimentação bancária (PUT /MovimentacoesDiretas/post). |
| `superlogica_ocorrencias_adicionarsugestao` | Ocorrências: Criar sugestão (POST /ocorrencias/adicionarsugestao). |
| `superlogica_ocorrencias_create` | Ocorrências: Criar ocorrência (POST /ocorrencias). |
| `superlogica_ocorrencias_delete` | Ocorrências: Deletar ocorrência (POST /ocorrencias/delete). |
| `superlogica_ocorrencias_imprimircarta` | Ocorrências: Imprimir carta (POST /ocorrencias/imprimircarta). |
| `superlogica_ocorrencias_list` | Ocorrências: Listar ocorrências (GET /ocorrencias). |
| `superlogica_ocorrencias_susgestoes` | Ocorrências: Listar sugestões (GET /ocorrencias/susgestoes). |
| `superlogica_ocorrencias_update` | Ocorrências: Editar ocorrência (PUT /ocorrencias). |
| `superlogica_planocontas_deleteconta` | Condomínios / Plano de contas: Excluindo conta num plano de contas (PUT /planocontas/deleteconta). |
| `superlogica_planocontas_list` | Condomínios / Plano de contas: Listar IDs dos planos de contas (GET /planocontas/index). |
| `superlogica_planocontas_list_get` | Condomínios / Plano de contas: Listar contas de um plano de contas específico (GET /planocontas). |
| `superlogica_planocontas_postconta` | Condomínios / Plano de contas: Editar conta num plano de contas (PUT /planocontas/postconta). |
| `superlogica_planocontas_putconta` | Condomínios / Plano de contas: Nova conta num plano de contas (POST /planocontas/putconta). |
| `superlogica_processos_alterarstatus` | Receitas / Processos Judiciais: Alterar status de um processo (PUT /processos/alterarstatus). |
| `superlogica_processos_create` | Receitas / Processos Judiciais: Novo processo (POST /processos). |
| `superlogica_processos_delete` | Receitas / Processos Judiciais: Excluir processo (PUT /processos/delete). |
| `superlogica_processos_list` | Receitas / Processos Judiciais: Listar processos judiciais (GET /processos). |
| `superlogica_publico_downloadarquivo` | Documentos e Arquivos: Download arquivo (GET /publico/downloadarquivo). |
| `superlogica_relatorios_id_025a` | Relatórios: W025A - Previsão orçamentária mensal (GET /relatorios/id/025A). |
| `superlogica_relatorios_id_046a` | Relatórios: W046A - Previsão orçamentária (GET /relatorios/id/046A). |
| `superlogica_relatorios_list` | Prestação de contas: Listar relatórios (GET /relatorios). |
| `superlogica_relatoriosselecao_list` | Prestação de contas: Listar relatórios configurados nas prestações de contas (GET /relatoriosselecao/index). |
| `superlogica_relatoriosselecao_put_create` | Prestação de contas: Adicionar relatórios numa prestação de contas (POST /relatoriosselecao/put). |
| `superlogica_relatoriosselecao_put_update` | Prestação de contas: Excluir relatórios da prestação de contas (PUT /relatoriosselecao/put). |
| `superlogica_reservas_areas` | Reservas: Listar áreas comuns (GET /reservas/areas). |
| `superlogica_reservas_areasreservas` | Reservas: Listar reservas das áreas comuns (GET /reservas/areasreservas). |
| `superlogica_reservas_cancelar` | Reservas: Cancelar reserva (PUT /reservas/cancelar). |
| `superlogica_reservas_create` | Reservas: Reservar para uma unidade (POST /reservas). |
| `superlogica_reservas_reserva` | Reservas: Confirmar reserva (PUT /reservas/reserva). |
| `superlogica_responsaveis_list` | Solicitações (Tickets): Listar condôminos (GET /responsaveis/index). |
| `superlogica_retorno_put` | Receitas / Retorno: Processar arquivo retorno (POST /retorno/put). |
| `superlogica_sindicos_cargos` | Responsáveis Legais: Listagem de cargos de Responsável Legal (GET /sindicos/cargos). |
| `superlogica_sindicos_delete` | Responsáveis Legais: Excluir Responsável Legal (PUT /Sindicos/delete). |
| `superlogica_sindicos_list` | Responsáveis Legais: Listar os responsáveis legais (GET /sindicos). |
| `superlogica_sindicos_list_get` | Solicitações (Tickets): Listar Síndico/Presidente ou Conselheiro (GET /sindicos/index). |
| `superlogica_sindicos_post` | Responsáveis Legais: Editar Responsável Legal (PUT /Sindicos/post). |
| `superlogica_sindicos_put` | Responsáveis Legais: Cadastrar novo Responsável Legal (POST /Sindicos/put). |
| `superlogica_tickets_create` | Solicitações (Tickets): Nova solicitação (POST /tickets). |
| `superlogica_tickets_list` | Solicitações (Tickets): Listar solicitações (GET /tickets). |
| `superlogica_tickets_puthistorico` | Solicitações (Tickets): Adicionar uma resposta ou anotação a um ticket (POST /tickets/puthistorico). |
| `superlogica_unidades_delete` | Unidades: Excluir uma unidade (POST /unidades/delete). |
| `superlogica_unidades_list` | Unidades: Listar unidades de um condomínio (GET /unidades/index). |
| `superlogica_unidades_post_create` | Unidades: Cadastrar nova unidade (POST /unidades/post). |
| `superlogica_unidades_post_update` | Unidades: Editar uma unidade (PUT /unidades/post). |
| `superlogica_usuario_list` | Solicitações (Tickets): Listar responsáveis (GET /usuario/index). |

Details for each tool: [docs/ferramentas.md](docs/ferramentas.md) (PT-BR)


---

## What you can ask

| Area | Coverage | Writes |
|---|---|---|
| **Billing and delinquency** | Invoices by period, by unit and by status, delinquency position with updated amounts, revenue summary, second-copy link, collections CRM with history and scheduling | Read and write |
| **Settlements and lawsuits** | Existing settlements with installments and composition, installment simulation before closing, lawsuits with status changes | Read and write |
| **Expenses** | Expenses by period, by chart-of-accounts entry and by status, recurring ones not yet posted, payees and payment details, taxes, attachments, pouches and labels | Read and write |
| **Bank accounts** | Balance per account and per date, cash statement by period, direct transactions with edit and reversal, full chart of accounts | Read and write |
| **Condos and units** | Condo portfolio, groups, global and per-condo settings, payment methods, units with contacts, legal representatives and roles | Read and write |
| **Financial statements** | Monthly income and expense trial balance, reports configured in the statement, monthly and yearly budget forecast, print queue | Read and write |
| **Day to day** | Amenity bookings, incidents with letters and suggestions, announcements with dispatch, tickets with history, documents and files, meter readings | Read and write |

### Before connecting, two honest notes

1. **The API is available from the Enterprise I plan up.** The token pair is
   generated inside the ERP itself, under All users (top right), API (Integration
   with other systems), Applications, New App Token. If that menu does not show
   up for you, the license is below Enterprise I. Without the token pair there is
   nothing to connect, with any tool.
2. **The token inherits the permissions of the user who created it.** If you
   generate the pair with a user who sees 3 of the 40 condos in the portfolio,
   that is what this MCP will see. It is not our limitation nor a connection
   error: generate it with a user who reaches the portfolio you want to query.

### What is deliberately out of scope

The **resident portal** and the **public second-copy by CPF** are not included.
They live on per-license hosts like `yourlicense.superlogica.net` and use the
**resident's** login, not the property manager's token pair. That is a different
authentication flow, so we would rather declare it than promise it.

---

## Pricing

See [docs/precos.md](docs/precos.md) (PT-BR).

---

## Privacy & data protection

- **Sub-processors**: Superlógica, the LLM host you choose (Claude, ChatGPT, Cursor, your own agent). Full list in [docs/privacidade-lgpd.md](docs/privacidade-lgpd.md).
- Data returned by the tools is sent to **the LLM host you choose**, a sub-processor outside our control. We recommend plans with training opt-out.

---

## FAQ

**Is this the official Superlógica MCP?**
No. This is an **independent** MCP that talks to the official Superlógica API using your own license's token pair. It is **not affiliated with Superlógica** and implies no partnership. As far as we could establish, no official or third-party MCP for Superlógica exists. Superlógica is a trademark of its owner, referenced here nominatively.

**What data do you access?**
Only what **your license's token pair** already reaches, and within the permissions of the user who generated the token. Writes exist and they are explicit: create a charge or an expense, settle, reverse, open a settlement, book an amenity, file an incident, send an announcement. Nothing happens unless you ask.

**Where do my tokens live?**
Encrypted, and used only in the authentication headers of calls to the Superlógica API. They never show up in a tool response or in logs.

**I cannot find the Applications option in my Superlógica.**
The path is All users (top right), API (Integration with other systems), Applications, New App Token. It only exists from the **Enterprise I plan** up. If your license is below that, the next step is asking the Superlógica team about your plan.

**I connected, but only some condos in my portfolio show up.**
The token **inherits the permissions of the user who created it**. If it was generated by a user with restricted access, this MCP sees the same slice. Generate a new pair with a user who reaches the whole portfolio and reconnect.

**I manage more than one Superlógica license. Does it work?**
Yes. Connect one token pair per license and say which one you mean in the conversation. Each connection stays separate, and a revoked token does not take the others down. All condos in the same license already come together, with no need for a connection per condo.

**Superlógica dates are in the US format. Is that a problem?**
The API really does use `MM/DD/YYYY`, which is a genuine trap in a Brazilian system. This MCP knows the rule and refuses a date written as `DD/MM/YYYY` when it is unambiguous, telling you the correct form, instead of letting the system silently read the day as the month.

**Can I reach the resident portal or the public second-copy by CPF?**
No. Those two live on per-license hosts and use the **resident's** login, not the property manager's token pair. That is a different authentication flow and is out of scope for this MCP.


---

## Support

- 📧 [superlogica@mcp.ai](mailto:superlogica@mcp.ai)
- 🐛 [GitHub Issues](https://github.com/mcp-dir/superlogica-mcp/issues)
- 📄 [docs/](docs/)

---

## License

MIT — see [LICENSE](LICENSE). The MCP server at `api.mcp.ai/p_superlogica` is proprietary (hosted); this repo (manifests, docs, skills) is MIT.
