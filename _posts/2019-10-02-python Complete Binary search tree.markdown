---
layout: post
title:  "python - Complete Binary Search Tree"
date:   2019-10-02
categories: programming
tags: algorithm
---
# Complete Binary Search Tree
이진 탐색 트리의 연산은 간단히 구현된다. 하지만 만약 완전 이진 트리의 특성과 이진 탐색트리의 특성이 합쳐진 완전 이진 탐색 트리는 어떻게 만들어야 할까.
<br>

가장 많이 고민했던 부분은 바로 완전 이진 트리를 구현하는 부분이다. 먼저 특성들을 살펴보겠다.
<br>

- Complete binary tree
  - 높이가 $k$일 때 레벨 $1$부터 $k-1$까지는 노드가 다 채워져있고, 마지막 레벨 $k$에서는 <i>왼쪽부터 오른쪽으로 노드가 순서대로 채워져야</i>한다.

- Binary search tree
  - 모든 노드의 키는 유일하다.
  - 왼쪽 서브 트리의 키들은 루트의 키보다 작다.
  - 오른쪽 서브 트리의 키들은 루트의 키보다 크다.
  - 왼쪽과 오른쪽 서브 트리도 이진 탐색 트리이다.

'왼쪽부터 오른쪽으로 노드가 순서대로 채워져야'하기 때문에 추가할 노드를 선정하는데 꽤 많은 고민을 했다.
<br>

예시(이진 탐색)
<br>
<details>
<summary> 문제 보기(클릭) </summary>
<div markdown = "1">
1부터 N까지의 자연수를 이진 탐색 트리에 저장하려고 한다.
<br>
이진 탐색 트리는 어떤 경우에도 저장된 값이 왼쪽 서브트리의 루트 <현재 노드 <오른쪽 서브 트리의 루트인 규칙을 만족한다.
<br>
추가나 삭제가 없는 경우에는, 완전 이진 트리가 되도록 만들면 효율적인 이진 탐색 트리를 만들수 있다.
<br>
다음은 1부터 6까지의 숫자를 완전 이진 트리 형태인 이진 탐색 트리에 저장한 경우이다.
<br>
완전 이진 트리의 노드 번호는 루트를 1번으로 하고 아래로 내려가면서 왼쪽에서 오른쪽 순으로 증가한다.
<br>
N이 주어졌을 때 완전 이진 트리로 만든 이진 탐색 트리의 루트에 저장된 값과, N/2번 노드(N이 홀수인 경우 소수점 버림)에 저장된 값을 출력하는 프로그램을 만드시오.
<br>
[입력]
<br>
첫 줄에 테스트케이스의 수 T가 주어진다. 1<=T<=50
<br>
다음 줄부터 테스트 케이스의 별로 N이 주어진다. 1<=N<=1000
<br>
[출력]
<br>
각 줄마다 "#T" (T는 테스트 케이스 번호)를 출력한 뒤, 답을 출력한다.
<br>
[입력]<br>
3<br>
6<br>
8<br>
15<br>
[출력]<br>
\#1 4 6<br>
\#2 5 2<br>
\#3 8 14<br>

_문제 출처 : [SW Expert Academy](https://swexpertacademy.com/main/learn/course/subjectDetail.do?courseId=AVuPDN86AAXw5UW6&subjectId=AWOVJ-_6qfsDFAWg&&#)_
</div>
</details>
<br>

```python
# T = int(input())

f = open("cases.txt", "r")
T = int(f.readline())

import queue

class Node:
    def __init__(self, key):
        self.key = key
        self.left = None
        self.right = None
        self.p = None

class BinarySearchTree:
    def __init__(self):
        self.root = None
        self.count = 0

    def insertion(self, z):
        y = None
        x = self.root
        while x != None:
            y = x
            if z.key < x.key:
                x = x.left
            else:
                x = x.right
        z.p = y
        if y == None:
            self.root = z
        elif z.key < y.key:
            y.left = z
        else:
            y.right = z

    def buildTree(self, start, end):
        if start > end:
            return
        if start == end:
            self.insertion(Node(end))
            self.count += 1
            return
        count = 0
        pivot = 0
        while True:
            if (end-start)-(2**count-1) <= (2**(count+1)-1):
                if (end-start)-(2**count-1) <= (2**count-1):
                    pivot = start + (2**count-1)
                else:
                    pivot = end - (2**count-1)
                break
            count += 1
        # print(pivot)
        self.insertion(Node(pivot))
        self.count += 1
        if start < end:
            self.buildTree(start, pivot-1)
            self.buildTree(pivot+1, end)
        return


    def BFS_by_index(self, index):

        if index == 0:
            return 0

        tmp = []

        visited = [0]*self.count
        q = queue.Queue()
        q.put(self.root)
        idx = 0
        while not q.empty():
            t = q.get_nowait()
            tmp.append(t.key)
            idx += 1
            if idx == index:
                return t.key
            if not visited[t.key-1]:
                visited[t.key - 1] = True
            for node in [t.left, t.right]:
                if node == None:
                    continue
                if not visited[node.key-1]:
                    q.put_nowait(node)
        # print(tmp)

for case in range(1, T + 1):

    N = int(f.readline())

    # print("num : ", N)

    bst = BinarySearchTree()

    bst.buildTree(1, N)

    count = 0
    ans1 = 0
    while True:
        if (N-1) - (2 ** count - 1) <= (2 ** (count + 1) - 1):
            if (N-1) - (2 ** count - 1) <= (2 ** count - 1):
                ans1 = 1 + (2 ** count - 1)
            else:
                ans1 = N - (2 ** count - 1)
            break
        count += 1
    ans2 = bst.BFS_by_index(N//2)

    if N == 1:
        ans1, ans2 = 1, 0

    print("#%d"%case, ans1, ans2)

f.close()
```
