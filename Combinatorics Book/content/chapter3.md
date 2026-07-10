# Chapter 3: Introduction to Counting Techniques

### Warmup

````{prf:question}
   :label:chapter3warmup
Physics 533 and Math 325 occur at the same time (12:10-1PM MWF). Phys
533 has 5 people enrolled while Math 325 has 21.
1. How many people are in Math 325 or Physics 533 from 12:10-1 MWF?
2. How many people are in Math 325 and Physics 533 from 12:10-1 MWF?

````

This may seem immediately obvious to some, but this highlights key
counting principles used in combinatorics.

> **Answer:**
>
> 1. There are 21 people in Math 325. There are 5 in Phys 533. So, there
>    are 21+5 in either during the class period.
> 2. Nobody can be in two places at once, so there must be zero people in
>    both classrooms during the class period.

This is a nice set up. We know the set of students in 325 is completely
separate from the set of students in 533. If we use set theoretic
language, the set of students in 325 is *disjoint* from the set of
students in 533. More on this later.  
For now, consider yet another problem:

````{prf:question}
How many ways are there to flip a coin then a six sided dice? More
generally, rolling an $m$ sided dice then an $n$ sided dice?

````

You might note that my first roll *does not affect* my second roll. They
are independent! Intuitively, if I roll heads, I have the opportunity to
roll 1-6 on the dice. Likewise if roll tails. As such:

> **Answer:**
> There are 2 options for my first roll. Since each roll is independent,
> there are 6 options for my second roll. So, there must be $2\cdot 6=12$
> ways to do this. More generally, since each roll is independent, there
> are $m\cdot n$ ways to do this with an $m$ sided dice and an $n$ sided
> dice.

## More Set Theory

````{prf:definition} Subset
Let $B$ be some set. Another set $A$ is a *subset* of $B$ if every
element of $A$ is an element of $B$ (for every $a\in A$, $a\in B$). We
denote this relationship by $A\subseteq B$ if $A$ could equal $B$
itself. If $A$ cannot equal $B$, we write $A\subset B$.
````

````{prf:definition} Set Complement
Let $A\subseteq S$. The *complement* of $A$ with respect to $S$,
$A^C=S\setminus A$, is the set of elements in $S$ that are not in $A$
($A^C=\{s\in S|s\notin A\}$). The complement of $S$ with respect to
itself, $S^C=S\setminus S$, is the set with zero elements,
$\emptyset=\{\}$.

````

We can think of the set complement $S\setminus A$ as considering all the
elements of $S$ that are not in $A$. If there are no such elements (i.e.
$A\nsubseteq S$), $S\setminus A$ is $\emptyset$. For example, let $A=\{$integers between 28 and 352 divisible by 3$\}$ and $S=\{$integers between 28 and 352 inclusive$\}$. Then:

- $A\subset S$
- $A^C=S\setminus A=\{$integers between 28 and 352 not divisible by 3}

Note that the choice of $S$ is important. If $S=\mathbb{Z}$ (the set of all integers), then $A^C$ in the previous example would become the set of
*all* integers excluding only integers between 28 and 352 that are
divisible by 3.

````{prf:question}
Let $A\subseteq S$. Is the function $f(A)=A^C$ a bijection? If so, what
is $f^{-1}$?
````

> **Answer:**
>$f$ assigns subset $A$ to its complement $A^C=S\setminus A$. Let us say $f(A)=A^C=B$.
> - By the definition of a set's complement, $B$ contains every element
   of $S$ that is not in $A$. Likewise, $A$ contains every element of
   $S$ that is not in $B$.
> - In other words, $A^C=B$ *and* $A=B^C$.
> - So, $f^{-1}(B)=B^C$. Hence, $f^{-1}$ exists and $f$ is a bijection!

This is a nice property. We can use this property to enumerate all sorts of things. For example, consider the problem of enumerating $k$-element
subsets of $S=\{1,2,3,4,\dots, n\}$ ($k<n$).

- Let $A$ be the set of all $k$-elements subsets $A_i\subset S$.
   Moreover, let $B$ be the set of all the complements of elements in
   $A$.
- Then for each $A_i$, there is some set $B_i$ such that
   $f(A_i)=A_i^C=B_i\subset S$ of size $n-k$.
- Since $f(A_i)=A_i^C$ is a bijection, the set of all $k$-element
   subsets, $A$, is the same size as the set of all ($n-k$)-element
   subsets, $B$. That is, $|A|=|B|$.

We will talk about what the actual sizes $|A|$ and $|B|$ later.

````{prf:definition} Union
The *union* of two sets $A$ and $B$, denoted $A\cup B$, is the set of
all elements in $A$ or $B$ ($A\cup B=\{x|x\in A$ or $x\in B$}).
````

````{prf:definition} Intersection & Disjointness
The *intersection* of two sets $A$ and $B$, denoted $A\cap B$, is the
set of all elements in $A$ and $B$ ($A\cap B=\{x|x\in A$ and $x\in B$}). If the intersection between sets $A$ and $B$ is empty, denoted
$A\cap B=\emptyset$, we say $A$ and $B$ are *disjoint*.
````


````{prf:example}
Let $A=\{$the set of students in Math 325$\}$ and $B=\{$the set of
students in Physics 533$\}$.

