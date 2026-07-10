---
author:
  - Garrett J. Kepler
date: Updated 2.4.26
title: 'Lecture Notes on Combinatorics: Draft'
---

# Chapter 4: "Counting"

## Warmups

````{prf:question}
:label:warmup
1. How many total subsets of $S=\{1,2,3,\dots, 50\}$ are there?
2. Calculate $1+2+3+\cdots+49+50$. Could you form a general formula for
$1+2+3+4+\cdots+n$?
3. Determine the number of subsets of $S=\{1,2,3,\dots,50\}$ whose sum of
elements is larger than or equal to 638.
````
> **Answer:**
> 1. Consider a subset $\mathcal{S}$ of $S$.
>   - For each $i=1,2,3,\dots, 50$, either $i$ is in $\mathcal{S}$ or not.
>   - For each $i$, define $\mathcal{S}_{i}=\{0,1\}$ where $0$ is the case where $i$ is in $\mathcal{S}$ and 0 where $i$ is not.
>   - Then, the total number of ways we can create subsets is given by $|\mathcal{S}_1\times \mathcal{S}_2\times \mathcal{S}_3\times \cdots\times \mathcal{S}_{50}|$.
>   - By the multiplication principle, this tell us the number of possible subsets of $S$ is
>
>$$\begin{align} |\mathcal{S}_1\times \mathcal{S}_2\times \mathcal{S}_3\times \cdots\times \mathcal{S}_{50}|&=|\mathcal{S}_1|\cdot |>\mathcal{S}_2|\cdot |\mathcal{S}_3|\cdots |\mathcal{S}_{50}|\\ &= 2\cdot 2\cdot 2\cdots 2=2^{50} \end{align}$$
>
>This is a totally valid solution. But, there are multiple ways to solve a problem. So, let's try and solve this problem by finding a bijection. Consider taking a subset $A\subseteq S$.
>   - For each element $s$ in $S$, $s$ is either in $A$ or not.
>   - We could think of assigning each element $s$ a 1 or 0 depending on if it is in $A$ (say, 1 if $s\in A$, 0 if $s\notin A$).
>   - Then, $f(A)$ could be a vector of length $n$ with entries 1 or 0. For example, $f(\{1,3,4, 6\})=[1,0,1,1,0,1,0,\dots, 0]^T=X_A$.
>   - What $f^{-1}$ be then? If the $i$-th entry of $X_A$ is 1, put $i$ in a set $A$. If the $i$-th entry of $X_A$ is 0, exclude $i$ from $A$.
>   - Thus, $f^{-1}$ exists and $f$ is a bijection. So, the number of subsets $A$ of $S$ equals the number of possible 0,1-vectors $X_A$ of size $|S|$.
>   - How many vectors are there? There's 2 options for each $|S|$ entries of a vector $X_A$. So, again, by the multiplication principle, there are $2^{|S|}$ possible such vectors. And so, the total number of subsets is equal to $2^{|S|}$.
>   - In our case, this means there are $2^{50}$ subsets.
>   There are multiple ways to solve a problem. The benefit of this is that we may learn different things about the objects in question. For example, in the bijection proof we learn about the relationship between 0,1-vectors of size $n$ and total subsets of a set of size $n$. They are equivalent!
> 2. You might try the following: 
>
> $$\begin{align} L &= 1+2+3+\cdots+49+50\\ \implies 2L &= 1+2+3+\cdots+49+50\\ &+50+49+48+\cdots+2+1\\ \implies2L&= (1+50)+(2+49)+(3+48)\\ &+\cdots+(49+2)+(50+1)\\ &= 51+51+51+\cdots+51+51\\ &=50(51)\\ \implies 2L&=50(51)\implies L=\frac{50(51)}{2}=1275 \end{align}$$ 
>
> This generalizes to $\frac{n(n+1)}{2}$ when we sum 1 through $n$.
> 3. Again, let us try and find a bijection. Let $T$ be the collection of all possible subsets of $S$. From warmup problem 1, we know $|T|=2^{50}$. From warmup problem 2, the sum of elements of $S$ is 1275.
>   - Let $A$ be the set of all subsets of $S$ whose sum is $\geq 638$ and $B$ be the set of all subsets of $S$ whose sum is $<638$. Since either a subset sums to $\geq 638$ or $<638$ and not both, $A\cup B=T$ and $A\cap B=\emptyset$. Thus, $|T|=|A\cup B|=|A|+|B|$.
>   - Moreover, if $A_i\in A$, then the sum of elements in $A_i$ is $\geq 638$. Since the sum of elements in $S$ is 1275, the sum of elements in $A_i^C$ must be less than or equal $1275-638=637$.
>   - From Friday's class, we know $f(A_i)=A_i^C$ is a bijection. So, $|A|=|B|$. 
>   - So, $|T|=|A|+|B|=|A|+|A|=2|A|$.
>   - Since $|T|=2^{50}=2|A|$, we know $|A|=2^{49}$. You might try and generalize this to $S=\{1,2,3,\cdots, n\}$ with a specific choice of sum for the subsets, say 325.

