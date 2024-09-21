---
layout: post
title: The big casino of sports betting
excerpt_separator: <!--more-->
date: 2023-08-21
categories: jekyll blogging
description: sports betting in Brazil
related_posts: false
---

The sports betting houses have [taken over Brazilian football][clubes-aposta] in recent years. Their brands seem ubiquitous: advertising on TV and the internet, sponsorships on uniforms, and billboards. Interestingly, until very recently, these companies benefited from regulatory and tax loopholes that provided additional incentives for the proliferation of their activity - a situation that should be (at least partially) addressed with an [executive order by Minister Haddad][mp].

<!--more-->

But what is behind the interest of so many agents in mediating sports bets? What are the fundamentals of the profitability of this activity? In this article, I intend to present some reflections on the mathematics and economics of sports betting. Although I am using the term *sports*, I should add that I will focus on football betting. Additionally, I will discuss the "standard" bets (i.e. betting on who won the match) - which I assume to account for most of the money spent on those platforms.

1) **Explaining the odds**

For the standard bets, for each game, the house sets odds for a home team win, an away team win, and a draw. For example, let's imagine that Real Madrid will face Barcelona, and a betting platform has set the following odds for each result: 2.5 if Real Madrid wins, 3.0 if Barcelona wins, and 1.5 if the match ends in a draw. If one bets R$1 in a Real Madrid victory, one receives R$2.5 if this event indeed happens (yielding a return of R$1.5, as the initial R$1 is part of the payout), and alternatively loses the initial R$1 if any other result takes place. In other words, the bottom line for this bettor is either a profit of R$1.5 if Real Madrid wins, or a loss of R$1 else. Analogously, betting on Barcelona yields a return of +R$2.0 (Barcelona wins) or -R$1 (else), and on a draw leads to +R$0.5 in the case of score equality, or again -R$1 if any other result.

2) **Why can $$\frac{1}{\text{odds}}$$ represent the probability of the event?**

In our previous example, many sites will indicate that the probability of a draw implied by the odds of 1.5 is $$\frac{1}{1.5} \approx 67\%$$.  But how is this calculation justified?

My current understanding is that this comes from a *perfect competition* argument. In a perfectly competitive market among betting houses, the odds should be set such that the expected return for the bettor is zero (if the presented odds implied positive expected returns, the house would lose money in the long run; if negative, other houses could offer better odds and capture market share).

Let $$R$$ be the random variable representing the return of the bettor for each R$1 bet, and $$k_{\text{event}}$$ be the odds for a particular event (e.g., home team victory).

$$
R = \begin{cases}
k_{\text{event}}-1 & \text{if the event occurs } (\text{w/ probability } p_{\text{event}}) \\
-1 & \text{if not } (\text{w/ probability } 1-p_{\text{event}})
\end{cases}
$$

Então,

$$
\mathbb{E}(R) = (k_{\text{event}}-1)p_{\text{event}} + (-1)(1-p_{\text{event}}) = 0 \implies p_{\text{event}} = \frac{1}{k_{\text{event}}}
$$

In other words, if the house believes that the probability of the event is 50%, then, under perfect competition, it would be "forced" (by market dynamics) to offer odds of $$k_{\text{event}} = \frac{1}{p_{\text{event}}} = \frac{1}{0.5} = 2$$. This is a simplified explanation, but it helps to understand the rationale. Similar arguments (and with greater formalization) can be found in basic Microeconomics textbooks.

3) **Is the perfect competition hypothesis valid in practice?**

No. There is no perfect competition in this market (which resembles more of an oligopoly), and there are operational costs that the house must cover.

Thus, $$\frac{1}{k_{\text{event}}}$$ does not represent the house's estimated implicit probability of the event. At most, it is a *proxy* for this quantity.

An additional piece of evidence for this claim is that the sum $$\frac{1}{k_{\text{Home}}} + \frac{1}{k_{\text{Away}}} + \frac{1}{k_{\text{Draw}}}$$ is usually greater than 1. For example, looking at the odds from a popular platform for the grand match between Sydney Olympic vs. Sydney United, we have the following odds: 4.00 (Sydney Olympic win), 1.80 (Sydney United win), and 3.60 (draw). Note that $$\frac{1}{4.00} + \frac{1}{1.80} + \frac{1}{3.60} = 108.3$$%. The sum of the "probabilities" exceeds 100%.

