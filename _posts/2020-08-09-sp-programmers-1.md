---
title: programmers | 두 개 뽑아서 더하기
author: youbin
date: 2020-08-09 11:33:00 +0800
categories: [Solve coding problems, programmers]
tags: [programmers, python, javascript]
# pin: true

---

# [programmers | 두 개 뽑아서 더하기](https://programmers.co.kr/learn/courses/30/lessons/68644)

> 코딩 테스트 연습 > 월간 코드 챌린지 시즌 1 > 두 개 뽑아서 더하기
>
> level 1

## 구현한 코드

이중 for문을 이용하여 numbers 리스트의 서로 다른 인덱스 두 개가 다 더해지도록 한다.

이때 if문을 이용하여 answer에 없는 값만 추가하여 중복이 없도록 한다.

오름차순으로 출력하기 위해서 python에서는 sort()를 이용하면 된다.

하지만 javascript 같은 경우 sort() 만 사용할 경우 원하는 대로 동작하지 않는 경우가 있다. 예를 들면 [2, 5, 7, 9, 12]의 순으로 출력되어야 하지만 [12,2,5,7,9]의 순으로 출력되기 때문이다.

### python

```python
def solution(numbers):
    answer = []
    for i in range(len(numbers)):
        for j in range(i+1, len(numbers)):
            temp = numbers[i] + numbers[j]
            if temp not in answer:
                answer.append(temp)
    answer.sort()
    return answer
```

### javascript

- javascript로 문제푸는 것을 익히고 싶을 때 풀면 좋을 문제인 것 같다.

- tip!

  - VSC를 이용하면 변수에 let으로 선언을 안해도 동작은 하나 programmers에서 실행시 에러가 발생하므로 새로운 변수를 사용할 때 `let`, `const`, `var` 사용을 잊지 말자~! (python의 편안함에 다시 한번 감동)

  - sort() 주의하기!

    sort() 만 사용시 12가 2보다 앞에 정렬되게 된다.

```javascript
function solution(numbers) {
  let answer = [];
  let temp = 0;
  for (let i = 0; i < numbers.length - 1; i++) {
    for (let j = i + 1; j < numbers.length; j++) {
      temp = numbers[i] + numbers[j];
      if (answer.includes(temp) === false) {
        answer.push(temp);
      }
    }
  }

  answer.sort(function (a, b) {
    return a - b;
  });
  return answer;
}
```