## Permutations, Combinations, & Double Counting

Combinatorics differs itself from many fields by its proof techniques. We have been talking about bijections the last few classes. What bijections allow us to do is say the following:
- We want to find a formula to count something
- We can transform the problem into an equivalent problem with a bijection
- Finding a formula in this equivalent problem tells us the count of the original problem
But, what if we found formulas for both problems? These are equivalent problems, so they should have equivalent formulas! This is what is referred to as "double counting" or "counting with equivalence" or "counting in two ways". The backbone of double counting can be summarized as follows:

````{prf:theorem} Double Counting
If $f(n)$ and $g(n)$ are functions that count the solutions to a problem
involving $n$ objects, then $f(n)=g(n)$ for every $n$.
````
That is, if there are two equivalent ways to count something, they must be equivalent all the time!

````{prf:definition}
A *combinatorial proof* works as follows:
- **Problem**: We must count the number of solutions to a problem on $n$ objects.
- **LHS**: Count one way and find a function $f(n)$ counts these solutions.
- **RHS**: Count another way and find a function $g(n)$ counts these
   solutions.
- **Conclusion**: Then, $f(n)=g(n)$ for every $n$.
The result, $f(n)=g(n)$, is what we call a *combinatorial identity*.
````

This first step is crucial. Sometimes we are given the problem we are going to solve (e.g. "How many ways are there to permute $n$ objects?"). Then, we find two equivalent formulas. Other times, we are given an identity to prove and we must identify a problem to count (e.g. "Prove $\binom{n}{k}=\binom{n}{n-k}$"). Then, we must show that both the left hand side and right hand side count the solutions to the problem we have identified.

