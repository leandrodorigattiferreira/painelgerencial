# Painel do Leandro

Ferramenta de produtividade para gestores de marketing. Organiza tarefas em três lentes — **Minhas** (operacional), **Time** (acompanhamento, dividido por praça: CAM, RIB, SCA, CE) e **Gestão** (1:1s, pessoas) — com status e progresso por tarefa, calendário, agenda de compromissos/reuniões/viagens e backup dos dados.

É um único arquivo `index.html`, sem dependências de build. Abre em qualquer navegador.

## Funcionalidades

- **Três lentes** com cores próprias e contagem de tarefas abertas.
- **Divisão por praça** na lente Time (CAM, RIB, SCA, CE), com agrupamento e filtro.
- **Status e progresso**: A fazer / Em andamento / Bloqueada / Concluída, com subtarefas que alimentam uma barra de evolução.
- **Calendário** mensal com tarefas (pelo prazo) e eventos.
- **Agenda** de reuniões, compromissos e viagens, agrupada por proximidade.
- **Tela Hoje**: foco do dia, agenda do dia e indicadores.
- **Matriz Urgente × Importante** (Eisenhower) para priorizar.
- **Exportar / Importar** os dados em JSON (somar ou substituir).

## Como usar

Basta abrir o `index.html` no navegador. Não precisa instalar nada.

### Onde os dados ficam salvos

O app detecta o ambiente e salva sozinho:

- **No Claude (artefato publicado):** usa o armazenamento da sua conta.
- **Hospedado no GitHub Pages ou aberto localmente:** salva automaticamente **neste navegador** (localStorage). Os dados ficam no navegador/dispositivo em que você usou.

O indicador no rodapé da barra lateral mostra o estado atual ("Salvo na sua conta" / "Salvo neste navegador"). Como o localStorage é por navegador, use **Exportar** para levar seus dados de um dispositivo para outro (e **Importar** no destino).

## Publicar no GitHub Pages (link online grátis)

1. Crie um repositório no GitHub (ex.: `painel-do-leandro`).
2. Suba os arquivos `index.html` e `README.md`.
3. No repositório: **Settings → Pages**.
4. Em **Build and deployment → Source**, escolha **Deploy from a branch**.
5. Selecione a branch `main` e a pasta `/ (root)`. Salve.
6. Aguarde ~1 minuto. O link aparece em **Settings → Pages** no formato:
   `https://SEU-USUARIO.github.io/painel-do-leandro/`

Pronto — é só salvar esse link nos favoritos e usar no dia a dia.

## Privacidade

Tudo roda no seu navegador. O app não envia seus dados para nenhum servidor próprio. Mesmo publicado no GitHub Pages, o que outras pessoas eventualmente acessarem pelo link é a **ferramenta vazia** — os dados ficam no localStorage de cada navegador, não no código do repositório.

> Não versione backups com dados reais (arquivos `.json` exportados) no repositório se não quiser que fiquem públicos.

## Jobs de Marketing · Clientes

**Identidade visual "Reserva"**: papel-porcelana e tinta quase-preta, um único acento vinho reservado pra ações principais (Salvar, Fechar, Novo job) — o resto fica em contorno, hairline ou texto simples. Cantos retos, sem sombra. Tipografia Lexend (números e títulos) + Manrope (texto) + Spline Sans Mono (valores/códigos), sem serifa. Funciona em claro e escuro.

Arquivo `jobs.html` — ferramenta separada para acompanhar os jobs/projetos de clientes. Cada **job** tem um número de registro único no formato `INICIAIS_seqCliente_seqGeral` (ex.: `SAV_002_44` — 2º job desse cliente, 44º job da ferramenta inteira) e avança pelas fases **Recebido → Em desenvolvimento → Entregue → Fechado/Declinado**. O **fechamento é uma decisão única do job inteiro** (quando fecha, fecha tudo junto — a data é única), mas o **valor fechado é registrado por veículo**: cada linha de veículo tem seu próprio valor orçado e, quando o job fecha, seu próprio valor fechado (por padrão igual ao orçado, editável se houve negociação por canal).

Cada job também tem praça — CAM, RIB, SCA e VAR são praças geográficas normais, e **CE é diferente: é "Contas Especiais", não uma praça geográfica** — origem (Solicitação interna/Proativo), analista, executivo de conta, prioridade, situação, marcação de **conta especial (estratégica)** (usada especificamente para as contas de varejo/VAR de destaque, não confundir com a praça CE), três datas (**solicitação**, **prazo**, **entrega**), **briefing recebido**, um **checklist** (manual ou gerado por IA a partir do briefing), próximos passos, um link de **Plano de Mídia** e uma lista de **planilhas** (nome + link — não há upload de arquivo dentro do artifact, então entram por link). **% de conclusão** e **alerta de prazo** são calculados automaticamente a partir da fase do job.