- $A\cup B=\{$the set of students in either couse$\}$
- $A\cap B=\emptyset$ since now student is in both classes
````

## Addition & Multiplication Principle

Thinking back to the initial problem of this chapter
{prf:ref}`chapter3warmup`, we could simply add the number of people in 325
and 533 to get the total number *since no student is in both classes*.
This principle of complete separation allowing simple addition can be
formalized:
````{prf:theorem}
If $A\cap B=\emptyset$, $|A\cup B|=|A|+|B|$.  
More generally, if $A_i\cap A_j=\emptyset$ for all $i\neq j$ and
$1\leq i,j\leq n$, then
$|A_1\cup A_2\cup \cdots \cup A_n|=|A_1|+|A_2|+\cdots +|A_n|$.
````

Let $A\times B$ be the set of ordered pairs $(a,b)$ where $a\in A$ and
$b\in B$.

````{prf:theorem}
Let $S=A\times B$. Then, $|S|=|A\times B|=|A|\cdot|B|$.  
More generally, let $S=A_1\times A_2\times \cdots \times A_n$. Then,
$|S|=|A_1\times A_2\times \cdots \times A_n|=|A_1||A_2|\cdots|A_n|$
````

````{prf:example}
From warmup problem 2, let $A=\{H,T\}$ be the results from flipping a
coin and $B=\{1,2,3,4,5,6\}$ be the results from rolling the six-sided
dice. Then,

$$A\times B=\{(H,1),(H,2),(H,3),\dots,(T,5),(T,6)\}$$

and $|S|=|A\times B|=|A||B|=2\cdot 6=12$.
````

### (In)dependence

Note that the *independence* of warmup problem 2 is important. Flipping
a coin *has no impact* on the rolling of the dice. Consider a different
problem:

````{prf:question}
There are four orbs labelled $A,B,C,D$ in an urn. You will draw from the
urn four times. For each draw, you take a single orb out, write down its
label, and replace it in the urn. How many possible label sequences
could you write down?
````

> **Answer:**
>- Let $A_1, A_2, A_3,$ and $A_4$ be the sets of possible draws on draw 1, 2, 3, and 4 respectively and $S$ be the set of possible label sequences you could write down.
>- Since all four balls in the urn before you draw first, $A_1=\{A,B,C,D\}$.
>- Moreover, since you placed the orb you drew back into the urn, you have a chance to draw any of the four orbs again: $A_2=\{A,B,C,D\}$.
>- Likewise with $A_3$ and $A_4$.
>- Thus, the total possible label sequences there are is: $|S|=|A_1\times A_2\times A_3\times A_4|=|A_1||A_2||A_3||A_4|=4^4=256$.

Consider a small change to your process:

````{prf:question}
You really like writing down labels, so you continue with your setup
from the previous problem. However, this time instead of replacing the
orb after drawing it, you set it to the side. You then draw another orb
and set it next to the previously drawn orb. You repeat this process
until there are no orbs left. Then, you write down the sequence of
labels you see. How many possible label sequences could you see?
````

> **Answer:**
>- Let $B_1, B_2, B_3,$ and $B_4$ be the sets of possible draws on draw
   1, 2, 3, and 4 respectively and $T$ be the set of possible label
   sequences you could write down.
>- Since all four balls in the urn before you draw first, $|B_1|=4$.
>- Whatever you drew, it stays outside of the urn. Since there are 3
   orbs left, you have 3 options for your next draw: $|B_2|=3$.
>- Continuing on, you have taken yet another option for your third draw
   away: $|B_3|=2$.
>- Lastly, since you drew one of the two remaining orbs, that leaves
   one left for your final draw $|B_4|=1$.
>- Thus,
   $|T|=|B_1\times B_2\times B_3\times B_4|=|B_1||B_2||B_3||B_4|=4\cdot 3\cdot 2\cdot 1=24$.

So, replacing the orbs every time gave us a count of 256 while leaving
them out every time gave us a count of 24. What happened? One way to
think of this is that by replacing the orbs, you have allowed for
*repetitions* to exist in your set $S$ (e.g. by drawing $A$ then $A$
then $C$ then $A$). Contrarily, by leaving the orbs out after drawing,
you remove the ability to have repeats. As such, you remove every
element in $S$ that has any repeat labels to obtain a new set $T$, the
set of label sequences with *distinct* labels.

````{prf:question} To Ponder
- Let $S$ and $T$ be defined as in the above problem. What is
$T^C=S\setminus T$? How big is $T^C$ in this case?

- Let $S$ be defined as in the above problem. How many label sequences
have only 2 repeats? i.e. sequences like $(A,A,B,C)$ or $(D,A,C,D)$.

- Consider drawing $n$ labelled orbs from an urn with replacement. How
many ways can you do this? Without replacement?
````

## Summary

What we've covered here:

- A function $f:A\to B$ having an inverse function $f^{-1}:B\to A$
   means $|A|=|B|$.
- Set complements, unions, and intersections.
- Addition principle: the size of a union of disjoint sets is the sum
   of their sizes.
- Multiplication principle: the size of a product of two sets is the
   product of their sizes.
- The difference between counting with dependence versus without.