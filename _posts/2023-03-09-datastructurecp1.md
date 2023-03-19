---
title: "[자료구조] 챕터1 정리"
excerpt: "자료구조와 알고리즘"

categories:
  - DataStructure
tags:
  - [data_structure]

permalink: /DataStructure/cp1/

toc: true
toc_sticky: true

date: 2023-03-09
last_modified_at: 2023-03-09 
---

## 자료구조?
자료구조 (data structure)란 데이터를 구조적으로 표현하는 방식과, 이를 구현하는 데 필요한 알고리즘을 말한다.

현실 세계의 다차원 데이터를 1차원인 컴퓨터 메모리에서 다루는 방법을 익히는 것이다.

사용한 교재는 'C언어로 쉽게 풀어쓴 자료구조' 3판이다.

책에서 예제 설명을 C로 하고 있기 때문에, 자료구조 포스팅에서는 C를 주 언어로 사용할 것 같다.

---

## Cp1. 자료구조와 알고리즘

자료구조와 알고리즘은 밀접한 관계가 있다. 자료의 빠른 저장, 검색, 분석, 전송을 위해서는 잘 조직된 자료구조와 적합한 알고리즘이 필요하다.

+ 알고리즘(algorithm) : 주어진 문제를 처리하는 절차
    + 0개 이상의 입력
    + 1개 이상의 출력
    + 절차의 의미가 모호하지 않아야 함
    + 절차의 수가 유한해야 함
    + 각 절차는 실행 가능한 연산으로 이루어져 있어야 함

알고리즘에는 입력은 없어도 되지만, 반드시 하나 이상의 출력이 있어야 한다.  

### 알고리즘의 성능 분석

알고리즘의 복잡도를 고려해 알고리즘의 전체적인 성능을 분석한다.  
복잡도는 두 분야에서 볼 수 있다.  
+ 시간 복잡도(time complexity) : 알고리즘이 실행되는 데 걸리는 시간(연산의 횟수)을 나타낸 것.
+ 공간 복잡도(space complexity) : 알고리즘이 실행될 때 필요한 메모리 공간(자원)을 나타낸 것.
    + 하드웨어의 발전에 따라 공간 복잡도는 시간 복잡도에 비해 중요성이 떨어졌다.

### 빅오 표기법

빅오 표기법(big-O notation)이란 알고리즘이 해당 차수 또는 그보다 낮은 차수의 시간복잡도를 가진다는 표기이다.  
즉, 빅오 표기법은 시간 복잡도의 상한값(최악의 경우)을 간단하게 나타낸다.

중학교 때 '극한'이라는 개념을 배우게 된다. 무한대로 증가하는 변수에 따른 변화를 예상하는 것이다.  
빅오 표기법도 극한과 일맥상통한다. 

+ 입력의 갯수가 n일 때 A 알고리즘은 실행되는 데 1000*n^2 + 1000n + 30 번의 연산 횟수를,
B 알고리즘은 n^3 - 1000000n - 100000 번의 연산 횟수를 가질 때 더 효율적인 알고리즘은 무엇인가?

A, B 알고리즘의 시간 복잡도를 빅오 표기법으로 나타내 보면 O(n^2), O(n^3)이다.
빅오 표기법을 토대로 생각해보면 더 효율적인 알고리즘은 A알고리즘이다.  
n이 커지면 커질수록, 알고리즘이 실행해야 할 연산의 수는 차수의 영향을 크게 받는다.  
위 A, B 알고리즘은 극단적인 예지만, 보통 시간복잡도 함수에서 가장 차수가 큰 하나의 항만을 고려하면 충분하다.

아래 그림은 차수의 시간복잡도의 크기를 순서별로 나타낸 것이다.

![big_o_complexity](/assets/images/data_structure/big_o_complexity.png)

### 의사 코드

알고리즘을 기술하는 방법에는 제한이 없지만, 모호성을 제거하기 위해 프로그래밍 언어나 의사 코드(pseudo code)를 사용한다.

+ 배열에서 최대값을 찾는 경우
 ```
 findArrayMax(list, N)
    largest = list[0]
    for i=1 to N-1 do
        if list[i] > largest
            then largest = list[i]
    return largest
 ```

 위의 의사 코드는 쉽게 알아볼 수 있다.  
 1. 배열과 배열의 크기를 입력으로 받고, 배열의 첫 번째 원소를 largest에 저장한다.
 1. 배열의 두 번째 원소부터 마지막 원소까지 largest와 비교하고, 해당 원소가 largest보다 크다면 largest에 대입한다.
 1. 배열을 모두 탐색했다면 largest를 출력한다.

 ---

## 추상 자료형

추상 자료형(abstract data type)이란 자료들과 그 자료들에 대한 연산들을 명시한 것이다.  
추상 자료형은 구체적인 구현 방법은 포함하지 않고, 단순히 추상화만 제공할 뿐이다.

### 추상 자료형의 예
 
+ 정수 추상 자료형 int

```
object : 0 ~ INT_MAX 사이의 정수

function : 
boolean is_zero (int x)
    if (x == 0)
        retrun true
    else
        return false

boolean is_equal (int x, int y)
    if (x == y)
        return true
    else
        return false

int add (int x, int y)
    return x+y

int sub (int x, int y)
    return x-y

int mul (int x, int y)
    return x*y

int div(int x., int y)
    return x/y

int mod (int x, int y)
    return x%y
```

위와 같이 추상 자료형은 객체와 그 객체에 대한 연산(메서드)를 정의한다.

---

1장에는 별 내용이 없다.
