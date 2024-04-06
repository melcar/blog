---
title: BWT algorithm
description: What is it?
pubDate: Apr 6 2024
heroImage: /blog-placeholder-3.jpg
tags:
     - Rust
     - CMPRSD
categories:
     - Draft 
--- 

WHAT is BWT?

Input: Text $T: |T| = N \text{ and } T \subset\text{ where } T \subset C \times N$ with
$C = \{c1,c2, C3. \}$ the set of all possible characters
and $N = \{ 0, 1, ... n-1\}$ the indices of all the characters making up the text $T$. And $ b \in N \forall x \in T | x=(a,b)$ all elements of $N$ present in T are there only once.

Output: $(i, E)$ where $i \in \{0,..., n-1\}$
and $E: |E| = |T| \text{ and }$ 

step 1= generates an n by n grid where each line is the original shifted by the index of the row it is in.

output : $G:=\{(t, i)\}$ where
$i \in \{o, ... n-1\}$ and same constraint as above for uniqueness
and $t \in \{(a, b+i \mod n) \forall x=(a,b) \in T\}$


