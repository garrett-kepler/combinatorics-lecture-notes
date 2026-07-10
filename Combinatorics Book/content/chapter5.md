# Chapter 5: Pigeonhole Principle

## Warmup 
````{prf:question}
There are $n$ married couples waiting at tables around a dance floor.
1. Pairing the $2n$ people up to dance, how many ways are there to select a pair of dance partners?
2. How many people must be on the dance floor to guarantee a married couple is somewhere on the dance floor?
````
> **Answer:**
> 1. This is a case where we would like to use our new notion of combination:
>      - We are selecting 2 people from $2n$ people.
>      - There are $C(2n,2)=\binom{2n}{2}$ ways to do this.
> 2. We want to *guarantee* that a married couple is on the dance floor. If we invite $n$ people to the floor, there is a chance we could have a couple. But, what if invite only one spouse from each couple? Then there is no couple on the floor. Consider this case.
>       - Select one spouse from each married couple to the dance floor. There are now $n$ people ready to dance.
>       - If we invite any one else to the dance floor, we are guaranteed their spouse is on the dance floor.
>       - So, to *guarantee* we have a couple on the dance floor, we need to invite $n+1$ people to the floor.


This is what we call the *pigeonhole principle*. It is an incredible powerful tool:
````{prf:theorem} Pigeonhole Principle: *Simple Form*
If $n+1$ objects are distributed into $n$ boxes, then at least one box
contains two or more objects.
````
````{prf:proof}
If each of the $n$ boxes has at most one object, then the total number of objects is at most $1+1+1+\cdots+1=n$. There is one object not counted. So, there is at least one box with two or more objects.
````

````{prf:example}
Out of Garrett, the Dalai Lama, and Lionel Messi, there are at least two people either inside Garrett's office or outside of Garrett's office.
````

We can also exploit a more general case of the pigeonhole principle when we have potentially more than $n+1$ objects:
````{prf:theorem} Pigeonhole Principle (Strong Form)
Let $q_1,q_2,\dots,q_n$ be positive integers. If 

$$\begin{align}
q_1+q_2+q_3+\cdots+q_n-n+1
\end{align}$$ 

objects are distributed into $n$ boxes, then either the 1st box contains at least $q_1$ objects or the 2nd box contains at least $q_2$ objects,$\dots$, or the $n$th box contains at least $q_n$ objects.
````
````{prf:proof}
Distribute the $q_1+q_2+q_3+\cdots+q_n-n+1$ objects into $n$ boxes. If each $i$th box contains at most $q_i$ objects, then the number of objects in boxes is at most

$$\begin{align}
(q_1-1)+(q_2-1)+\cdots+(q_n-1)&=q_1+q_2+\cdots+q_n-n
\end{align}$$ 

There is an object not counted. So, we can say there is at least one box $i$ with $q_i$ or more objects.
````

````{prf:example}
Out of the 21 students in a class, there are 3 whose birthday lie on the same day of the week.
````

What both the simple form and strong form of the pigeonhole principle say in plain english is: ***distributing too many objects into too few boxes forces overlaps***. 

## The 2nd E: Existence 
Recall the 4 E's of combinatorics:
- Enumeration: How many ways...?
- Existence: Does there exist...?
- Extremal: What is the largest/smallest possible...?
- Expectation: What is the expected number of objects such that...?

We have been covering how to answer questions of enumeration. The pigeonhole principle is our first technique to answer questions of existence!  
For example, we can answer the following existence question using the pigeonhole principle:

````{prf:question}
Consider choosing 101 integers from $S=\{1,2,3,4,\dots, 200\}$. Show that there are two chosen integers such that one divides the other. Hint: try factoring out as many 2's as possible from each term in $S$.
````
````{prf:proof}
Each number in $S=\{1,2,3,4,\dots, 200\}$ is either even or odd. Consider writing each integer $s\in S$ as $s=2^k\cdot t$ where $t$ is odd and $k\geq 0$. Each $t$ comes from the set $T=\{1,3,5,\dots, 199\}$ of size 100. By picking 101 integers from $S$, we are also picking 101 odd factors from $T$. Since 101=100+1 factors are chosen from 100 factors, by the pigeonhole principle, there are two integers chosen from $S$ that share a factor from $T$. That is, from the chosen integers of $S$, there are two, say $s_1$ and $s_2$, such that $s_1=2^m\cdot t$ and $s_2=2^n\cdot t$. Either $m>n$ and $s_2$ divides $s_1$ or $n>m$ and $s_1$ divides $s_2$. As such, there are two integers such that one divides the other.
````

