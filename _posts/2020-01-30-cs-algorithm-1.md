---
title: "[Algorithm] chapter 2. Array1"
author: youbin
date: 2020-01-31 11:33:00 +0800
categories: [Computer Science, Algorithm]
tags: [Algorithm, Computer Science, CS, array]
---

# 배열

- 일정한 자료형의 변수들을 하나의 이름으로 열거하여 사용하는 자료구조입니다.

  - 여기서 자료형(Data types)은 정수형(integer, long), 실수형(float, double), 문자형(char) 을 의미합니다.

  - 참고)

    **procedual language** (절차지향 언어)는 BASIC, C, PASCAL, FORTRAN 등이 있고

    **object-oriented language**(객체 지향 언어)는 python, Java 등이 있습니다.

    이때 객체 지향 언어의 자료형은 `절차지향 언어의 기본 자료형 + 객체(object) + 클래스(class)`를 갖습니다.

## 배열의 필요성 + 중요성

- 하나의 선언으로 둘 이상의 변수 선언 가능합니다.

  - 예를 들어 num 이라는 2차원 배열을 보면 다음과 같습니다.

    num = [ [1,2], [3,4], [5,6] ] # num은 3행 2열인 2차원 행렬입니다.

## 배열과 관련된 문제

### 1. gravity 문제

#### 문제 설명

- 총 26개의 상자가 시계방향으로 90도 회전할 시 각 상자마다의 낙차가 가장 큰 결과를 리턴하여라.

- 입력은 다음과 같이 각 위치(index)별 상자의 수(높이) 가 주어진다.

  ```
  7 4 2 0 0 6 0 7 0
  ```

  ![questionImg](https://user-images.githubusercontent.com/60081201/105607141-8cba2900-5de0-11eb-9493-db0d38910e13.JPG)

  주어진 입력에 대한 상황은 그림과 같다.

#### 해결방법 1

1. 2차원 배열을 만들어서 상자가 있는 자리에는 1, 빈 공간에는 0을 저장한다.
2. 빈 공간의 수 상자의 오른쪽에서 왼쪽 방향으로 열마다 0의 개수를 카운트해 준다. → 낙차 구하기!
   - 이때 가장 낙차가 큰 값을 원하기에 **상자의 꼭대기의 값만** 구하면 된다.
   - 상자 가장 높은 곳의 인데스만 가져와서 0의 개수를 카운트해주면 된다.

#### 해결방법 2

1차원 배열을 이용하여 문제를 풀 수 있다.

입력값이 박스의 높이라는 점을 이용하여 각 위치(인덱스)에서 오른쪽 방향에 있는 위치의 높이를 비교하여 작은 경우를 카운트해주면 낙차를 구할 수 있다.

```python
# python 코드

box = list(map(int, input().split()))
result = []

for i in range(len(box)): # 기준이 되는 위치의 높이
    cnt = 0
    for j in range(i+1, len(box)): # 오른쪽 방향으로 기준이 되는 높이와 비교하기
        if box[i] > box[j]:
            cnt += 1
    result.append(cnt) # 각 위치별 낙차 저장하기

print(max(result))
```

### 2. baby-gin Game 문제

#### 문제 설명

- 0~9 사이의 숫자 카드에서 임의의 카드 6장을 뽑았을 때, 3장의 카드가 연속적인 번호를 갖는 경우면 run, 3장의 카드가 동일한 번호를 갖는 경우 triplet 이라 한다.

  6장의 카드가 run, triplet로만 구성될 경우 baby-gin으로 부른다.

  6자리 숫자를 입력 받아 baby-gin여부를 판단하는 프로그램을 작성하라.

- 입력은 다음과 같다.

  첫번쨰 줄에는 게임 횟수가 주어지고 이후 게임 횟수마다 6개의 숫자가 주어진다.

  주어진 숫자가 baby-gin을 만족하면 baby-gin을 아니면 fail를 출력하라.

  ```
  3
  667767
  054060
  101123
  ```

  첫번째 입력 667767은 baby-gin이고 054060도 baby-gin이다.

  101123 입력에서는 fail이 출력되어야 한다.

#### 해결 방법

1. card 라는 리스트에 주어진 카드에 대한 숫자의 수를 카운트한다.

   이때 해당 숫자가 3번 나왔을 경우(triplet), 0으로 바꿔준다.

2. 3장의 카드가 연속적인 번호를 갖는 경우(run)를 찾아 해당 경우이면 값을 -1 해준다.

3. card 리스트의 요소들이 모두 0인 경우 baby-gin이고 그렇지 않으면 fail를 출력한다.

```python
# python code

for t in range(int(input())):
    card = [0] * 10
    mycard = input()

    # 1번 과정
    for i in mycard:
        card[int(i)] += 1
        if card[int(i)] == 3: # triplet인 경우
            card[int(i)] = 0
    # 2번 과정
    for i in range(8):
        sum = card[i] + card[i+1] + card[i+2]
        if sum == 3 or sum == 6:
            for j in range(3):
                card[i+j] -= 1
	# 3번 과정
    if sum(card) == 0:
        print('babygin')
    else:
        print('fail')
```
