---
title: CMPRSD - What?
description: What is it?
pubDate: Apr 6 2024
heroImage: /blog-placeholder-3.jpg
tags:
     - Rust
     - CMPRSD
categories:
     - Published 
---

CMPRSD is, as the name hints, a project to implement compression algorithms.
Indeed COMPRESSED=>CMPRSD, the name has been compressed with loss. 

But why start a project on compression? Well, I wanted to start working on something in my free time but I did not know what to choose. I chose to retrospectively look back at the classes at university that I was the most fond of.
I came up with the following list : 
- Information Theory
- Computational geometry
- Game theory/Probabilistic algorithms
- Algorithms for Big Data
- (Introduction to) Cryptography 

You can expect at some points for the other subjects to be explored too. The next one should be a follow-up on my master thesis on polygon triangulation on GPU, but this time better executed. 

I know, currently, only one algorithm is implemented, but I already have quite a roadmap planned out.
- Lossless compression (Huffman, [BWT](https://en.wikipedia.org/wiki/Burrows%E2%80%93Wheeler_transform), LZ77/78)
- Lossy compression (images, audio... )
- adaptive compression
- Streaming compression
- Error Resilient
- ...

I do not think of this project or any projects that I will start, as a project with a start and a clear end.
The idea is to have multiple *"playgrounds of interest"* where I can explore, extend, and optimize. They are also opportunities to learn about test frameworks, benchmarks, CI/CD in different languages. 

For this project, I chose to use Rust. I have always thought of this language and the promises it makes as interesting.
I also have some acquaintance with Haskell and I was quite fond of the way you have to think of your code as maps, filters, folds, and higher-order procedures. 

So far it has been going well. A few fights with the borrow checker, or using the heap using ([Box](https://doc.rust-lang.org/std/boxed/struct.Box.html)), but that's it. 
It is also really enjoyable with modern language that they directly come with test, bench, and documentation frameworks.  It allows me at the beginning of a project to spend more time coding the tests and benches than setting them up.

What are the next steps?
- Regarding compression algorithms, it will be to implement [BWT](https://en.wikipedia.org/wiki/Burrows%E2%80%93Wheeler_transform) followed by [LZ77](https://en.wikipedia.org/wiki/LZ77_and_LZ78). Having Huffman and  LZ77 will enable me to implement [DEFLATE](https://en.wikipedia.org/wiki/Deflate). 
- On a more Dev-Ops side, I will need to have a report system. Currently, I already have a benchmark page. But regarding compression algorithms, I would also like to have a page reporting compression efficiency and comparisons. 
- Then on a more Rust side, I would like to add more genericity. For example currently, when I manipulate bits I work on a byte byte-by-byte basis. But I would like for my byte manipulation code to work with u8, u16, ...  in search of what would be the the best in terms of performance.
- Finally, something that I will do for all my projects is to compile the code to WASM to have it exposed in a sample on my website. For example, text can be inputted and the compressed data can be downloaded or interacted with. Not only do I think that providing WASM bindings is important knowledge to have as different languages can have different limitations/workflow. But it's also nice to know that it might increase the number of people who will use my code. 


See you soon for more entries!