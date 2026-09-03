# Ferramentas

Superlógica Condomínios expõe 114 ferramentas.

### 1. `superlogica_list_accounts`
**Input**: `account` (opcional)

Lista as conexões (licenças) Superlógica vinculadas a este install — id, label.

### 2. `superlogica_acordos_desfazer`
**Input**: `account` (opcional), `body` (opcional), `query` (opcional)

Receitas / Acordos: Desfazer acordo (PUT /acordos/desfazer).

### 3. `superlogica_acordos_list`
**Input**: `account` (opcional), `query` (opcional)

Receitas / Acordos / Obtendo dados para gerar o acordo: Listar acordos existentes (GET /Acordos).

### 4. `superlogica_acordos_put`
**Input**: `account` (opcional), `body` (opcional), `query` (opcional)

Receitas / Acordos: Novo acordo (POST /acordos/put).

### 5. `superlogica_acordos_simularparcelas`
**Input**: `account` (opcional), `query` (opcional)

Receitas / Acordos / Obtendo dados para gerar o acordo: Simulando as parcelas do acordo (GET /acordos/simularparcelas).

### 6. `superlogica_arquivos_adicionaretiqueta`
**Input**: `account` (opcional), `body` (opcional), `query` (opcional)

Despesas / Etiquetas: Adicionar etiquetas (PUT /arquivos/adicionaretiqueta).

### 7. `superlogica_arquivos_create`
**Input**: `account` (opcional), `body` (opcional), `query` (opcional)

Documentos e Arquivos: Salvar novo arquivo (POST /arquivos).

### 8. `superlogica_arquivos_etiquetas`
**Input**: `account` (opcional), `query` (opcional)

Despesas / Etiquetas: Listar etiquetas (GET /arquivos/etiquetas).

### 9. `superlogica_arquivos_list`
**Input**: `account` (opcional), `query` (opcional)

Unidades: Listar arquivos (GET /arquivos/index).

### 10. `superlogica_arquivos_put`
**Input**: `account` (opcional), `body` (opcional), `query` (opcional)

Unidades: Adicionar arquivo (POST /arquivos/put).

### 11. `superlogica_arquivos_removeetiqueta`
**Input**: `account` (opcional), `body` (opcional), `query` (opcional)

Despesas / Etiquetas: Remover etiquetas (PUT /arquivos/removeetiqueta).

### 12. `superlogica_arrecadacoes_resumo`
**Input**: `account` (opcional), `query` (opcional)

Receitas: Resumo da arrecadação (GET /arrecadacoes/resumo).

### 13. `superlogica_balancetes_list`
**Input**: `account` (opcional), `query` (opcional)

Relatórios: W011A - Demonstrativo de receitas e despesas anual (GET /balancetes/index).

### 14. `superlogica_caixa_list`
**Input**: `account` (opcional), `query` (opcional)

Condomínios / Contas bancárias: Listar movimentações bancárias (GET /caixa).

### 15. `superlogica_caixa_saldo`
**Input**: `account` (opcional), `query` (opcional)

Condomínios / Contas bancárias: Obter saldo de conta bancária (GET /caixa/saldo).

### 16. `superlogica_cobranca_create`
**Input**: `account` (opcional), `body` (opcional), `query` (opcional)

Receitas: Cadastrar nova cobrança (POST /cobranca).

### 17. `superlogica_cobranca_desinvalidar`
**Input**: `account` (opcional), `body` (opcional), `query` (opcional)

Receitas: Cancelar invalidação de uma cobrança (PUT /cobranca/desinvalidar).

### 18. `superlogica_cobranca_estornar`
**Input**: `account` (opcional), `body` (opcional), `query` (opcional)

Receitas: Estornar uma cobrança (PUT /cobranca/estornar).

### 19. `superlogica_cobranca_excluir`
**Input**: `account` (opcional), `body` (opcional), `query` (opcional)

Receitas: Excluir uma cobrança (PUT /cobranca/excluir).

### 20. `superlogica_cobranca_gerarlinksegundavia`
**Input**: `account` (opcional), `query` (opcional)

2a via: Gerar link para download de 2a via de boleto (GET /cobranca/gerarlinksegundavia).

### 21. `superlogica_cobranca_liquidar`
**Input**: `account` (opcional), `body` (opcional), `query` (opcional)

Receitas: Liquidar uma cobrança (PUT /cobranca/liquidar).

### 22. `superlogica_cobranca_list`
**Input**: `account` (opcional), `query` (opcional)

Receitas / Acordos / Obtendo dados para gerar o acordo: Listando composições do acordo (GET /cobranca/index).

