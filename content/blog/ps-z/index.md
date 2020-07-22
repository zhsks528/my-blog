---
title: "백준알고리즘 - 1074. Z"
date: "2020-07-22T10:40:53.114Z"
category: "algorithm"
emoji: "🛶"
---

## 백준알고리즘 - 1074. Z

- 관련된 알고리즘 : Recursive

### 문제

한수는 2차원 배열 (항상 2^N * 2^N 크기이다)을 Z모양으로 탐색하려고 한다. 예를 들어, 2*2배열을 왼쪽 위칸, 오른쪽 위칸, 왼쪽 아래칸, 오른쪽 아래칸 순서대로 방문하면 Z모양이다.

![img](https://www.acmicpc.net/upload/201003/z1.JPG)

만약, 2차원 배열의 크기가 2^N * 2^N라서 왼쪽 위에 있는 칸이 하나가 아니라면, 배열을 4등분 한 후에 (크기가 같은 2^(N-1)로) 재귀적으로 순서대로 방문한다.

다음 예는 2^2 * 2^2 크기의 배열을 방문한 순서이다.

![img](https://www.acmicpc.net/upload/201003/z2.JPG)

N이 주어졌을 때, (r, c)를 몇 번째로 방문하는지 출력하는 프로그램을 작성하시오.

다음 그림은 N=3일 때의 예이다.

![img](https://www.acmicpc.net/upload/201003/z3.JPG)

### 입력

첫째 줄에 N r c가 주어진다. N은 15보다 작거나 같은 자연수이고, r과 c는 0보다 크거나 같고, 2^N-1보다 작거나 같은 정수이다

### 출력

첫째 줄에 문제의 정답을 출력한다.

### 예제 1

```
Input : 2 3 1
Output : 11
```

### 예제 2

```
Input : 3 7 7
Output : 63
```

### 해결

```python
def solve(n, r, c):
    global count
    
    if n == 2:
        if r == R and c == C:
            print(count)
            return
        count += 1 
        
        if r == R and c + 1 == C:
            print(count)
            return
        count += 1
        
        if r + 1 == R and c == C:
            print(count)
            return
        count += 1
        
        if r + 1 == R and c + 1 == C:
            print(count)
            return
        count += 1
        return
    
    solve(n / 2, r, c)
    solve(n / 2, r, c + n / 2)
    solve(n / 2, r + n / 2, c)
    solve(n / 2, r, c + n / 2)
            
N, R, C = map(int, input().split(' '))
count = 0;
solve(2 ** N, 0, 0)
```

### 설명

1. Z 모양을 구성하는 4가지 방향에 대하여 차례대로 재귀적으로 호출한다.

### 출처

- https://www.acmicpc.net/problem/1074

