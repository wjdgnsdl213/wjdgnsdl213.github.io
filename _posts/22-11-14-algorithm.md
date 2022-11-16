---
layout: post
title: "[22.11.14] 알고리즘 문제풀이"
subtitle: "과일 장수"
author: "Jeonghun"
header-style: text
catalog:      true
tags:
  - Algorithm
  - Programmers
---

오늘은 프로그래머스 "과일 장수" 문제를 풀었어요~~

https://school.programmers.co.kr/learn/courses/30/lessons/135808#


전 먼저 사과 점수 배열을 정렬 한 다음,
한 박스 단위로 사과 요소를 하나씩 빼면서 그 값이 최소면 저장하고, 한 박스가 끝나면 사과 개수를 곱하는 방식으로 풀었습니다.

```python
# 내 코드
def solution(k, m, score):
    profit = 0
    score.sort()
    for i in range(len(score)//m):
        min = 10
        for j in range(m):
            v = score.pop()
            if v < min:
                min = v
        profit += min*m
    return profit
            
```

그런데 생각해보니 정렬하고 나니깐, 상자 별로 최소값의 인덱스가 정해져 있더라구요
그래서 그 최소값만 모두 더한 다음에 사과개수를 곱해서 반환하는 식의 코드입니다.

```python
# 다른 방법
def solution(k, m, score):
    profit = 0
    score.sort()
    minidx = len(score) % m
    while minidx < len(score):
        profit += score[minidx]
        minidx += m
    return profit*m
```


결과는 이렇게 나왔습니다!

```python
score1 = [1,2,3,1,2,3,1]
score2 = [4,1,2,2,4,4,4,4,1,2,4,2]

print(solution(3,4,score1))
print(solution(4,3,score2))
```
    8
    33

