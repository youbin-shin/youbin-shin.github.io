---
title: "[programmers] SQL 고득점 Kit - SELECT 문제 답모음"
author: youbin
date: 2021-02-01 11:33:00 +0800
categories: [Solve coding problems, programmers]
tags: [programmers, select, sql]
# pin: true
---

# SQL 고득점 Kit - SELECT 문제 답모음

##### [SQL SELECT문 개념 정리하러 가기](https://youbin-shin.github.io/posts/cs-database-1/)

### SELECT 기본 구문

```sql
SELECT <column> FROM <table>
[WHERE <condition>]
[GROUP BY <column>]
[ORDER BY <column [ASC/DESC]>]
[LIMIT <integer>];
```



## 모든 레코드 조회하기

[**모든 레코드 조회하기** 문제 풀러가기](https://programmers.co.kr/learn/courses/30/lessons/59034)

```sql
SELECT ANIMAL_ID, ANIMAL_TYPE, DATETIME, INTAKE_CONDITION, NAME, SEX_UPON_INTAKE FROM ANIMAL_INS
```



## 역순 정렬하기

[**역순 정렬하기** 문제 풀러가기](https://programmers.co.kr/learn/courses/30/lessons/59035)

```sql
SELECT NAME, DATETIME FROM ANIMAL_INS ORDER BY ANIMAL_ID DESC
```

- `ORDER BY` 를 이용하여 내림차순(역순)으로 정렬되도록 한다.



## 아픈 동물 찾기

[**아픈 동물 찾기** 문제 풀러가기](https://programmers.co.kr/learn/courses/30/lessons/59036)

```sql
SELECT ANIMAL_ID, NAME FROM ANIMAL_INS WHERE INTAKE_CONDITION='Sick' ORDER BY ANIMAL_ID;
```

- `WHERE` 을 이용하여 아픈 동물의 조건을 추가한다.
- `ORDER BY`를 통해 ANIMAL_ID 아이디 순으로 조회할 수 있도록 한다.



## 어린 동물 찾기

[**어린 동물 찾기** 문제 풀러가기](https://programmers.co.kr/learn/courses/30/lessons/59037)

```sql
SELECT ANIMAL_ID, NAME FROM ANIMAL_INS WHERE INTAKE_CONDITION != 'Aged';
```

- `WHERE`을 통해 젊은 동물의 조건을 만족한다.



## 동물의 아이디와 이름

[**동물의 아이디와 이름** 문제 풀러가기](https://programmers.co.kr/learn/courses/30/lessons/59403)

```sql
SELECT ANIMAL_ID, NAME FROM ANIMAL_INS ORDER BY ANIMAL_ID
```

- `ORDER BY`를 통해 ANIMAL_ID 순으로 조회되도록 한다.



## 여러 기준으로 정렬하기

[**여러 기준으로 정렬하기** 문제 풀러가기](https://programmers.co.kr/learn/courses/30/lessons/59404)

```sql
SELECT ANIMAL_ID, NAME, DATETIME FROM ANIMAL_INS ORDER BY NAME, DATETIME DESC;
```

- `ORDER BY` 를 통해 NAME 순으로 조회되도록 한다.

- 아래의 문제 조건을 만족하기 위해 DATETIME DESC 조건을 추가한다.

  > 단, 이름이 같은 동물 중에서는 보호를 나중에 시작한 동물을 먼저 보여줘야 합니다.



## 상위 n개 레코드

[**상위 n개 레코드** 문제 풀러가기](https://programmers.co.kr/learn/courses/30/lessons/59405)

```sql
SELECT NAME FROM ANIMAL_INS ORDER BY DATETIME LIMIT 1;
```

- `ORDER BY`를 통해 DATETIME를 오름차순으로 정렬하고 `LIMIT`을 통해 1개의 레코드만 보이도록 한다.