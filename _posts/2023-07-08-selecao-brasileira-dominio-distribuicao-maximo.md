---
layout: post
title: "Por que pequenos países conseguem formar grandes seleções?"
date: 2023-07-08
categories: jekyll blogging
feature_image: feature-image.jpg
---

09/12/2022: A Croácia elimina o Brasil nas quartas de final da Copa do Mundo. Além da indignação de ver Vinicius Junior, o jogador mais decisivo do time na competição, ser substituído na metade da segunda etapa, outra questão atormenta o meu grande (e genial) amigo Pedro Augusto B. - que possivelmente contribuirá com um post nesse blog sobre números complexos, os detalhes contratuais ainda estão sendo costurados: **como pode o Brasil (~210 milhões de habitantes) perder para a seleção de um país tão pequeno como a Croácia (~4 milhões)?**

De fato, Uruguai, Chile, Portugal, Holanda, Croácia, entre vários outros pequenos países, são capazes de produzir sucessivas gerações tecnicamente comparáveis às de nações mais populosas, como Brasil, Alemanha e França.

Naturalmente, essa discussão demanda uma análise multidimensional. Evidentemente, não basta ser grande, mas é necessário que o esporte seja praticado em larga escala e que existam mecanismos de busca de talentos. China e Índia, por exemplo, são países em que tais condições não parecem ser satisfeitas. Além disso, existe um mínimo de estrutura imprescindível - especialmente treinadores, campos e campeonatos - para o desenvolvimento técnico e tático dos atletas. América do Sul e Europa parecem oferecer tal estrutura de formação.

Vamos nos restringir a países em que o futebol é um componente cultural importante. Voltemos para a pergunta central do artigo. A explicação que proponho a seguir nada mais é do que um argumento probabilístico baseado em algumas hipóteses que serão enunciadas. Mais importante, não acredito que haja uma maneira simples de testar a validade dessas hipóteses. Em outras palavras, o que ofereço aqui é uma forma de pensar sobre o problema, ao invés de uma solução definitiva (uma conclusão que o leitor mais cético certamente já teria em mente).

Vamos em frente.

Um país é capaz de formar $n$ equipes para jogar uma partida de futebol e a seleção nacional é definida como a melhor dentre elas. Suponha que sejamos capazes de definir uma quantidade $H$ que mede o nível técnico futebolístico de um time (que chamaremos vagamente de habilidade). A habilidade da população (no sentido estatístico) é distribuída de acordo com uma distribuição de probabilidade desconhecida ($H \sim F_H$) e as $n$ equipes que o país é capaz de formar com seu povo formam uma amostra aleatória $\lbrace H_1, ..., H_n \rbrace$ onde cada $H_i$ é uma cópia independente de $H$.

Pois bem, enunciemos agora uma forte hipótese: suponhamos que esta habilidade esteja confinada a um intervalo finito $H \in [0, c]$, ou seja, existe uma habilidade máxima que nenhum time pode superar - que será representada pelo $c$ em homenagem ao [Cruzeiro de 2003][cruzeiro_2003], que foi provavelmente a única equipe na história do futebol a atingi-la. Proponho entendermos esse limite máximo de habilidade como derivado de restrições físicas humanas, afinal há, a priori, limitações de quão rápido podemos correr ou reagir, por exemplo.

Com essa descrição, a habilidade da seleção pode ser definida como a variável aleatória $H_S = \max \lbrace H_1, ..., H_n \rbrace$. A questão agora é: como se distribui $H_S$? Para isso, tomaremos um número $\epsilon$ pequeno e calcularemos $\mathbb{P}(H_S \geq c - \epsilon)$, o que nos permitirá ter uma ideia de como se comporta a probabilidade de que a seleção nacional se aproxime da habilidade máxima para $n$ suficientemente grande.

Ora,

$$
\begin{aligned}
 \mathbb{P}(H_S \geq c - \epsilon) 
  & = \mathbb{P}(\max \lbrace H_1, ..., H_n \rbrace \geq c - \epsilon) \\ 
  & = 1 - \mathbb{P}(\max \lbrace H_1, ..., H_n \rbrace < c - \epsilon) && \text{(por complementaridade)}  \\
  & = 1 - \mathbb{P}(H_1 < c - \epsilon, ..., H_n < c - \epsilon) && \text{(o evento máximo ser menor é equivalente a todos serem menores)}  \\
  & = 1 - \prod_{i=1}^{n} \mathbb{P}(H_i < c - \epsilon) && \text{(pela independência dos eventos)}  \\
  & = 1 - \prod_{i=1}^{n} F_H(c - \epsilon) && \text{(todas as v.a.s da amostra aleatória seguem a mesma distribuição de $H$)}  \\
  & = 1 - F_H(c - \epsilon)^n \\
\end{aligned}
$$

Note que para qualquer $\epsilon > 0$, mesmo que pequeno, $F_H(c - \epsilon) < 1$, pois a função de probabilidade acumulada só atingirá o valor 1 em $c$. Nesse caso,

$$
F_H(c - \epsilon) < 1 \implies F_H(c - \epsilon)^n \xrightarrow[n \to \infty]{} 0
$$

Portanto, para todo $\epsilon > 0$,

$$
\mathbb{P}(H_S \geq c - \epsilon) \xrightarrow[n \to \infty]{} 1
$$

Em outras palavras, a probabilidade de que a seleção nacional apresente uma habilidade arbitrariamente próxima do limite máximo converge para 1 a medida em que o tamanho da população (ou mais precisamente, do número de equipes que ela é capaz de formar) aumenta. Não temos, no entanto, a velocidade dessa convergência. Conjecturo, porém, que ela seja rápida o suficiente para que um $n$ na ordem de grandeza de centenas de milhares ou milhões seja suficiente para uma aproximação bastante razoável de $c$ para a maior parte das distribuições conhecidas (possivelmente teríamos que adicionar algumas restrições sobre a variância, mas deixaremos isso de lado no momento).

O interessante é que o fenômeno aqui descrito não depende da forma exata da distribuição de habilidade para um país. Parece-me razoável supor que $H_{\text{Brasil}}$ seja uma v.a. com média maior que $H_{\text{Bélgica}}$, por exemplo, e com uma distribuição mais concentrada em níveis de habilidade maiores que a belga. No entanto, a seleção nacional não é ditada pela média da habilidade de um país, mas pelo seu máximo. E supondo que exista este limite máximo de habilidade, uma população futebolisticamente ativa com alguns milhões de habitantes seria suficiente para encontrar 11 jogadores extremamente competitivos com o nível internacional, conforme sugere a equação 2.

Assim, tudo indica que teremos que continuar nos preocupando com as seleções de pequenos países da Africa, América do Sul e Europa. Além disso, sob a premissa do futebol continuar se desenvolvendo em países asiáticos e nos Estados Unidos, é possível que surjam novas seleções poderosas. Na minha visão, o Brasil deveria se preparar para perder ainda mais seu destaque esportivo relativo no cenário futebolístico internacional, mas pensar em como manter seu poder institucional e sua imagem do jogo bonito.   


Por hoje é só. Até breve!

[cruzeiro_2003]: https://en.wikipedia.org/wiki/2003_Campeonato_Brasileiro_S%C3%A9rie_A

