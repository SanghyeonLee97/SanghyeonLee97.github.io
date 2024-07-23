---
layout: single
title:  "[Python] 자료형 - 문자열"
toc: true
toc_sticky: true
toc_label: "Table of Contents"
---

# 파이썬 문자열
파이썬에서 문자열은 문자들의 집합으로, 작은따옴표(')나 큰따옴표(')를 사용하여 생성할 수 있습니다. 문자열을 사용하는 다양한 방법을 알아봅시다.

## 1. 문자열 생성 및 사용
파이썬에서는 문자열을 작은따옴표(')나 큰따옴표(")를 사용하여 생성할 수 있습니다.


```python
# 작은따옴표 사용
string1 = 'Hello, World!'

# 큰따옴표 사용
string2 = "Hello, World!"

print(string1)  # 출력: Hello, World!
print(string2)  # 출력: Hello, World!
```

## 2. 문자열 안에 작은따옴표나 큰따옴표를 포함해야할 때
문자열 안에 작은따옴표나 큰따옴표를 포함시키기 위해서는 서로 다른 따옴표를 사용하거나 이스케이프 문자()를 사용할 수 있습니다.


```python
# 큰따옴표 안에 작은따옴표 포함
quote1 = "He said, 'Python is awesome!'"

# 작은따옴표 안에 큰따옴표 포함
quote2 = 'She replied, "Indeed it is!"'

# 이스케이프 문자 사용
quote3 = "It\'s a wonderful day!"
quote4 = "He said, \"Python is awesome!\""

print(quote1)  # 출력: He said, 'Python is awesome!'
print(quote2)  # 출력: She replied, "Indeed it is!"
print(quote3)  # 출력: It's a wonderful day!
print(quote4)  # 출력: He said, "Python is awesome!"
```

## 3. 여러 줄인 문자열을 변수에 대입하고 싶을 때
여러 줄 문자열은 세 개의 작은따옴표(''') 또는 세 개의 큰따옴표(""")를 사용하여 생성할 수 있습니다.


```python
multi_line_string = """This is a multi-line string.
It can span multiple lines.
Just like this."""

print(multi_line_string)
# 출력:
# This is a multi-line string.
# It can span multiple lines.
# Just like this.
```

## 4. 문자열의 연산
문자열은 덧셈 `+` 과 곱셈 `*` 연산을 지원합니다.


```python
# 문자열 덧셈
greeting = "Hello" + " " + "World"
print(greeting)  # 출력: Hello World

# 문자열 곱셈
repeat = "Hello " * 3
print(repeat)  # 출력: Hello Hello Hello 
```

## 5. 문자열 길이 구하기
파이썬에서는 len() 함수를 사용하여 문자열의 길이를 구할 수 있습니다.


```python
message = "Hello, World!"
length = len(message)
print(length)  # 출력: 13
```

## 6. 문자열 인덱싱, 슬라이싱
문자열은 인덱싱과 슬라이싱을 통해 부분 문자열을 추출할 수 있습니다.


```python
# 인덱싱
print(message[0])   # 출력: H
print(message[-1])  # 출력: !

# 슬라이싱
print(message[0:5])  # 출력: Hello
print(message[7:])   # 출력: World!
print(message[:5])   # 출력: Hello
print(message[::2])  # 출력: Hlo ol!
```

## 7. 문자열 포매팅
파이썬에서는 여러 가지 방법으로 문자열을 포매팅할 수 있습니다.

### 7-1. % 포매팅

`%` 포매팅을 사용하여 문자열을 포매팅할 수 있습니다. 다음은 다양한 포맷 코드와 그 의미입니다:

| 코드   | 의미                       | 예제                                    | 출력                            |
|--------|----------------------------|-----------------------------------------|---------------------------------|
| %s     | 문자열                     | `"Hello %s" % "World"`                  | `Hello World`                   |
| %d     | 정수                       | `"I have %d apples" % 5`                | `I have 5 apples`               |
| %f     | 부동 소수점                | `"PI is approximately %f" % 3.14`       | `PI is approximately 3.140000`  |
| %.2f   | 소수점 2자리 부동 소수점   | `"PI is approximately %.2f" % 3.14`     | `PI is approximately 3.14`      |


```python
name = "Alice"
age = 25

# % 포매팅
formatted_string = "My name is %s and I am %d years old." % (name, age)
print(formatted_string)  # 출력: My name is Alice and I am 25 years old.
```

### 7-2. format 함수를 사용한 포매팅
str.format() 함수를 사용하여 문자열을 포매팅할 수 있습니다.


```python
name = "Bob"
age = 30

formatted_string = "My name is {} and I am {} years old.".format(name, age)
print(formatted_string)  # 출력: My name is Bob and I am 30 years old.
```

### 7-3. f 문자열 포매팅
파이썬 3.6 이상에서는 f 문자열 포매팅을 사용할 수 있습니다.


```python
name = "Charlie"
age = 35

formatted_string = f"My name is {name} and I am {age} years old."
print(formatted_string)  # 출력: My name is Charlie and I am 35 years old.
```
