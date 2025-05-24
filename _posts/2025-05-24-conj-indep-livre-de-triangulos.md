---
layout: post
title: "Sobre o número de independência de grafos livres de triângulos (Questão do livro Combinatória)"
category: grafos e combinatória
slug: conjunto-independente-grafos-livres-de-triangulos
---

Neste semestre, eu estou cursando a disciplina de Métodos Probabilísticos. O livro que está sendo usado na disciplina é o [Combinatória](https://impa.br/wp-content/uploads/2022/01/33CBM02-eBook.pdf). A primeira avaliação desta disciplina está sendo resolver as questões do Capítulo 5 deste livro. A questão 3 é a seguinte.

> **Questão 3.8.5.** Seja $$G$$ um grafo livre de triângulos. Mostre que
> $$\alpha(G) \geq \sum_{v \in V(G)}\frac{d(v)}{1+d(v)+d_2(v)}$$,
> onde $$d_2(v)$$ denota o número de vértices a distância 2 de $$v$$ em $$G$$.

No início do Capítulo 5, um outro teorema sobre o número de independência é provado e é natural pensar que podemos provar este acima de maneira bem similar. O teorema ao qual estou me referindo é o que diz que $$\alpha(G) \geq \sum_{v \in V(G)} \frac{1}{1+d(v)}.$$

Para prová-lo, sorteamos uma ordem aleatória dos vértices de $$G$$ e construímos um conjunto independente da seguinte maneira. Escolhemos um vértice $$v$$ para entrar no conjunto independente se $$v$$ vem antes de todos os seus vizinhos nessa ordenação. Como a probabilidade de $$v$$ estar no conjunto independente é $$\frac{1}{1+d(v)}$$, obtemos o limitante desejado calculando o tamanho esperado de um conjunto independente construído desta maneira.

Uma ideia natural para provar o teorema da questão 3 é também sortear uma ordenação dos vértices e, para cada $$v \in V(G)$$, incluirmos no conjunto independente os vértices de $$N_G(v)$$, uma vez que estes vértices não possuem arestas entre si (o grafo é livre de triângulos). Infelizmente, essa ideia não funciona. Abaixo, eu coloco a resolução deste teorema, que saiu após uma discussão do problema com meus amigos Brito e Rodrigo.

---
{: data-content="Prova do Teorema da Questão 3"}

Seja $$\sigma:V(G) \rightarrow [n]$$ uma ordenação aleatória dos vértices do grafo. Seja $$S \subseteq V(G)$$ o conjunto de vértices $$v$$ de $$G$$ tais que $$\exists u \in N_G(v) [\sigma(u) < \sigma(v)]$$ e $$\forall w \in N_G^2(v) [\sigma(v) < \sigma(w)]$$, onde $$N_G^2(v)$$ denota os vértices a distância 2 de $$v$$ em $$G$$. Ou seja, $$S$$ é o conjunto de vértices de $$G$$ que estão depois de pelo menos um vértice de sua vizinhança e antes de todos os vértices da sua vizinhança segunda.

Afirmamos que $$S$$ é um conjunto independente de $$G$$. Para ver isto, assuma por absurdo que existe dois vértices $$u, v \in S$$ tais que $$uv \in E(G)$$. Se $$u$$ e $$v$$ possuem algum vizinho em comum, digamos $$w$$, então $$\{u, v, w\}$$ é um triângulo de $$G$$, o que é absurdo uma vez que $$G$$ é livre de triângulos. Suponha então que $$N_G(u) \cap N_G(v) = \emptyset$$. Suponha ainda, sem perda de generalidade, que $$\sigma(u) < \sigma(v)$$. Como $$u \in S$$, existe um vértice $$w \in N_G(u)$$ tal que $$\sigma(w) < \sigma(u) < \sigma(v)$$. Mas veja que $$w \in N_G^2(v)$$ uma vez que as vizinhanças de $$v$$ e $$u$$ são disjuntas. Isso contradiz a escolha de $$v$$ para $$S$$. Concluímos então que $$S$$ é, de fato, um conjunto independente de $$G$$.

Agora, vamos calcular a probabilidade de um dado vértice $$v$$ estar em $$S$$. Temos $$(1+d(v)+d_2(v))!$$ ordens parciais dos vértices de $$\{v\} \cup N_G(v) \cup N_G^2(v)$$. Podemos escolher $$y \leq d(v)$$ vértices para vir antes de $$v$$ na ordem parcial. Fixe $$y \in \{1, 2, \dots, d(v)\}$$. As ordens válidas são apenas aquelas em que os $$y$$ vértices escolhidos de $$N_G(v)$$ vem antes de $$v$$ e $$v$$ vem antes de todos os vértices de $$N_G^2(v)$$. Dado que essa regra é respeitada, os $$y$$ vértices podem estar em qualquer ordem entre si, e o mesmo vale para todos os vértices de $$N_G^2(v)$$. Temos então $${y+d_2(v) \choose y}y!d_2(v)!$$ permutações válidas dentre um total de $$(1+d(v)+d_2(v))!$$. Então,

$$P(v \in S) = \sum_{y=1}^{d(v)} \frac{y!d_2(v)!{y+d_2(v) \choose y}}{(1+d(v)+d_2(v))!} = \sum_{y=1}^{d(v)}\frac{1}{1+d(v)+d_2(v)} = \frac{d(v)}{1 + d(v) + d_2(v)}.$$

Agora, calculando o tamanho esperado de $$S$$, concluímos que $$\alpha(G) \geq \sum_{v \in V(G)} \frac{d(v)}{1+d(v)+d_2(v)}$$, como desejado.

---
{: data-content="Fim da Prova"}

É isso! Achei essa questão interessante e resolvi registrar aqui essa resolução que é bem legal também. Até a próxima! 👋