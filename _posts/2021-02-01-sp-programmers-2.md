---
title: "[programmers] SQL 고득점 Kit - SELECT 문제 정복하기"
author: youbin
date: 2021-02-01 11:33:00 +0800
categories: [Solve coding problems, programmers]
tags: [programmers, select, sql]
# pin: true
---

# SELECT

SELECT 문은 데이터를 읽어올 수 있으며 특정한 테이블을 반환한다.

- 대소문자 구분없지만 키워드들은 대문자로 구분할 것이다.
- 키워드: SELECT, FROM

### 가장 간단한 구문

```sql
SELECT * FROM (table 이름);
```

- `*` : 전체를 의미하여 전체 컬럼을 보여준다.
- 특정한 칼럼을 나열하고 싶다면 `*` 부분에 나열하고 싶은 칼럼을 순서대로 작성하면 된다.



### 기본 구문

```sql
SELECT <column> FROM <table>
[WHERE <condition>]
[GROUP BY <column>]
[ORDER BY <column [ASC/DESC]>]
[LIMIT <integer>];
```



---

## 모든 레코드 조회하기

```sql
SELECT ANIMAL_ID, ANIMAL_TYPE, DATETIME, INTAKE_CONDITION, NAME, SEX_UPON_INTAKE FROM ANIMAL_INS
```

## 역순 정렬하기

```sql
SELECT NAME, DATETIME FROM ANIMAL_INS ORDER BY ANIMAL_ID DESC
```

## 아픈 동물 찾기

```sql
SELECT ANIMAL_ID, NAME FROM ANIMAL_INS WHERE INTAKE_CONDITION='Sick' ORDER BY ANIMAL_ID;
```

## 어린 동물 찾기

```sql
SELECT ANIMAL_ID, NAME FROM ANIMAL_INS WHERE INTAKE_CONDITION != 'Aged';
```

## 동물의 아이디와 이름

```sql
SELECT ANIMAL_ID, NAME FROM ANIMAL_INS ORDER BY ANIMAL_ID
```

## 여러 기준으로 정렬하기

```sql
SELECT ANIMAL_ID, NAME, DATETIME FROM ANIMAL_INS ORDER BY NAME, DATETIME DESC;
```

## 상위 n개 레코드

```sql
SELECT NAME FROM ANIMAL_INS ORDER BY DATETIME LIMIT 1;
```

