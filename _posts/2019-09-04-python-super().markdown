---
layout: post
title:  "python - super()"
date:   2019-09-04
categories: programming
---

# super()
<br>
- 자식 클래스에서 부모클래스의 내용을 사용하고 싶은 경우
- 사용 방법 : super().부모클래스내용
- 예

```python
class Animal( ):
    def __init__( self, name ):
        self.name = name

class Human( Animal ):
    def __init__( self, name, hand ):
        super().__init__( name ) # 부모클래스의 __init__ 메소드 호출
        self.hand = hand

person = Human( "사람", "오른손" )
```



출처 : 프로그래머스[프로그래머스](https://programmers.co.kr/learn/courses/2/lessons/330)
