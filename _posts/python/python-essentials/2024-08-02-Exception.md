---
layout: single
title:  "[Python] 예외처리 (Exception)"
categories: 
    - python-essentials
sidebar: false
toc: true
toc_sticky: true
toc_label: "Table of Contents"
comments: true
---

오류(Error)는 프로그램 실행 중에 발생하는 예기치 않은 상황을 말합니다. 이러한 오류는 다양한 이유로 발생할 수 있습니다. 예를 들어, 잘못된 사용자 입력, 파일을 찾을 수 없음, 네트워크 연결 실패 등이 있습니다. 예외처리(Exception Handling)는 이러한 오류 상황을 처리하여 프로그램이 중단되지 않고 계속 실행되도록 도와줍니다.


## 1. 오류와 예외의 개념

### 1.1 오류가 발생하는 이유
프로그램 실행 중 다양한 이유로 오류가 발생할 수 있습니다.
#### 1. **문법 오류 (Syntax Errors):** 파이썬의 문법 규칙을 위반했을 때 발생합니다.
```python
# 잘못된 문법 예시
if x = 5:  # '='는 할당 연산자, 비교는 '=='를 사용해야 함
    print("x는 5입니다.")
```
#### 2. **논리 오류 (Logical Errors):** 문법적으로는 올바르지만, 의도한 대로 동작하지 않는 오류입니다.
```python
# 논리 오류 예시
def calculate_average(numbers):
    return sum(numbers) / len(numbers) + 1  # '+1'이 불필요하게 추가됨
```
#### 3. **런타임 오류 (Runtime Errors):** 프로그램 실행 중에 발생하는 오류입니다.
```python
# 런타임 오류 예시
numbers = [1, 2, 3]
print(numbers[3])  # IndexError: 리스트의 인덱스가 범위를 벗어남
```



### 1.2 예외처리의 중요성
예외처리는 다음과 같은 이유로 중요합니다:
#### 1. 프로그램의 비정상적인 종료 방지:
```python
try:
    result = 10 / 0
except ZeroDivisionError:
    print("0으로 나눌 수 없습니다.")
    result = None
print("프로그램이 계속 실행됩니다.")
```
#### 2. 오류 상황에 대한 적절한 대처:
```python
try:
    file = open("config.txt", "r")
except FileNotFoundError:
    print("설정 파일이 없습니다. 기본 설정을 사용합니다.")
    # 기본 설정을 적용하는 코드
```
#### 3. 디버깅 용이성 증가:
```python
import logging

try:
    # 복잡한 연산 수행
    result = complex_calculation()
except Exception as e:
    logging.error(f"연산 중 오류 발생: {e}")
    # 오류 로그를 통해 문제 원인 파악 가능
```


## 2. 기본적인 예외처리 구조
파이썬에서는 `try`, `except`, `else`, `finally` 블록을 사용하여 예외를 처리할 수 있습니다.

### 2.1 try-except 구문
가장 기본적인 예외처리 방법입니다.
```python
try:
    age = int(input("나이를 입력하세요: "))
    if age < 0:
        raise ValueError("나이는 음수일 수 없습니다.")
except ValueError as e:
    print(f"잘못된 입력입니다: {e}")
```
이 예제에서는 사용자 입력을 받아 정수로 변환하고, 음수인 경우 `ValueError`를 발생시킵니다. `except` 블록에서는 이 예외를 잡아 적절한 메시지를 출력합니다.

### 2.2 여러 예외 처리하기
다양한 예외를 개별적으로 처리할 수 있습니다.
```python
try:
    number = int(input("숫자를 입력하세요: "))
    result = 100 / number
    print(f"결과: {result}")
except ValueError:
    print("올바른 숫자를 입력하세요.")
except ZeroDivisionError:
    print("0으로 나눌 수 없습니다.")
except Exception as e:
    print(f"예상치 못한 오류 발생: {e}")
```
이 예제는 입력값이 숫자가 아닐 경우(`ValueError`), 0으로 나누려 할 경우(`ZeroDivisionError`), 그리고 그 외의 모든 예외(`Exception`)를 각각 다르게 처리합니다.

