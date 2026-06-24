---
title: "Symbolic AI (1): Introduction and example"
date: 2026-06-23
draft: true
# cover:
#     image: /img/coverImg/lovely2.jpg
#     alt: An image of lovely flowers
series: ["neural - symbolic AI"]
tags: ["AI"]
---
This post belong to series `neural - symbolic AI`

Materials: [Notion page for GOAI](https://www.notion.so/Symbolic-AI-3827d3e8b76f8066bc81c7117132cc10?source=copy_link)

---


## What is symbolic AI?
Symbolic Artificial Intelligence (A Good OldFashioned AI - GOAI) is the term for the collection of all methods in artificial intelligence research that are based on high-level "symbolic" (human-readable) representations of problems, logic and search. [See Stefan Woltran slides](https://caiml.org/dighum/summerschool2023/program/stefan-woltran-symbolic-ai.pdf)

Symbolic AI is a whole difference approach from Machine Learning, which harnessing the power of data and statistical methods, but using knowledge and logic based instead.

### Example: Cyc's Knowledge Base, Inference Engines
The best example for symbolic AI is CYC. This is the definition of CYC in their homepage:

> CYC is Machine Reasoning AI that uses codified human common sense and knowledge (not patterns and statistics) for human-like cognitive processing 

[CYC home page](https://cyc.com/)

### Example: PROLOG program with family relationship

```prolog
% Knowledge base
child(oscar, karen, frank). 
child(mary, karen, frank). 
child(eve, anne, oscar). 
child(henry, anne, oscar). 
child(isolde, anne, oscar). 
child(clyde, mary, oscarb). 

% Rules
child(X, Z, Y) :- child(X, Y, Z). 

descendant(X, Y) :- child(X, Y, Z). 
descendant(X, Y) :- child(X, U, V), descendant(U, Y).
```
This is a program writen by PROLOG language. The first part is knowledge base which help the computer make inferences, for example `child(oscar, karen, frank)` means oscar is karen and frank' child. The second part is the logic rule, e.g `descendant(X, Y) :- child(X, Y, Z)` means that X is Y desdendant if X is childe of Y and another guy Z. 

We can make query as below:
```prolog
?- descendant(X,Y).  

X = oscar 
Y = karen 

Yes
```

### Example: AlphaGo

## Symbolic vs Subsymbolic AI
Sybsymbolic AI or Connectionism, on the other hand uses statistical and data - driven methods: Machine Learning and Deep Learning techniques.

| Symbolic AI | Subsymbolic AI |
| :--- | :--- |
| Rule-driven | Data-driven |
| Explicit representation | Implicit representation |
| Logic and search | Statistics |
| Explainable results | Black-Box |
| Combinatorial Explosion | Training on Huge Datasets |
| Heuristics / structural features | Parallelisation |
| Applications:<br>Planning, Expert Systems, Configuration, Scheduling, Logical Reasoning, Games, ... | Applications:<br>Clustering, Image/Music/... Recognition, Generative AI, Recommender Systems, Games ... |

[Ref: Stefan Woltran](https://caiml.org/dighum/summerschool2023/program/stefan-woltran-symbolic-ai.pdf)

## Neural - Symbolic AI


--- 
Mọi góp ý về bài viết qua xin được gửi qua email: uyennguyen.nbu@gmail.com




