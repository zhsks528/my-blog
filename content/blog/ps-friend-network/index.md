---
title: "백준알고리즘 - 4195. 친구 네트워크"
date: "2020-07-13T14:00:20.284Z"
category: "algorithm"
emoji: "😡"

---

## 백준알고리즘 - 4195. 친구 네트워크

- 관련된 알고리즘 : Hash

### 문제

민혁이는 소셜 네트워크 사이트에서 친구를 만드는 것을 좋아하는 친구이다. 우표를 모으는 취미가 있듯이, 민혁이는 소셜 네트워크 사이트에서 친구를 모으는 것이 취미이다.

어떤 사이트의 친구 관계가 생긴 순서대로 주어졌을 때, 두 사람의 친구 네트워크에 몇 명이 있는지 구하는 프로그램을 작성하시오.

친구 네트워크란 친구 관계만으로 이동할 수 있는 사이를 말한다.

### 입력

첫째 줄에 테스트 케이스의 개수가 주어진다. 각 테스트 케이스의 첫째 줄에는 친구 관계의 수 F가 주어지며, 이 값은 100,000을 넘지 않는다. 다음 F개의 줄에는 친구 관계가 생긴 순서대로 주어진다. 친구 관계는 두 사용자의 아이디로 이루어져 있으며, 알파벳 대문자 또는 소문자로만 이루어진 길이 20 이하의 문자열이다.

### 출력

친구 관계가 생길 때마다, 두 사람의 친구 네트워크에 몇 명이 있는지 구하는 프로그램을 작성하시오.

### 예제

```
Input : 2
        3
        Fred Barney
        Barney Betty
        Betty Wilma
        3
        Fred Barney
        Betty Wilma
        Barney Betty
Output : 2
         3
         4
         2
         2
         4
```

### 해결

```python
def find(x):
    if x == parent[x]:
        return x
    else:
        p = find(parent[x])
        parent[x] = p
        return p

def union(x, y):
    x = find(x)
    y = find(y)
    
    if x != y:
        parent[y] = x
        number[x] += number[y]
        
test_case = int(input())

for _ in range(test_case):
    parent = dict()
    number = dict()
    
    f = int(input())
    
    for _ in range(f):
        x, y = input().split(' ')
        
        if x not in parent:
            parent[x] = x
            number[x] = 1
        if y not in parent:
            parent[y] = y
            number[y] = 1
        
        union(x, y)
        print(number[find(x)])
```

### 설명

1. 해시를 활용한 Union-Find 알고리즘을 이용해 문제를 풀 수 있다.
2. Python에서는 dictionary 자료형을 해시처럼 사용할 수 있다.

### 출처

- https://www.acmicpc.net/problem/4195

