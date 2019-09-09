---
layout: post
title:  "python - BFS(Breadth First Search)"
date:   2019-09-09
categories: programming
---
# BFS
BFS!BFS!
<br>
깊이 우선 탐색.
<br>
아래는 pseudocode.
<br>
```
BFS(G, s)
  for each vertex u ∈ V[G] − {s}
    do color[u] ← WHITE
      d[u]←∞
      π[u]← NIL
  color[s] ← GRAY
  d[s] ← 0
  π[s] ← NIL
  Q ← ∅
  ENQUEUE(Q, s)
  while Q not equal to ∅
    do u ← DEQUEUE(Q)
      for each v ∈ Adj[u]
        do if color[v] = WHITE
          then color[v] ← GRAY
            d[v] ← d[u] + 1
            π[v]← u
            ENQUEUE(Q, v)
      color[u] ← BLACK
```
- G : graph
- s : start node(or vertex)
- V[G] : G의 모든 vertexes
- color[u] : u의 색, 'color' array의 u에 해당하는 것
- π[u] : u의 predecesor, 'π' array의 u에 애당하는 것
<br>

이걸 잘 응용해서 쓰면 될거 같다
