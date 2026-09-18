# Painel do Leandro

Este repositório tem duas ferramentas independentes, cada uma em um único arquivo HTML:

- **`index.html`** — produtividade (tarefas, calendário, agenda).
- **`financas.html`** — controle financeiro pessoal (entradas, saídas, cartão de crédito). Veja detalhes abaixo.

---


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

---

## Finanças (`financas.html`)

Controle financeiro pessoal focado em input rápido: abra, aperte "＋ Lançar agora" (ou tecle **N**), digite o valor e pronto.

### Funcionalidades

- **Lançamento rápido**: valor, descrição, categoria (em chips de um clique), forma de pagamento (Pix, débito, dinheiro, cartão) e data — tudo num único modal, com atalho de teclado (`N`) e botão flutuante sempre visível.
- **Editar e excluir** qualquer lançamento: clique numa linha (no painel ou na lista) para abrir o mesmo modal já preenchido.
- **Entradas e saídas** com categorias personalizáveis (crie novas categorias na tela "Categorias").
- **Cartões de crédito**: cadastre um ou mais cartões com dia de fechamento e vencimento; cada compra lançada no cartão entra automaticamente na fatura correta (mês seguinte se a compra for depois do fechamento).
- **Parcelamentos**: ao lançar no cartão, informe o número de parcelas — o app divide o valor e cria uma compra por mês automaticamente. A tela "Parcelamentos" mostra tudo que ainda está em aberto, com valor e parcelas restantes.
- **Recorrentes**: ao lançar algo, marque "repetir todo mês" para contas fixas e assinaturas — elas são lançadas sozinhas nos meses seguintes.
- **Lançamentos**: lista com busca por descrição, filtro por categoria e opção de ver todo o histórico (não só o mês atual).
- **Painel do mês**: saldo, total de entradas/saídas, fatura do cartão, saídas por categoria e um indicador de **comprometimento de receita** (quanto da sua renda média já está preso em parcelas e contas fixas nos próximos meses).
- **Contas**: cadastre contas (corrente, poupança, carteira...) com saldo inicial; cada lançamento (fora cartão) fica ligado a uma conta e o saldo é calculado automaticamente. Dá pra fazer **transferência** entre contas sem afetar entradas/saídas.
- **Orçamento**: defina um teto mensal por categoria de saída e acompanhe o gasto até o limite, com aviso visual quando estoura.
- **Metas**: reservas e objetivos (ex: reserva de emergência) com valor alvo, valor guardado e aportes rápidos.
- **Projeção de fluxo de caixa**: próximos 6 meses de saldo projetado, somando recorrentes e parcelas já assumidas.
- **Patrimônio**: investimentos, bens e dívidas cadastrados manualmente, com patrimônio líquido calculado (contas + investimentos/bens − dívidas).
- **Relatórios**: comparativo de entradas × saídas dos últimos 6 meses, maior gasto do mês e categoria que mais pesou.
- **Exportar / Importar** os dados em JSON (somar ou substituir), igual ao `index.html`.

### Dados

Segue o mesmo esquema de armazenamento do `index.html`: salva sozinho no ambiente do Claude (artefato publicado) ou no `localStorage` do navegador quando hospedado/local. Os dois arquivos usam chaves de armazenamento diferentes, então não se misturam.
