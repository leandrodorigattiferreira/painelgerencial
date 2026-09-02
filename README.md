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

Arquivo `jobs.html` — ferramenta separada para acompanhar os jobs/projetos de clientes. Cada **job** tem um número de registro único (`JOB-2026-001`) e pode conter **várias linhas de veículo de mídia** (Google Ads, Meta Ads, TV/Rádio, etc.) — cada linha avança pelas suas próprias fases **Recebido → Em desenvolvimento → Entregue → Fechado** (ou **Declinado**, a qualquer momento antes de fechar), independente das outras linhas do mesmo job. Isso permite ver facilmente qual veículo fechou, qual foi declinado e qual ainda está em andamento, dentro do mesmo cliente/job.

Cada job também tem praça (CAM/RIB/SCA/VAR/CE), origem (Cliente/EP Labs), analista, executivo de conta, prioridade, situação, data de recebimento, prazo previsto, último contato e próximos passos. Cada linha de veículo tem valor orçado, valor fechado, data de entrega/fechamento e motivo (quando declinada). **% de conclusão**, **dias em aberto** e **alerta de prazo** são calculados automaticamente por linha.

- **Aba Jobs**: quadro kanban com uma coluna por fase — cada card representa uma linha de veículo (com o número do job e o cliente destacados), com botões "▶ Avançar" e "✕ Declinar" para atualizar o status daquela linha com um clique. Filtros por status (em andamento/fechado/declinado/atrasado/aguardando cliente), praça, analista, executivo, veículo, cliente e período.
- **Aba Dashboard**: KPIs (total de linhas, em andamento, fechadas, declinadas, atrasadas + valor orçado/fechado/jobs distintos), funil por fase, e quebras por praça, situação, origem, prioridade, veículo, analista e executivo de conta — incluindo "Valor fechado por veículo" para comparar o desempenho de cada canal de mídia.
- **⚙ Cadastros**: tela para cadastrar os nomes de analistas, executivos de conta e veículos de mídia (viram sugestão nos campos do job; um nome novo digitado ali já entra automaticamente no cadastro).
