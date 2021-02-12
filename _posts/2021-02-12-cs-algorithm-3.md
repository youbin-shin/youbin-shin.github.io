---
title: "[Algorithm] MST에 대한 모든 것! with 크루스칼 알고리즘, 프림 알고리즘 (python)"
author: youbin
date: 2021-02-12 11:33:00 +0800
categories: [Computer Science, Algorithm]
tags: [Algorithm, Computer Science, CS, MST, spanning tree, Kruskal, greedy, Prim, python]
---

# Spanning Tree란?

> spanning tree = 신장 트리 = 스패닝 트리

MST에 대해 알기 위해서는 먼저 Spanning Tree에 대해 알아야 합니다.

spanning tree란 그래프 내의 모든 정점을 포함하는 트리로 그래프의 **최소 연결 부분 그래프**입니다.

즉 다음의 **2가지 조건**을 모두 만족하는 그래프가 spanning tree입니다.

1. **n개의 정점** + **(n - 1)개의 간선**으로 연결된 그래프 → 필연적 트리 형태
2. 모든 정점이 연결되어 있지만 사이클이 존재하지 않는 그래프



다음 그래프와 같이 5개의 정점을 4개의 간선으로 모든 연결된 형태가 spanning tree입니다.

<img src="https://user-images.githubusercontent.com/60081201/107760320-e1f8b300-6d6c-11eb-8127-a0e796715825.JPG" alt="스패닝 트리 예시 그림" style="zoom:50%;" />





# MST 란?

> MST = Minimum Spanning Tree = 최소 신장 트리

MST란 Spanning Tree 중 사용된 간선들의 가중치 합이 최소인 트리를 의미합니다.

즉 spanning tree의 조건에 하나가 더 추가된 3가지의 조건을 모두 만족하면 MST입니다.

1. **n개의 정점** + **(n - 1)개의 간선**으로 연결된 그래프 (spanning tree 조건)
2. 모든 정점이 연결되어 있지만 사이클이 존재하지 않는 그래프 (spanning tree 조건)
3. 간선 가중치의 합이 최소인 그래프

<img src="https://user-images.githubusercontent.com/60081201/107761191-4e27e680-6d6e-11eb-9378-bdfe830ad982.JPG" alt="mst 관련 그림" style="zoom:67%;" />





# Kruskal MST 알고리즘

### Kruskal MST 알고리즘이란?

탐욕적인 방법(greedy method) 을 이용하여 가중치를 간선에 할당한 그래프의 모든 정점을 최소 비용으로 연결하는 최적 해답을 구하는 알고리즘입니다.

- **간선 선택을 기반**으로 하는 알고리즘
- 이전 단계에 만들어진 신장 트리와 상관없이 무조건 최소 간선만 선택하는 방법



### Kruskal MST 동작 과정

1. 그래프 간선들 가중치의 오름차순으로 정렬한다.
2. 정렬된 간선 리스트에서 순서대로 사이클을 형성하지 않는 간선 선택한다.
   1. 가장 낮은 가중치 선택한다.
   2. 사이클 형성하는 간선인지를 체크하여 사이클을 형성하지 않는 경우에 해당 간선을 MST 집합에 추가한다.
3. 2번의 과정을 반복하며 선택된 간선의 개수가 (정점의 개수 - 1) 개가 되었을 때 종료한다.



#### 필요한 변수 설명

- `p` : 정점의 부모 노드를 저장하는 리스트 ★

  정점이 어느 정점과 연결되어 있는지 확인 가능한 리스트이다.

  - p의 초기 설정은 다음과 같다. (n = 4일 때 가정)

    p = [0, 1, 2, 3]

    각 인덱스(정점)마다 자기 자신의 정점과 연결된 것으로 기본 설정을 한다.

  - ex) 초기 설정에서 만약 0번 정점이 1번 정점과 연결되었을 경우 p는 다음과 같다.

    p = [0, 0, 2, 3]

    1번 정점의 부모노드를 0번 정점으로 저장하여 연결됨을 보인다.