### 23. `superlogica_cobranca_update`
**Input**: `account` (opcional), `body` (opcional), `query` (opcional)

Receitas: Editar uma cobrança (PUT /cobranca/update).

### 24. `superlogica_comunicados_create`
**Input**: `account` (opcional), `body` (opcional), `query` (opcional)

Comunicados: Criar novo comunicado (POST /comunicados).

### 25. `superlogica_comunicados_notificarcomunicado`
**Input**: `account` (opcional), `body` (opcional), `query` (opcional)

Comunicados: Disparar comunicados pendentes (POST /comunicados/notificarcomunicado).

### 26. `superlogica_condominiogrupos_list`
**Input**: `account` (opcional), `query` (opcional)

Condomínios: Listar grupos de condominios (GET /condominiogrupos/index).

### 27. `superlogica_condominios_create`
**Input**: `account` (opcional), `body` (opcional), `query` (opcional)

Condomínios: Cadastrar novo condomínio (POST /condominios).

### 28. `superlogica_condominios_get`
**Input**: `account` (opcional), `query` (opcional)

Condomínios: Listar todos os condomínios (GET /condominios/get).

### 29. `superlogica_condominios_update`
**Input**: `account` (opcional), `body` (opcional), `query` (opcional)

Condomínios: Editar dados condomínio (PUT /condominios).

### 30. `superlogica_configuracoes_create`
**Input**: `account` (opcional), `body` (opcional), `query` (opcional)

Condomínios: Alterar valor de uma configuração específica de um condomínio (POST /configuracoes).

### 31. `superlogica_configuracoes_list`
**Input**: `account` (opcional), `query` (opcional)

Condomínios: Listar configurações específicas de um condomínio (GET /configuracoes).

### 32. `superlogica_configuracoes_list_get`
**Input**: `account` (opcional), `query` (opcional)

Receitas: Configurações de boletos em um condomínio (GET /configuracoes/index).

### 33. `superlogica_consumo_list`
**Input**: `account` (opcional), `query` (opcional)

Consumo: Consulta de consumo (GET /consumo/index).

### 34. `superlogica_consumo_put_create`
**Input**: `account` (opcional), `body` (opcional), `query` (opcional)

Consumo: Inserir consumo (POST /consumo/put).

### 35. `superlogica_consumo_put_update`
**Input**: `account` (opcional), `body` (opcional), `query` (opcional)

Consumo: Edição de consumo (PUT /consumo/put).

### 36. `superlogica_contabancos_list`
**Input**: `account` (opcional), `query` (opcional)

Condomínios / Contas bancárias: Listar contas bancárias (GET /contabancos/index).

### 37. `superlogica_contatofavorecido_create`
**Input**: `account` (opcional), `body` (opcional), `query` (opcional)

Despesas: Cadastrar dados de pagamento favorecido (POST /contatofavorecido).

### 38. `superlogica_contatofavorecido_list`
**Input**: `account` (opcional), `query` (opcional)

Despesas: Listar dados pagamento favorecido (GET /contatofavorecido/index).

### 39. `superlogica_contatos_delete`
**Input**: `account` (opcional), `body` (opcional), `query` (opcional)

Unidades: Excluir um contato (POST /contatos/delete).

### 40. `superlogica_despesas_anexar`
**Input**: `account` (opcional), `body` (opcional), `query` (opcional)

Despesas: Anexar arquivos (POST /despesas/anexar).

### 41. `superlogica_despesas_create`
**Input**: `account` (opcional), `body` (opcional), `query` (opcional)

Despesas: Cadastrar nova despesa (POST /despesas).

### 42. `superlogica_despesas_delete`
**Input**: `account` (opcional), `body` (opcional), `query` (opcional)

Despesas: Excluir despesa (PUT /despesas/delete).

### 43. `superlogica_despesas_despesasrecorrente`
**Input**: `account` (opcional), `query` (opcional)

Despesas: Listar despesas recorrentes não lançadas (GET /despesas/despesasrecorrente).

### 44. `superlogica_despesas_estornar`
**Input**: `account` (opcional), `body` (opcional), `query` (opcional)

Despesas: Estornar despesa (PUT /despesas/estornar).

### 45. `superlogica_despesas_liquidar`
**Input**: `account` (opcional), `body` (opcional), `query` (opcional)

Despesas: Liquidar despesa (PUT /despesas/liquidar).

### 46. `superlogica_despesas_list`
**Input**: `account` (opcional), `query` (opcional)

Despesas: Listar despesas por período (GET /despesas/index).

### 47. `superlogica_despesas_post`
**Input**: `account` (opcional), `body` (opcional), `query` (opcional)

