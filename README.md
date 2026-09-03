# Superlógica Condomínios

### MCP para Superlógica Condomínios, a carteira inteira da administradora em linguagem natural

Converse com o **Superlógica Condomínios** da sua administradora a partir do Claude, do ChatGPT ou de qualquer cliente MCP. Roda sobre a **API oficial da Superlógica**, com o **par de tokens da sua própria licença**. A cunha é atravessar a **carteira inteira de uma vez**, que é o que hoje vira relatório exportado e colado em planilha: **inadimplência e cobrança** (boletos por período, por unidade, acordos e processos), **despesas e favorecidos**, **contas bancárias e movimentações**, **prestação de contas e balancetes**. Também escreve: cadastra cobrança e despesa, liquida, estorna, cria acordo, reserva área comum, abre ocorrência, dispara comunicado e responde solicitação. **Não afiliado à Superlógica.**

- 📉 **Inadimplência da carteira inteira** — boletos por período ou por unidade, posição de inadimplência com valores atualizados, acordos e processos judiciais, resumo da arrecadação
- 💸 **Despesas e favorecidos** — despesas por período e por conta do plano, recorrentes ainda não lançadas, cadastro de favorecido e dados de pagamento, liquidação e estorno
- 🏦 **Contas bancárias e movimentações** — saldo por conta e por data, extrato do caixa por período, lançamento direto, edição e estorno
- 📊 **Prestação de contas** — balancete de receitas e despesas por mês, relatórios da prestação, previsão orçamentária e fila de impressão
- 🏠 **O dia a dia do condomínio** — unidades e condôminos, responsáveis legais, reservas de área comum, ocorrências, comunicados, solicitações e CRM de cobrança
- 💬 **Funciona com qualquer cliente MCP**: Claude Desktop, ChatGPT, Cursor, VS Code, Cline, Continue

[English version](README.en.md) · [Documentação completa](docs/) · [Skill pra agentes](skills/)

---

## Instalar em 1 clique

### Claude (Web e Desktop)

A Anthropic unificou a instalação de MCPs em `claude.ai/customize/connectors`. **O mesmo link serve pra Claude Web e Claude Desktop** (basta estar logado):