4) **Why does the sum exceed 1?**

This is the mechanism that allows houses to ensure profits regardless of the final match result. Let $$k_{i}$$ be the odds for each event, and $$V_{i}$$ the respective amounts bet. The platform's "operational profit" will be the amount collected from losing bets minus the amount paid to the winners.

In the case of a **home win**, the platform's operational bottom line is given by:

$$
V_{\text{Away}} + V_{\text{Draw}} - (k_{\text{Home}}-1)V_{\text{Home}}
$$

Similarly, in the case of an **away win**:

$$
V_{\text{Home}} + V_{\text{Draw}} - (k_{\text{Away}}-1)V_{\text{Away}}
$$

Finally, if the match ends in a **draw**:

$$
V_{\text{Home}} + V_{\text{Away}} - (k_{\text{Draw}}-1)V_{\text{Draw}}
$$

For the betting house to profit in any scenario, all three expressions must be positive. Assuming $$k_i > 1$$ (which is always the case, as otherwise the bettor is guaranteed to lose money):

$$
\begin{cases}
V_{\text{Away}} + V_{\text{Draw}} - (k_{\text{Home}}-1)V_{\text{Home}} > 0  \\
V_{\text{Home}} + V_{\text{Draw}} - (k_{\text{Away}}-1)V_{\text{Away}} > 0 \\
V_{\text{Home}} + V_{\text{Away}} - (k_{\text{Draw}}-1)V_{\text{Draw}} > 0
\end{cases}
\iff 
\begin{cases}
V_{\text{Home}} < \frac{V_{\text{Away}} + V_{\text{Draw}}}{k_{\text{Home}}-1}  \\
V_{\text{Away}} < \frac{V_{\text{Home}} + V_{\text{Draw}}}{k_{\text{Away}}-1} \\
V_{\text{Draw}} < \frac{V_{\text{Home}} + V_{\text{Away}}}{k_{\text{Draw}}-1}
\end{cases}
$$

Let $$V$$ be the total financial volume of bets for that match, i.e., $$V = V_{\text{Home}} + V_{\text{Away}} + V_{\text{Draw}}$$. The previous inequalities can be rewritten as (remembering that $$k_{i} = \frac{1}{p_i}$$):

$$
V_{i} < \frac{V - V_{i}}{k_{i} - 1} \iff V_{i}k_{i} < V \implies V_{i} < \frac{V}{k_{i}} \iff V_{i} < p_{i}V
$$

Thus, given a set of odds, we need to find $$V_{\text{Home}}$$, $$V_{\text{Away}}$$ e $$V_{\text{Draw}}$$ such that:

$$
\begin{cases}
V_{i} < p_{i}V \\
\sum_{i} V_i = V
\end{cases}
$$

The fact that $$\sum_{i} p_i > 1$$ ensures that the system has a solution for any financial volume $$V$$ (this is left as an exercise for the reader). Therefore, regardless of the match outcome, if the distribution of bets respects the above constraints, the house will make money.

Of course, attentive readers will notice that we are being somewhat imprecise with the accounting terms in this section. Houses incur multiple operational costs (server costs, teams of programmers, data scientists, etc.) and expenses (e.g., marketing), so what we have been calling profit is not quite that.

Moreover, in the reasoning above, we fixed the odds and assumed the house could adjust the volume of each bet. In reality, this process occurs dynamically, with the platform offering more or less advantageous odds over time to balance the bet portfolio.
   
5) **Is it possible to beat the market (i.e., consistently achieve positive returns)?**

This is highly unlikely. Outperforming the platforms' predictive models is extremely hard and, even in the unlikely scenario where you find one, betting houses seem to be able to hinder some strategies as soon as they are proven capable of consistently generating positive returns (as showed in [this paper][paper]).

Your football club is sponsored by a betting company, not by your neighbor. So my recommendation is to always remember who is really making the money in this activity before falling into the illusion of getting rich quickly.


[clubes-aposta]: https://www.uol.com.br/esporte/futebol/ultimas-noticias/2023/03/31/patrocinios-de-sites-de-apostas-a-clubes-da-serie-a-batem-r-330-mi-por-ano.htm
[mp]: https://g1.globo.com/politica/noticia/2023/07/25/mp-das-apostas.ghtml
[paper]: https://arxiv.org/abs/1710.02824