Despesas: Editar despesa (PUT /despesas/post).

### 48. `superlogica_documentos_create`
**Input**: `account` (opcional), `body` (opcional), `query` (opcional)

Documentos e Arquivos: Inserir novo documento (POST /documentos).

### 49. `superlogica_formasdepagamento_list`
**Input**: `account` (opcional), `query` (opcional)

Condomínios: Listar formas de pagamento (GET /formasdepagamento).

### 50. `superlogica_fornecedores_create`
**Input**: `account` (opcional), `body` (opcional), `query` (opcional)

Despesas: Cadastrar favorecido (POST /fornecedores).

### 51. `superlogica_fornecedores_list`
**Input**: `account` (opcional), `query` (opcional)

Despesas: Listar favorecidos (GET /fornecedores/index).

### 52. `superlogica_fornecedores_update`
**Input**: `account` (opcional), `body` (opcional), `query` (opcional)

Despesas: Editar favorecido (PUT /fornecedores).

### 53. `superlogica_grupousuarios_list`
**Input**: `account` (opcional), `query` (opcional)

Solicitações (Tickets): Listar departamentos (GET /grupousuarios/index).

### 54. `superlogica_historicocobranca_create`
**Input**: `account` (opcional), `body` (opcional), `query` (opcional)

CRM de Cobrança: Criar agendamento (POST /historicocobranca).

### 55. `superlogica_historicocobranca_list`
**Input**: `account` (opcional), `query` (opcional)

CRM de Cobrança: Listar históricos de Cobranças (GET /historicocobranca/index).

### 56. `superlogica_historicocobranca_update`
**Input**: `account` (opcional), `body` (opcional), `query` (opcional)

CRM de Cobrança: Editar agendamento (PUT /historicocobranca).

### 57. `superlogica_impostos_list`
**Input**: `account` (opcional), `query` (opcional)

Despesas: Listar imposto (GET /impostos).

### 58. `superlogica_impressoes_list`
**Input**: `account` (opcional), `query` (opcional)

Documentos e Arquivos: Listar os documentos de um condomínio (GET /impressoes/index).

### 59. `superlogica_impressoes_post`
**Input**: `account` (opcional), `query` (opcional)

Relatórios: Fila de Impressão (GET /impressoes/post).

### 60. `superlogica_inadimplencia_list`
**Input**: `account` (opcional), `query` (opcional)

Receitas / Acordos / Obtendo dados para gerar o acordo: Listar inadimplência de uma unidade (GET /inadimplencia).

### 61. `superlogica_inadimplencia_list_get`
**Input**: `account` (opcional), `query` (opcional)

Receitas: Listar inadimplência por período (GET /inadimplencia/index).

### 62. `superlogica_ini_config`
**Input**: `account` (opcional), `query` (opcional)

Condomínios: Listar o valor de uma configuração global do sistema (GET /ini/config).

### 63. `superlogica_ini_postconfig`
**Input**: `account` (opcional), `body` (opcional), `query` (opcional)

Condomínios: Alterar valor de uma configuração global do sistema (POST /ini/postconfig).

### 64. `superlogica_malotes_delete`
**Input**: `account` (opcional), `body` (opcional), `query` (opcional)

Despesas / Malotes: Excluir malote (POST /malotes/delete).

### 65. `superlogica_malotes_list`
**Input**: `account` (opcional), `query` (opcional)

Despesas / Malotes: Listar malotes (GET /malotes/index).

### 66. `superlogica_malotes_post`
**Input**: `account` (opcional), `body` (opcional), `query` (opcional)

Despesas / Malotes: Editar malote (POST /malotes/post).

### 67. `superlogica_malotes_put`
**Input**: `account` (opcional), `body` (opcional), `query` (opcional)

Despesas / Malotes: Cadastrar malote (POST /malotes/put).

### 68. `superlogica_movimentacoesdiretas_create`
**Input**: `account` (opcional), `body` (opcional), `query` (opcional)

Condomínios / Contas bancárias: Adicionar nova movimentação bancária (POST /MovimentacoesDiretas).

### 69. `superlogica_movimentacoesdiretas_estornar`
**Input**: `account` (opcional), `body` (opcional), `query` (opcional)

Condomínios / Contas bancárias: Estornar movimentação bancária (PUT /movimentacoesDiretas/estornar).

### 70. `superlogica_movimentacoesdiretas_post`
**Input**: `account` (opcional), `body` (opcional), `query` (opcional)

Condomínios / Contas bancárias: Editar movimentação bancária (PUT /MovimentacoesDiretas/post).

