---
layout: post
title: "O cassino das apostas esportivas"
excerpt_separator: <!--more-->
date: 2023-08-21
categories: jekyll blogging
feature_image: feature-image.jpg
---

As casas de aposta esportiva [dominaram o futebol brasileiro][clubes-aposta] nos últimos anos. Suas marcas parecem onipresentes: publicidade em TV e internet, patrocínios estampados em uniformes, outdoors. Curiosamente, até há pouquíssimo tempo, estas empresas ainda gozavam de lacunas tributária e regulatória que criavam incentivos adicionais à proliferação da atividade - situação que deve ser resolvida com uma [recente MP proposta por Haddad][mp].

<!--more-->

Mas o que está por trás do interesse de tantos agentes em mediar apostas esportivas? Quais são os fundamentos da lucratividade dessa atividade? Apesar de nunca ter apostado em resultados esportivos (com exceção de uma pizza que tive de pagar para meu grande amigo Artur S. após a vitória da Itália na Eurocopa de 2020), pretendo apresentar algumas reflexões sobre a matemática das apostas.

1) **Funcionamento das apostas no Brasil**

Para apostas no vencedor da partida, a casa precifica cotações para a vitória do mandante, visitante e empate. Por exemplo, suponha que a cotação do empate seja $2.5$. Caso o jogo termine em igualdade de placar, para cada <code>$</code>
1 colocado nesse resultado, o apostador receberá <code>$</code>
2.50 (tendo, assim, uma rentabilidade de <code>$</code>
1.50 - pois o real inicialmente apostado faz parte do pagamento). 

2) **Por que $\frac{1}{\text{cotação}}$ pode traduzir a probabilidade do evento?**

No nosso exemplo anterior, muitos sites indicarão que a probabilidade de empate implícita na cotação de 2.5 é $\frac{1}{2.5} 
= 40$%. Mas como justificar essa conta?

Isso deriva de um argumento de *competição perfeita*. Em um mercado perfeitamente competitivo entre as casas de aposta, as cotações devem ser tais que o rendimento esperado para o apostador seja nulo (se as cotações apresentadas implicassem redimentos esperados positivos, a casa perderia dinheiro no longo prazo; se negativos, abririam oportunidade para que outras casas oferecessem melhores cotações e absorvessem *market share*). 

Sejam $R$ a variável aleatória que representa o **rendimento** do apostador para cada <code>$</code>1 apostado e $k_{\text{evento}}$ a cotação de um determinado evento (e.g. vitória do mandante).

$$
R = \begin{cases}
k_{\text{evento}}-1 & \text{se evento ocorre } (p_{\text{evento}}) \\
-1 & \text{se evento não ocorre } (1-p_{\text{evento}})
\end{cases}
$$

Então,

$$
\mathbb{E}(R) = (k_{\text{evento}}-1)p_{\text{evento}} + (-1)(1-p_{\text{evento}}) = 0 \implies p_{\text{evento}} = \frac{1}{k_{\text{evento}}}
$$

Ou seja, se a casa acredita que a probabilidade do evento é de $50$%, então, sob hipótese de competição perfeita, ela seria "forçada" (pela própria dinâmica do mercado) a oferecer uma cotação de $k_{\text{evento}} = \frac{1}{p_{\text{evento}}} = \frac{1}{0.5} = 2$. É evidente que esta é uma explicação simplificada, mas ajuda a entender o racional. Argumentos similares (e com maior grau de formalidade) podem ser encontrados em livros básicos de Microeconomia.

3) **A hipótese de competição perfeita é válida na prática?**

Não. Não há competição perfeita nesse mercado (que parece mais uma espécie de oligopólio) e, ainda, há custos de operação que devem ser cobertos pela casa.

Dessa forma, $\frac{1}{k_{\text{evento}}}$ não representa a probabilidade implícita do evento estimada pela casa. Representa, no máximo, uma *proxy* dessa quantidade.

Uma evidência adicional dessa afirmação é que a soma $\frac{1}{k_{\text{Mandante}}} + \frac{1}{k_{\text{Visitante}}} + \frac{1}{k_{\text{Empate}}}$ é usualmente maior que $1$. Por exemplo, consultando as cotações de uma famosa plataforma para o majestoso clássico entre Sydney Olympic vs Sydney United, temos as seguintes cotações: $4.00$ (vitória Sydney Olympic), $1.80$ (Sydney United) e $3.60$ (empate). Ora, $\frac{1}{4.00} + \frac{1}{1.80} + \frac{1}{3.60} = 108.3$%. A soma das "probabilidades" é superior a $100$%.

4) **Por que a soma é superior a 1?**

Este é o ingrediente que permite as casas garantirem lucros que independem do resultado final da partida. Sejam $k_{i}$ as cotações de cada evento e $V_{i}$ os respectivos valores apostados. O "lucro operacional" da plataforma será dado pelo que ela arrecada de apostas derrotadas menos o que ela precisa pagar aos vencedores.

No caso da **vitória do mandante**, o *bottom line* operacional da plataforma é dado por:

$$
V_{\text{Visitante}} + V_{\text{Empate}} - (k_{\text{Mandante}}-1)V_{\text{Mandante}}
$$

Analogamente, em caso de **vitória do visitante**:

$$
V_{\text{Mandante}} + V_{\text{Empate}} - (k_{\text{Visitante}}-1)V_{\text{Visitante}}
$$

