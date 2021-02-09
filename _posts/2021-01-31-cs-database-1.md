---
title: "[Database] SQL - SELECT문 정복하기"
author: youbin
date: 2021-01-31 11:33:00 +0800
categories: [Computer Science, Database]
tags: [Database, Computer Science, SQL, select, count, avg, sum, min, max, where, like, order by, limit, group by]
---

# SELECT

SELECT 문은 데이터를 읽을 수 있으며 특정한 테이블을 반환한다.

- 대소문자 구분없지만 키워드들은 대문자로 구분할 것이다.
- 키워드: SELECT, FROM



## 기본 구문

```sql
SELECT <column> FROM <table>
[WHERE <condition>]
[GROUP BY <column>]
[ORDER BY <column [ASC/DESC]>]
[LIMIT <integer>];
```

### 읽기

- 테이블 전체 조회할 수 있다.

  ```sql
  SELECT * FROM (table 이름);
  ```

  - `*` : 전체를 의미하여 전체 컬럼을 보여준다.
  - 특정한 칼럼을 나열하고 싶다면 `*` 부분에 나열하고 싶은 칼럼을 순서대로 작성하면 된다.

- `WHERE`을 통해 조건(condition)을 추가하여 테이블에 특정 레코드의 특정 column 조회할 수 있다.

  ```sql
  SELECT column1, ... FROM (table 이름) WHERE condition;
  ```

- `DISTINCT` 를 통해 중복 없이 조회할 수 있다.

  ```sql
  SELECT DISTINCT column FROM (table 이름);
  ```

  ```sql
  -- 예시: classmates라는 테이블에서 동명이인이 있을 경우 한 명의 이름만 조회할 수 있도록 하는 코드이다.
  SELECT DISTINCT name FROM classmates;
  ```



### 표현식

#### COUNT()

테이블에 특정 레코드의 개수를 조회한다.

```sql
SELECT COUNT(column) FROM (table 이름);
```



#### AVG()

테이블의 특정 레코드의 평균을 보여준다.

```sql
SELECT AVG(column) FROM (table 이름);
```



#### SUM()

 테이블에 특정 레코드의 합을 보여준다.
 ```sql
SELECT SUM(column) FROM (table 이름);
 ```



#### MIN()

테이블에 특정 레코드의 최소값을 보여준다.

  ```sql
SELECT MIN(column) FROM (table 이름);
  ```
   ```sql
-- 예시: classmates 테이블에 가장 어린 학생의 이름과 나이를 보여준다.
SELECT name, MIN(age) FROM classmates;
   ```



#### MAX()

테이블에 특정 레코드의 최대값을 보여준다.

  ```sql
SELECT MAX(column) FROM (table 이름);
  ```

  ```sql
-- 예시: classmates 테이블에 가장 적은 나이와 가장 많은 나이를 보여준다.
SELECT MIN(age), MAX(age) FROM classmates;
  ```



### 조건식

#### WHERE

테이블에서 특정 조건(`condition`)을 만족하는 특정 레코드를 조회할 수 있다.

```sql
SELECT column FROM (table 이름) WHERE condition;
```

- `condition`에 올 수 있는 예시
  - age>=18
  - last_name='김'
  - balance < 100000



#### AND, OR

테이블에서 **조건 2개 이상**을 만족하는 특정 레코드를 조회할 수 있다.

- `AND`: condition1과 conditioin2를 모두 만족하는 레코드를 조회한다.
- `OR`: condition1 또는 conditioin2를 만족하는 레코드를 조회한다.
  - 즉, 둘 중 하나의 조건만 만족해도 조회된다.

```sql
SELESELECT column FROM (table 이름) WHERE condition1 [AND|OR] condition2;
```

```sql
-- 예시: classmates라는 테이블에서 이름은 김이고 나이는 18살 이상을 만족하는 레코드를 조회한다.
SELECT * FROM classmates WHERE name='김' and age>=18;
```



#### LIKE

**LIKE**의 **와일드 카드**를 통해 테이블에서 특정한 패턴을 만족하는 특정 레코드를 조회할 수 있다.

```sql
SELECT * FROM (table 이름) WHERE column LIKE 'patterns';
```

```sql
-- 예시: classmates 테이블에서 phone 번호가 010-으로 시작하는 레코드를 조회할 수 있다.
SELECT * FROM classmates WHERE phone LIKE '010-%';
```

##### 와일드 카드

- `%` : 문자열이 있을 수도 있고 없을 수도 있다.
- `_` : 반드시 이자리에 '한 개'의 문자가 존재해야 한다.

|     예     |                     의미                     |
| :--------: | :------------------------------------------: |
|     2%     |               2로 시작하는 값                |
|     %2     |                2로 끝나는 값                 |
|    %2%     |               2가 들어가는 값                |
|    _2%     | 아무값이나 들어가고 두번째가 2로 시작하는 값 |
|    1___    |           1로 시작하고 4자리인 값            |
| 2_%_%/2__% |        2로 시작하고 적어도 3자리인 값        |



#### ORDER BY

특정 column 을 기준으로 정렬할 수 있다.

- `ASC`(default) : 오름차순으로 정렬한다.
- `DESC` : 내림차순으로 정렬한다.

```sql
-- column1과 column2를 ASC라면 오름차순으로 DESC라면 내림차순으로 정렬한다.
SELECT colums FROM (table 이름) ORDER BY column1, column2, ASC|DESC;
```

```sql
-- column1은 ASC 오름차순으로 column2는 DESC 내림차순으로 정렬한다.
-- 행렬 각각 정렬 조건을 줄 수 있다.
SELECT colums FROM (table 이름) ORDER BY column1 ASC column2 DESC;
```

```sql
-- 예제: classmates 테이블에서 age는 오름차순으로 name은 내림차순으로 정렬하여 조회한다.
SELECT * FROM classmates ORDER BY age ASC name DESC;
```

- 주의!  **type 이 text 일 경우** 

  숫자로 보이지만 type이 text일 경우 주의해야 한다.

  오름차순으로 정렬할 때 숫자라면 99, 100으로 보여줄 것이지만 type이 text일 경우 100, 99 순으로 정렬됨을 주의하자!



#### LIMIT

특정 table에서 원하는 개수만큼 가져올 수 있다.

```sql
SELECT colums FROM (table 이름) LIMIT num;
```

```sql
-- 예시: classmates 테이블에서 10개의 이름만 조회한다.
SELECT name FROM classmates LIMIT 10;
```

- `OFFSET` : 조회하고 싶은 레코드의 시작 번호를 줄 수 있다. 
  - 몇번째 레코드부터 출력할 지 결정하고 1번째부터면 OFFSET 0이다.

```sql
SELECT colums FROM (table 이름) LIMIT num OFFSET num;
```

```sql
-- 예시: 10행씩 페이지에 출력하는 경우 다음과 같다.
SELECT name FROM classmates LIMIT 10 OFFSET 0; -- 1페이지
SELECT name FROM classmates LIMIT 10 OFFSET 10; -- 2페이지
```



#### GROUP BY

특정 컬럼을 기준으로 그룹화 할 수 있다.

```sql
SELECT colums FROM (table 이름) GROUP BY num;
```

```sql
-- 예시: classmates 테이블에서 sex의 컬럼으로 그룹화하여 성별에 따른 수를 조회할 수 있다.
SELECT sex, COUNT(name) FROM classmates GROUP BY sex;
```

