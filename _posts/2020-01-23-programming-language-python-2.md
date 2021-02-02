---
title: "[Python 배우기] 2. python 자료형"
author: youbin
date: 2020-01-23 00:34:00 +0800
categories: [Programming language, Python]
tags: [python, type, complex, bool]
toc: false

---

# python 자료형

## 숫자형 (Numbers)

### int (정수, integers)

- 모든 정수는 `int`로 표현된다.
- python 3.x 버전에서 `long` 타입 없다.

```python
num = 3
print(type(num)) # 출력: <class 'int'>
```



#### 진수 변환하는 방법

##### 10진수 → 2진수, 8진수, 16진수

###### 1. `bin()`, `oct()`, `hex()`내장 함수 이용

```python
print(bin(10)) # 출력: 0b1010
print(oct(10)) # 출력: 0o12
print(hex(10)) # 출력: 0xa
print(hex(16)) # 출력: 0x10
```

###### 2. `format()` 내장함수 이용

```python
print(format(8, '#b')) # 출력: 0b1000
print(format(8, '#o')) # 출력: 0o10
print(format(8, '#x')) # 출력: 0x8

# #을 제거해주면 변환된 값 자체만 출력 가능하다.
print(format(8, 'b')) # 출력: 1000
print(format(8, 'o')) # 출력: 10
print(format(8, 'x')) # 출력: 8
```

###### 3. `0b`, `0o`, `0x` 이용

- 2진수 : `0b` + (2진수로 바꾸고싶은 10진수)
- 8진수 : `0o` + (8진수로 바꾸고싶은 10진수)
- 16진수 : `0x` + (16진수로 바꾸고싶은 10진수)

```python
binary_number = 0b10
octal_number = 0o10
decimal_number = 10
hexadecimal_number = 0x10
print(f"""
2진수 : {binary_number}
8진수 : {octal_number}
10진수 : {decimal_number}
16진수 : {hexadecimal_number}
""")

# 출력
# 2진수 : 2
# 8진수 : 8
# 10진수 : 10
# 16진수 : 16
```



##### 2진수, 8진수, 16진수 → 10진수

###### `int` 함수 이용

```python
print(int('0b1010', 2)) # 출력: 10
print(int('0o12', 8)) # 출력: 10
print(int('0xa', 16)) # 출력: 10
```



- 파이썬에서 표현 가능한 가장 큰 수

  #### overflow가 발생하지 않는다!

  > overflow : 메모리 크기 제한으로 표현 가능한 수의 범위를 넘어갈 때 출력이 제대로 안되는 현상

  ```python
  # 가장 큰 수 출력하기
  import sys
  max_int = sys.maxsize
  # sys.maxsize 의 값은 2**63 - 1 => 64 비트에서 부호비트를 뺀 63개의 최대 치
  print(max_int)
  super_max = max_int * max_int
  print(super_max) # 출력 가능 (overflow 일어나지 X)
  ```

  

### float (부동소수점, 실수, floating point numbers)

모든 실수는 `float`으로 표현된다.

```python
a = 3.12
print(type(a)) # 출력: <class 'float'>
```

- 반올림하기 : `round()`

  - 0~4 내림
  - 5는 짝수면 내림, 혹수에선 올림하여 반올림된다.

  ```python
  round(3.5 - 3.12, 2) # 출력: 0.38
  ```

  

### complex (복소수, complex numbers)

```python
a = 3 - 4j
type(a) # 출력: complex
print(a.real) # 출력: 3.0
print(a.imag) # 출력: -4.0
print(a.conjugate()) # 출력: (3+4j) 켤레 복소수

complex('1+2j') # 복소수로 반환 (이때 공백있으면 안된다.)
```

---

## bool

- True 와 False로 이뤄진 bool 타입

- False 반환

  0, 0.0, (), [], {}, '', None

```python
a = True
print(type(a)) # 출력: <class 'bool'>
```

---

## None

```python
type(None) # Nonetype

a = None
print(a) # 출력: None
```

---

## 문자열 (String)

- 사용자에게 받은 입력은 기본적으로 str 이다.

  ```python
  user_input = input()
  print(type(user_input)) # <class 'str'>
  ```

  

- **이스케이프 시퀀스**

  : 문자열을 활용하는 경우 특수문자 혹은 조작을 하기 위해 사용되는 것으로 `/` 활용하여 구분한다.

  | 예약 문자 | 내용 (의미) |
  | :-------: | :---------: |
  |    /n     |   줄 바꿈   |
  |    /t     |     탭      |
  |    /r     | 캐리지리턴  |
  |    /0     |   널 Null   |
  |    //     |      /      |
  |    /'     |      '      |
  |    /''    |     ''      |

  ```python
  print("줄바꾸기\n탭하기\t널\0슬라이스\\작은따옴표\'큰따옴표\"")
  
  """
  출력값
  줄바꾸기
  탭하기	널 슬라이스\작은따옴표'큰따옴표"
  """
  ```

  

- String interpolation

  - % - formatting

  - str.format()

  - f-strings (파이썬 3.6 이후 버전에서 지원)

    1. datetime 모듈

       ```python
       from datetime import datetime
       today = datetime.now()
       
       print(today) # 출력: 2020-01-20 16:31:51.328290
       
       print(f'{today:%Y}년 {today:%m}월 {today:%d}일 {today:%A}')
       # 출력: '오늘은 2020년 01월 20일 Monday'
       ```

    2. 숫자 출력 형식 지정

       ```python
       pi = 3.141592
       print(f'원주율 {pi:.4}. 반지름 2인 원의 넓이 {pi*2*2:.2}')
       # 출력: 원주율 3.142 반지름 2인 원의 넓이 1.3e+01
       ```

    3. 천단위 구분 인자

       ```python
       price = 15000
       
       print(f'{price:,}')
       # 출력: 15,000
       ```

       