### 71. `superlogica_ocorrencias_adicionarsugestao`
**Input**: `account` (opcional), `body` (opcional), `query` (opcional)

Ocorrências: Criar sugestão (POST /ocorrencias/adicionarsugestao).

### 72. `superlogica_ocorrencias_create`
**Input**: `account` (opcional), `body` (opcional), `query` (opcional)

Ocorrências: Criar ocorrência (POST /ocorrencias).

### 73. `superlogica_ocorrencias_delete`
**Input**: `account` (opcional), `body` (opcional), `query` (opcional)

Ocorrências: Deletar ocorrência (POST /ocorrencias/delete).

### 74. `superlogica_ocorrencias_imprimircarta`
**Input**: `account` (opcional), `body` (opcional), `query` (opcional)

Ocorrências: Imprimir carta (POST /ocorrencias/imprimircarta).

### 75. `superlogica_ocorrencias_list`
**Input**: `account` (opcional), `query` (opcional)

Ocorrências: Listar ocorrências (GET /ocorrencias).

### 76. `superlogica_ocorrencias_susgestoes`
**Input**: `account` (opcional), `query` (opcional)

Ocorrências: Listar sugestões (GET /ocorrencias/susgestoes).

### 77. `superlogica_ocorrencias_update`
**Input**: `account` (opcional), `body` (opcional), `query` (opcional)

Ocorrências: Editar ocorrência (PUT /ocorrencias).

### 78. `superlogica_planocontas_deleteconta`
**Input**: `account` (opcional), `body` (opcional), `query` (opcional)

Condomínios / Plano de contas: Excluindo conta num plano de contas (PUT /planocontas/deleteconta).

### 79. `superlogica_planocontas_list`
**Input**: `account` (opcional), `query` (opcional)

Condomínios / Plano de contas: Listar IDs dos planos de contas (GET /planocontas/index).

### 80. `superlogica_planocontas_list_get`
**Input**: `account` (opcional), `query` (opcional)

Condomínios / Plano de contas: Listar contas de um plano de contas específico (GET /planocontas).

### 81. `superlogica_planocontas_postconta`
**Input**: `account` (opcional), `body` (opcional), `query` (opcional)

Condomínios / Plano de contas: Editar conta num plano de contas (PUT /planocontas/postconta).

### 82. `superlogica_planocontas_putconta`
**Input**: `account` (opcional), `body` (opcional), `query` (opcional)

Condomínios / Plano de contas: Nova conta num plano de contas (POST /planocontas/putconta).

### 83. `superlogica_processos_alterarstatus`
**Input**: `account` (opcional), `body` (opcional), `query` (opcional)

Receitas / Processos Judiciais: Alterar status de um processo (PUT /processos/alterarstatus).

### 84. `superlogica_processos_create`
**Input**: `account` (opcional), `body` (opcional), `query` (opcional)

Receitas / Processos Judiciais: Novo processo (POST /processos).

### 85. `superlogica_processos_delete`
**Input**: `account` (opcional), `body` (opcional), `query` (opcional)

Receitas / Processos Judiciais: Excluir processo (PUT /processos/delete).

### 86. `superlogica_processos_list`
**Input**: `account` (opcional), `query` (opcional)

Receitas / Processos Judiciais: Listar processos judiciais (GET /processos).

### 87. `superlogica_publico_downloadarquivo`
**Input**: `account` (opcional), `query` (opcional)

Documentos e Arquivos: Download arquivo (GET /publico/downloadarquivo).

### 88. `superlogica_relatorios_id_025a`
**Input**: `account` (opcional), `query` (opcional)

Relatórios: W025A - Previsão orçamentária mensal (GET /relatorios/id/025A).

### 89. `superlogica_relatorios_id_046a`
**Input**: `account` (opcional), `query` (opcional)

Relatórios: W046A - Previsão orçamentária (GET /relatorios/id/046A).

### 90. `superlogica_relatorios_list`
**Input**: `account` (opcional), `query` (opcional)

Prestação de contas: Listar relatórios (GET /relatorios).

### 91. `superlogica_relatoriosselecao_list`
**Input**: `account` (opcional), `query` (opcional)

Prestação de contas: Listar relatórios configurados nas prestações de contas (GET /relatoriosselecao/index).

### 92. `superlogica_relatoriosselecao_put_create`
**Input**: `account` (opcional), `body` (opcional), `query` (opcional)

Prestação de contas: Adicionar relatórios numa prestação de contas (POST /relatoriosselecao/put).

### 93. `superlogica_relatoriosselecao_put_update`
**Input**: `account` (opcional), `body` (opcional), `query` (opcional)