[➕ Abrir no Claude e conectar](https://claude.ai/new?modal=add-custom-connector#settings/customize-connectors)

**Manual** (se o deeplink não abrir): [claude.ai/customize/connectors](https://claude.ai/customize/connectors?surface=cowork) → **+** → **Adicionar conector personalizado** → cole **Nome** `Superlógica Condomínios` e **URL** `https://api.mcp.ai/p_superlogica`.

### Cursor

[➕ Instalar Superlógica Condomínios no Cursor](cursor://anysphere.cursor-deeplink/mcp/install?name=superlogica&config=eyJ1cmwiOiJodHRwczovL2FwaS5tY3AuYWkvcF9zdXBlcmxvZ2ljYSJ9)

### VS Code (Copilot Chat)

[➕ Instalar Superlógica Condomínios no VS Code](vscode:mcp/install?name=superlogica&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A%2F%2Fapi.mcp.ai%2Fp_superlogica%22%7D)

### ChatGPT, Manus, OpenClaw e mais 40+ clientes

Funciona em qualquer cliente MCP que suporte **MCP over HTTP**. A URL do servidor é sempre:

```
https://api.mcp.ai/p_superlogica
```

Detalhes por cliente: [INSTALL.md](INSTALL.md).

---

## Exemplos de uso

```
Qual a inadimplência total da minha carteira hoje, por condomínio?
Liste as cobranças que vencem nos próximos 7 dias no condomínio 32
Quais despesas estão pendentes de pagamento neste mês?
Mostre o saldo de todas as contas bancárias do condomínio 2
Gere o balancete de receitas e despesas do ano passado, mês a mês
Quais unidades estão inadimplentes há mais de 90 dias?
```

---

## 114 ferramentas disponíveis

| Tool | Descrição |
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

Detalhe de cada tool: [docs/ferramentas.md](docs/ferramentas.md)


---

## O que dá para perguntar

| Área | Cobertura | Escrita |
|---|---|---|
| **Cobrança e inadimplência** | Boletos por período, por unidade e por status, posição de inadimplência com valores atualizados, resumo da arrecadação, link de 2ª via, CRM de cobrança com históricos e agendamentos | Leitura e escrita |
| **Acordos e processos** | Acordos existentes com parcelas e composições, simulação de parcelas antes de fechar, processos judiciais com alteração de status | Leitura e escrita |
| **Despesas** | Despesas por período, por conta do plano e por status, recorrentes ainda não lançadas, favorecidos e dados de pagamento, impostos, anexos, malotes e etiquetas | Leitura e escrita |
| **Contas bancárias** | Saldo por conta e por data, extrato do caixa por período, movimentações diretas com edição e estorno, plano de contas completo | Leitura e escrita |
| **Condomínios e unidades** | Carteira de condomínios, grupos, configurações globais e por condomínio, formas de pagamento, unidades com contatos, responsáveis legais e cargos | Leitura e escrita |
| **Prestação de contas** | Balancete de receitas e despesas por mês, relatórios configurados na prestação, previsão orçamentária mensal e anual, fila de impressão | Leitura e escrita |
| **Dia a dia** | Reservas de área comum, ocorrências com carta e sugestões, comunicados com disparo, solicitações (tickets) com histórico, documentos e arquivos, leitura de consumo | Leitura e escrita |

### Antes de conectar, dois avisos honestos

1. **A API existe a partir do plano Enterprise I.** O par de tokens sai dentro
   do próprio ERP, em Todos os usuários (canto superior direito), API (Integração
   com outros sistemas), Aplicativos, Novo App Token. Se esse menu não aparece
   para você, a licença da administradora está abaixo do Enterprise I. Sem o par
   de tokens não há o que conectar, com nenhuma ferramenta.
2. **O token herda as permissões do usuário que o criou.** Se você gerar o par
   com um usuário que enxerga 3 dos 40 condomínios da carteira, é isso que o MCP
   vai enxergar. Não é limitação nossa nem erro de conexão: gere com um usuário
   que alcance a carteira que você quer consultar.

### O que fica de fora, de propósito

A **Área do condômino** e a **2ª via pública por CPF** não entram. Elas moram em
endereços por licença, do tipo `sualicenca.superlogica.net`, e usam o login do
**morador**, não o par de tokens da administradora. São outro fluxo de
autenticação, então preferimos declarar do que prometer.

---

## Preços

Veja [docs/precos.md](docs/precos.md).

---

## Privacidade & LGPD

- **Sub-processadores**: Superlógica, o LLM host que você escolher (Claude, ChatGPT, Cursor, agente próprio). Lista completa em [docs/privacidade-lgpd.md](docs/privacidade-lgpd.md).
- Os dados retornados pelas tools são enviados ao **LLM host que você escolher**, sub-processador fora do nosso controle. Recomendamos planos com opt-out de treinamento.

---

## Perguntas frequentes

**É o MCP oficial da Superlógica?**
Não. Este é um MCP **independente**, que fala com a API oficial da Superlógica usando o par de tokens da sua própria licença. **Não é afiliado à Superlógica** e não implica parceria. Até onde apuramos, não existe MCP oficial nem de terceiro para a Superlógica. Superlógica é marca do seu titular, citada aqui de forma nominativa.

**Que dados vocês acessam?**
Só os que o **par de tokens da sua licença** já alcança, e dentro das permissões do usuário que gerou o token. Há escrita, e ela é explícita: cadastrar cobrança ou despesa, liquidar, estornar, criar acordo, reservar área comum, abrir ocorrência, disparar comunicado. Nada acontece sem você pedir.

**Onde ficam os meus tokens?**
Cifrados, e usados só nos cabeçalhos de autenticação das chamadas à API da Superlógica. Eles não aparecem em resposta de ferramenta nem em log.

**Não acho a opção de Aplicativos no meu Superlógica.**
O caminho é Todos os usuários (canto superior direito), API (Integração com outros sistemas), Aplicativos, Novo App Token. Ele só existe a partir do **plano Enterprise I**. Se a sua licença está abaixo disso, o caminho é falar com o time da Superlógica sobre o plano da administradora.

**Conectei, mas só aparecem alguns condomínios da minha carteira.**
O token **herda as permissões do usuário que o criou**. Se ele foi gerado por um usuário com acesso restrito, o MCP enxerga o mesmo recorte. Gere um par novo com um usuário que alcance a carteira inteira e reconecte.

**Administro mais de uma licença Superlógica. Funciona?**
Funciona. Conecte um par de tokens por licença e diga na conversa qual delas você quer. Cada conexão fica separada, e um token revogado não derruba as outras. Os condomínios de uma mesma licença já vêm todos juntos, sem precisar de conexão por condomínio.

**As datas da Superlógica são no formato americano. Isso atrapalha?**
A API usa mesmo `MM/DD/AAAA`, o que é uma pegadinha real num sistema brasileiro. O MCP conhece a regra e recusa uma data escrita em `DD/MM/AAAA` quando ela é inequívoca, dizendo qual seria a forma certa, em vez de deixar o sistema interpretar o dia como mês em silêncio.

**Dá para acessar a Área do condômino ou a 2ª via por CPF?**
Não. Esses dois moram em endereços por licença e usam o login do **morador**, não o par de tokens da administradora. É outro fluxo de autenticação e está fora deste MCP.


---

## Suporte

- 📧 [superlogica@mcp.ai](mailto:superlogica@mcp.ai)
- 🐛 [GitHub Issues](https://github.com/mcp-dir/superlogica-mcp/issues)
- 📄 [docs/](docs/)

---

## Licença

MIT — veja [LICENSE](LICENSE). O servidor MCP em `api.mcp.ai/p_superlogica` é proprietário (hosted); este repositório (manifestos, docs, skills) é MIT.
