---
layout: post
title: 'python-About Hash'
date: 2019-09-24
categories: programming
---
# Hashing hash functions
Hashing의 요점은 데이터의 내용과 저장한 곳의 주소를 연결시킴으로서, 효율적으로 데이터를 관리하는데 있다.
<br>

원래 데이터 값을 key, key 값의 연산에 의해 직접 접근이 가능한 구조를 hash table, 그리고 이 hash table을 이용한 탐색을 hashing이라고 한다.
<br>

Hash function은 탐색 키를 입력으로 받아 hash address를 생성하고 이 hash address가 배열로 구현된 hash table의 인덱스가 된다.
<br>

#### 기존 direct-access table의 문제점

Dirct-access table의 아이디어는 key들을 집합 $U \subseteq \\{0,1, \dots , m-1\\}$에서 가져온다고 가정했을때 크기가 $m$인 array를 미리 만들어놓고 때려넣자는 것이다. 그럼 사실상 계산 복잡도도 $O(1)$밖에 안된다
<br>

하지만 말이 $O(1)$이지 만약 64bit 숫자를 key로 한다면 만들어야 하는 array의 크기는 18,446,744,073,709,551,616이 된다. key가 글자면 더 크다.
<br>

그렇기 때문에 hashing을 한다.
<br>

#### Hash functions

탐색 효율을 높이기 위해선 좋은 hash function을 설계해야 한다. 그 조건은 다음과 같다.
- 최소한의 충돌
- hash functions의 값이 hash table의 주소 영역 내에서 고르게 분포
- 빠른 계산

- Division method : $h(k) = k \mod M$<br>
(이때 $M$은 hash table의 크기로 고르게 분포시키기 위해 소수로 설정하는 것이 좋다)
- Multiplication method : $h(k)=(A \cdot k \mod 2^w) rsh (w-r)$<br>
(rsh : bitwise right-shift, $A$ : odd integer in the range $2^{w-1}<A<2^w$, $A$를 경계와 가까지 잡지 않는다)


- Open addressing : $U \times \\{0,1,\dots,m-1\\} \to \\{0,1,\dots,m-1\\}$<br>
(The probe sequence $<h(k,0),h(k,1),\dots,h(k,m-1)>$은 permuatation of $\\{0,1,\dots,m-1\\}$, 채우는건 쉽지만, 삭제는 어렵다.)
- Linear probing : $h(k,i)=(h'(k)+i)\mod m$<br>
($h'(k)$: 일반적인 hash function, primary clustering 위험(평균 탐색 시간이 늘어남))
- Double hashing : $h(k,i) = (h_1(k) + i \cdot h_2(k)) \mod m$<br>
($h_1(k), h_2(k)$: 일반적인 hash functions, 왠만하면 $h_2(k)$는 $m$과 relatively prime인게 좋다. 하나의 방법으로 $m$을 2의 배수로, $h_2(k)$를 홀수로 한다.)
