---
title: "[programmers] SQL 고득점 Kit - SUM, MAX, MIN 문제 답모음 (MySQL)"
author: youbin
date: 2021-02-02 12:33:00 +0800
categories: [Solve coding problems, programmers]
tags: [programmers, select, sql, sum, max, min, MySQL]
# pin: true
---

# SQL 고득점 Kit - SUM, MAX, MIN 문제 답모음 (MySQL)

##### [SQL SELECT문 개념 정리하러 가기](https://youbin-shin.github.io/posts/cs-database-1/)

### SELECT 기본 구문

```sql
SELECT <column> FROM <table>
[WHERE <condition>]
[GROUP BY <column>]
[ORDER BY <column [ASC/DESC]>]
[LIMIT <integer>];
```



## 최댓값 구하기

[**최댓값 구하기** 문제 풀러가기](https://programmers.co.kr/learn/courses/30/lessons/59415)

### Solution 1 - MAX 이용

```sql
SELECT MAX(DATETIME) FROM ANIMAL_INS;
```

- `MAX()`를 이용해서 특정 레코드의 최댓값을 구할 수 있다.

### Solution 2 - ORDER BY, LIMIT 이용

```sql
SELECT DATETIME FROM ANIMAL_INS ORDER BY DATETIME DESC LIMIT 1;
```

- `ORDER BY`를 통해 날짜를 내림차순으로 정렬하고 `LIMIT`을 이용하여 1개의 레코드를 보일 수 있도록 한다.



## 최솟값 구하기

[**최솟값 구하기** 문제 풀러가기](https://programmers.co.kr/learn/courses/30/lessons/59038)

### Solution 1 - MIN 이용

```sql
SELECT MIN(DATETIME) FROM ANIMAL_INS;
```

- `MIN()`를 이용해서 특정 레코드의 최솟값을 구할 수 있다.

### Solution 2 - ORDER BY, LIMIT 이용

```sql
SELECT DATETIME FROM ANIMAL_INS ORDER BY DATETIME LIMIT 1;
```

- `ORDER BY`를 통해 날짜를 오름차순으로 정렬하고 `LIMIT`을 이용하여 1개의 레코드를 보여 최솟값을 구할 수 있다.



## 동물 수 구하기

[**동물 수 구하기** 문제 풀러가기](https://programmers.co.kr/learn/courses/30/lessons/59406)

```sql
SELECT COUNT(*) FROM ANIMAL_INS;
```

- `COUNT` 를 이용하여 레코드의 개수를 조회한다.



## 중복 제거하기

[**중복 제거하기** 문제 풀러가기](https://programmers.co.kr/learn/courses/30/lessons/59408)

```sql
SELECT COUNT(DISTINCT NAME) FROM ANIMAL_INS WHERE NAME != "NULL";
```

- `DISTINCT`를 통해 NAME 레코드에서 중복을 제거하여 개수를 조회할 수 있도록 한다.
- `WHERE` 조건을 통해 동물의 이름이 NULL 인 경우를 제외시킨다.



