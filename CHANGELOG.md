# Changelog

Todas as mudanças relevantes do projeto são registradas aqui.
O formato segue o [Keep a Changelog](https://keepachangelog.com/pt-BR/1.1.0/).

## [Não lançado] — Alpha

### Adicionado

- **Rede de sentinelas** que responde ao ARCHON K-9 (veja a seção no [README](README.md#rede-de-sentinelas)):
  - Atua em cinco salas: Corredor do Cofre, Sala de Servidores, Datavault Omega, Beco de Dados e Antecâmara de Segurança.
  - A Unidade 01, depois de alertada e de uma fuga, continua caçando o jogador por toda a malha.
  - Perseguição pós-fuga com prazo de 4 ações e chance de alcance que cresce com o Ruído.
  - Reforços numerados (Unidades 02 e 03) com cooldown de 1 ação, Ruído mínimo 4 e 65% de chance por ação; disparam ao mover, esperar, descansar, saquear e hackear.
  - Reforço que fugiu volta ao estoque da central e pode ser reenviado.
  - Narrativa própria para cada etapa (perda de unidade, perseguição, reforços e esgotamento da central) e nova entrada de Codex (`sentry_net`).
- **Rifle Eletromagnético** (Mercado de Sucata, 20 cr) e **Projétil Ferromagnético .50** (par por 5 cr): Ranged +1 passivo; disparo de tiro único com d8 + Ranged (≤ 5 erra, 6 falha e poupa munição, 7 acerta, ≥ 8 crítico). Liberado após 2 objetivos concluídos.
- **Dois desafios de hack na Sala de Servidores**: o 1º (DR 12) libera a Cifra de Rede; o 2º (DR 13) destrava os elevadores do Núcleo K-9. Usar a Cifra na sala também resolve o 2º estágio.
- **Loot no chão** quando a mochila está cheia (drops de inimigos, caches e a Capa Termo-óptica comprada do hacker): o item fica na área e pode ser recolhido depois. No Núcleo K-9 sobrevive pelo menos mais uma sala.
- **Modo de tela cheia** (botão ⛶ e comando `fullscreen`/`telacheia`) e meta tags para uso como app em dispositivos móveis.
- Meta `description` para compartilhamento e GitHub Pages.
- README, CHANGELOG, LICENSE e banner ilustrativo para publicação no GitHub.

### Alterado

- **Colete Reforçado** passou a ser passivo, como a Lâmina Curta: o bônus de ARM +1 vale assim que o item está na mochila e aparece na hora nos painéis de Status e Inventário.
- O painel de Status mostra **`Ranged N (+1)`** quando o Rifle está equipado (e o comando `status` detalha a origem do bônus).
- A **Varredura** em combate usa a mesma DR dos demais testes (12 + ARM do inimigo), em vez de um valor fixo.
- A **Capa Termo-óptica** deixou de ser vendida no mercado; é obtida pelo hacker anônimo do Núcleo K-9 ou como loot raro. Seu lugar na loja ficou com o Rifle Eletromagnético.
- Layout **fluido** para telas pequenas e de baixa resolução (`clamp()`, `dvh`/`svh` e breakpoints extras).
- Manual embutido no cabeçalho do `index.html` atualizado (sentinelas, itens, objetivos e DRs).

### Corrigido

- O **Drone-Sentinela do Corredor** continuava perseguindo e "emergindo" depois de neutralizado: o abate só era registrado quando o combate começava por conversa. Agora qualquer abate encerra o alerta, libera a grade sul e cancela a perseguição.
- A **Unidade 01 ressurgia** depois de neutralizada ao **esperar ou descansar** no Corredor do Cofre (cerca de 2% das ações): o evento aleatório de espera sorteava inimigos direto do pool da sala, que ainda continha o drone. Agora todo sorteio de sala filtra a sentinela depois do abate, e `startCombat` recusa recriá-la como salvaguarda.
- A perseguição do drone não tinha prazo, atingia qualquer sala (inclusive depois de descer ao Núcleo K-9) e disparava com 100% de certeza.
- A mensagem de "Oferta especial" do Rifle aparecia na loja da Dra. Vale (Clínica de Latão) em vez de só no Mercado de Sucata.
- O **crítico do Rifle** (≥ 8) não dobrava o dano; agora dobra, como os demais críticos do jogador.
- A **Cifra de Rede** podia ser saqueada sem hackear a sala; agora o saque exige o 1º hack bem-sucedido.
- Removido um ramo de código inalcançável no uso da Cifra (o item só existe depois do 1º hack).
- Valor de DR do Datavault Omega no manual corrigido (13 após o 1º hack nos Servidores, 16 antes).
