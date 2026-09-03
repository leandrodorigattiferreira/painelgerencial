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

Arquivo `jobs.html` — ferramenta separada para acompanhar os jobs/projetos de clientes. Cada **job** tem um número de registro único (`JOB-2026-001`) e avança em conjunto pelas fases **Recebido → Em desenvolvimento → Entregue → Concluído**. Dentro de um job, cada **linha de veículo de mídia** (Google Ads, Meta Ads, TV/Rádio, etc.) é desenvolvida junto com as demais, mas tem seu **próprio desfecho** — Em aberto, Fechado ou Declinado — decidido individualmente, com valor orçado/fechado e motivo (quando declinada). Isso reflete como o trabalho acontece de verdade: o desenvolvimento é conjunto, mas cada veículo fecha ou não por si só.

Cada job também tem praça (CAM/RIB/SCA/VAR/CE), origem (Solicitação interna/EP Labs/Proativo), analista, executivo de conta, prioridade, situação, marcação de **conta especial (estratégica)**, datas de recebimento/entrega/conclusão, prazo previsto, último contato, **briefing recebido** (texto do briefing enviado ao analista), próximos passos, um link de **Plano de Mídia** e uma lista de **planilhas** (nome + link, quantas forem necessárias — não há upload de arquivo dentro do artifact, então planilhas e plano de mídia entram por link). **% de conclusão**, **dias em aberto** e **alerta de prazo** são calculados automaticamente a partir da fase do job.

- **Aba Jobs**: quadro kanban com uma coluna por fase — um card por job, mostrando o número, o cliente, os links de Plano de Mídia/planilhas (quando preenchidos) e a lista de linhas de veículo com seu status (com botões ✓/✕ para fechar ou declinar cada linha direto no card). O botão "▶ Avançar" no rodapé do card move o job inteiro para a próxima fase. Filtros por status do job (em andamento/concluído/atrasado/aguardando cliente), praça, analista, executivo, veículo, cliente e período.
- **Régua de cobrança ("dinheiro na mesa")**: toda linha de veículo **Em aberto** guarda a data do último contato. Depois de **7 dias sem contato**, aparece um alerta ⚠ no card (com um botão 🔔 para marcar que o contato foi feito e reiniciar a contagem). Depois de **21 dias**, a linha é **declinada automaticamente** (motivo "Sem retorno (automático)"), mas fica marcada como **recuperável** — um botão ↺ some ou reabre a proposta a qualquer momento. O painel **Dashboard** tem uma seção dedicada listando todas as propostas paradas e as recuperáveis.
- **Aba Dashboard**: KPIs de jobs (total, em andamento, concluídos, atrasados, aguardando cliente) e de linhas (valor orçado/fechado, **% fechado por valor ofertado** e **% fechado por quantidade de propostas** — separados —, ticket médio); painel de **4 objetivos estratégicos** (EP Labs realizados, ticket médio de contas especiais no varejo, conversão de propostas estratégicas, multicanalidade média); seção **Dinheiro na mesa**; gráficos de **evolução mensal** (jobs recebidos e valor fechado nos últimos 6 meses); **comparativo anual** (jobs, valores, % fechado e EP Labs por ano, ex. 2025 vs 2026); funil por fase; e quebras por praça, situação, origem, prioridade, veículo, analista e executivo de conta.
- **⚙ Cadastros**: tela para cadastrar os nomes de analistas, executivos de conta e veículos de mídia (viram sugestão nos campos do job; um nome novo digitado ali já entra automaticamente no cadastro).
- **Visão por praça**: ao abrir pela primeira vez (em cada navegador), a pessoa escolhe se quer ver **tudo** (gestão) ou só a **própria praça** — a escolha fica salva nesse navegador e pode ser trocada a qualquer momento pelo link "trocar" no topo. Isso é só um filtro de conveniência (guardado no navegador de quem está usando), não é uma trava de segurança — os dados no artifact continuam os mesmos para todo mundo que tiver acesso a ele.
