---
layout: post
title:  "python - Thread"
date:   2019-09-05
categories: programming
---
# Thread
파이썬에선 기본적으로 하나의 Thread에서 실행된다.
<br>
즉, 그 하나의 Thread가 코드를 순차적으로 실행한다.
<br>
병렬 실행을 하기위해 별도의 Thread를 생성해야한다. subThread를 생성하는 2가지 방법이 있다.
<br>

1. Thread가 실행할 함수(메서드)를 작성 후, 함수명을 threading.Tread()의 target argument에 지정
<br>
(args는 튜플로 parameter전달, kwargs는 dict로 전달)
<br>

```python
def sumation(low, high):
    total = 0
    for i in range(low, high):
        total += i
    print("Subthread", total)

t = threading.Thread(target=sumation, args=(1,1000000))
t.start()

tmp = 0
for j in range(1,1000):
    tmp += j

print("Main Thread", tmp)

# 결과
# Main Thread 499500
# Subthread 499999500000
```
결과를 보면 병렬 실행이 됬다는것을 알 수 있다.
<br>

2. threading.Tread를 상속받아 run()메서드를 재정의
<br>
Thread 클래스에서 run()은 Thread가 실행을 하는 메서드고 start()는 내부적으로 얘를 호출해주는 애
<br>

```python
total = 0

class SumSum(threading.Thread):    
    def __init__(self, low, high):
        super().__init__()
        self.low = low
        self.high = high
        self.deamon = True

    def run(self):
        global total
        for j in range(self.low,self.high):
            total += j
        print("Subtrhead", total)

t = SumSum(1, 1000000)
t.start()

print("Main Thread, total : " , total)

# 결과
# Main Thread, total :  51597561
# Subtrhead 499999500000
```
썸썸~
<br>

- daemon Thread
<br>
백그라운드에서 실행되는 Thread. Main Thread가 종료되면 그냥 SubThread와 다르게 바로 종료된다.
<br>

```python
import threading, time

def count():
    for j in range(10):
        time.sleep(1)
        print('count!', j)


# 데몬 쓰레드
t1 = threading.Thread(target=count,)
t1.daemon = True
t1.start()

time.sleep(4)
print("### End ###")

# 결과
# count! 0
# count! 1
# count! 2
# ### End ###
```
<br>
근데 이상한게 pycharm이나 터미널에서 실행시키면 Main Thread가 종료될때 딱 잘 종료되는데, jupyter notebook에선 그냥 다 실행된다...뭐징
