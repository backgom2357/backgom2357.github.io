---
layout: post
title:  "python - Inside of Linked List"
date:   2019-09-10
categories: programming
---
# Inside of linked List
Python에서는 Linked list를 직접 클래스로 구현해야되는 것 같다. 근데 구현을 하고나서 입력을 할때

```Python
sll = SinglyLinkedList()
sll.addtoLast(Node('data1'))
sll.addtoLast(Node('data2'))
sll.addtoLast(Node('data3'))
```
이런 식으로 들어가는데, 어떻게 선언된 객체 안에 따로 선언되지 않은 객체가 들어갈 수 있나 하고 고민을 해보았더니 아마 sll안의 변수 head를 통해 Node가 선언되고 그것 안의 변수 link에 의해 다음 Node가 선언되는 식으로 되는 듯하다. 즉, 겉으로는 안그래 보여도 사실은 객체 안에서 그 변수로 선언이 된것이다.
<br>
```python
self.head = Node('data1')
self.head.link = (Node('data1').link) = Node('data2')
self.head.link.link = (Node('data1').link.link) = (Node('data2').link) = Node('data3')
```
<br>

- Singly linked list(메서드 몇개만 구현한 것)

```python
class Node:
    def __init__(self, data):
        self.data = data
        self.link = None


class SinglyLinkedList:
    def __init__(self):
        self.head = None

    def addtoLast(self, node):
        if self.head == None
            self.head = node
        else:
            cur = self.head
            while cur.link != None:
                cur = cur.link
            cur.link = node

    def add(self, node, index):
        idx = 0
        cur = self.head
        n = node

        if index == 0:
            n.link = cur
            self.head = n
            return 0

        while cur.link != None:
            idx += 1
            if idx == index:
                n.link = cur.link
                cur.link = n
                return 0
            cur = cur.link

        return -1

        def addContinuously(self, dataList, index):
            idx = 0
            cur = self.head
            n0 = Node(dataList[0])
            cur_in_dataList = n0

            for data in dataList[1:]:
                cur_in_dataList.link = Node(data)
                cur_in_dataList = cur_in_dataList.link
                self.count += 1

            if index == 0:
                cur_in_dataList.link = cur
                self.head = n0
                self.count += 1
                return 0

            while cur.link != None:
                idx += 1
                if idx == index:
                    cur_in_dataList.link = cur.link
                    cur.link = n0
                    self.count += 1
                    return 0
                cur = cur.link

            cur.link = n0
            self.count += 1

            return -1

        def get(self, index):
            idx = 0
            cur = self.head
            if self.head == None:
                return -1
            while cur.link != None:
                if idx == index:
                    return cur.data
                cur = cur.link
                idx += 1

            return cur.data

        def getLast10Node(self):
            tmp = []

            idx = 0
            cur = self.head
            while cur.link != None:
                if idx >= self.count - 10:
                    tmp.append(cur.data)
                cur = cur.link
                idx += 1
            tmp.append(cur.data)

            return tmp
```
