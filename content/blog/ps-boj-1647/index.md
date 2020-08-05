---
title: "백준알고리즘 - 1647. 도시 분할 계획"
date: "2020-08-05T14:47:51:112Z"
category: "ps"
emoji: "🏙️"
---

## 백준알고리즘 - 1647. 도시 분할 계획

- 관련된 알고리즘 : 최소 스패닝 트리(MST)

### 문제

동물원에서 막 탈출한 원숭이 한 마리가 세상구경을 하고 있다. 그러다가 평화로운 마을에 가게 되었는데, 그곳에서는 알 수 없는 일이 벌어지고 있었다.

마을은 N개의 집과 그 집들을 연결하는 M개의 길로 이루어져 있다. 길은 어느 방향으로든지 다닐 수 있는 편리한 길이다. 그리고 각 길마다 길을 유지하는데 드는 유지비가 있다.

마을의 이장은 마을을 두 개의 분리된 마을로 분할할 계획을 가지고 있다. 마을이 너무 커서 혼자서는 관리할 수 없기 때문이다. 마을을 분할할 때는 각 분리된 마을 안에 집들이 서로 연결되도록 분할해야 한다. 각 분리된 마을 안에 있는 임의의 두 집 사이에 경로가 항상 존재해야 한다는 뜻이다. 마을에는 집이 하나 이상 있어야 한다.

그렇게 마을의 이장은 계획을 세우다가 마을 안에 길이 너무 많다는 생각을 하게 되었다. 일단 분리된 두 마을 사이에 있는 길들은 필요가 없으므로 없앨 수 있다. 그리고 각 분리된 마을 안에서도 임의의 두 집 사이에 경로가 항상 존재하게 하면서 길을 더 없앨 수 있다. 마을의 이장은 위 조건을 만족하도록 길들을 모두 없애고 나머지 길의 유지비의 합을 최소로 하고 싶다. 이것을 구하는 프로그램을 작성하시오.

### 입력

첫째 줄에 집의 개수N, 길의 개수M이 주어진다. N은 2이상 100,000이하인 정수이고, M은 1이상 1,000,000이하인 정수이다. 그 다음 줄부터 M줄에 걸쳐 길의 정보가 A B C 세 개의 정수로 주어지는데 A번 집과 B번 집을 연결하는 길의 유지비가 C (1 ≤ C ≤ 1,000)라는 뜻이다.

### 출력

첫째 줄에 없애고 남은 길 유지비의 합의 최솟값을 출력한다.

### 예제

```
Input : 7 12
        1 2 3
        1 3 2
        3 2 1
        2 5 2
        3 4 4
        7 3 6
        5 1 5
        1 6 2
        6 4 1
        6 5 3
        4 5 3
        6 7 4
Output : 8
```

### 해결

```python
import sys

v, e = map(int, sys.stdin.readline().split())

vertices = list()
data = list()

for i in range(v):
    vertices.append(i + 1)
    
for _ in range(e):
    node_a, node_b, weight = map(int, sys.stdin.readline().split())
    data.append((node_a, node_b, weight))
    
mygraph = dict()
mygraph['vertices'] = vertices
mygraph['edges'] = data

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
    root1= find(node_a)
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
    edges.sort(key=lambda x: x[2])
    
    for edge in graph['edges']:
        node_a, node_b, weight = edge
        
        if find(node_a) != find(node_b):
            union(node_a, node_b)
            mst.append(edge)
    
    sum = 0
    max_edge = 0
    for i in range(len(mst)):
        sum += mst[i][2]
        max_edge = max(max_edge, mst[i][2])
    
    min_price = sum - max_edge
    return min_price

result = kruskal(mygraph)
print(result)
```

### 설명

1. 유지비가 최소가 되도록하려면 최소 스패닝 트리를 적용해야 구할 수 있으므로 오름차순으로 가중치를 기준으로 잡아서 오름차순정렬을 한다.
2. 크루스칼 알고리즘을 이용하였다.
3. 유지비가 최소가 되도록 두 마을로 분리한다는 뜻 = 가장 유지비가 많이 드는 길을 제거한다는 의미
4. 최소 유지비에서 가장 큰 유지비를 빼면 문제를 해결할 수 있다.

- https://www.acmicpc.net/problem/1647
