---
title: "[programmers] SQL 고득점 Kit - GROUP BY 문제 답모음 (MySQL)"
author: youbin
date: 2021-02-04 10:33:00 +0800
categories: [Solve coding problems, programmers]
tags: [programmers, select, sql, group by, MySQL]
# pin: true
---

# SQL 고득점 Kit - GROUP BY 문제 답모음 (MySQL)

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



## 고양이와 개는 몇 마리 있을까

[**고양이와 개는 몇 마리 있을까** 문제 풀러가기](https://programmers.co.kr/learn/courses/30/lessons/59040)

```sql
SELECT ANIMAL_TYPE, COUNT(ANIMAL_TYPE) AS COUNT
FROM ANIMAL_INS
GROUP BY ANIMAL_TYPE
ORDER BY ANIMAL_TYPE;
```

- `GROUP BY` 란 레코드의 값이 같은 것끼리 하나로 묶어주는 것이다.
  - ANIMAL_TYPE으로 묶어 Cat과 Dog가 몇 마리인지 정리할 수 있다.
- 고양이가 개보다 먼저 조회되기 위해 `ORDER BY`를 사용하였다.





## 동명 동물 수 찾기

[**동명 동물 수 찾기** 문제 풀러가기](https://programmers.co.kr/learn/courses/30/lessons/59041)

```sql
SELECT NAME, COUNT(NAME) AS COUNT
FROM ANIMAL_INS
GROUP BY NAME
HAVING COUNT(NAME) >= 2
ORDER BY NAME;
```

- **레코드를 그룹화하여 조건 처리**하여 문제 풀고자 다음의 기본 구조를 변형하였다.

  ```sql
  SELECT <column> FROM <table> GROUP BY <그룹화할 컬럼> HAVING <조건식>;
  ```

- NAME으로 그룹화하여 동물 이름 중 두 번 이상 쓰인 이름을 찾기 위해 `HAVING` 을 통해 구현하였다.





## 입양 시각 구하기(1)

[**입양 시각 구하기(1)** 문제 풀러가기](https://programmers.co.kr/learn/courses/30/lessons/59412)

```sql
SELECT HOUR(DATETIME) AS HOUR, COUNT(DATETIME) AS COUNT
FROM ANIMAL_OUTS
GROUP BY HOUR(DATETIME)
HAVING 9 <= HOUR AND HOUR <= 19
ORDER BY HOUR;
```

- DATETIME에 시간대별로 조회하기 위해 `GROUP BY`를 HOUR(DATETIME)하고 `HAVING`을 통해 조회하고 싶은 9시부터 19시까지의 시간대의 조건을 두었다.
- 시간대 별로 정렬하기 위해 `ORDER BY` 을 사용한다.





## 입양 시각 구하기(2)

[**입양 시각 구하기(2)** 문제 풀러가기](https://programmers.co.kr/learn/courses/30/lessons/59413)

```sql
SET @HOUR = -1;
SELECT
    (@HOUR := @HOUR + 1) AS HOUR,
    (SELECT COUNT(*) FROM ANIMAL_OUTS WHERE HOUR(DATETIME) = @HOUR) AS COUNT
FROM ANIMAL_OUTS
WHERE @HOUR < 23;
```

- 입양 시간대를 0시부터 23시까지를 조회해야 하기에 `HOUR`의 변수를 이용한다.
- 참고) **대입 연산자**
  - `=` : 왼쪽 피연산자에 오른쪽 피연산자를 대입한다. 
    - SET문이나 UPDATE 문의 SET절에서만 대입 연산자로 사용된다.
  - `:=` : 왼쪽 피연산자에 오른쪽 피연산자를 대입한다.

