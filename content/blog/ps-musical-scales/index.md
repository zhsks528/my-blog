---
title: "백준알고리즘 - 2028. 음계"
date: "2020-07-09T22:31:03.284Z"
category: "algorithm"
emoji: "🎹"
---

## 백준알고리즘 - 2028. 음계

- 관련된 알고리즘 : Array

### 문제

다장조는 c d e f g a b C, 총 8개 음으로 이루어져있다. 이 문제에서 8개 음은 다음과 같이 숫자로 바꾸어 표현한다. c는 1로, d는 2로, ..., C를 8로 바꾼다.

1부터 8까지 차례대로 연주한다면 ascending, 8부터 1까지 차례대로 연주한다면 descending, 둘 다 아니라면 mixed 이다.

연주한 순서가 주어졌을 때, 이것이 ascending인지, descending인지, 아니면 mixed인지 판별하는 프로그램을 작성하시오.

### 입력

첫째 줄에 8개 숫자가 주어진다. 이 숫자는 문제 설명에서 설명한 음이며, 1부터 8까지 숫자가 한 번씩 등장한다.

### 출력

첫째 줄에 ascending, descending, mixed 중 하나를 출력한다.

### 예제 1

```
Input : 1 2 3 4 5 6 7 8
Output : ascending
```

### 예제 2

```
Input : 8 7 6 5 4 3 2 1
Output : descending
```

### 예제 3

```
Input : 8 1 7 2 6 3 5 4 
Output : mixed
```

### 해결

```python
# 입력값
value = list(map(int, input().split(' ')))

ascending = True
descending = True

for index in range(1, 8):
    # 오름차순
    if value[index] > value[index - 1]:
        descending = False
    # 내림차순
    else:
        ascending = False
        
if ascending:
    print("ascending")
elif descending == True:
    print("descending")
else:
    print("mixed")
```

### 설명

1. 리스트에서의 원소를 차례대로 비교한다.
2. 비교할 때 두 원소를 기준으로 오름차순/ 내림차순 여부를 체크한다.

### 출처

- https://www.acmicpc.net/problem/2920