- `mst` : mst에 확정이 된 두 정점을 저장하는 리스트
  - 즉 mst에 해당하는 간선인 경우 해당 간선의 두 정점을 저장한다.



#### 그림으로 이해하기!

![쿠르스칼 그림1](https://user-images.githubusercontent.com/60081201/107766639-183b3000-6d77-11eb-89b8-c0071d2bb7dc.JPG)



![크루스칼 그림2](https://user-images.githubusercontent.com/60081201/107766645-1a04f380-6d77-11eb-8ac8-8a3c4e4c5dd2.JPG)



![크루스칼 그림3](https://user-images.githubusercontent.com/60081201/107766644-196c5d00-6d77-11eb-84d9-57ede8db401f.JPG)



### Kruskal MST 코드 (python)

```python
def find(u): # u의 최상위 부모 노드를 반환하는 함수
    if u != p[u]: # u의 최상위 부모 노드가 아니기에 다시 find 함수 호출
        p[u] = find(p[u])
    return p[u] # 최상위 부모 노드를 찾아 반환!


def union(u, v): # u, v를 간선을 연결하는 함수
   # u와 v의 최상위 부모 노드를 찾아 포함시키기 위해 부모 노드를 갱신한다.
   root1 = find(u)
   root2 = find(v)
   p[root2] = root1


# graph : 연결된 정점 번호(graph[i][0], graph[i][1]), 두 정점을 연결하는 가중치(graph[i][2])의 정보를 갖는다.
graph = [
    (0, 1, 13), (0, 2, 5), (1, 3, 9), (2, 3, 15),
    (2, 4, 3), (3, 4, 1), (3, 5, 7), (4, 5, 2)
    ]
graph.sort(key = lambda x: x[2]) # 가중치 오름차순으로 정렬한다.

mst = [] # mst에 포함되는 간선의 정보를 저장할 리스트
n = 6 # 정점의 개수
p = [i for i in range(n)] # 부모 노드를 저장하는 리스트

tree_edges = 0 # 간선 개수
mst_cost = 0 # mst 최소 가중치 합

while True:
    if tree_edges == n - 1: # mst 조건(종료 조건)
        break
    u, v, wt = graph.pop(0)

    if find(u) != find(v): # 서로 다른 집합에 속해 있으면(사이클이 없는 경우로 연결 가능!)
        union(u, v) # 간선을 연결해준다.
        mst.append((u, v)) # mst 리스트에 추가한다.
        mst_cost += wt # 가중치를 더해준다.
        tree_edges += 1 # 간선이 하나 추가되었기에 해당 변수에 더해준다.

print(mst) # [(3, 4), (4, 5), (2, 4), (0, 2), (1, 3)]
print(mst_cost) # 20
```





# Prim MST 알고리즘

추후 추가될 예정입니다!



# Kruskal vs Prim 알고리즘 비교

정점의 개수 n, 간선의 개수 e 인 경우

### 시간 복잡도

- Kruskal 알고리즘 : O(eloge)
  - 간선 e개를 퀵 정렬과 같은 효율적인 알고리즘으로 정렬한다면
- Prim 알고리즘 : O(n ^ 2)
  - 반복문이 정점의 수 n만큼 반복하고 내부 반복문이 n 번 반복되기에



### 특징 비교

- Kruskal : 간선 위주 알고리즘
- Prim : 정점 위주 알고리즘



### 문제풀때 어떤 알고리즘이 적합할까?

- 그래프 내에 적은 숫자의 간선만을 가지는 희소 그래프(Sparse Graph)의 경우에 Kruskal 알고리즘이 적합하다.
- 그래프에 간선이 많이 존재하는 밀집 그래프(Dense Graph)의 경우에는 Prim 알고리즘이 적합하다.

### 