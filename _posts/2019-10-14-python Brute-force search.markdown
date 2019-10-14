---
layout: post
title:  "python - Brute-force Search"
date:   2019-10-14
categories: programming
---
# Brute-force search
이 무식한 탐색은 그냥 모든 가능한 후보를 확인하는 기법이다. 그냥 컴퓨터에게 모든것을 맡긴다.
<br>

설계하고 실행시키는데는 얼마 안걸리나 결과가 나오기 까지는 시간이 매우 오래 걸릴 수 있다.
<br>

Backtracking과 혼동하면 안된다.
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
