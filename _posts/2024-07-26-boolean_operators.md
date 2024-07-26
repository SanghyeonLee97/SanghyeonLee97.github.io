---
layout: single
title:  "[Python] 자료형 - 불(boolean)"
categories: 
    - python-datatypes
author_profile: false
sidebar: false
toc: true
toc_sticky: true
toc_label: "Table of Contents"
comments: true
---

불리언(Boolean) 자료형은 참 `True`과 거짓 `False`을 나타내는 자료형입니다. 불리언 값은 논리 연산, 조건문, 제어 흐름 등에서 많이 사용됩니다.

## 1. 불리언 값

파이썬에서 불리언 값은 `True` 와 `False` 로 표기합니다. 이 두 값은 대소문자를 구분하므로 반드시 첫 글자는 대문자로 작성해야 합니다.

```python
is_true = True
is_false = False

print(is_true)  # 출력: True
print(is_false) # 출력: False
```

## 2. 불리언 연산
불리언 자료형은 논리 연산자를 사용하여 연산할 수 있습니다. 주요 논리 연산자는 `and`, `or`, `not` 입니다.
### 논리 연산자
- `and` : 두 값이 모두 참일 때만 참입니다.
- `or` : 두 값 중 하나라도 참이면 참입니다.
- `not` : 참을 거짓으로, 거짓을 참으로 변환합니다.

```python
a = True
b = False

print(a and b)  # 출력: False
print(a or b)   # 출력: True
print(not a)    # 출력: False
```

## 3. 비교 연산자
비교 연산자는 두 값을 비교하여 불리언 값을 반환합니다. 주요 비교 연산자는 다음과 같습니다:
- `==` : 두 값이 같으면 참
- `!=` : 두 값이 다르면 참
- `>` : 왼쪽 값이 크면 참
- `<` : 오른쪽 값이 크면 참
- `>=` : 왼쪽 값이 크거나 같으면 참
- `<=` : 오른쪽 값이 크거나 같으면 참

```python
x = 10
y = 20

print(x == y)  # 출력: False
print(x != y)  # 출력: True
print(x > y)   # 출력: False
print(x < y)   # 출력: True
print(x >= y)  # 출력: False
print(x <= y)  # 출력: True
```

## 4. 불리언 캐스팅
다른 데이터 타입을 불리언으로 변환할 수 있습니다. 파이썬에서 `bool()` 함수를 사용하면 됩니다. 대부분의 값은 참으로 평가되지만, 다음 값들은 거짓으로 평가됩니다:
- `None`
- `False`
- `0` (숫자 0)
- `0.0` (부동 소수점 0)
- `''` (빈 문자열)
- `[]` (빈 리스트)
- `{}` (빈 딕셔너리)
- `()` (빈 튜플)
- `set()` (빈 집합)

```python
print(bool(1))        # 출력: True
print(bool(0))        # 출력: False
print(bool([]))       # 출력: False
print(bool([1, 2, 3]))# 출력: True
print(bool(''))       # 출력: False
print(bool('Hello'))  # 출력: True
```

## 5. 조건문과 불리언
불리언 값은 조건문에서 자주 사용됩니다. 조건문은 주어진 조건이 참일 때 특정 코드 블록을 실행합니다.

```python
is_raining = True

if is_raining:
    print("Take an umbrella!")  # 출력: Take an umbrella!
else:
    print("No need for an umbrella.")
```