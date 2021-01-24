---
title: Python | 1. python intro
author: youbin
date: 2020-01-22 00:34:00 +0800
categories: [Programming language, Python]
tags: [python, keyword, comment]
toc: false
---

# python intro

### 식별자

> 식별자 : 변수, 함수, 모듈, 클래스 등을 식별하는데 사용되는 이름(name)

- 식별자의 이름은 영문 대소문자, 밑줄, 숫자로 구성된다.
- 첫 글자에 숫자가 올 수 없다.
- 길이 제한이 없다.
- 대소문자(case)를 구별한다.
- 내장 함수나 모듈 등의 이름으로도 만들면 안된다.

```python
# 예약어 확인하기
import keyword
print(keyword.kwlist)
```

### 주석 (Comment)

- 주석은 `#`으로 표현한다.
- docstring은 `"""`으로 표현한다.
  - 여러 줄 주석을 작성 가능하다.
  - 보통 함수/클래스 선언 다음에 해당하는 설명을 위해 활용한다.

```python
# docstring 확인하기
def myfun(a):
    """ 이 함수의 docstring
    확인하려면?
    """
    return a

print(myfun.__doc__)
```

### 코드 라인

- 기본적으로 파이썬에서 `;` 작성하지 않는다.

- 한 줄로 표기할 때 `;` 작성하여 표기 가능하다.

- 줄을 여러줄 작성할 때는 `/` 역슬래시를 사용하면 된다.

  ```python
  print('/
        오류안뜬다! 출력가능')
  ```

  - [], {}, () 는 `/` 없이도 가능하다.

### 변수(variable) 및 자료형

- 변수 할당 방법 : `=`
- 자료형 확인 : `type()`
- 메모리 주소 확인 : `id()`

#### 숫자형 (Numbers)

##### int (정수, ingtegers)

- 모든 정수는 `int`로 표현된다.

- python 3.x 버전에서 `long` 타입 없다.

- 진수 표현

  - 8진수 : `0o`
  - 2진수 : `0b`
  - 16진수 : `0x`

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

- 파이썬에서 표현 가능한 가장 큰 수

  - overflow 일어나지 않는다.

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

##### float (부동소수점, 실수, floating point numbers)

- round()

  - 0~4 내림
  - 5는 짝수면 내림, 혹수에선 올림하여 반올림된다.

  ```python
  round(3.5 - 3.12, 2) # 0.38
  ```

##### complex (복소수, complex numbers)

```python
a = 3 - 4j
type(a) # complex
print(a.real) # 3.0
print(a.imag) # -4.0
print(a.conjugate()) # (3+4j) 켤레 복소수

complex('1+2j') # 복소수로 반환 (이때 공백있으면 안된다.)
```

#### bool

- True 와 False로 이뤄진 bool 타입

- False 반환

  0, 0.0, (), [], {}, '', None

#### None

```python
type(None) # Nonetype

a = None
print(a) # None
```

#### 문자열 (String)

- 사용자에게 받은 입력은 기본적으로 str 이다.

- 이스케이프 시퀀스

  문자열을 활용하는 경우 특수문자 혹은 조작을 하기 위해 사용되는 것으로 `/` 활용하여 구분한다.

  | 예약 문자 | 내용 (의미) |
  | :-------: | :---------: |
  |    /n     |   줄 바꿈   |
  |    /t     |     탭      |
  |    /r     | 캐리지리턴  |
  |    /0     |   널 Null   |
  |    //     |      /      |
  |    /'     |      '      |
  |    /''    |     ''      |

- String interpolation

  - % - formatting

  - str.format()

  - f-strings (파이썬 3.6 이후 버전에서 지원)

    ```python
    # f-strings 형식 지정 예시

    # 1. datetime 모듈
    from datetime import datetime
    today = datetime.now()
    print(today) # 2020-01-20 16:31:51.328290

    print(f'{today:%Y}년 {today:%m}월 {today:%d}일 {today:%A}') # '오늘은 2020년 01월 20일 Monday'

    # 2. 숫자 출력 형식 지정
    pi = 3.141592
    print(f'원주율 {pi:.4}. 반지름 2인 원의 넓이 {pi*2*2:.2}') # 원주율 3.142 반지름 2인 원의 넓이 1.3e+01

    # 3. 천단위 구분 인자
    price = 15000
    print(f'{price:,}') # 15,000
    ```
