---
title: "[Python 배우기] 3. python 연산자"
author: youbin
date: 2020-01-24 00:34:00 +0800
categories: [Programming language, Python]
tags: [python]
toc: false
---

# python 연산자

## 산술 연산자

### 더하기 `+`

```python
a = 3
b = 2
c = a + b
print(c) # 출력: 5
print(10 + 20) # 출력: 30
```

### 빼기 `-`

```python
a = 5
b = 2
c = a - b
print(c) # 출력: 3
print(10 - 20) # 출력: -10
```

### 곱하기 `*`

```python
a = 3
b = 2
c = a * b
print(c) # 출력: 6
print(10 * 20) # 출력: 200
```

### 나누기 `/`

```python
a = 3
b = 2
c = a / b
print(c) # 출력: 1.5
print(10 / 20) # 출력: 0.5
```

#### 몫 구하기 `//`

```python
a = 10
b = 5
c = a // b
print(c) # 출력: 2
```

#### 나머지 구하기 `%`

```python
a = 10
b = 6
c = a % b
print(c) # 출력: 4
```

#### 몫과 나머지 한번에 구하기 `divmod`

몫과 나머지 한번에 구할 수 있다.

```python
print(divmod(5, 2)) # (2, 1) : 2가 몫, 1이 나머지 값

a, b = divmod(5, 2)
print(a) # 2
```

### 거듭제곱 구하기 `**`

```python
a = 10
b = 3
print(a ** b) # 출력: 1000
print(2 ** 3) # 출력: 8
```

## 비교 연산자

- <, <=, >, >=, ==, !=
- is (객체 아이텐티티), is not (부정된 객체 아이덴티티)

## 논리 연산자

- a and b, a or b, not a

- 단축평가

  - 첫번째 값이 확실할 때 두번째 값 확인하지 않음.

  - 조건문에서 뒷부분을 판단하지 않아도 되기 때문에 속도 향상

    ```python
    vowels = 'aeiou'
    print(('b' and 'a') in vowels) # True
    ```

## 기타 연산자

### Concatenation

```python
print('hi ' + 'bye') # hi bye
print([1, 2, 3] + [4, 5, 6]) # [1, 2, 3, 4, 5, 6]
```

### Containment Test

`in` 연산자를 통해 요소 속해있는지 여부 확인 가능

```python
print('a' in 'apple') # True
print(1 in [1, 2, 3]) # True
print(5 in range(5)) # False
```

### Identity

`is` 연산자를 통해 동일한 object 인지 확인 가능

- 파이썬에서 -5 ~ 256 까지는 id 동일

  ```python
  a = 3
  b = 3
  print(a == b) # True
  print(a is b) # True
  
  a = 257
  b = 257
  print(a == b) # True
  print(a is b) # False
  ```

### Indexing/Slicing

`[]`을 통한 값을 접근하고 `[:]`로 리스트 슬라이싱 가능

## 연산자 우선 순위

1. `()` 통한 grouping

2. Slicing

   ```python
   a = [0, 10, 20, 30, 40, 50, 60, 70, 80, 90]
   a[1:1] # []
   a[4: -1] # [40, 50, 60, 70, 80] (인덱스 4부터 -2까지의 요소를 가져옴)
   a[2: 8: 3] # [20, 50]
   a[::-1] # [90, 80, 70, 60, 50, 40, 30, 20, 10, 0]
   ```

3. Indexing

4. `**`

5. 단항 연산자 `+`, `-` (음수/양수 부호)

6. 산술 연산자 `*`, `/`, `%`

7. 산술 연산자 `+`, `-`

8. 비교 연산자, `in`, `is`

9. `not`

10. `and`

11. `or`

## 명시적 형변환 (Explicit Type Conversion)

- string --> integer (형식에 맞는 숫자만 가능)

- integer --> string (모든 가능)

  ---

- `int()` : string, float --> int

- `float()` : string, int --> float

- `str()` : int, float, list, tuple, dictionary --> 문자열