### 2.3 else와 finally 절
`else`와 `finally` 절을 사용하여 예외 처리를 더 정교하게 할 수 있습니다.
```python
try:
    file = open("example.txt", "r")
    content = file.read()
except FileNotFoundError:
    print("파일을 찾을 수 없습니다.")
else:
    print(f"파일 내용: {content}")
    file.close()
finally:
    print("파일 처리가 완료되었습니다.")
```
이 예제에서 `else` 블록은 예외가 발생하지 않았을 때 실행되며, `finally` 블록은 예외 발생 여부와 관계없이 항상 실행됩니다.


## 3. 고급 예외처리 기법
### 3.1 예외 정보 얻기
예외 객체를 통해 상세한 정보를 얻을 수 있습니다.
```python
try:
    x = 10
    y = x / 0
except Exception as e:
    print(f"예외 타입: {type(e).__name__}")
    print(f"예외 메시지: {str(e)}")
    import traceback
    print(f"스택 트레이스:\n{traceback.format_exc()}")
```
예외의 타입, 메시지, 그리고 전체 스택 트레이스를 출력합니다.

### 3.2 예외 다시 발생시키기 (re-raising)
예외를 처리한 후 다시 발생시켜 상위 레벨에서 처리할 수 있게 합니다.
```python
def process_data(data):
    try:
        return int(data)
    except ValueError:
        print("데이터 처리 중 오류 발생")
        raise  # 예외를 다시 발생시킴

try:
    result = process_data("abc")
except ValueError:
    print("최종 예외 처리")
```
이 예제에서 `process_data` 함수는 예외를 일부 처리한 후 다시 발생시켜, 호출자에게 예외 처리의 기회를 제공합니다.

### 3.3 오류 회피
때로는 특정 예외를 무시하고 계속 실행하는 것이 필요할 수 있습니다.
```python
def read_file(filename):
    try:
        with open(filename, "r") as file:
            return file.read()
    except FileNotFoundError:
        return None  # 파일이 없으면 None 반환

content = read_file("config.txt")
if content is None:
    print("설정 파일이 없습니다. 기본 설정을 사용합니다.")
else:
    print("설정 파일을 읽었습니다.")
```
파일이 없을 경우 예외를 발생시키지 않고 `None`을 반환하여 오류를 회피합니다.


## 4. 사용자 정의 예외

### 4.1 예외 만들기
사용자 정의 예외를 만들어 프로그램의 특정 상황을 더 명확하게 표현할 수 있습니다.
```python
class InsufficientFundsError(Exception):
    def __init__(self, balance, amount):
        self.balance = balance
        self.amount = amount
    
    def __str__(self):
        return f"잔액 부족: 현재 잔액 {self.balance}, 요청 금액 {self.amount}"

def withdraw(balance, amount):
    if amount > balance:
        raise InsufficientFundsError(balance, amount)
    return balance - amount

try:
    new_balance = withdraw(100, 150)
except InsufficientFundsError as e:
    print(e)
```
은행 계좌에서 출금할 때 잔액이 부족한 경우를 위한 사용자 정의 예외를 생성하는 예제입니다.

### 4.2 사용자 정의 예외 활용
사용자 정의 예외를 활용하여 프로그램의 다양한 상황을 더 명확하게 처리할 수 있습니다.
```python
class NetworkError(Exception):
    pass

class DatabaseError(Exception):
    pass

def fetch_data():
    # 네트워크 오류 시뮬레이션
    raise NetworkError("서버에 연결할 수 없습니다.")

def process_data():
    try:
        data = fetch_data()
    except NetworkError as e:
        print(f"네트워크 오류: {e}")
        # 네트워크 재연결 시도 등의 처리
    except DatabaseError as e:
        print(f"데이터베이스 오류: {e}")
        # 데이터베이스 복구 시도 등의 처리

process_data()
```
네트워크 오류와 데이터베이스 오류를 구분하여 처리하는 방법을 보여주는 예제입니다.