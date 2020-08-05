---
title: "백준알고리즘 - 1922. 네트워크 연결"
date: "2020-08-05T13:29:33.123Z"
category: "ps"
emoji: "🖧"
---

## 백준알고리즘 - 1922. 네트워크 연결

- 관련된 알고리즘 : 최소 스패닝 트리(MST)

### 문제

도현이는 컴퓨터와 컴퓨터를 모두 연결하는 네트워크를 구축하려 한다. 하지만 아쉽게도 허브가 있지 않아 컴퓨터와 컴퓨터를 직접 연결하여야 한다. 그런데 모두가 자료를 공유하기 위해서는 모든 컴퓨터가 연결이 되어 있어야 한다. (a와 b가 연결이 되어 있다는 말은 a에서 b로의 경로가 존재한다는 것을 의미한다. a에서 b를 연결하는 선이 있고, b와 c를 연결하는 선이 있으면 a와 c는 연결이 되어 있다.)

그런데 이왕이면 컴퓨터를 연결하는 비용을 최소로 하여야 컴퓨터를 연결하는 비용 외에 다른 곳에 돈을 더 쓸 수 있을 것이다. 이제 각 컴퓨터를 연결하는데 필요한 비용이 주어졌을 때 모든 컴퓨터를 연결하는데 필요한 최소비용을 출력하라. 모든 컴퓨터를 연결할 수 없는 경우는 없다.

### 입력

첫째 줄에 컴퓨터의 수 N (1 ≤ N ≤ 1000)가 주어진다.

둘째 줄에는 연결할 수 있는 선의 수 M (1 ≤ M ≤ 100,000)가 주어진다.

셋째 줄부터 M+2번째 줄까지 총 M개의 줄에 각 컴퓨터를 연결하는데 드는 비용이 주어진다. 이 비용의 정보는 세 개의 정수로 주어지는데, 만약에 a b c 가 주어져 있다고 하면 a컴퓨터와 b컴퓨터를 연결하는데 비용이 c (1 ≤ c ≤ 10,000) 만큼 든다는 것을 의미한다. a와 b는 같을 수도 있다.

### 출력

모든 컴퓨터를 연결하는데 필요한 최소비용을 첫째 줄에 출력한다.

### 예제

```
Input : 6
        9
        1 2 5
        1 3 4
        2 3 2
        2 4 7
        3 4 6
        3 5 11
        4 5 3
        4 6 8
        5 6 8
Output : 23
```

### 힌트

이 경우에 1-3, 2-3, 3-4, 4-5, 4-6을 연결하면 주어진 output이 나오게 된다.

### 해결

```python
n = int(input())
m = int(input())

computer = list()

for i in range(n):
    computer.append(i+1)
    
array = list()

for _ in range(m):
    node_a, node_b, weight = map(int, input().split())
    array.append((node_a, node_b, weight))

mygraph = dict()
mygraph['vertices'] = computer
mygraph['edges'] = array

parents = dict()
ranks = dict()

def make_set(node):
    parents[node] = node
    ranks[node] = 0

def find(node):
    if parents[node] != node:
        parents[node] = find(parents[node])
    
    return parents[node]

def union(node_a, node_b):
    root1 = find(node_a)
    root2 = find(node_b)
    
    if ranks[root1] > ranks[root2]:
        parents[root2] = root1
    else:
        parents[root1] = root2
        
        if ranks[root1] == ranks[root2]:
            ranks[root2] += 1
        
def kruskal(graph):
    mst = list()
    
    for node in graph['vertices']:
        make_set(node)
    
    edges = graph['edges']
    edges.sort(key=lambda x : x[2])
    
    for edge in graph['edges']:
        node_a, node_b, weight = edge
        
        if find(node_a) != find(node_b):
            union(node_a, node_b)
            mst.append(edge)
    
    sum = 0
    for i in range(len(mst)):
        sum += mst[i][2]
        
    return sum

result = kruskal(mygraph)

print(result)
```

### 설명

1. 최소신장트리 중 크루스칼 알고리즘을 이용하여 문제를 해결했다.
2. 간선을 기준으로 정렬한 후 최상단 노드가 다르다면 합치는 작업(union)을 하면 문제를 해결할 수 있다.
3. 최상단 노드가 같게되면 연결되는 그래프가 되버리기 때문에 제외 시켜야한다.

### 출처

- https://www.acmicpc.net/problem/1922
