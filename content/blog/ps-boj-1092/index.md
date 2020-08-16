---
title: "백준알고리즘 - 1092. 배"
date: "2020-08-03T10:48:12.226Z"
category: "ps"
emoji: "🛳️"
---

## 백준알고리즘 - 1092. 배

- 관련된 알고리즘 : 탐욕 알고리즘, 정렬

### 문제

지민이는 항구에서 일한다. 그리고 화물을 배에 실어야 한다. 모든 화물은 박스에 안에 넣어져 있다. 항구에는 크레인이 N대 있고, 1분에 박스를 하나씩 배에 실을 수 있다. 모든 크레인은 동시에 움직인다.

각 크레인은 무게 제한이 있다. 이 무게 제한보다 무거운 박스는 크레인으로 움직일 수 없다. 모든 박스를 배로 옮기는데 드는 시간의 최솟값을 구하는 프로그램을 작성하시오.

### 입력

첫째 줄에 N이 주어진다. N은 50보다 작거나 같은 자연수이다. 둘째 줄에는 각 크레인의 무게 제한이 주어진다. 이 값은 1,000,000보다 작거나 같다. 셋째 줄에는 박스의 수 M이 주어진다. M은 10,000보다 작거나 같은 자연수이다. 넷째 줄에는 각 박스의 무게가 주어진다. 이 값도 1,000,000보다 작거나 같은 자연수이다.

### 출력

첫째 줄에 모든 박스를 배로 옮기는데 드는 시간의 최솟값을 출력한다. 만약 모든 박스를 배로 옮길 수 없으면 -1을 출력한다.

### 예제

```
Input : 3
        6 8 9
        5
        2 5 2 4 7
Output : 2
```

### 해결 

```python
import sys
from collections import deque
read = sys.stdin.readline
 
N = int(read())
crane = list(map(int, read().split()))
M = int(read())
box = list(map(int, read().split()))
 
crane.sort(reverse=True)
box.sort(reverse=True)
box = deque(box)
container = []
temp = []
ans = 0
 
while box or temp:
    if not box and len(container) != N:
        container.clear()
        ans += 1
        box.extendleft(reversed(temp))
        temp.clear()
 
    if len(container) == N:
        container.clear()
        ans += 1
        box.extendleft(reversed(temp))
        temp.clear()
 
    if box[0] > crane[0]:
        print(-1)
        sys.exit(0)
    
    if crane[len(container)] >= box[0]:
        container.append(box.popleft())
    
    else:
        temp.append(box.popleft())

print(ans+1)
```

### 설명

없음.

### 출처

- https://www.acmicpc.net/problem/1092
