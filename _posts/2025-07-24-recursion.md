---
title: "(토픽)재귀함수"
date: 2025-07-24
categories: [알고리즘]
tags: [재귀함수, Python]
---

# 재귀함수란?

스스로를 호출하는 함수

## 예시 코드
```python
def factorial(n):
    if n == 0:
        return 1
    return n * factorial(n-1)
```


---

## 🔢 5번: 재귀함수 - 팰린드롬 & 거듭제곱 정리

### 🧩 1. 팰린드롬 (Palindrome)

| 내용      | 설명                                         |
| ------- | ------------------------------------------ |
| 정의      | 앞뒤로 읽어도 같은 문자열 (`기러기`, `racecar`, `12321`) |
| 사용 조건   | for / while 없이 **재귀 함수만** 사용               |
| 핵심 아이디어 | 첫 문자와 마지막 문자를 비교하며 점점 안쪽으로 줄여가기            |

#### ✅ 코드(예시답안):재귀 방식

```python
def is_palindrome(my_str):
    if len(my_str) <= 1:
        return True
    if my_str[0] != my_str[-1]:
        return False 
    return is_palindrome(my_str[1: -1])
```
#### ✅ 코드(작성답안): 슬라이싱 방식
```python
def is_palindrome(my_str):
    return my_str[:len(my_str)//2] == my_str[-(len(my_str)//2):][::-1]
```
---

### ⚡ 2. 거듭제곱 (Exponentiation by Recursion)

| 내용     | 설명                       |
| ------ | ------------------------ |
| 정의     | xⁿ (x의 n제곱) 계산           |
| 사용 조건  | `**` 연산자 ❌, 반복문 ❌        |
| 핵심 포인트 | 지수를 2로 나누며 **재귀적으로 곱하기**.n번 곱셈 → log₂(n) 단계 |

#### ✅ 코드(큰 문제를 작은 하위 문제로 나눔 (재귀))

```python
def power(x, n):
    if n == 0:
        return 1
    if n == 1:
        return x
    
    temp = power(x, n // 2)
    if n % 2 == 0:
        return temp * temp
    else:
        return x * temp * temp
```

#### 예시: `power(2, 3)`

```plaintext
power(2, 3) ---temp = power(2, 1) 호출됨
-> 홀수니까: 2 * power(2,1) * power(2,1)
-> power(2,1) = 2 ---temp = 2
-> 결과: 2 * 2 * 2 = 8
temp는 재귀 호출 결과를 저장하는 변수입니다.  
  power(x, n//2)를 두 번 계산하지 않고 한 번만 호출한 뒤, 그 결과를 재사용합니다.  
  → 하위 문제 결과를 캐싱하는 역할을 합니다.
```

---

