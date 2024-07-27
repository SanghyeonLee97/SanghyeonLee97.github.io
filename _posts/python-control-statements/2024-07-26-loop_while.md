---
layout: single
title:  "[Python] 반복문 (while)"
categories: 
    - python-cs
sidebar: false
toc: true
toc_sticky: true
toc_label: "Table of Contents"
comments: true
---


파이썬에서 `while` 문은 조건이 참인 동안 반복적으로 코드를 실행하는 데 사용됩니다. 조건이 거짓이 되면 반복이 종료됩니다. `while` 문은 주로 반복 횟수가 명확하지 않은 경우에 많이 사용됩니다.


## 기본 while 문
`while` 문은 주어진 조건이 참일 때 코드를 반복적으로 실행합니다.

```python
# 0부터 4까지의 숫자를 출력하는 예제
i = 0
while i < 5:
    print(i)
    i += 1
# 출력:
# 0
# 1
# 2
# 3
# 4
```
이 예제에서는 `i` 가 5보다 작을 때 계속 반복되며, `i` 가 5가 되면 조건이 거짓이 되어 반복이 종료됩니다.


## 조건을 사용하는 while 문
`while` 문은 다양한 조건을 사용할 수 있습니다.

```python
# 사용자 입력을 받아 'exit'을 입력할 때까지 반복하는 예제
response = ""
while response != "exit":
    response = input("종료하려면 'exit'을 입력하세요: ")
    print("입력하신 값:", response)
# 출력 (예시):
# 종료하려면 'exit'을 입력하세요: hello
# 입력하신 값: hello
# 종료하려면 'exit'을 입력하세요: exit
# 입력하신 값: exit
```
이 예제에서는 사용자가 **'exit'** 을 입력할 때까지 반복적으로 입력을 받습니다.


## 무한 루프와 break 문
`while True` 는 무한 루프를 생성합니다. `break` 문을 사용하여 무한 루프를 종료할 수 있습니다.

```python
# 'exit'을 입력하면 무한 루프를 종료하는 예제
while True:
    response = input("종료하려면 'exit'을 입력하세요: ")
    if response == "exit":
        break
    print("입력하신 값:", response)
# 출력 (예시):
# 종료하려면 'exit'을 입력하세요: hello
# 입력하신 값: hello
# 종료하려면 'exit'을 입력하세요: exit
```
이 예제에서는 `while True`로 무한 루프를 생성하고, `response` 가 **'exit'**일 때 `break` 문으로 루프를 종료합니다.


## continue 문
`continue` 문은 현재 반복을 건너뛰고 다음 반복을 실행합니다.

```python
# 짝수는 건너뛰고 홀수만 출력하는 예제
i = 0
while i < 10:
    i += 1
    if i % 2 == 0:
        continue
    print(i)
# 출력:
# 1
# 3
# 5
# 7
# 9
```
이 예제에서는 `i`가 짝수일 때 `continue` 문이 실행되어 해당 반복을 건너뛰고, 홀수일 때만 `print(i)` 가 실행됩니다.


## 중첩 while 문
`while` 문 안에 또 다른 `while` 문을 사용할 수 있습니다. 이를 중첩 `while` 문이라고 합니다.

```python
# 구구단 출력 예제
i = 2
while i <= 9:
    j = 1
    while j <= 9:
        print(f"{i} * {j} = {i * j}")
        j += 1
    print()  # 단 사이에 빈 줄 추가
    i += 1
# 출력 (부분 예시):
# 2 * 1 = 2
# 2 * 2 = 4
# ...
# 2 * 9 = 18
# 3 * 1 = 3
# 3 * 2 = 6
# ...
# 3 * 9 = 27
# ...
# 9 * 9 = 81
```
이 예제에서는 2단부터 9단까지의 구구단을 출력합니다. 바깥쪽 `while` 문이 단을 제어하고, 안쪽 `while` 문이 각 단의 곱셈을 제어합니다.


## 반복문에서 break와 continue의 사용
- `break` 문: 반복문을 즉시 종료합니다.
- `continue` 문: 현재 반복을 건너뛰고 다음 반복을 실행합니다.

### break 문 예제
```python
# 5가 나오면 반복문을 종료하는 예제
i = 0
while i < 10:
    if i == 5:
        break
    print(i)
    i += 1
# 출력:
# 0
# 1
# 2
# 3
# 4
```
이 예제에서는 `i`가 5일 때 `break` 문이 실행되어 반복문이 종료됩니다.

### continue 문 예제
```python
# 짝수는 건너뛰고 홀수만 출력하는 예제
i = 0
while i < 10:
    i += 1
    if i % 2 == 0:
        continue
    print(i)
# 출력:
# 1
# 3
# 5
# 7
# 9
```
이 예제에서는 `i` 가 짝수일 때 `continue` 문이 실행되어 해당 반복을 건너뛰고, 홀수일 때만 `print(i)` 가 실행됩니다.


## 반복문에 else 절 추가
`while` 문에 `else` 절을 추가하면, 반복문이 정상적으로 완료된 경우에 `else` 블록이 실행됩니다. `break` 문으로 중단된 경우에는 실행되지 않습니다.

```python
# 정상적으로 반복문이 완료되었는지 확인하는 예제
i = 0
while i < 5:
    if i == 3:
        break
    print(i)
    i += 1
else:
    print("반복문이 정상적으로 완료되었습니다.")
# 출력:
# 0
# 1
# 2
```
이 예제에서는 `i` 가 3일 때 `break` 문이 실행되어 `else` 블록이 실행되지 않습니다.