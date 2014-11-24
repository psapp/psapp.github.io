---
layout: post
title:  "Haskabelle and character widths"
date:   2014-11-24 01:10:00
categories: haskabelle isabelle
---

Today's joy with tooling is this obvious bug with Haskabelle.

Isabelle's `char` type is explicitly 8 bits (it literally is an enumeration of every possible pair of 4 bit nibbles). Haskell's `Char` type is explicitly 32 bits. There's a direct translation with no attempt to consider this, so for a proof to be valid you'd need a solid precondition that everything going in is 8 bit, and you'd need to know there's no mutation in your code that would convert an codepoint that sits in 0-255 to something that lies outside it. (You should be right for 0-127, but if you take an interesting code-page for 128-255 and you want to, say, correctly upcase something, all bets are off.) 

So yeah, that's a thing.
