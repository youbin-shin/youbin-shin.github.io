---
title: "[programmers] SQL 고득점 Kit - IS NULL 문제 답모음 (MySQL)"
author: youbin
date: 2021-02-06 12:33:00 +0800
categories: [Solve coding problems, programmers]
tags: [programmers, select, sql, "IS NULL", MySQL]
# pin: true
---

# SQL 고득점 Kit - IS NULL 문제 답모음 (MySQL)

##### [SQL SELECT문 개념 정리하러 가기](https://youbin-shin.github.io/posts/cs-database-1/)

> SELECT 기본 구문
>
> ```sql
> SELECT <column> FROM <table>
> [WHERE <condition>]
> [GROUP BY <column>]
> [ORDER BY <column [ASC/DESC]>]
> [LIMIT <integer>];
> ```



## 이름이 없는 동물의 아이디

[**이름이 없는 동물의 아이디** 문제 풀러가기](https://programmers.co.kr/learn/courses/30/lessons/59039)

```sql
SELECT ANIMAL_ID
FROM ANIMAL_INS
WHERE NAME IS NULL
ORDER BY ANIMAL_ID;
```

- NAME이 없는 조건을 두기 위해 `IS NULL`을 이용한다.



## 이름이 있는 동물의 아이디

[**이름이 있는 동물의 아이디** 문제 풀러가기](https://programmers.co.kr/learn/courses/30/lessons/59407)

```sql
SELECT ANIMAL_ID
FROM ANIMAL_INS
WHERE NAME IS NOT NULL
ORDER BY ANIMAL_ID;
```

- NAME이 있는 조건을 만족하기 위해 `IS NOT NULL`을 이용한다.




## NULL 처리하기

[**NULL 처리하기** 문제 풀러가기](https://programmers.co.kr/learn/courses/30/lessons/59410)

```sql
SELECT ANIMAL_TYPE, IFNULL(NAME, "No name"), SEX_UPON_INTAKE 
FROM ANIMAL_INS;
```

- `IFNULL(컬럼명, NULL 시 값);` 을 통해 NAME이 NULL일 경우 "No name"으로 보이도록 한다.

