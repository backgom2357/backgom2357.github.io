---
layout: post
title:  "python - Heap"
date:   2019-10-02
categories: programming
---
# Heap
Heap은 여러 값들 중 가장 큰 값이나 가장 작은 값을 빠르게 찾을수 있게 설계된 자료구조다. 즉, 부모 노드의 키 값이 자식 노드의 키 값보다 항상 크거나 작은 이진 트리다.
<br>

- Max heap
  - $\text{parent node}.key \geq \text{current node}.key$

- Min heap
  - $\text{parent node}.key \leq \text{current node}.key$

Heap은 Complete binary tree이다.

- $\text{left index} = index * 2$
- $\text{right index} = index * 2 + 1$
- $\text{parent index} = index / 2$

```python
class Node:
    def __init__(self, key):
        self.key = key

class MinHeap:
    def __init__(self):
        self.heap = [None]
        self.count = 0

    def insert(self, key):
        self.count += 1
        i = self.count
        self.heap.append(Node(key))
        while i != 1 and key < self.heap[i//2].key:
            self.heap[i], self.heap[i//2] = self.heap[i//2], self.heap[i]
            i //= 2
        return

    def Sum_of_parents_of_last_node(self):
        sum = 0
        i = self.count

        while i > 1:
            i //= 2
            sum += self.heap[i].key

        return sum

    def print(self):
        tmp = []
        for i in range(1, self.count+1):
            tmp.append(self.heap[i].key)
        print(tmp)
```
