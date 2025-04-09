---
layout: page
title: Game Design Document
---

# Game Design Document

## Visão Geral
- Gênero: Auto Battler + Roguelike
- Inspirações: Teamfight Tactics (TFT), Balatro, Slay the Spire
- História: Derrote demônios para proteger sua vila

## Progressão do Jogo

O jogo é separado em 4 estações do ano, em cada estação ocorre 6 tentativas de invasão dos demônios na vila.

Os inimigos vão ficando gradativamente mais fortes, acompanhando a evolução do time do jogador.

A 6ª batalha de cada estação é a mais difícil, contra um inimigo boss, com melhores atributos e habilidades especiais.

O jogador precisa derrotar as 24 ondas de inimigos em batalhas para vencer.

Após vencer, o jogador pode continuar jogando e sua progressão até ser derrotado será marcado em um leaderboard das suas melhores jogadas.

## Mecânicas Principais

### Sistema de Personagens
- Time de 10 personagens
- Cada personagem tem um nome e atributos
- Atributos:
  - Vida (inteiro)
  - Dano de ataque (inteiro)
  - Velocidade de ataque (inteiro ataques/minuto)
  - Taxa de esquiva (float - porcentagem de chance de desviar do ataque inimigo)
  - Range de ataque (número de posições no tabuleiro)
- Máximo de 5 personagens podem batalhar por vez
- Todos os personagens começam com os mesmos atributos
- Personagens no banco de reservas são curados uma quantidade base de vida após cada batalha

### Sistema de Batalha

#### Tabuleiro
- 6 linhas x 5 colunas
- 3 linhas inferiores para posicionamento dos personagens do jogador
- 3 linhas superiores para posicionamento dos inimigos

#### Fase de Preparação
- Jogador posiciona até 5 personagens nas 3 linhas inferiores
- Cada posição pode ser ocupada por apenas um personagem
- Jogador pode ver a disposição dos inimigos antes da batalha
- Sem limite de tempo para preparação
- Batalha inicia quando o jogador estiver pronto

#### Batalha
- Personagens e inimigos atuam automaticamente
- Comportamento básico:
  1. Mover até adversário ficar no range
  2. Atacar de acordo com velocidade de ataque
  3. Causar dano baseado no atributo
  4. Se adversário morrer, repetir ciclo
- Batalha dividida em etapas de 1 minuto
- Personagens abatidos são perdidos até o final da batalha

#### Pós-Batalha
- Vitória: Todos os inimigos derrotados
- Derrota: Todos os aliados derrotados (fim do jogo)
- Em caso de vitória, personagens abatidos retornam para próxima batalha

### Sistema de Loja e Melhorias

#### Pontos de Experiência
- Ganhos por vitória
- Cálculo considera:
  - Pontos base por vitória
  - Quantidade de personagens diferentes usados
  - Número de aliados abatidos

#### Loja
- 10 melhorias aleatórias disponíveis
- Atualização manual possível (custa pontos)
- Melhorias podem persistir entre atualizações

#### Tipos de Melhorias
1. **Melhorias Individuais Simples**
   - Aplicadas a um personagem
   - Modificam atributos básicos

2. **Melhorias Individuais de Classe**
   - Aplicadas a um personagem
   - Adicionam habilidades especiais
   - Uma classe por personagem

3. **Melhorias Gerais Simples**
   - Aplicadas a todo o time
   - Modificam atributos base

4. **Melhorias Gerais Avançadas**
   - Aplicadas a todo o time
   - Adicionam efeitos especiais

5. **Melhorias de Suporte**
   - Bônus não relacionados a batalha
   - Ex: Cura no banco, mais pontos de experiência

6. **Itens**
   - Consumíveis para uso durante batalha
   - Perdidos após uso

#### Sistema de Inventário
- Armazenamento de melhorias compradas
- Venda de melhorias por 100% do valor
- Sem limite de melhorias ativas

### Sistema de Inimigos
- Mesmos atributos que personagens aliados
- Quantidade, tipo e atributos variam por fase 