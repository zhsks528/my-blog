---
title: "백준알고리즘 - 1076. 저항"
date: "2020-08-04T16:24:11.222Z"
category: "ps"
emoji: "🔌"
---

## 백준알고리즘 - 1076. 저항

- 관련된 알고리즘 : .

### 문제

전자 제품에는 저항이 들어간다. 저항은 색 3개를 이용해서 그 저항이 몇 옴인지 나타낸다.

처음 색 2개는 저항의 값이고, 마지막 색은 곱해야 하는 값이다.

저항의 값은 다음 표를 이용해서 구한다.

| 색     | 값   | 곱         |
| :----- | :--- | :--------- |
| black  | 0    | 1          |
| brown  | 1    | 10         |
| red    | 2    | 100        |
| orange | 3    | 1000       |
| yellow | 4    | 10000      |
| green  | 5    | 100000     |
| blue   | 6    | 1000000    |
| violet | 7    | 10000000   |
| grey   | 8    | 100000000  |
| white  | 9    | 1000000000 |

예를 들어, 저항에 색이 yellow, violet, red였다면 저항의 값은 4,700이 된다.

### 입력

첫째 줄에 첫 번째 색, 둘째 줄에 두 번째 색, 셋째 줄에 세 번째 색이 주어진다. 색은 모두 위의 표에 쓰여 있는 색만 주어진다.

### 출력

입력으로 주어진 저항의 저항값을 계산하여 첫째 줄에 출력한다.

### 예제

```
Input : yellow
        violet
        red
Output : 4700
```

### 해결

```python
resistance = {'black': 0, 'brown': 1, 'red': 2, 'orange': 3, 'yellow': 4, 'green': 5, 'blue': 6, 'violet': 7, 'grey': 8, 'white': 9}

array = list()

for _ in range(3):
    data = input()
    array.append(data)

string = ""

for i in range(2):
    string += str(resistance[array[i]])

result = int(string) * 10 **resistance[array[-1]]

print(result)
```

### 설명

1. 저항표를 dict()으로 표현하여 문제를 해결할 수 있다.

### 출처

- https://www.acmicpc.net/problem/1076
