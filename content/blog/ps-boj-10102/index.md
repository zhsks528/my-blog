---
title: "백준알고리즘 - 10102. 개표"
date: "2020-08-11T14:25:41.631Z"
category: "ps"
emoji: "🗳️"
---

## 백준알고리즘 - 10102. 개표

- 관련된 알고리즘 : 다이나믹 프로그래밍

### 문제

A와 B가 한 오디션 프로의 결승전에 진출했다. 결승전의 승자는 심사위원의 투표로 결정된다.

심사위원의 투표 결과가 주어졌을 때, 어떤 사람이 우승하는지 구하는 프로그램을 작성하시오.

### 입력

입력은 총 두 줄로 이루어져 있다. 첫째 줄에는 심사위원의 수 V (1 ≤  V ≤  15)가 주어지고, 둘째 줄에는 각 심사위원이 누구에게 투표했는지가 주어진다. A와 B는 각각 그 참가자를 나타낸다.

### 출력

- A가 받은 표가 B보다 많은 경우에는 A
- B가 받은 표가 A보다 많은 경우에는 B
- 같은 경우에는 Tie

### 예제

```
Input : 6
        ABBABB
Output : B
```

### 해결

```python
v = int(input())
ballot = list(input())

a, b = 0, 0

for i in ballot:
    if i == 'A':
        a += 1
    else:
        b += 1

if a > b:
    print('A')
elif a < b:
    print('B')
else:
    print('Tie')
        
```

### 설명

없음.

### 출처

- https://www.acmicpc.net/problem/10102
