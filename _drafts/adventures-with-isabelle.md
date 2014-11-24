---
layout: post
title:  "Adventures with Isabelle"
date:   2014-11-24 00:07:59
categories: isabelle
---

Isabelle is an interesting piece of software.

NICTA has had great success using it to prove the correctness of seL4, although they did build several very nifty tools along the way (e.g. Autocorres).

Isabelle does not seem to be particularly great at string processing, however. Let us count the ways:

The issue with upper/lower case is mostly that Isabelle does not like to mix wildcard with non-wildcard arguments: if you have a case for `a` and `_` that return different things, it will get horribly confused. You'd sort of expect that if the case for `a` is above the `_`, that the `a` would match and processing would stop (from e.g. a Haskell point of view by analogy with `otherwise`). Apparently not.

Code generation and code interpretation is terrible.

Obvious bug with Haskabelle: Isabelle's `char` type is explicitly 8 bits. Haskell's `Char` type is explicitly 32 bits. There's a direct translation with no attempt to consider this, so for a proof to be valid you'd need a solid precondition that everything going in is 8 bit, and you'd need to know there's no mutation in your code that would convert an codepoint that sits in 0-255 to something that lies outside it. (You should be right for 0-127, but if you take an interesting code-page for 128-255 and you want to, say, correctly upcase something, all bets are off.) So yeah, that's a thing.
