---
layout: post
title:  "python - Queue"
date:   2019-09-09
categories: programming
---
# Queue
queue 모듈에 저장되어 있는 클래스들. (maxsize는 해당 클래스가 저장 할 수 있는 최대 아이템 개수)
<br>
벼뎓.뼈뎓ㅋ

- queue.Queue(maxsize) : FIFO 큐 객체 생성
- queue.LifoQueue(maxsize) : LIFO 큐 객체 생성
- queue.PriorityQueue(maxsize) : 우선순위 큐 객체 생성
(우선순위가 높은 순으로 나감, 숫자가 낮을수록 순위가 높음, (순위, item)의 튜플로 입력)
<br>

위 클래스들은 다음의 메서드를 동일하게 가지고 있다.
- qsize() : 큐의 아이템수 반환
- put(item[,block[,timeout]]) : 큐에 아이템 입력, 큐가 가득차면 빈자리 날때까지 기다림
- put_nowait(item) : 안기다리고 때려넣음(blocking이 없음). 자리가 즉지 나지 않으면 QueueFull을 일으킴
- get([block[,timeout]]) : 아이템 1개 반환. 큐가 비어있으면 들어올때까지 기다림
- get_nowait() : 아이템 1개 즉시 반환. 큐가 비어있으면 QueueEmpty를 발생
- empty() : 큐가 비어있음 True, 아님 False
- full() : maxsize가 설정된 상태에서 가득차있으면 True, 아님 False
<br>

예(미로에서 시작(2)에서 끝(3)까지의 거리 찾기)

<details>
<summary> 문제 보기(클릭) </summary>
<div markdown = "1">
NxN 크기의 미로에서 출발지 목적지가 주어진다.
<br>
이때 최소 몇 개의 칸을 지나면 출발지에서 도착지에 다다를 수 있는지 알아내는 프로그램을 작성하시오.
<br>
경로가 있는 경우 출발에서 도착까지 가는데 지나야 하는 최소한의 칸 수를, 경로가 없는 경우 0을 출력한다.
<br>
다음은 5x5 미로의 예이다. 1은 벽, 0은 통로를 나타내며 미로 밖으로 벗어나서는 안된다.
<br>
13101<br>
10101<br>
10101<br>
10101<br>
10021<br>
마지막 줄의 2에서 출발해서 0인 통로를 따라 이동하면 맨 윗줄의 3에 5개의 칸을 지나 도착할 수 있다.
<br>

[입력]
<br>
첫 줄에 테스트 케이스 개수 T가 주어진다.  1<=T<=50
<br>
다음 줄부터 테스트 케이스의 별로 미로의 크기 N과 N개의 줄에 걸쳐 미로의 통로와 벽에 대한 정보가 주어진다. 5<=N<=100
<br>
0은 통로, 1은 벽, 2는 출발, 3은 도착이다.
<br>
[출력]
<br>
각 줄마다 "#T" (T는 테스트 케이스 번호)를 출력한 뒤, 답을 출력한다.
<br>
[입력]<br>
3<br>
5<br>
13101<br>
10101<br>
10101<br>
10101<br>
10021<br>
5<br>
10031<br>
10111<br>
10101<br>
10101<br>
12001<br>
5<br>
00013<br>
01110<br>
21000<br>
01111<br>
00000<br>
[출력]<br>
\#1 5<br>
\#2 5<br>
\#3 0<br>
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
    # N = int(input())
    N = int(f.readline())
    maze = []
    find_start = False
    get_end = False
    q = queue.Queue()
    step = 0

    # start
    y, x = 0, 0

    for i in range(N+2):
        if i == 0 or i == N+1:
            maze.append([1]*(N+2))
            continue
        line_of_maze = [1] + list(map(int,list(f.readline()[:N]))) + [1]

        idx = 0
        while not find_start and idx < (N+2):
            n = line_of_maze[idx]
            if n == 2:
                y, x = i, idx
                find_start = True
                break
            idx += 1

        maze.append(line_of_maze)

    q.put((y, x, step))

    # print(x,y)

    while not q.empty():

        if maze[y][x] == 3:
            get_end = True
            break

        maze[y][x] = 1

        if maze[y][x+1] != 1:
            q.put((y,x+1,step+1))
        if maze[y+1][x] != 1:
            q.put((y+1, x,step+1))
        if maze[y][x - 1] != 1:
            q.put((y, x-1,step+1))
        if maze[y - 1][x] != 1:
            q.put((y-1 , x,step+1))

        tmp = q.get()
        y, x, step = tmp[0], tmp[1], tmp[2]
        # print(tmp, maze[y][x], q.qsize(), q.empty())

    if get_end:
        print("#%d" % case, step-1)
    else:
        print("#%d" % case, 0)
f.close()
```
