# Painel do Leandro

Ferramenta de produtividade para gestores de marketing. Organiza tarefas em três lentes — **Minhas** (operacional), **Time** (acompanhamento, dividido por praça: CAM, RIB, SCA, CE) e **Gestão** (1:1s, pessoas) — com status e progresso por tarefa, calendário, agenda de compromissos/reuniões/viagens e backup dos dados.

É um único arquivo `index.html`, sem dependências de build. Abre em qualquer navegador.

Este repositório também tem o `jobs.html`, uma ferramenta separada para as analistas registrarem os jobs de clientes que recebem e o resultado do fechamento — veja a seção [Jobs de Marketing](#jobs-de-marketing--clientes) abaixo.

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

## Jobs de Marketing · Clientes

Arquivo `jobs.html` — ferramenta separada para acompanhar os jobs/projetos de clientes, espelhando a planilha de acompanhamento (Antecipa): cada job passa pelas fases **Briefing → Desenvolvimento → Validação Interna → Aprovação Cliente → Concluído** (ou Pausado/Cancelado), com praça (CAM/RIB/SCA/VAR/CE), origem (Cliente/EP Labs), analista, executivo de conta, prioridade, situação, datas por fase, prazo previsto, último contato e próximos passos. **% de conclusão**, **dias em aberto** e **alerta de prazo** são calculados automaticamente a partir da fase e do prazo, do mesmo jeito que a planilha.

Por cima disso, uma camada comercial: valor orçado, valor fechado e o **veículo de mídia** onde o valor foi fechado (Google Ads, Meta Ads, TV/Rádio, etc.).

- **Aba Jobs**: lista em cards com um botão de "▶ Avançar fase" para progredir o job com um clique, além de editar/excluir. Filtros por situação (em andamento/concluído/atrasado/aguardando cliente), praça, analista, executivo, veículo, cliente e período.
- **Aba Dashboard**: reúne tudo — KPIs (total, em andamento, concluídos, atrasados, aguardando cliente + valor orçado/fechado), funil por fase, e quebras por praça, situação, origem, prioridade, veículo, analista e executivo de conta.
- **⚙ Cadastros**: tela para cadastrar os nomes de analistas, executivos de conta e veículos de mídia (viram sugestão nos campos do job; um nome novo digitado ali já entra automaticamente no cadastro).

Os dados são salvos automaticamente (conta ou navegador, como no Painel do Leandro) e podem ser exportados/importados em JSON.

Basta abrir `jobs.html` no navegador — não precisa instalar nada.

## Privacidade

Tudo roda no seu navegador. O app não envia seus dados para nenhum servidor próprio. Mesmo publicado no GitHub Pages, o que outras pessoas eventualmente acessarem pelo link é a **ferramenta vazia** — os dados ficam no localStorage de cada navegador, não no código do repositório.

> Não versione backups com dados reais (arquivos `.json` exportados) no repositório se não quiser que fiquem públicos.