````{prf"definition} Selection & Combination
A *selection* is the creation of a subset of a set. The resulting subset is called a *combination*. We do not care about the ordering of the elements. Simply what elements are chosen.
````

The number of ways to select a subset of $k$ objects from a set $n$ distinct objects, $C(n,k)$, is denoted: $\begin{align}C(n,k)&=_nC_k=\binom{n}{k} \end{align}$ The right hand side is what we call a _binomial coefficient_. We read this as "$n$ choose $k$".



````{prf:definition} Arrangement & Permutation
An *arrangement* is a selection. Each resulting ordered arrangement is
called a *permutation*.
````

The number of ways to arrange $k$ objects from a set of $n$ distinct
objects, $P(n,k)$, is denoted: $\begin{align} P(n,k)&=_nP_k=(n)_k \end{align}$

````{prf:example} Combination vs. Permutation

1. How many ways are there to make a sundae with 3 toppings from an ice
cream shop with 10 toppings? (Topping order doesn't matter, so this is a combination problem!)

2. How many ways are there to schedule the performances of 4 finalists on the reality show for singers? (Singing schedule does matter, so this is a permutation problem!)
````
> **Answer:** 
> 1. We are *selecting* 3 objects from 10 objects, so there are $C(10,3)$ ways.
> 2. To recall a previous example "How many ways can we draw 4 labelled orbs (A,B,C,D) from an urn without replacement?" Using the multiplication principle, we found there was 4 options for the first draw, 3 for the second, and so on giving a count of $4\cdot 3\cdot 2\cdot 1=4!=12$. Equivalently, there are $P(4,4)$ ways.

````{prf:question}
How many ways are there to arrange $k$ objects from a set of $n$
distinct objects?
````

````{prf:proof}
- **Identify Problem**: How many ways are there to arrange $k$ objects
   from a set of $n$ distinct objects?
- **LHS**: We know by definition $P(n,k)$ counts this.
- **RHS**: We can think of assigning $n$ objects to $k$ boxes. For box
   1, there are $n$ possible objects that can be assigned to it. For
   box 2, there are $n-1$ possible objects. Continuing on to the $k$th
   box, all $k-1$ boxes before it have an object, so there are
   $n-(k-1)$ possible objects that can be assigned box $k$. Using the
   multiplication principle, there are
   $n\cdot(n-1)\cdot (n-2)\cdot (n-(k-1))$ ways to do this.
- **Conclusion**: Thus, there are
   $P(n,k)=n\cdot (n-1)\cdot (n-2)\cdot (n-(k-1))$ ways to arrange $k$
   objects from a set of $n$.
````
The proof above allows us to immediately say the following as well:

$$\begin{align}
P(n,k)=n\cdot (n-1)\cdot (n-2)\cdot (n-(k-1))=\frac{n!}{(n-k)!}
\end{align}$$ 
where
$n!=n\cdot(n-1)\cdot(n-2)\cdots 3\cdot 2\cdot 1$ and referred to as "$n$ factorial". By convention, $0!=1$.

Coming back to a version of our orbs and urn problem: "You draw from an urn with 4 labeled orbs (A,B,C,D) one by one without replacement. How many ways are there to do this?"

We are arranging 4 objects from a set of 4. There are $P(4,4)$ ways to do this. So, there are $P(4,4)=\frac{4!}{(4-4)!}=4!$ ways to do this.

We also asked the following: "You draw the orbs from the urn with replacement, you write down 4 labels. How many ways are there to do this so their is only a pair of repeats?" (e.g. (A,B,C,A) is okay but not (D,D,C,D)).

Consider a set of four slots $S$ in which you will write the labels. We select one of the labels to repeat, there are 4 ways to do this. We select 2 slots from the 4 slots for this label, there are $C(4,2)=\binom{4}{2}$ ways to do this. After this label has been placed, there are 3 labels to be arranged in 2 slots, there are $P(3,2)=\frac{3!}{(3-2)!}=3!$ to do this. This means there are $4\cdot C(4,2)\cdot P(3,2)=4\cdot\binom{4}{2}\cdot 3!$ ways in total to get exactly one pair in this case. This is a totally valid response to a combinatorics question. For an concise answer, we can simplify to obtain 144 ways.
````{prf:question} To Ponder
- How many ways are there to draw $n$ labeled orbs from an urn with replacement?

- How many ways are there to draw $n$ labeled orbs from an urn with replacement only $m$ times when $m<n$? What about $m>n$?

- Consider drawing $n$ labelled orbs from an urn with replacement. How many ways can you do this? Without replacement?
````

Now that we have some practice with combinations and permutations, let's get some practice with combinatorial proofs and show how they are different from non-combinatorial proofs.

````{prf:question}
Use a combinatorial proof to show that $P(n,k)=P(k,k)C(n,k)$.
````
````{prf:proof} A Combinatorial Proof
- **Identify Problem**: How many ways are there to arrange $k$ objects
   from a set of $n$ objects?
- **LHS**: By definition, $P(n,k)$ counts this.
- **RHS**: $C(n,k)$ counts the number of ways to select a subset of
   $k$ objects from a set of $n$. This ignores the order of the
   objects. For each $k$-element selection, there are $P(k,k)$ ways to
   arrange the elements. Thus, by the multiplication principle, there
   are $C(n,k)P(k,k)$ ways to arrange $k$ elements from a set of $n$
   objects.
- **Conclusion**: Therefore, $P(n,k)=P(k,k)C(n,k)$.
````

From the proof above, we can immediately algebraically deduce:
````{prf:theorem}
$$\begin{align}
C(n,k)=\binom{n}{k}=\frac{n!}{k!(n-k)!}
\end{align}$$
````
````{prf:proof} A Non-Combinatorial Proof

$$\begin{align}
P(n,k)=P(k,k)C(n,k)&\implies \frac{n!}{(n-k)!}=\frac{k!}{(k-k)!}C(n,k)\\
&\implies C(n,k)=\frac{n!}{k!(n-k)!}=\binom{n}{k}
\end{align}$$

````

What we've done here is simply use algebra and pre-established relationships to reach our result. We have counted nothing. This is an example of a *non-combinatorial proof*.

Using the above theorem, here is another good example of a non-combinatorial proof:
````{prf:theorem}
$$\begin{aligned}
\binom{n}{k}=\binom{n}{n-k}\end{aligned}$$  
(That is, the number of ways to select $k$ objects from $n$ is equal to the number of ways to select $n-k$ objects from $n$.)
````
````{prf:proof} A Non-Combinatorial Proof

$$\begin{align}
\binom{n}{k}=\frac{n!}{k!(n-k)!}=\frac{n!}{(n-(n-k))!(n-k)!}=\binom{n}{n-k}
\end{align}$$

````
How could we change this into a combinatorial proof?
````{prf:proof} A Combinatorial Proof
- **Identify Problem**: How many ways are there to select $k$ objects
   from a set of $n$?
- **LHS**: By definition, $\binom{n}{k}$ counts the number of ways to
   select $k$ objects from a set of $n$ objects.
- **RHS**: By definition, $\binom{n}{n-k}$ counts the number of ways to select $n-k$ objects from a set of $n$. By including $n-k$ objects in a set, we are creating a set of $k$ excluded objects. If instead, we select the $n-k$ objects from a set of $n$ to exclude, we are including the other $k$ objects. Thus, $\binom{n}{n-k}$ counts the number of ways to select $k$ from a set of $n$.
- **Conclusion**: Therefore, $\binom{n}{k}=\binom{n}{n-k}$.
````
Double counting gives us many ways to count the same thing! A few great examples:

$$\begin{aligned}
\binom{n}{k}&=\binom{n}{n-k}=\frac{n}{n-k}\binom{n-1}{k}\\
&=\frac{n}{k}\binom{n-1}{k-1}=\binom{n-1}{k}+\binom{n-1}{k-1}
\end{aligned}$$

## Summary
What we've covered here:
- something