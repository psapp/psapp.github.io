---
layout: post
title:  "Learning Isabelle"
date:   2014-11-24 00:07:59
categories: isabelle
---

Firstly, what do we mean by saying that something is "proven correct"?

Take an implementation of the `reverse` function. You might say that the a good test is `reverse(reverse(list)) = list`. In a C/Python/Haskell/whatever impementation, we'd test this with a set of fixed strings, or maybe QuickCheck or even a fuzzer; but whatever way we do it, it's not exhaustive: this testing can't prove that statement holds for all inputs.

Isabelle provides a tool to enable us to prove that this propery holds for all inputs. That's not particularly exciting for `reverse(reverse(list)) = list`, but it does become more interesting if you can prove more ambitious statements. See for example seL4, which proved an entire operating system kernel correct.

Now, saying that something is "proven correct" gives rise to the question "What is correct?". That's actually a really difficult question to answer: what behaviour is correct, and what questions/tests can you apply to the algorithm to be convinced of that? It helps to have a spec to begin with, but then you still need to turn the loose written spec into a set of formal, provable properties. That's non-trivial.

With that out of the way, let's turn to Isabelle. Isabelle is powerful, but the learning curve is extraordinarily steep. I am still very much in the foothills, so here are some pointers from my limited vantage point:

 * Start with functional programming. If you are only comfortable with imperative languages, your life will be much much harder.
 
 * If you've programmed for a while, you might be the sort of person who likes to learn just enough syntax to get things to compile/interpret and then implement whatever you set out to implement. This has worked for me in Python, Ruby and even Haskell, but it really doesn't work for Isabelle. 
 
  * Documentation sucks. Try the supplied Tutorial as a good start. Try the exercises [online](http://isabelle.in.tum.de/exercises/).
 
  * There's two different ways to prove things in Isabelle. Firstly there's the `apply`/`done` method, and then there's Isar (`prove`/`qed`). Isar is apparently better for longer proofs, but the introduction/docs is terrible. I'm still trying to figure it out.
  
  * Don't start by trying to process strings. Process anything other than strings.