Finalmente, se a partida termina **empatada**:

$$
V_{\text{Mandante}} + V_{\text{Visitante}} - (k_{\text{Empate}}-1)V_{\text{Empate}}
$$

Para que a casa de apostas tenha lucro em qualquer caso, basta que as três expressões sejam positivas.

$$
\begin{cases}
V_{\text{Visitante}} + V_{\text{Empate}} - (k_{\text{Mandante}}-1)V_{\text{Mandante}} > 0  \\
V_{\text{Mandante}} + V_{\text{Empate}} - (k_{\text{Visitante}}-1)V_{\text{Visitante}} > 0 \\
V_{\text{Mandante}} + V_{\text{Visitante}} - (k_{\text{Empate}}-1)V_{\text{Empate}} > 0
\end{cases}
\implies 
\begin{cases}
V_{\text{Mandante}} < \frac{V_{\text{Visitante}} + V_{\text{Empate}}}{k_{\text{Mandante}}-1}  \\
V_{\text{Visitante}} < \frac{V_{\text{Mandante}} + V_{\text{Empate}}}{k_{\text{Visitante}}-1} \\
V_{\text{Empate}} < \frac{V_{\text{Mandante}} + V_{\text{Visitante}}}{k_{\text{Empate}}-1}
\end{cases}
$$

Seja $V$ o volume financeiro total de apostas para aquela partida, ou seja, $V = V_{\text{Mandante}} + V_{\text{Visitante}} + V_{\text{Empate}}$. As inequações anteriores podem ser reescritas como (lembrando que $k_{i} = \frac{1}{p_i}$):

$$
V_{i} < \frac{V - V_{i}}{k_{i} - 1} \implies V_{i}k_{i} < V \implies V_{i} < \frac{V}{k_{i}} \implies V_{i} < p_{i}V
$$

Dessa forma, dado um conjunto de cotações, basta encontrarmos $V_{\text{Mandante}}$, $V_{\text{Visitante}}$ e $V_{\text{Empate}}$ tais que:

$$
\begin{cases}
V_{i} < p_{i}V \\
\sum_{i} V_i = V
\end{cases}
$$

O fato de que $\sum_{i} p_i > 1$ faz com que o sistema tenha solução para qualquer volume financeiro $V$ (isto fica como exercício para o leitor). Portanto, seja qual for o resultado da partida, se a distribuição das apostas estiver coerente com as restrições acima, a casa ganhará dinheiro.

Obviamente, o leitor atento certamente percebeu que estamos sendo pouco precisos com os termos contábeis desta seção. As casas incorrem múltiplos custos operacionais (custos de servidores, equipes de programadores, cientistas de dados, etc), e despesas (e.g. *marketing*) e, dessa forma, o que temos chamado de *lucro*, não o é de fato.

Além disso, no raciocício acima, fixamos as cotações e assumimos que a casa é capaz de ajustar os volumes de cada aposta. Na realidade, este processo ocorre de maneira dinâmica, com a plataforma oferecendo cotações mais ou menos vantajosas ao longo do tempo para ajustar o portfólio de apostas.
   
5) **É possível bater o mercado (i.e. obter retornos positivos interesantes de maneira consistente)?**

Se eu soubesse a resposta dessa pergunta, provavelmente estaria tomando um *mojito* em uma praia do Caribe e não escrevendo um post de um blog que (quase) ninguém lê. Em teoria, alguém que dispõe de um modelo preditivo de altíssima acurácia (em outras palavras, cujas estimativas das distribuições de probabilidade dos resultados seja, de fato, muito próximas das reais) poderia apostar em jogos em que haja discordância em relação às "probabilidades implícitas" nas cotações. Ou seja, se a casa precifica uma cotação cuja probabilidade implícita de vitória do mandante é de 30% e o seu poderoso modelo indica 90%, deve valer a pena comprar esta aposta. No longo prazo, esta estratégia deve quase certamente retornar lucros consistentes. No entanto, é evidente que obter um tal sistema preditivo é extremamente complicado. Lembre-se que as principais casas de apostas empregam vastas equipes de cientistas de dados trabalhando nos modelos de cotação e, portanto, "superá-los" não é uma tarefa simples.

Existem, porém, alternativas que não dependem da criação de sistemas proprietários. [Kaunitz, Zhong & Kreiner (2017)][paper] apresentam uma estratégia baseada na comparação de cotações providas por várias plataformas. O ponto mais interessante do artigo, entretanto, é o fato de que as casas começaram a dificultar as apostas dos pesquisadores assim que a estratégia se provou capaz de originar retornos positivos de maneira consistente. Isso mostra que as plataformas exercem uma discriminação operacional contra apostadores recorrentemente vitoriosos.

Quem faz dinheiro com apostas esportivas são as casas, não os apostadores. Afinal, o patrocínio master do seu clube é provavelmente uma *bet* qualquer e não o nome do seu vizinho.


[clubes-aposta]: https://www.uol.com.br/esporte/futebol/ultimas-noticias/2023/03/31/patrocinios-de-sites-de-apostas-a-clubes-da-serie-a-batem-r-330-mi-por-ano.htm
[mp]: https://g1.globo.com/politica/noticia/2023/07/25/mp-das-apostas.ghtml
[paper]: https://arxiv.org/abs/1710.02824
