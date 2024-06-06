---
layout: post
title: Why can small countries form great national squads?
date: 2023-07-08
categories: jekyll blogging
description: a hypothetical (probabilistic) argument
related_posts: false
---

09/12/2022: Croatia eliminates Brazil in the quarterfinals of the World Cup. Besides the indignation of seeing Vinicius Junior, the most decisive player on the team, being substituted halfway through the second half, I wonder whether another issue torments the general public: **how can Brazil, a country with a population of ~210 million people, lose (again) against such a small country (population-wise) like Croatia (~4 million)?**

Indeed, Uruguay, Chile, Portugal, the Netherlands, Croatia, among several other small countries, are capable of producing successive generations that are technically comparable to those of more populous nations such as Brazil, Germany, and France.

Naturally, this discussion demands a multidimensional analysis. Evidently, it is not enough to be large; it is necessary that the sport is practiced on a large scale and that there are mechanisms for talent scouting. Furthermore, there is a minimum level of essential infrastructure - especially coaches, fields, and youth championships - for the technical and tactical development of athletes. South America and Europe seem to offer such a developmental structure.

Let us restrict ourselves to countries where football is an important cultural component. Let's return to the central question of the article. The explanation I propose next is nothing more than a probabilistic argument based on some hypotheses that will be stated. More importantly, I do not believe there is a simple way to test the validity of these hypotheses. In other words, what I offer here is a way to think about the problem, rather than a definitive solution (a conclusion that the more skeptical reader would certainly already have in mind).

Let's move forward.

A country is capable of forming $$n$$ teams to play a football match, and the national team is defined as the best among them. Suppose we are able to define a quantity $$H$$ that measures the technical level of a team (which we will vaguely call *skill*). The skill of the population (in the statistical sense) is distributed according to an unknown probability distribution ($$H \sim F_H$$), and the $$n$$ teams that the country is capable of forming with its people constitute a random sample $$\lbrace H_1, ..., H_n \rbrace$$ where each $$H_i$$ is an independent copy of $$H$$.

Now, let's state a restrictive hypothesis: suppose that this skill is confined to a finite interval $$H \in [0, c]$$, that is, there is a maximum skill that no team can surpass - which will be represented by $$c$$ in honor of [Cruzeiro (2003)][cruzeiro_2003], which was probably the only team in the history of football to reach it. I propose we understand this maximum skill bound as derived from human physical constraints, after all, there are, a priori, limitations on how fast we can run or react, for example.

With this description, the skill of the national team can be defined as the random variable $$H_S = \max \lbrace H_1, ..., H_n \rbrace$$. The question now is: how is $$H_S$$ distributed? For this, we will take a small number $$\epsilon$$ and compute $$\mathbb{P}(H_S \geq c - \epsilon)$$, which will allow us to get an idea of how the probability that the national team approaches the maximum skill behaves for sufficiently large $$n$$.

We have:

$$
\begin{aligned}
 \mathbb{P}(H_S \geq c - \epsilon) 
  & = \mathbb{P}(\max \lbrace H_1, ..., H_n \rbrace \geq c - \epsilon) \\ 
  & = 1 - \mathbb{P}(\max \lbrace H_1, ..., H_n \rbrace < c - \epsilon) && \text{(by complementarity)}  \\
  & = 1 - \mathbb{P}(H_1 < c - \epsilon, ..., H_n < c - \epsilon) && \text{(max being smaller is equivalent to all being smaller)}  \\
  & = 1 - \prod_{i=1}^{n} \mathbb{P}(H_i < c - \epsilon) && \text{(independence)}  \\
  & = 1 - \prod_{i=1}^{n} F_H(c - \epsilon) && \text{(identically distributed)}  \\
  & = 1 - F_H(c - \epsilon)^n \\
\end{aligned}
$$

Note that for any $$\epsilon > 0$$, even if very small, $$F_H(c - \epsilon) < 1$$, since the cumulative distribution function will only reach the value 1 at $$c$$. In this case,

$$
F_H(c - \epsilon) < 1 \implies F_H(c - \epsilon)^n \xrightarrow[n \to \infty]{} 0
$$

Therefore, for all $$\epsilon > 0$$,

$$
\mathbb{P}(H_S \geq c - \epsilon) \xrightarrow[n \to \infty]{} 1
$$

In other words, the probability that the national team exhibits a skill arbitrarily close to the maximum limit converges to 1 as the population size (or more precisely, the number of teams the country is capable of forming) increases. However, we do not have the speed of this convergence. I conjecture, though, that it is fast enough that an $$n$$ on the order of hundreds of thousands or millions is sufficient for a quite reasonable approximation of $$c$$ for most known distributions (we might possibly have to add some restrictions on the variances, but we will leave that aside for now).

The interesting thing is that the phenomenon described above does not depend on the exact shape of the skill distribution for a country. It seems reasonable to assume that $$H_{\text{Brazil}}$$ is a random variable with a higher mean than, say, Belgium $$H_{\text{Belgium}}$$, and with a distribution more concentrated at higher skill levels. However, the national team is not dictated by the average skill, but by its maximum. And assuming this maximum skill bound exists, a football-active population with a few million inhabitants could be sufficient to find 11 extremely competitive players at the international level, as suggested by equation 2.

Thus, it seems we will have to continue worrying about the national squads from small countries in Africa, South America, and Europe. Moreover, under the premise that football continues to develop in Asian countries and the United States, new powerful teams may emerge. In my view, Brazil should prepare to lose even more of its relative prominence in the international football scene but think about how to maintain its institutional power and image of *joga bonito*.

[cruzeiro_2003]: https://en.wikipedia.org/wiki/2003_Campeonato_Brasileiro_S%C3%A9rie_A

