---
layout: post
title:  "python - About inheritance 상속에 관하여"
date:   2019-09-05
categories: programming
---
# About ingeritance
Thread 공부를 하다가 상속에 대해 궁금한것이 생겨서 이것저것 해보았다.
<br>

```python
class Animal( ):
    def __init__( self, name="코코팜", hand = "왼손", walk = True, fly = False ):
        self.name = name
        self.walk = walk
        self.fly = fly
        self.hand = hand

    def run(self):
        print("DADADADADADA")

class Human1(Animal):
    def __init__( self, name, hand ):
        super().__init__(name, hand) # 부모클래스의 __init__ 메소드 호출

class Human2():
    def __init__( self, name, hand ):
        Animal.__init__(self, name, hand)

person1 = Human1( "사람", "오른손" )
person2 = Human2( "사람", "오른손" )

print(person1.name, person1.hand, person1.walk, person1.fly)    # 사람 오른손 True False
print(person2.name, person2.hand, person2.walk, person2.fly)    # 사람 오른손 True False

person1.run()   # DADADADADADA
person2.run()   # error
```
<br>

person2는 못달린다.
<br>
Human2 방식은 Animal의 init만 가져온다.
<br>

```python
class Animal( ):
    def __init__( self, name="코코팜", hand = "왼손", walk = True, fly = False ):
        self.name = name
        self.walk = walk
        self.fly = fly
        self.hand = hand

    age = 10

    def run(self):
        print("DADADADADADA")

class Human1(Animal):
    def __init__( self, name, hand ):
        self.name = name
        self.hand = hand

person1 = Human1( "사람", "오른손" )

print(person1.age)  # 10
print(person1.walk, person1.fly)  # error
```
<br>

상속을 통해서는 클래스의 메서드와 클래스 내에서 생성된 변수만 받아올 수 있다.
<br><br>

즉, 다른 클래스의 init을 받으려면
1. inheritance을 하고 init에서 super()를 하거나
2. init에서 받을 클래스를 직접 호출해야한다

만약 다른 클래스의 메서드도 써야된다면 1번을 쓰자
