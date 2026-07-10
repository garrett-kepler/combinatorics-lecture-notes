---
author:
  - Garrett J. Kepler
date: Updated
title: 'Lecture Notes on Combinatorics: Draft'
---


# Chapter 8: Graphs

## Warmup
````{prf:question}
1. Given 5 points on the surface of a sphere, show that there is a closed hemisphere that contains 4 points. (A closed hemisphere is a sphere cut in half including the boundary that was cut)
2. How many ways are there to select $k$ objects from $n$?
3. After selecting, how many ways are there to permute those $k$ objects?
4. How many ways are there permute $k$ objects from $n$?
5. Courtesy of Zvezdelina Stankova, a combinatorial thinking builder: Given $n$ points on the boundary of a circle, connect each pair of points such that any line crossings involve only two lines. How many regions does this create?
6. Given an $n\times n$ board, how many ways can we place $n$ points so that no point shares a column or row with any other point?
````

## Graphs
One fundamental combinatorial object we study in combinatorics is the *graph*. You may have already seen these. For example, see Figure
[\[fig:network\]](#fig:network){reference-type="ref"
reference="fig:network"}. We will formalize the idea in this section.

![Examples of graphs. On the left, a network of the internet. On the right, a graph corresponding to a molecule. Courtesy of
[https://en.wikipedia.org/wiki/Computernetwork](https://en.wikipedia.org/wiki/Computer_network)
and <https://en.wikipedia.org/wiki/Molecule>
respectively.[]{label="fig:network"}](math 325/book/content/photos/Internet_map_1024.png "fig:"){#fig:network
height="0.2\textheight"} ![Examples of graphs. On the left, a network of the internet. On the right, a graph corresponding to a molecule.
Courtesy of
[https://en.wikipedia.org/wiki/Computernetwork](https://en.wikipedia.org/wiki/Computer_network)
and <https://en.wikipedia.org/wiki/Molecule>
respectively.[]{label="fig:network"}](math 325/book/content/photos/TOAT_AFM.png "fig:"){#fig:network
height=".2\textheight"}

````{prf:definition} Graph
A *graph* $G=(V,E)$ is a collection of vertices $V$ and edges $E$ where $E$ is a set of pairs of vertices.
````

We can synonymously call vertices and edges nodes and arcs, but I will try to remain consistent with the former. We typically assume $E$ is a set of edges defined over $V$. Otherwise, this object would indeed be hard to interpret. Consider the following graphs.

````{prf:example}
Let $G=(\{1,2,3\},\{(1,2),(2,3)\}$. Then, we can visualize $G$ as 

$$visualization here$$

Notice, if we remove $(2,3)$, we end up with a different, yet similar
graph $H=(\{1,2,3\},\{(1,2)\}$
$$visualization here$$

````

Note that in drawing these graphs, we have an ordered pair $(x,y)$ telling us our edge begins at $x$ and ends at $y$. As such, we have an arrow indicating the starting node and ending node for each edge. A graph where this *direction* is important we call a *directed graph*. If instead, order does not matter, we have an *undirected graph*.

````{prf:definition} Directed
A graph $G=(V,E)$ is *directed* when $E$ consists of *ordered pairs* of vertices (e.g. $(2,3)$). Conversely, a graph is *undirected* when $E$ consists of *unordered pairs* of vertices (e.g. $\{2,3\}$).
````

Consider the graph from before, $G=(\{1,2,3\},\{(1,2),(2,3)\}$.

$$visualization here$$ 

We can form an undirected analogue, $H=(\{1,2,3\},\{\{1,2\},\{2,3\}\}$.

$$visualization here$$ 

Note, we do not require that the vertices in an edge be distinct. That is, we could have a *self-loop* $(x,x)$ for some $x\in V$.

$$visualization here$$ 

We also do not require that there is only one edge between a pair of nodes.

$$visualization here$$ 

We can even weight edges!

$$visualization here$$ 

These objects can be very complicated indeed. As such, we can further restrict our graphs to what we call *simple*.
````{prf:definition} Simple
A *simple* graph is an undirected, unweighted graph without self-loops and multiple edges.
````

A simple graph is arguably the easiest graph to think of. But, simple and not simple graphs have the pros and cons when dealing with them in practice. 

Consider the following question:

````{prf:question}
How many simple, undirected graphs in general are there on $n$ nodes?
````
> **Answer:** For an edge to exist, we have to pair up two nodes. How many ways can we do this? $\binom{n}{2}$ ways. For each of those potential edges, there is 2 possibilities: the edge exists or it doesn't. So, by multiplication principle, there are $2^{\binom{n}{2}}$ possible graphs in general.


Okay, $2^{\binom{n}{2}}$ in general. But, consider the two following graphs.

$$visualization here$$ 

Intuitively, these are representatives of the same structure. One could say these are the same graph with different labels. This idea is what we call *isomorphic graphs*. The question of "How many simple *non-isomorphic* graphs are there on $n$ nodes?" is a much more difficult question to answer. See here for more: $$link here$$. 

There are many features of graphs we care about. One particular example is the number of edges each node is represented in.
````{prf:definition} Degree
The number of edges incident with a node $v$ is the *degree* of $v$ denoted $d(v)$.
````
For the following graph, the degree of each node is: $d(1)=1$, $d(2)=2$, and $d(3)=1$.

````{prf:theorem} Handshaking Lemma
Let $G=(V,E)$. Then, 

$$\begin{align}
\sum_{v\in V} d(v)&=2|E|
\end{align}$$
````
````{prf:proof}
For each node $v$, $d(v)$ counts the number of edges $v$ appears in (i.e. the number of edges $(v,u)$ or $\{v,u\}$). The sum over all $v$ will count $(v,u)$ and $(u,v)$ for every edge in the graph. As such, we count twice the number of edges in the graph.
````

````{prf:corollary}
In a graph $G$, there are an even number of odd degree nodes.
````



````{prf:question}
Using the binomial theorem, how many *directed* graphs are there on $n$ nodes in general?
````

## Summary
What we've covered here: 
- something