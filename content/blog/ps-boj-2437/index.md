---
title: "백준알고리즘 - 2437. 저울"
date: "2020-08-02T00:13:11.321Z"
category: "ps"
emoji: "🐟"
---

## 백준알고리즘 - 2437. 저울

- 관련된 알고리즘 : 탐욕 알고리즘

### 문제

하나의 양팔 저울을 이용하여 물건의 무게를 측정하려고 한다. 이 저울의 양 팔의 끝에는 물건이나 추를 올려놓는 접시가 달려 있고, 양팔의 길이는 같다. 또한, 저울의 한쪽에는 저울추들만 놓을 수 있고, 다른 쪽에는 무게를 측정하려는 물건만 올려놓을 수 있다.

![img](https://www.acmicpc.net/upload/images/Screen%20Shot%202012-09-07%20at%20%EC%98%A4%ED%9B%84%203_42_35.png)

무게가 양의 정수인 N개의 저울추가 주어질 때, 이 추들을 사용하여 측정할 수 없는 양의 정수 무게 중 최솟값을 구하는 프로그램을 작성하시오.

예를 들어, 무게가 각각 3, 1, 6, 2, 7, 30, 1인 7개의 저울추가 주어졌을 때, 이 추들로 측정할 수 없는 양의 정수 무게 중 최솟값은 21이다. 

### 입력

첫 째 줄에는 저울추의 개수를 나타내는 양의 정수 N이 주어진다. N은 1 이상 1,000 이하이다. 둘째 줄에는 저울추의 무게를 나타내는 N개의 양의 정수가 빈칸을 사이에 두고 주어진다. 각 추의 무게는 1이상 1,000,000 이하이다.

### 출력

첫째 줄에 주어진 추들로 측정할 수 없는 양의 정수 무게 중 최솟값을 출력한다.

### 예제

```
Input : 7
        3 1 6 2 7 30 1
Output : 21
```

### 해결

```python
n = int(input())
a = list(map(int, input().split(' ')))

a.sort()

min_weight = 1

for i in range(n):
    if min_weight < a[i]:
        break
        
    min_weight += a[i]

print(min_weight)
```

### 설명

1. 오름차순으로 정렬을 한 후 값을 더한다. 
2. 더한 값이 최대값보다 작을 때를 구하면 문제를 해결 할 수 있다.

### 출처

- https://www.acmicpc.net/problem/2437