This problem exemplifies why the pigeonhole principle is so useful:
- How many ways are there to select 101 integers from $S=\{1,2,3,\dots, 200\}$? $C(200,101)=\binom{200}{101}>10^{57}$.
- This is an insanely large number. More than the number of atoms in 1 million Earths (Earth is about $\approx 10^{51}$ atoms).
- But, without going through every single possible subset choice, we know something about *every single one of these choices*. Namely, that there must be two numbers in each such that one divides the other.

\centering
=\[font=\] (5,11.75) to\[short, -o\] (5,11.75) ; (4.75,11.5) to\[short,
-o\] (4.75,11.5) ; (8.75,11.5) rectangle (8.75,11.5); (8.5,11.5)
rectangle (9.5,10.5); (9,10.5) rectangle (8.75,10.5); (9.25,8.75)
rectangle (9.25,8.75); (8.5,9.75) rectangle (9.5,8.75); (9,8.75)
rectangle (9,8.75); (9.5,11) rectangle (9.5,10.75); (9.5,11) rectangle
(9.5,10.5); (8.5,8) rectangle (9.5,7); (8.5,13) rectangle (9.5,12);
(tikzmaker) \[shift=(0, -0.125)\] at (3,8.75) ![Simple example of the
pigeonhole principle (using
pigeons!)[]{label="fig:placeholder"}](math 325/lecture notes/week 3/pigeon.jpg "fig:"){#fig:placeholder
width="0cm"}; (tikzmaker) \[shift=(.75, -0.75)\] at (3.5,7.75) ![Simple
example of the pigeonhole principle (using
pigeons!)[]{label="fig:placeholder"}](math 325/lecture notes/week 3/pigeon.jpg "fig:"){#fig:placeholder
width="1.5cm"}; (tikzmaker) \[shift=(-0.75, --0.75)\] at (5,12.75)
![Simple example of the pigeonhole principle (using
pigeons!)[]{label="fig:placeholder"}](math 325/lecture notes/week 3/pigeon.jpg "fig:"){#fig:placeholder
width="1.5cm"}; (tikzmaker) \[shift=(0.75, -0.75)\] at (3.5,9.25)
![Simple example of the pigeonhole principle (using
pigeons!)[]{label="fig:placeholder"}](math 325/lecture notes/week 3/pigeon.jpg "fig:"){#fig:placeholder
width="1.5cm"}; (tikzmaker) \[shift=(-0.65, --0.75)\] at (5,11.25)
![Simple example of the pigeonhole principle (using
pigeons!)[]{label="fig:placeholder"}](math 325/lecture notes/week 3/pigeon.jpg "fig:"){#fig:placeholder
width="1.5cm"}; (tikzmaker) \[shift=(0.75, -0.75)\] at (3.5,11) ![Simple
example of the pigeonhole principle (using
pigeons!)[]{label="fig:placeholder"}](math 325/lecture notes/week 3/pigeon.jpg "fig:"){#fig:placeholder
width="1.5cm"}; (4.75,13.5) -- (8.25,12.5); (5,12) -- (8.25,11);
(5,10.25) -- (8.25,9.25); (4.75,8.75) -- (8.25,7.5); (5.25,6.75) --
(8.25,7.25); at (9,12.5) 1; at (9,11) 2; at (9,7.5) 4; at (9,9.25) 3;


To end this section, let's work through a few problems:

````{prf:question} To Ponder
Pretend we are going to group the 21 combinatorics students into 4 study groups. Each group will have a leader.
- How many ways can we select the leaders?
- Pretend we number the groups 1,2,3, and 4. How many ways can we assign leaders to groups?
- Use the pigeonhole principle to show that there is a group with at least 2 people.
- Use the pigeonhole principle to show that there is a group with at least 6 people.
````

## Summary

What we've covered here:
- something