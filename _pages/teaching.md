---
layout: page
permalink: /capstone/
title: Hybrid Search System
description: A description of my Capstone Project for NYU's Archives and Public History MA Program.
nav: true
nav_order: 6
---
{% include figure.liquid path="assets/img/hybrid-search.jpg" class="img-fluid rounded z-depth-1" %}

Most online archives and digital collections use a traditional keyword search that only finds exact word matches. However, users often have a concept or idea in mind that they want to explore, and may not know the exact words used in the archival records - making traditional keyword searches frustrating.

My Hybrid Search System aims to mitigate this issue by combining a semantic search (that understands the contextual meaning of the query) with a keyword search, in the hopes that it will increase the accessibility and discoverability of archival records.
                           
Here is how it works:

**Semantic Search**  
Using a transformer encoder model, the query is converted into a numerical representation (an embedding) that captures its *meaning*. This is compared against pre-computed embeddings for every record in the database, allowing the system to find conceptually related results even when the exact words don't match.
                            
**Keyword Search (BM25)**  
A traditional keyword scoring algorithm ranks records based on how well their text matches the specific terms in the query. This ensures that precise term matches are still valued.
                           
**Hybrid Scoring**  
The semantic and keyword scores are combined into a single hybrid score, balancing meaning-based relevance with exact-match precision.
                            
**Reranking**  
The top candidates from the hybrid scoring step are passed through a cross-encoder reranker, which is a powerful transformer model that reads the query and each candidate record together to produce a refined relevance score. The final ranking is based on a weighted combination of the reranker score and the hybrid score.
                            
This multi-stage approach captures both the *intent* behind the query and the *specific terms* used, producing more relevant results than either method alone.

*This project is currently under closed beta testing to ensure data privacy. To request access, please contact prithvi.dineshchandra@gmail.com or pdc307@nyu.edu*
