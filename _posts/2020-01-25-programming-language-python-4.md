---
title: "[Python 배우기] 4. python 시퀀스(Sequence) 자료형"
author: youbin
date: 2020-01-22 00:34:00 +0800
categories: [Programming language, Python]
tags: [python]
toc: false
---

# python 시퀀스(sequence) 자료형

- 시퀀스는 데이터가 순서대로 나열된 형식을 나타낸다.

  ※ 주의 : 순서대로 나열된 것이 정렬되었다는 뜻이 아니다!

- 시퀀스 타입

  - list, tuple, range, string, binary

## list

- 리스트 생성 : `[]`, `list()`

## tuple

- `()`로 묶어서 표현됨.

- 튜플 생성 : `()`

- immutable (수정 불가능, 불변)하고 읽기만 가능하다.

- 직접 사용하기 보단 파이썬 내부에서 사용하고 있다.

  ```python
  # 하나의 항목으로 구성된 튜플은 값 뒤에 쉼표를 붙여서 만든다.
  mytuple = ('hello', )
  print(type(mytuple)) # <class 'tuple'>
  print(len(mytuple)) # 1
  ```

## range()

- 기본형 : range(n)
- 범위 지정 : range(n, m)
- 범위 및 스텝 지정: range(n, m, s)

#### 시퀀스에서 활용가능한 연산자/함수

| operation      | 설명                         |
| -------------- | ---------------------------- |
| x `in` s       | containment(연결, 연쇄) test |
| x `not in` s   | containment test             |
| s1 `+` s2      | concatenation                |
| s `*` n        | n번만큼 반복하여 더하기      |
| s[i]           | indexing                     |
| s[i: j]        | slicing                      |
| s[i: j: k]     | k만큼으로 slicing            |
| len(s)         | 길이                         |
| min(s), max(s) | 최솟값, 최댓값               |
| s.count(x)     | x의 개수                     |

## set, dictionary

### set 

- 순서가 없는 자료구조

- 집합과 동일, 중복 X

- 빈 집합 생성 : `set()`

  ※ 주의 `{}` 사용 불가능

| 연산자/함수                  | 설명   |
| ---------------------------- | ------ |
| a`-` b , a`.difference(b)`   | 차집합 |
| a `|` b, a`.union(b)`        | 합집합 |
| a `&` b, a`.intersection(b)` | 교집합 |

### dictionary

- key, value 쌍으로 이뤄져있음.
- 빈 딕셔너리 생성 : `{}`, `dict()`
- key : immutable 한 모든 것 가능
  - 불변값 : string, integer, float, boolean, tuple, range
  - key 가 중복되는 경우 마지막 value로 입력된다.
- value : list, dictionary 포함한 모든 것이 가능하다.
- 메소드
  - `.keys()` : key 확인 가능
  - `.values()` : value 확인 가능
  - `.items()` : key, value 확인 가능

## 데이터 타입 정리

- Sequence(Ordered)
  - 'String' - immutable
  - [list] - mutable
  - (tuple) - immutable
  - range() - immutable
- Unordered
  - {set} - mutable
  - {dictionary: } - mutable

### + 출력하기 print

```python
print('하나', '둘', '셋', sep='/', end='끝!')
# 하나/둘/셋끝!
```





