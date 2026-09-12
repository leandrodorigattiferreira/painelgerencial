# Painel do Leandro

---

## Plano de Mídia (para alunos)

Arquivo `plano-de-midia.html` — ferramenta separada, independente do painel acima, para os alunos montarem planos de mídia completos.

- **Catálogo com ~40 veículos**: TV aberta/paga, CTV/streaming, rádio, OOH/DOOH, cinema, impresso, áudio/podcast, busca paga, social ads (Meta, TikTok, LinkedIn, Pinterest, X, Snapchat, Kwai), display/programática, vídeo online, retail media (Mercado Livre, Amazon, Magalu, Shopee), influenciadores/creators, afiliados, CRM/retenção, app/UA e gaming/in-game — cada um com etapa de funil, modelo de compra e faixa de referência de custo do mercado brasileiro.
- **Múltiplos planos**: cada aluno cria, duplica e gerencia vários planos (por marca/trabalho).
- **Linhas de veiculação**: escolha do veículo, etapa do funil, modelo de compra (CPM/CPC/CPV/CPA/CPL/CPI/CPP/Fixo), custo unitário e verba, com cálculo automático de impressões/cliques/views/conversões estimadas.
- **Painéis analíticos**: verba por veículo, por etapa do funil, offline × digital, e cronograma de veiculação (flighting) por linha.
- **Glossário de mídia**: mais de 25 termos modernos (CPM, ROAS, viewability, attention metrics, MMM/incrementalidade, cookieless, retail media etc.), com busca.
- **Exportar/Importar** todos os planos em JSON e **Imprimir/gerar PDF** do plano ativo.
- Mesmo padrão do painel acima: arquivo único sem build, salva localmente no navegador (localStorage) ou na conta quando publicado como artefato.

> Ainda sem multiusuário/nuvem: cada aluno usa e salva no próprio navegador, exportando o JSON para levar entre dispositivos.


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
