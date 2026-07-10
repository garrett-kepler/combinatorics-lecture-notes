---
author:
  - Garrett J. Kepler
date: Updated 2.4.26
title: 'Lecture Notes on Combinatorics: Draft'
---

# Chapter 1: What is Combinatorics?

One great property of the field of combinatorics is most people have
already encountered combinatorial questions in their own life.

*Considering the optimal path we should take to get groceries and visit
the coffee shop then return home. Now that we have the groceries,
figuring out which set of dishes we can cook for the party when we've
invited a vegetarian, a non-vegetarian, and someone allergic to peanuts.
Now that we know what to cook, determining the best drinks paired with
which dishes.*

As simple of an example party planning is, we have described three
combinatorial problems already: minimal path, dish enumeration, and
drink/dish combinations.  
Many of the questions we ask in combinatorics focus on counting of some
sort.

- Enumeration: How many ways$\dots$?
- Existence: Does there exist$\dots$?
- Extremal: What is the largest/smallest possible$\dots$?
- Expectation: What is the expected number of$\dots$?

## Warmup

````{prf:question}
1. How many ways are there to assign 3 students 3 distinct Math 325 projects? 4 students 4 distinct projects? $n$ students $n$ distinct projects?
2. How many people must attend the first day of lecture in Math 325 to guarantee 2 people either both have met before or both have not met before?
3. How many people must attend the first day of lecture in Math 325 to guarantee 3 people either have all met before or have all not met before?
````


These preliminary warmup problems are classic combinatorial questions.
The first, a question of enumeration, we may have a straightforward way
to answer already:

> **Answer:**
> Well, we could assign student A project 1. Or, we could assign them
> project 2. Or, we could assign them project 3. That's 3 ways. Okay, for
> student B, we could assign project 1. Or, we could assign them project 2. Or, $\dots~\dots~\dots$ This is exhausting listing them out. I'm bored.

What we are going to learn in this class is methods to avoid this one by
one counting. Instead, we will "count". Rather than assigning a specific
student to a specific project one by one, we'll deal with the collection
of students and the collection of projects in their entirety:

> **Answer:**
> Given a student, we assign them 1 of the 3 projects. Since we want
> distinct assignments, the next student must be assigned one of the other
> 2 projects. Likewise, the final student must be assigned the leftover
> project. Using what we will later refer to as the *multiplication
> principle*, we have $3\cdot 2\cdot 1=6$ ways to do this.

The final two warmups ask questions of guaranteed substructures that we
will discuss later in the Ramsey Theory section.