- **Aba Jobs**: quadro kanban com 5 colunas (Recebido, Em desenvolvimento, Entregue, Fechado, Declinado) — um card por job, mostrando o número, o cliente, os veículos com seus valores e os links de Plano de Mídia/planilhas (quando preenchidos). Botões no rodapé do card: "▶ Avançar" percorre as fases de desenvolvimento, "✕ Declinar" encerra o job como perdido, e um job encerrado ganha um botão "↺ Reabrir". Filtros por status do job (em andamento/fechado/atrasado/aguardando cliente), praça, analista, executivo, veículo, cliente e período.
- **Confirmação de fechamento**: clicar em "✓ Fechar" abre um popup listando cada veículo do job com o valor orçado à mostra e um campo pra confirmar/ajustar o valor fechado (vem preenchido com o orçado, editável se houve negociação por canal) — só depois de confirmar o job vira Fechado. Isso deixa explícito, no momento de fechar, exatamente quanto foi fechado em cada canal.
- **Tipo do job**: todo job tem um **Tipo** — **Proposta comercial** (o padrão, uma proposta customizada da marketing), **Pós-venda** (acompanhamento/atendimento de um cliente já fechado) ou **Fechamento direto** (mídia fechada direto, sem passar por uma proposta customizada). O campo aparece tanto no formulário do job quanto no briefing do executivo, então o tipo já vem definido desde a entrada. Um job de Pós-venda ou Fechamento direto continua normal no quadro (avança fase, fecha, aparece nos filtros), mas o **Dashboard conta os dois tipos à parte**: ficam de fora do valor orçado/fechado, % de conversão, meta por praça, segmentação, funil, comparativo anual e das quebras de conversão por analista/executivo — só entram nos números operacionais do topo (total de jobs, em andamento, atrasados) e cada um numa seção própria ("Pós-venda" e "Fechamentos diretos", com quantidade, valor fechado e ticket médio). Assim esses tipos não inflam os indicadores que medem o trabalho de proposta comercial customizada da marketing. Tem também uma quebra **"Jobs por tipo"** no Dashboard mostrando a proporção entre os três.
- **EP Labs**: saiu do campo "Origem" do job e virou um registro próprio (botão "📋 EP Labs" na barra lateral) — data, horário, local e se gerou proposta. Cada registro conta automaticamente para a meta 1 (EP Labs realizados) no Dashboard.
- **Régua de cobrança ("dinheiro na mesa")**: todo job **não encerrado** guarda a data do último contato. Depois de **7 dias sem contato**, aparece um alerta ⚠ no card (com um botão 🔔 para marcar que o contato foi feito e reiniciar a contagem). Depois de **21 dias**, o job é **declinado automaticamente** (motivo "Sem retorno (automático)"), mas fica marcado como **recuperável** — um botão ↺ reabre o job a qualquer momento. O painel **Dashboard** tem uma seção dedicada listando todos os jobs parados e os recuperáveis.
- **Aba Dashboard**: KPIs de jobs (total, em andamento, fechados, atrasados, aguardando cliente) e comerciais (valor orçado/fechado, **% fechado por valor ofertado** e **% fechado por quantidade de jobs** — os dois em percentual —, ticket médio); painel de **4 objetivos estratégicos**; **Resumo do dia** (só na visão de praça/contas especiais — números fixos de recebidos hoje, fechados hoje com valor, jobs parados e em andamento, mais um botão "📋 Gerar resumo do dia (IA)" pra virar um texto curto pronto pra colar num Slack, pensado pra dupla analista + estagiária de cada praça); **meta mensal por praça em gráfico de barras** (uma torre por mês, com uma linha tracejada marcando a meta, cada barra colorida de verde quando bate a meta e de vermelho quando fica abaixo, e o % de atingimento embaixo — respeita a mesma hierarquia de acesso do resto da ferramenta: a gestão sem filtro vê sempre as 5 praças, na ordem CAM/RIB/SCA/VAR e depois CE (contas especiais, à parte por não ser praça geográfica); um filtro manual de praça na gestão ou o acesso de uma praça/contas especiais mostra só o gráfico correspondente — em todos os casos o gráfico aparece mesmo que a praça ainda não tenha nenhum job fechado, com as barras zeradas. Metas configuráveis em ⚙ Cadastros, uma por praça); **dois mapas de calor** — atingimento de meta por praça e mês (verde/amarelo/vermelho conforme a % batida) e verba orçada por praça e mês (intensidade da cor conforme o valor pedido, pra ver onde a demanda está concentrada); seção **Dinheiro na mesa**; **Radar de risco** e **Resumo da semana** (IA, ver abaixo); **funil por fase em formato de funil de verdade** (barras afunilando, com os declinados contados à parte); **segmentação mês a mês** (contas especiais de varejo, comparando cada mês de 2026 com o mesmo mês de 2025, cliente por cliente); gráficos de evolução mensal; comparativo anual; e quebras por praça, situação, origem, prioridade, **papel (analista/estagiária)**, veículo — com **conversão por analista e por executivo mostrando dois indicadores lado a lado: % por quantidade de jobs e % por valor proposto** (esse indicador aparece tanto na visão geral da gestão quanto na visão de cada praça, já filtrado pros jobs daquela praça).
- **Visão por praça / executivo / contas especiais**: ao abrir pela primeira vez (em cada navegador), a pessoa escolhe **ver tudo** (gestão), **uma praça geográfica** (CAM/RIB/SCA/VAR — "CE" não aparece nessa lista, já que não é uma praça de analista), **sou executivo** ou **contas especiais** — a escolha fica salva nesse navegador e pode ser trocada pelo link "trocar" no topo. É um filtro/atalho de conveniência (guardado no navegador de quem está usando), não uma trava de segurança.
- **Senha por visão (opcional)**: em ⚙ Cadastros dá pra configurar uma senha pra cada visão (gestão, cada praça, contas especiais, executivo). Se configurada, ao escolher aquela visão aparece uma tela pedindo a senha antes de mostrar qualquer dado; uma vez digitada certo, fica liberada só naquela aba/navegador até fechar (usa sessionStorage — abrir de novo numa aba nova pede de novo). **Importante: isso é só uma trava simples do navegador contra abertura casual/acidental, não é segurança de verdade** — os dados (incluindo as próprias senhas configuradas) continuam visíveis a quem tiver acesso ao artifact e souber olhar o código-fonte da página. Não é um substituto pra controlar quem tem o link do artifact.
- **Visão do executivo**: uma tela só com um formulário simples (cliente, tipo, praça, origem, prioridade, prazo, executivo e o texto do briefing). Ao enviar, vira um job novo na fase Recebido, já com o tipo e o briefing preenchidos, pronto pra aparecer no quadro da analista responsável pela praça assumir e completar (veículos, valores, analista etc.).
- **Visão de contas especiais**: funciona **igual à visão de uma praça normal** — mesmos filtros, mesmo "＋ Novo job", mesmas abas Jobs/Dashboard — só que restrita aos jobs com **praça = CE** (hoje demandados só pela executiva Tayra Rodrigues). A diferença aparece em dois lugares: (1) a aba **Jobs** mostra um quadro kanban separado por cliente — cada um dos ~10 clientes tem seu próprio mini-quadro de 5 colunas, no mesmo esquema do quadro geral; (2) a aba **Dashboard** ganha duas seções extras, além de tudo que já existe (objetivos, meta mensal em gráfico de barras, funil, dinheiro na mesa etc.): **Desempenho por cliente** (jobs, fechados, orçado, fechado, ticket médio e conversão de cada um) e **Cliente × veículo (fechado)** (uma matriz de quanto cada cliente fechou em cada veículo).
- **Iniciativas de IA** (usam a capacidade `sample` do Claude — só funcionam no artifact publicado, e quem usa "paga" o custo da chamada, com consentimento na primeira vez): **✨ Gerar checklist do briefing** (extrai tarefas do texto do briefing pro analista); **💡 Sugerir veículos** (sugere canais complementares com base no histórico de jobs fechados da praça); **🔎 Radar de risco** (lê "próximos passos"/briefing dos jobs em aberto e aponta sinais de risco); **📋 Resumo da semana** (gera um texto curto com os números da semana, pronto pra colar num Slack/e-mail). Fora do artifact (uso local), esses botões ficam desativados.
- **⚙ Cadastros**: tela para cadastrar os nomes de analistas, executivos de conta e veículos de mídia (viram sugestão nos campos do job; um nome novo digitado ali já entra automaticamente no cadastro). Cada **analista** tem também um **papel** (Analista ou Estagiária, clicável pra alternar) — pensado pra dupla que cada praça e contas especiais tem, uma analista e uma estagiária que se apoiam. Também é onde ficam as **metas por praça** e a **senha por visão**.
- **Exportar para Excel**: além do backup completo em JSON, o botão "📊 Exportar Excel" na barra lateral baixa uma planilha CSV (abre direto no Excel/Google Sheets) com uma linha por veículo de cada job — número, cliente, praça, analista e papel, executivo, fase, datas, veículo, valores orçado/fechado etc. O registro de EP Labs tem seu próprio botão de exportação dentro do modal "📋 EP Labs".
