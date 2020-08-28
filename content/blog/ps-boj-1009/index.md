---
title: "백준알고리즘 - 1009. 분산처리"
date: "2020-08-04T17:02:11.555Z"
category: "ps"
emoji: "🖥️"
---

## 백준알고리즘 - 1009. 분산처리

- 관련된 알고리즘 : .

### 문제

재용이는 최신 컴퓨터 10대를 가지고 있다. 어느 날 재용이는 많은 데이터를 처리해야 될 일이 생겨서 각 컴퓨터에 1번부터 10번까지의 번호를 부여하고, 10대의 컴퓨터가 다음과 같은 방법으로 데이터들을 처리하기로 하였다.

1번 데이터는 1번 컴퓨터, 2번 데이터는 2번 컴퓨터, 3번 데이터는 3번 컴퓨터, ... ,

10번 데이터는 10번 컴퓨터, 11번 데이터는 1번 컴퓨터, 12번 데이터는 2번 컴퓨터, ...

총 데이터의 개수는 항상 ab개의 형태로 주어진다. 재용이는 문득 마지막 데이터가 처리될 컴퓨터의 번호가 궁금해졌다. 이를 수행해주는 프로그램을 작성하라.

### 입력

입력의 첫 줄에는 테스트 케이스의 개수 T가 주어진다. 그 다음 줄부터 각각의 테스트 케이스에 대해 정수 a와 b가 주어진다. (1 ≤ a < 100, 1 ≤ b < 1,000,000)

### 출력

각 테스트 케이스에 대해 마지막 데이터가 처리되는 컴퓨터의 번호를 출력한다.

### 예제

```
Input : 5
        1 6
        3 7
        6 2
        7 100
        9 635
Output : 1
         7
         6
         1
         9
```

### 해결 (오답)

```python
import sys

t = int(sys.stdin.readline())

array = list()

for _ in range(t):
    data = list(map(int, input().split()))
    array.append((data[0], data[1]))

for i in range(len(array)):
    result = array[i][0]**array[i][1] % 10
    print(result)
```

### 설명

1. 이렇게 하게되면 시간 7 100 & 9 635 를 계산할 때 값이 크기 때문에 시간초과가 난다.

### 해결 

```python
import sys
t = int(sys.stdin.readline())

for _ in range(t):
    a, b = map(int, sys.stdin.readline().split())
    
    result = [(a ** i) % 10 for i in range(1,5)][(b % 4) -1]
    
    print(result if result != 0 else 10)
```

### 설명

1. 제곱에서의 반복되는 규칙을 이용하면 문제를 해결할 수 있다.

2. 2의 제곱의 1의자리수: [2, 4, 8, 6] 계속 반복

   3의 제곱수의 1의자리수: [3, 9, 7, 1] 계속 반복

   4의 제곱수의 1의자리수: [4, 6, 4, 6] 계속 반복

   5의 제곱수의 1의자리수 : [5, 5, 5, 5] 계속 반복 등

### 출처

- https://www.acmicpc.net/problem/1009