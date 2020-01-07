---
layout: post
title:  "python - BFS(Breadth First Search)"
date:   2019-09-10
categories: programming
tags: algorithm
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

![BFS](/images/BFS.png){: width="60%" height="auto" .image-center}

<br>

이걸 잘 응용해서 쓰면 될거 같다
<br>
<br>

응용한 예(노드의 거리)
<br>
<details>
<summary> 문제 보기(클릭) </summary>
<div markdown = "1">
V개의 노드 개수와 방향성이 없는 E개의 간선 정보가 주어진다.
<br>
주어진 출발 노드에서 최소 몇 개의 간선을 지나면 도착 노드에 갈 수 있는지 알아내는 프로그램을 만드시오.
<br>
예를 들어 다음과 같은 그래프에서 1에서 6으로 가는 경우, 두 개의 간선을 지나면 되므로 2를 출력한다.
<br>
노드 번호는 1번부터 존재하며, 노드 중에는 간선으로 연결되지 않은 경우도 있을 수 있다.
<br>

[입력]
<br>
첫 줄에 테스트 케이스 개수 T가 주어진다.  1<=T<=50
<br>
다음 줄부터 테스트 케이스의 첫 줄에 V와 E가 주어진다. 5<=V=50, 4<=E<=1000
<br>
테스트케이스의 둘째 줄부터 E개의 줄에 걸쳐, 간선의 양쪽 노드 번호가 주어진다.
<br>
E개의 줄 이후에는 출발 노드 S와 도착 노드 G가 주어진다.
<br>
[출력]
<br>
각 줄마다 "#T" (T는 테스트 케이스 번호)를 출력한 뒤, 답을 출력한다.
<br>
[입력]<br>
3<br>
6 5<br>
1 4<br>
1 3<br>
2 3<br>
2 5<br>
4 6<br>
1 6<br>
7 4<br>
1 6<br>
2 3<br>
2 6<br>
3 5<br>
1 5<br>
9 9<br>
2 6<br>
4 7<br>
5 7<br>
1 5<br>
2 9<br>
3 9<br>
4 8<br>
5 3<br>
7 8<br>
1 9<br>
[출력]<br>
\#1 2<br>
\#2 4<br>
\#3 3<br>
<br>

_문제 출처 : [SW Expert Academy](https://swexpertacademy.com/main/learn/course/subjectDetail.do?courseId=AVuPDN86AAXw5UW6&subjectId=AWOVIoJqqfYDFAWg#)_
</div>
</details>
<br>

```python
import queue

# T = int(input())

f = open("cases.txt", "r")
T = int(f.readline())

for case in range(1, T + 1):
    V, E = map(int,f.readline().split())
    graph = {}

    for i in range(1, V+1):
        graph[i] = []

    for _ in range(E):
        n1, n2 = map(int, f.readline().split()[:2])
        graph[n1] += [n2]
        graph[n2] += [n1]

    # print(graph)

    S, G = map(int, f.readline().split()[:2])

    q = queue.Queue()
    color = ["w"]*V

    q.put([S, 0])
    color[S-1] = "g"

    find = 0

    # print("strat : ", S, "goal : ", G)

    while not q.empty():

        u = q.get_nowait()

        print(u[0], color)

        for c in graph[u[0]]:
            if c == G:
                find = u[1]+1
                break
            if color[c-1] == "w":
                color[c-1] = "g"
                q.put_nowait([c, u[1]+1])
        color[u[0]-1] = "b"

        if find != 0:
            break

    # print("#%d" % case, find)

f.close()
```


_참조 : Thomas H. Cormen, Charles E. Leiserson, Ronald L. Rivest, Clifford Stein-Introduction to algorithms-The MIT Press (2001)_
