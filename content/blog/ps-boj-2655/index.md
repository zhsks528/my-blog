---
title: "백준알고리즘 - 2655. 가장 높은 탑 쌓기"
date: "2020-08-14T15:57:31.141Z"
category: "ps"
emoji: "🧱"
---

## 백준알고리즘 - 2655. 가장 높은 탑 쌓기

- 관련된 알고리즘 : 다이나믹 프로그래밍

### 문제

밑면이 정사각형인 직육면체 벽돌들을 사용하여 탑을 쌓고자 한다. 탑은 벽돌을 한 개씩 아래에서 위로 쌓으면서 만들어 간다. 아래의 조건을 만족하면서 가장 높은 탑을 쌓을 수 있는 프로그램을 작성하시오.

1. 벽돌은 회전시킬 수 없다. 즉, 옆면을 밑면으로 사용할 수 없다.
2. 밑면의 넓이가 같은 벽돌은 없으며, 또한 무게가 같은 벽돌도 없다.
3. 벽돌들의 높이는 같을 수도 있다.
4. 탑을 쌓을 때 밑면이 좁은 벽돌 위에 밑면이 넓은 벽돌은 놓을 수 없다.
5. 무게가 무거운 벽돌을 무게가 가벼운 벽돌 위에 놓을 수 없다.

### 입력

첫째 줄에는 입력될 벽돌의 수가 주어진다. 입력으로 주어지는 벽돌의 수는 최대 100개이다. 둘째 줄부터는 각 줄에 한 개의 벽돌에 관한 정보인 벽돌 밑면의 넓이, 벽돌의 높이 그리고 무게가 차례대로 양의 정수로 주어진다. 각 벽돌은 입력되는 순서대로 1부터 연속적인 번호를 가진다. 벽돌의 넓이, 높이 무게는 10,000보다 작거나 같은 자연수이다.

### 출력

탑을 쌓을 때 사용된 벽돌의 수를 빈칸없이 출력하고, 두 번째 줄부터는 탑의 가장 위 벽돌부터 가장 아래 벽돌까지 차례로 한 줄에 하나씩 벽돌 번호를 빈칸없이 출력한다.

### 예제

```
Input : 5
        25 3 4
        4 4 6
        9 2 3
        16 2 5
        1 5 2
Output : 3
         5
         3
         1
```

### 해결

```python
n = int(input())

array = []

array.append((0, 0, 0, 0))

for i in range(1, n + 1):
    area, height, weight = map(int ,input().split())
    array.append((i,area, height, weight))
    

array.sort(key=lambda x: x[3])

dp = [0] * (n + 1)

for i in range(1, n + 1):
    for j in range(0, i):
        if array[i][1] > array[j][1]:
            dp[i] = max(dp[i], dp[j] + array[i][2])
            
max_value = max(dp)
index = n
result = []

while index != 0:
    if max_value == dp[index]:
        result.append(array[index][0])
        max_value -= array[index][2]
    index -= 1
    
result.reverse()
print(len(result))
[print(i) for i in result]
```

### 설명

![image-20200814155818860](https://user-images.githubusercontent.com/38130934/90222478-171c5b00-de47-11ea-8d8a-6e2cbc21454d.PNG)

1. 가장 먼저 벽돌을 무게 기준으로 정렬
2. D[i] = 인덱스가 i인 벽돌을 가장 아래에 두었을 떄의 최대 높이
3. 각 별돌에 대해서 확인하여 D[i]를 갱신
4. 모든 0 <= j < i 에 대하여 , D[i] = max(D[i], D[j] + height[i] if area(i > area[j]))

### 출처

- https://www.acmicpc.net/problem/2655
