---
title: "[2020 KAKAO BLIND RECRUITMENT] 외벽 점검 (python)"
author: youbin
date: 2021-02-01 11:33:00 +0800
categories: [Solve coding problems, programmers]
tags: [programmers, python, KAKAO]
# pin: true
---

### [[2020 KAKAO BLIND RECRUITMENT] 외벽 점검 문제 바로가기](https://programmers.co.kr/learn/courses/30/lessons/60062)

> 코딩테스트 연습 > 2020 KAKAO BLIND RECRUITMENT > 외벽 점검
>
> level 3



# 해결방법

모든 경우를 탐색하여 풀어야 했다.

- 경로를 어디 위치부터 선택할지는 `test_weak`를 통해 모든 경우를 탐색했다.
- 어떤 친구를 위치에 두어야할지는 `dist_list` 에 순열을 이용하여 정렬하여 모든 경우를 탐색했다.





## 주요 과정

1. `weak` 리스트에 각 원소에 `n`을 더한 값을 추가한다. → 반시계로 도는 경우 해결!

   ```python
   # 원래 주어진 weak
   weak = [1, 5, 6, 10]
   
   # 반시계로 도는 경우를 선형으로 펼쳐서 표현한 수정된 weak
   weak = [1, 5, 6, 10, 1 + 12, 5 + 12, 6 + 12, 10 + 12]
   weak = [1, 5, 6, 10, 13, 17, 18, 22]
   ```

   

2. `weak` 리스트에서 시작 지점을 선택하여 결정된 확인할 성벽 지점을  `test_weak` 에 저장하여 확인한다.

   ```python
   # test_weak은 다음과 같다.
   [1, 5, 6, 10]
   [5, 6, 10, 13]
   [6, 10, 13, 17]
   [10, 13, 17, 18]
   ```

   

3. 각 `test_weak`에 어떤 친구를 배치할지 `dist_list` 의 경우를 모두 확인한다.

   **필요한 변수**

   - `friend_idx` : 배치를 확정한 친구 인덱스
   - `cnt` : 배치 확정된 친구 수
   - `friend_max_d` ★ : `friend_idx` 의 친구가 이동할 수 있는 거리

   ------

   1. 변수에 초기 설정을 한다.

      위의 필요한 변수에 초기값을 저장한다.

   2. 외벽 점검이 가능한지 확인하기 위해 `test_weak` 의 값과 `friend_max_d`의 값을 비교한다.

      확인이 불가능한 경우 다음 친구 투입을 위해 `friend_idx` 의 값과 `cnt`의 값에 + 1 한다.

      - 투입할 친구가 없는 경우 break한다.

      - 투입할 친구가 있는 경우 `friend_max_d` 의 값 변경한다.

        새로운 친구가 투입됐기에 해당 위치(`test_weak[w]`)부터 `friend_idx`가 이동할 수 있는 거리를 더해주면 된다.

   ```python
   for d in range(len(dist_list)): # 친구들의 정렬에 따른 모든 경우 체크!
   		# 초기 설정
   		friend_idx = 0
   		cnt = 1
   		friend_max_d = test_weak[0] + dist_list[d][0] # 첫번째 친구가 이동할 수 있는 최대 거리
   		flag = True
   		# 외벽 점검 가능한지 확인하는 부분
   		for w in range(weak_n):
   		    if test_weak[w] > friend_max_d: # 확인할 수 있는 거리를 넘은 경우
   		        friend_idx += 1 # 다음 친구 투입!
   		        cnt += 1
   		        if cnt > dist_n: # 투입할 친구가 없는 경우
   		            flag = False
   		            break
   		        friend_max_d = test_weak[w] + dist_list[d][friend_idx] # 최대 확인할 수 있는 거리 갱신
   		if flag and answer > cnt:
   		    answer = cnt
   ```

   

4. 가장 작은 친구수가 투입되는 경우 `answer`을 갱신하고 변화가 없는 경우 `answer`에 -1 을 저장한다.



## 구현한 코드

```python
from itertools import permutations

def solution(n, weak, dist):
    weak_n = len(weak)
    dist_n = len(dist)
    for i in range(weak_n): # 반시계 방향을 선형으로 만들기
        weak.append(weak[i] + n)

    answer = dist_n + 1
    dist_list = list(permutations(dist, dist_n)) # 순열을 이용하여 친구들의 거리를 정렬하는 모든 경우의 수 저장!

    for j in range(weak_n):
        # test_weak : 시작할 j를 정해 체크 가능한 성벽 리스트를 저장한다.
        test_weak = [weak[k] for k in range(j, j + weak_n)]
        for d in range(len(dist_list)): # 친구들의 정렬에 따른 모든 경우 체크!
            # 초기 설정
            friend_idx = 0
            cnt = 1
            friend_max_d = test_weak[0] + dist_list[d][0] # 첫번째 친구가 이동할 수 있는 최대 거리
            flag = True
            # 외벽 점검 가능한지 확인하는 부분
            for w in range(weak_n):
                if test_weak[w] > friend_max_d: # 확인할 수 있는 거리를 넘은 경우
                    friend_idx += 1 # 다음 친구 투입!
                    cnt += 1
                    if cnt > dist_n: # 투입할 친구가 없는 경우
                        flag = False
                        break
                    friend_max_d = test_weak[w] + dist_list[d][friend_idx] # 최대 확인할 수 있는 거리 갱신
            if flag and answer > cnt:
                answer = cnt
    if answer == dist_n + 1: answer = -1 # 외벽 점검이 불가능한 경우 -1로 출력할 조건
    return answer
```





## 참고) 유용한 반례

- solution(30, [0, 3, 11, 21], [10, 4]) # 정답2
- solution(200, [0, 100], [1, 1])) # 정답 2

