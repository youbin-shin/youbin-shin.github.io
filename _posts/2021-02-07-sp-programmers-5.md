---
title: "[programmers] SQL 고득점 Kit - IS NULL 문제 답모음 (MySQL)"
author: youbin
date: 2021-02-07 12:33:00 +0800
categories: [Solve coding problems, programmers]
tags: [programmers, select, sql, IS NULL, MySQL]
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

