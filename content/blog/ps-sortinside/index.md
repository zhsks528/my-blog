---
title: "백준알고리즘 - 1427. 소트인사이드"
date: "2020-07-15T17:35:32.354Z"
category: "algorithm"
emoji: "😸"
---

## 백준알고리즘 - 1427. 소트인사이드

- 관련된 알고리즘 : Sort

### 문제

배열을 정렬하는 것은 쉽다. 수가 주어지면, 그 수의 각 자리수를 내림차순으로 정렬해보자.

### 입력

첫째 줄에 정렬하고자하는 수 N이 주어진다. N은 1,000,000,000보다 작거나 같은 자연수이다.

### 출력

첫째 줄에 자리수를 내림차순으로 정렬한 수를 출력한다.

### 예제

```
Input : 2143
Output : 4321
```

### 해결 1 

```python
array = input()

for i in range(9, -1, -1):
     for j in array:
         if int(j) == i:
             print(i, end='')
```

### 설명

1. 자릴수를 기준으로 정렬하므로 9부터 0까지 차례대로 확인한다.
2. 각 숫자에 대하여 해당 숫자의 개수를 계산하여 출력한다.

### 해결 2

```python
array = list(input())
array.sort(reverse=True)

length = len(array)
    
sum = 0

for index in range(length):
    sum += int(array[index]) * 10 ** (length-1-index)

print(sum)
```

### 설명

1. 자릿수를 이용하여 문제를 해결한다.

### 해결 3

```python
a = map(int, input())

text = ""
a = list(a)
a.sort()
a.reverse()

for i in range(len(a)):
    text += str(a[i])
    
print(text)
```

### 설명

1. 문자열로 추가해서 문제해결한다.

### 출처

- https://www.acmicpc.net/problem/1427

