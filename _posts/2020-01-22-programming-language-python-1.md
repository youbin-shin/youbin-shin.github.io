---
title: "[Python 배우기] 1. python intro"
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



### 변수(variable)

- 변수 할당 방법 : `=`
  - python은 `=` 만으로 쉽게 할당 가능하다. javascript 처럼 let, var, const 의 선언이 필요하지 않고 C ++ 와 같이 선언할 때 `int num = 5;`와 같이 자료형을 명시하지 않아도 된다!
- 자료형 확인 : `type()`
- 메모리 주소 확인 : `id()`

```python
n = 5 # 변수 n에 5 할당하기
print(type(n)) # <class 'int'>
print(id(n))# 140723026682640

a = "abc" # 변수 a에 "abc" 할당하기
print(type(a)) # <class 'str'>
print(id(a)) # 1458891262080
```



### 입출력방법

#### 입력 `input()`

- 입력된 값은 모두 str 타입을 갖는다. 

```python
user_input = input() # 5를 입력했다면
print(user_input) # 5
print(type(user_input)) # <class 'str'>
```



#### 출력 `print()`

- `print()`를 통해 원하는 값을 출력할 수 있다. 

  ```python
  a = 10
  print(a) # 10
  
  print("python") # python
  ```

  - `end=''` : 출력할 값 마지막에 붙을 문자나 기호나 숫자를 입력해도 되고 `end=''` 그대로 사용하여 다음 출력에 한줄로 출력될 수 있도록 할 수 있다.

    ```python
    # end 사용 X 경우
    for i in range(5):
        print(i)
    """
    0
    1
    2
    3
    4
    """
    
    # end 사용 O 경우
    for i in range(5):
        print(i, end=' ')
    """
    0 1 2 3 4 
    """
    ```

  - `sep=''` : 출력할 값들의 사이에 공통적으로 추가하고 싶은 문자나 기호나 숫자가 있다면 `''` 안에 넣어주면 된다.

    ```python
    print('하나', '둘', '셋', sep='/', end='끝!')
    # 하나/둘/셋끝!
    print('하나', '둘', '셋', sep=' ', end='끝!')
    # 하나 둘 셋끝!
    ```