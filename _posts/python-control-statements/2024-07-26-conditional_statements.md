---
layout: single
title:  "[Python] 조건문 (if, if-else, if-elif-else)"
categories: 
    - python-cs
sidebar: false
toc: true
toc_sticky: true
toc_label: "Table of Contents"
comments: true
---

파이썬에서 조건문은 프로그램의 흐름을 제어하는 데 사용됩니다. 특정 조건이 참(True)인지 거짓(False)인지에 따라 다른 코드를 실행할 수 있게 합니다.

## if 문

`if` 문은 가장 기본적인 조건문입니다. 조건이 참일 때 해당 블록의 코드를 실행합니다.

```python
x = 10
if x > 5:
    print("x는 5보다 큽니다.")
```


## if-else 문
`if-else` 문은 조건이 참일 때와 거짓일 때 각각 다른 코드를 실행할 수 있게 합니다.

```python
x = 3
if x > 5:
    print("x는 5보다 큽니다.")
else:
    print("x는 5보다 작거나 같습니다.")
```


## if-elif-else 문
여러 조건을 검사해야 할 때 `elif` (else if의 줄임말)를 사용할 수 있습니다.

```python
x = 7
if x > 10:
    print("x는 10보다 큽니다.")
elif x > 5:
    print("x는 5보다 큽니다.")
else:
    print("x는 5보다 작거나 같습니다.")
```


## 중첩 if 문
조건문 안에 또 다른 조건문을 사용할 수 있습니다. 이를 **중첩 if** 문이라고 합니다.

```python
x = 15
if x > 10:
    print("x는 10보다 큽니다.")
    if x > 20:
        print("x는 20보다 큽니다.")
    else:
        print("x는 20보다 작거나 같습니다.")
else:
    print("x는 10보다 작거나 같습니다.")
```


## 조건 표현식 (삼항 연산자)
파이썬은 조건 표현식을 사용하여 한 줄로 간단하게 조건문을 작성할 수 있습니다.

```python
x = 10
result = "x는 5보다 큽니다." if x > 5 else "x는 5보다 작거나 같습니다."
print(result)
```


## 조건문에 여러 조건 사용하기
`and` , `or` 등의 논리 연산자를 사용하여 여러 조건을 조합할 수 있습니다.

```python
x = 10
y = 20

# and 연산자
if x > 5 and y > 15:
    print("x는 5보다 크고, y는 15보다 큽니다.")

# or 연산자
if x > 15 or y > 15:
    print("x는 15보다 크거나, y는 15보다 큽니다.")
```


## 조건문에서 유용한 함수
- `in` **연산자**: 특정 값이 시퀀스(리스트, 튜플 등)에 포함되어 있는지 확인할 때 사용합니다.
- `is` **연산자**: 두 객체가 동일한 객체(메모리 주소가 같은)를 가리키는지 확인할 때 사용합니다.

```python
# in 연산자
fruits = ["apple", "banana", "cherry"]
if "apple" in fruits:
    print("사과가 목록에 있습니다.")

# is 연산자
a = [1, 2, 3]
b = a
if a is b:
    print("a와 b는 같은 객체를 가리킵니다.")
```