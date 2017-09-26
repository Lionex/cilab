# Natural Language Processing and LLNL

**Brian Bartoldson**

_Note_: LLNL is the Lawrence Livermore National Laboratory, which focuses on technology and information that could lead to the proliferation of conflicts, with special focus on nuclear non-proliferation.

## Motivation

LLNL wants to help analysts gain insights on large databases of information using advanced semantic search instead of simply using exact string matches.  To keep track of people with nuclear physics knowledge, they wanted to devise a semantic search-engine to see who has what knowledge, and track them.

> Brian is aware of how creepy it sounds.

## Overview

Using the word2vec framework, Brian took academics' home-pages and converted them to vector space to embed them and perform a semantic search using positive and negative keywords.  The pipeline was to take homepages, run them through deep learning black magic, and run a flask server that allows you to search through the homepages.

## Pipeline

1. Scrape web-pages
2. Use a deep convlutional neural network to build vector representations of words that encode their semantics
3. 

## History of Natural Language Processing

_Initially_, machine translation used a set of rigid rules which were esentially like regular expressions.  These formalized rules are hard to scale, and fall very easily under the curse of dimensionality.

_In the late 1980s_, we stumbled on the idea that the semantics of words depends on their probability distributions.  In other words, if we have a sequence of `n` words,

_In the 2000s_, Bengio realied we could build _distributed_ representations of word meanings.  We first build a co-occurance matrix of which words relate to othe words.  This allows us to understand how similar words are based on values in the vector.  Performing a single value composition on the co-occurance matrix for each word can build a low-rank, simplified representation that captures much of the information in the original matrix.

