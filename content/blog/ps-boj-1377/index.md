---
title: "백준알고리즘 - 1377. 버블 소트"
date: "2020-07-26T10:28:20.122Z"
category: "ps"
emoji: "🐹"
---

## 백준알고리즘 - 1377. 버블 소트

- 관련된 알고리즘 : Sort

### 문제

영식이는 다음과 같은 버블 소트 프로그램을 C++로 작성했다.

```c++
bool change = false;
for (int i=1; i<=n+1; i++) {
    change = false;
    for (int j=1; j<=n-i; j++) {
        if (a[j] > a[j+1]) {
            change = true;
            swap(a[j], a[j+1]);
        }
    }
    if (change == false) {
        cout << i << '\n';
        break;
    }
}
```

위 소스에서 n은 배열의 크기이고, a는 수가 들어있는 배열이다. 수는 배열의 1번방부터 채운다.

위와 같은 소스를 실행시켰을 때, 어떤 값이 출력되는지 구하는 프로그램을 작성하시오.

### 입력

첫째 줄에 N이 주어진다. N은 500,000보다 작거나 같은 자연수이다. 둘째 줄부터 N개의 줄에 A[1]부터 A[N]까지 하나씩 주어진다. A에 들어있는 수는 1,000,000보다 작거나 같은 자연수 또는 0이다.

### 출력

정답을 출력한다.

### 예제

```
Input : 5
        10
        1
        5
        2
        3
Output : 3
```

### 해결

```python
n = int(input())
arr = []

for i in range(n):
    arr.append( (int(input()), i) )

sorted_arr = sorted(arr) 
answer = [] 

for i in range(n):
    answer.append(sorted_arr[i][1] - arr[i][1])

print(max(answer) + 1)
```

### 설명

1. 버블 정렬로 문제를 해결하다보면 시간초과가 난다 . 시간복잡도 (On^2)
2. **정렬 전의 요소들의 인덱스 값과, 정렬 후의 요소들의 인덱스 값을 비교**한다면 문제를 해결할 수 있다.

### 출처

- https://www.acmicpc.net/problem/1377
