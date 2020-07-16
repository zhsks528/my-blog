---
title: "백준알고리즘 - 2747. 피보나치 수"
date: "2020-07-16T16:51:37.915Z"
category: "algorithm"
emoji: "🚴"
---

## 백준알고리즘 - 2747. 피보나치 수

- 관련된 알고리즘 : recursive

### 문제

피보나치 수는 0과 1로 시작한다. 0번째 피보나치 수는 0이고, 1번째 피보나치 수는 1이다. 그 다음 2번째 부터는 바로 앞 두 피보나치 수의 합이 된다.

이를 식으로 써보면 Fn = Fn-1 + Fn-2 (n>=2)가 된다.

n=17일때 까지 피보나치 수를 써보면 다음과 같다.

0, 1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89, 144, 233, 377, 610, 987, 1597

n이 주어졌을 때, n번째 피보나치 수를 구하는 프로그램을 작성하시오.

### 입력

첫째 줄에 n이 주어진다. n은 45보다 작거나 같은 자연수이다.

### 출력

첫째 줄에 n번째 피보나치 수를 출력한다.

### 예제

```
Input : 10
Output : 55
```

### 해결

```python
n = int(input())

a, b = 0, 1

while n > 0:
    a, b = b, a + b
    n -= 1
    
print(a)
```

### 설명

1. 동적 프로그래밍으로 풀어야함

### 재귀로 풀시 문제점

```python
n = int(input())

def fibonacci(n):
    if n == 0:
        return 0
    if n == 1:
        return 1
    return fibonacci(n-1) + fibonacci(n-2)
    
print(fibonacci(n))
```

### 설명

1. n이 계속 증가할수록 연산의 수가 많아지므로 적합하지 않다.

### 출처

- https://www.acmicpc.net/problem/2747