Prestação de contas: Excluir relatórios da prestação de contas (PUT /relatoriosselecao/put).

### 94. `superlogica_reservas_areas`
**Input**: `account` (opcional), `query` (opcional)

Reservas: Listar áreas comuns (GET /reservas/areas).

### 95. `superlogica_reservas_areasreservas`
**Input**: `account` (opcional), `query` (opcional)

Reservas: Listar reservas das áreas comuns (GET /reservas/areasreservas).

### 96. `superlogica_reservas_cancelar`
**Input**: `account` (opcional), `body` (opcional), `query` (opcional)

Reservas: Cancelar reserva (PUT /reservas/cancelar).

### 97. `superlogica_reservas_create`
**Input**: `account` (opcional), `body` (opcional), `query` (opcional)

Reservas: Reservar para uma unidade (POST /reservas).

### 98. `superlogica_reservas_reserva`
**Input**: `account` (opcional), `body` (opcional), `query` (opcional)

Reservas: Confirmar reserva (PUT /reservas/reserva).

### 99. `superlogica_responsaveis_list`
**Input**: `account` (opcional), `query` (opcional)

Solicitações (Tickets): Listar condôminos (GET /responsaveis/index).

### 100. `superlogica_retorno_put`
**Input**: `account` (opcional), `body` (opcional), `query` (opcional)

Receitas / Retorno: Processar arquivo retorno (POST /retorno/put).

### 101. `superlogica_sindicos_cargos`
**Input**: `account` (opcional), `query` (opcional)

Responsáveis Legais: Listagem de cargos de Responsável Legal (GET /sindicos/cargos).

### 102. `superlogica_sindicos_delete`
**Input**: `account` (opcional), `body` (opcional), `query` (opcional)

Responsáveis Legais: Excluir Responsável Legal (PUT /Sindicos/delete).

### 103. `superlogica_sindicos_list`
**Input**: `account` (opcional), `query` (opcional)

Responsáveis Legais: Listar os responsáveis legais (GET /sindicos).

### 104. `superlogica_sindicos_list_get`
**Input**: `account` (opcional), `query` (opcional)

Solicitações (Tickets): Listar Síndico/Presidente ou Conselheiro (GET /sindicos/index).

### 105. `superlogica_sindicos_post`
**Input**: `account` (opcional), `body` (opcional), `query` (opcional)

Responsáveis Legais: Editar Responsável Legal (PUT /Sindicos/post).

### 106. `superlogica_sindicos_put`
**Input**: `account` (opcional), `body` (opcional), `query` (opcional)

Responsáveis Legais: Cadastrar novo Responsável Legal (POST /Sindicos/put).

### 107. `superlogica_tickets_create`
**Input**: `account` (opcional), `body` (opcional), `query` (opcional)

Solicitações (Tickets): Nova solicitação (POST /tickets).

### 108. `superlogica_tickets_list`
**Input**: `account` (opcional), `query` (opcional)

Solicitações (Tickets): Listar solicitações (GET /tickets).

### 109. `superlogica_tickets_puthistorico`
**Input**: `account` (opcional), `body` (opcional), `query` (opcional)

Solicitações (Tickets): Adicionar uma resposta ou anotação a um ticket (POST /tickets/puthistorico).

### 110. `superlogica_unidades_delete`
**Input**: `account` (opcional), `body` (opcional), `query` (opcional)

Unidades: Excluir uma unidade (POST /unidades/delete).

### 111. `superlogica_unidades_list`
**Input**: `account` (opcional), `query` (opcional)

Unidades: Listar unidades de um condomínio (GET /unidades/index).

### 112. `superlogica_unidades_post_create`
**Input**: `account` (opcional), `body` (opcional), `query` (opcional)

Unidades: Cadastrar nova unidade (POST /unidades/post).

### 113. `superlogica_unidades_post_update`
**Input**: `account` (opcional), `body` (opcional), `query` (opcional)

Unidades: Editar uma unidade (PUT /unidades/post).

### 114. `superlogica_usuario_list`
**Input**: `account` (opcional), `query` (opcional)

Solicitações (Tickets): Listar responsáveis (GET /usuario/index).

## Prompts de exemplo

```
Qual a inadimplência total da minha carteira hoje, por condomínio?
Liste as cobranças que vencem nos próximos 7 dias no condomínio 32
Quais despesas estão pendentes de pagamento neste mês?
Mostre o saldo de todas as contas bancárias do condomínio 2
Gere o balancete de receitas e despesas do ano passado, mês a mês
Quais unidades estão inadimplentes há mais de 90 dias?
```
