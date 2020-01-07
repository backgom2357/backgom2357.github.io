---
layout: post
title:  "python - Brute-force Search"
date:   2019-10-14
categories: programming
tags: algorithm
---
# Brute-force search
이 무식한 탐색은 그냥 모든 가능한 후보를 확인하는 기법이다. 그냥 컴퓨터에게 모든것을 맡긴다.
<br>

설계하고 실행시키는데는 얼마 안걸리나 결과가 나오기 까지는 시간이 매우 오래 걸릴 수 있다.
<br>

위키 피디아에서 기본 알고리즘을 소개하고 있다.

<div class='box'>
 1. first (P): generate a first candidate solution for P.<br>
 2. next (P, c): generate the next candidate for P after the current one c.<br>
 3. valid (P, c): check whether candidate c is a solution for P.<br>
 4. output (P, c): use the solution c of P as appropriate to the application.<br>
</div>

```
c ← first(P)<br>
while c ≠ Λ do<br>
 if valid(P,c) then output(P, c)<br>
 c ← next(P,c)<br>
end while<br>
```
<I>참조 : [Brute-force search from Wikipedia](https://en.wikipedia.org/wiki/Brute-force_search#Basic_algorithm)</I>
<br><br>



Brute-force search algorithm의 대표적인 알고리즘 3개, Breadth first search, Depth first search, Iterative deepening depth-first search, 을 알아보자.
<br>



# Breath first Search

이건 전에 다뤘으나 인터넷에서 다른 pseudocode를 찾았다.
```
BFS(s_start)
  vector ← s_start
  while vector is not empty do
    next ← pop front from vector
    for each successor s_i of next do
      if s_i is not in CLOSED then
        Add s_i to closed
        Put s_i on the back of vector
      end if
    end for
  end while
```
<br>



# Depth fisrt Search

이름에 맞게 그래프에서 가장 깊은 곳부터 찾는 알고리즘이다.
<br>

현재 위치에서 가장 먼저 탐색된 곳으로 나아간다. 그렇게 나아가서 그 방향의 제일 깊은 곳까지 탐색이 완료되면 'backtrack'해서 남겨진(탐색이 안된)곳을 같은 방식으로 탐색한다.
<br>

빠르게 pseudocode를 보자.
<br>

```
DFS(G)
  for each vertex u ∈ V[G]
    do color[u] ← WHITE
      π[u]← NIL
  time ← 0
  for each vertex u ∈ V[G]
    do if color[u] = WHITE
      then DFS-VISIT(u)

DFS-VISIT(u)
  color[u] ← GRAY               ▷ White vertex u has just been discovered.
  time ← time+1
  d[u] ← time
  for each v ∈ Adj[u]           ▷ Explore edge (u, v).
    do if color[v] = WHITE
      then π[v] ← u
           DFS-VISIT(v)
  color[u] ← BLACK              ▷ Blacken u; it is finished.
  f [u] ← time ← time+1
```
- V[G] : G의 모든 vertexes
- color[u] : u의 색, 'color' array의 u에 해당하는 것
- π[u] : u의 predecesor, 'π' array의 u에 애당하는 것
- d[u] : u의 discovery time
- f[u] : u의 finishing time

![DFS](/images/DFS.png){: width="60%" height="auto" .image-center}

- 다른 버젼의 pseudocode
```
DFS(s_start)
  vector ← s_start
  while vector is not empty do
    next ← pop front from vector
    for each successor si of next do
      Put si on the front of vector
    end for
  end while
```
<br>

위의 pseudocode와 완벽히 부합하지는 않지만 어쨌든 DFS를 사용한 예 2개

<details>
<summary> 5188. 최소합 문제 보기(클릭) </summary>
<div markdown = "1">
그림처럼 NxN 칸에 숫자가 적힌 판이 주어지고, 각 칸에서는 오른쪽이나 아래로만 이동할 수 있다.
<br>
맨 왼쪽 위에서 오른쪽 아래까지 이동할 때, 지나는 칸에 써진 숫자의 합계가 최소가 되도록 움직였다면 이때의 합계가 얼마인지 출력하는 프로그램을 만드시오.
 <br>
그림의 경우 1, 2, 3, 4, 5순으로 움직이고 최소합계는 15가 된다. 가능한 모든 경로에 대해 합을 계산한 다음 최소값을 찾아도 된다.
<br>
[입력]
<br>
첫 줄에 테스트케이스의 수 T가 주어진다. 1<=T<=50
<br>
다음 줄부터 테스트 케이스의 별로 첫 줄에 가로 세로 칸 수 N이 주어지고, 다음 줄부터 N개씩 N개의 줄에 걸쳐 10이하의 자연수가 주어진다. 3<=N<=13
 <br>
[출력]
<br>
각 줄마다 "#T" (T는 테스트 케이스 번호)를 출력한 뒤, 답을 출력한다.<br>
[입력]<br>
3<br>
3<br>
1 2 3<br>
2 3 4<br>
3 4 5<br>
4<br>
2 4 1 3<br>
1 1 7 1<br>
9 1 7 10<br>
5 7 2 4<br>
5<br>
6 7 1 10 2<br>
10 2 7 5 9<br>
9 3 2 9 6<br>
1 6 8 2 9<br>
8 3 8 2 1<br>
[출력]<br>
\#1 15<br>
\#2 18<br>
\#3 33<br>
<br>

_문제 출처 : [SW Expert Academy](https://swexpertacademy.com/main/learn/course/subjectDetail.do?courseId=AVuPDYSqAAbw5UW6&subjectId=AWUYDrI61lYDFAVT)_
</div>
</details>

```python
# T = int(input())

f = open("cases.txt", "r")
T = int(f.readline())

for case in range(1, T + 1):

    N = int(f.readline())

    grid = []

    for _ in range(N):
        grid.append(list(map(int, f.readline().split())))

    x, y = 0, 0

    total = grid[0][0]

    right_count = 2
    down_count = 2

    stack_count = [2]
    stack_coordi = [(x,y)]

    just_visited = (x,y)

    bottom = 20*(N-1)

    ## DFS

    while stack_coordi:

        x, y = stack_coordi[-1][0], stack_coordi[-1][1]

        if x == N-1 and y == N-1:

            if bottom > total:
                bottom = total
            total -= grid[y][x]
            just_visited = stack_coordi.pop()
            x, y = stack_coordi[-1][0], stack_coordi[-1][1]
            stack_count.pop()
            continue

        if x + 1 < N and stack_count[-1] >0 and (x+1,y) != just_visited:
            x += 1
            total += grid[y][x]
            stack_count[-1] -= 1
            stack_coordi.append((x,y))
            if x == N-1:
                stack_count.append(1)
            else:
                stack_count.append(2)
            continue

        if y + 1 < N and stack_count[-1] >0 and (x,y+1) != just_visited:
            y += 1
            total += grid[y][x]
            stack_count[-1] -= 1
            stack_coordi.append((x, y))
            if y == N-1:
                stack_count.append(1)
            else:
                stack_count.append(2)
            continue

        total -= grid[y][x]
        just_visited = stack_coordi.pop()
        stack_count.pop()


    print("#%d" % case, bottom)

f.close()
```

<details>
<summary> 5189. 전자카트 문제 보기(클릭) </summary>
<div markdown = "1">
골프장 관리를 위해 전기 카트로 사무실에서 출발해 각 관리구역을 돌고 다시 사무실로 돌아와야 한다.
<br>
사무실에서 출발해 각 구역을 한 번씩만 방문하고 사무실로 돌아올 때의 최소 배터리 사용량을 구하시오.
<br>
각 구역을 이동할 때의 배터리 사용량은 표로 제공되며, 1번은 사무실을, 2번부터 N번은 관리구역 번호이다.
<br>
두 구역 사이도 갈 때와 올 때의 경사나 통행로가 다를 수 있으므로 배터리 소비량은 다를 수 있다.
<br>
N이 3인 경우 가능한 경로는 1-2-3-1, 1-3-2-1이며 각각의 배터리 소비량은 다음과 같이 계산할 수 있다.
<br>
e[1][2]+e[2][3]+e[3][1] = 18+55+18 = 91
<br>
e[1][3]+e[3][2]+e[2][1] = 34+7+48 = 89
<br>
이 경우 최소 소비량은 89가 된다.
<br>
[입력]
<br>
첫 줄에 테스트케이스의 수 T가 주어진다. 1<=T<=50
<br>
다음 줄부터 테스트 케이스의 별로 첫 줄에 N이 주어지고, 다음 줄부터 N개씩 N개의 줄에 걸쳐 100이하의 자연수가 주어진다. 3<=N<=10
<br>
[출력]
<br>
각 줄마다 "#T" (T는 테스트 케이스 번호)를 출력한 뒤, 답을 출력한다.<br>
[입력]<br>
3<br>
3<br>
1 2 3<br>
2 3 4<br>
3 4 5<br>
4<br>
2 4 1 3<br>
1 1 7 1<br>
9 1 7 10<br>
5 7 2 4<br>
5<br>
6 7 1 10 2<br>
10 2 7 5 9<br>
9 3 2 9 6<br>
1 6 8 2 9<br>
8 3 8 2 1<br>
[출력]<br>
\#1 89<br>
\#2 96<br>
\#3 139<br>
<br>

_문제 출처 : [SW Expert Academy](https://swexpertacademy.com/main/learn/course/subjectDetail.do?courseId=AVuPDYSqAAbw5UW6&subjectId=AWUYDrI61lYDFAVT)_
</div>
</details>

```python
# T = int(input())

f = open("cases.txt", "r")
T = int(f.readline())


def permutations_dfs(index_b4, arr, grid):

    global minimum, total

    if len(arr) == 0:
        total += grid[index_b4][0]
        if total < minimum:
            minimum = total
        total -= grid[index_b4][0]
        return
    for c in arr:
        total += grid[index_b4][c]
        tmp = arr.copy()
        tmp.remove(c)
        permutations_dfs(c, tmp, grid)
        total -= grid[index_b4][c]


for case in range(1, T + 1):
    N = int(f.readline())

    grid = [list(map(int, f.readline().split())) for _ in range(N)]

    minimum = 1000

    total = 0

    permutations_dfs(0, [x for x in range(1, N)], grid)

    print("#%d" % case, minimum)

f.close()
```
<br>

# Iterative Deepening Depth-first Search

DFS를 여러번 실행하는데, 각 search에서는 한정된 깊이까지만 탐색한다.
<br>

Pseudocode는 다음과 같다.
```
DFID(s_start, d)
  for i = 1 ... d do
    LIMITED DFS(s_start, i, 0)
  end for
LIMITED DFS(s, d, d_curr)
  if d_curr ≥ d then
    return
  end if
  for each successor s_i of s do
    LIMITED DFS(s_i, d, d_curr + 1)
  end for
```

속도를 비교하는데는 [difd 속도 비교](https://movingai.com/dfid.html)의 동영상에서 잘 보여주고 있다.
<br>
<br>


<I>참조 : <br>
Thomas H. Cormen, Charles E. Leiserson, Ronald L. Rivest, Clifford Stein-Introduction to algorithms-The MIT Press (2001)<br>
[Nathan Sturtevant - HW #1: Brute Force Search Algorithms Sample Solution](https://www.cs.du.edu/~sturtevant/sas-s12/sample.pdf)
</I>
