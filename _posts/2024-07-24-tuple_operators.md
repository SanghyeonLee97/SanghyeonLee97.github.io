---
layout: single
title:  "[Python] 자료형 - 튜플"
categories: 
    - python-datatypes
toc: true
toc_sticky: true
toc_label: "Table of Contents"
comments: true
author_profile: false
---



튜플은 파이썬에서 여러 개의 값을 하나의 변수에 저장할 수 있는 자료형으로, 리스트와 비슷하지만, **수정할 수 없는(immutable)** 자료형입니다.

튜플은 소괄호 `()` 를 사용하여 정의합니다.
<br><br>

## 1. 튜플 생성하기
튜플은 소괄호 `()` 안에 값을 쉼표 `,` 로 구분하여 생성할 수 있습니다.

```python
# 빈 튜플 생성
empty_tuple = ()

# 하나의 요소를 가진 튜플 생성 (쉼표를 꼭 붙여야 합니다)
single_element_tuple = (1,)

# 여러 요소를 가진 튜플 생성
numbers = (1, 2, 3, 4, 5)
strings = ("apple", "banana", "cherry")

# 다양한 자료형을 포함하는 튜플 생성
mixed = (1, "apple", 3.5, True)

print(empty_tuple)          # 출력: ()
print(single_element_tuple) # 출력: (1,)
print(numbers)              # 출력: (1, 2, 3, 4, 5)
print(strings)              # 출력: ('apple', 'banana', 'cherry')
print(mixed)                # 출력: (1, 'apple', 3.5, True)
```


## 2. 튜플 인덱싱과 슬라이싱
튜플은 인덱싱과 슬라이싱을 통해 개별 요소나 부분 튜플을 추출할 수 있습니다.

### 인덱싱
```python
fruits = ("apple", "banana", "cherry")

# 첫 번째 요소
print(fruits[0])  # 출력: apple

# 마지막 요소
print(fruits[-1])  # 출력: cherry
```

### 슬라이싱
```python
fruits = ("apple", "banana", "cherry", "date", "elderberry")

# 첫 번째부터 세 번째 요소까지
print(fruits[0:3])  # 출력: ('apple', 'banana', 'cherry')

# 두 번째부터 끝까지
print(fruits[1:])   # 출력: ('banana', 'cherry', 'date', 'elderberry')

# 처음부터 네 번째 요소까지
print(fruits[:4])   # 출력: ('apple', 'banana', 'cherry', 'date')

# 모든 요소
print(fruits[:])    # 출력: ('apple', 'banana', 'cherry', 'date', 'elderberry')
```

## 3. 튜플 연산
튜플은 덧셈 `+` 과 곱셈 `*` 연산을 지원합니다.

```python
# 튜플 덧셈
tuple1 = (1, 2, 3)
tuple2 = (4, 5, 6)
combined = tuple1 + tuple2
print(combined)  # 출력: (1, 2, 3, 4, 5, 6)

# 튜플 곱셈
repeat = tuple1 * 3
print(repeat)    # 출력: (1, 2, 3, 1, 2, 3, 1, 2, 3)
```

## 4. 튜플 수정
튜플은 **수정할 수 없는 (immutable)** 자료형이므로, 한 번 생성된 튜플의 요소는 변경할 수 없습니다. 하지만, 새로운 튜플을 생성할 수는 있습니다.

```python
fruits = ("apple", "banana", "cherry")

# 튜플 수정 시도 (에러 발생)
# fruits[1] = "blueberry"  # TypeError: 'tuple' object does not support item assignment

# 새로운 튜플 생성
new_fruits = fruits[:1] + ("blueberry",) + fruits[2:]
print(new_fruits)  # 출력: ('apple', 'blueberry', 'cherry')
```

## 5. 튜플 관련 함수와 메서드
튜플 자료형은 몇 가지 유용한 함수와 메서드를 제공합니다.

### 길이 구하기
```python
fruits = ("apple", "banana", "cherry")
print(len(fruits))  # 출력: 3
```

### 요소 존재 여부 확인
```python
fruits = ("apple", "banana", "cherry")
print("banana" in fruits)  # 출력: True
print("grape" in fruits)   # 출력: False
```

### 요소의 인덱스 찾기
```python
fruits = ("apple", "banana", "cherry")
print(fruits.index("banana"))  # 출력: 1
```

### 요소의 개수 세기
```python
numbers = (1, 2, 2, 3, 3, 3, 4)
print(numbers.count(2))  # 출력: 2
print(numbers.count(3))  # 출력: 3
```


## 6. 튜플 언패킹
튜플은 여러 변수에 한 번에 값을 할당하는 언패킹을 지원합니다.

```python
# 튜플 언패킹
fruits = ("apple", "banana", "cherry")
first, second, third = fruits

print(first)   # 출력: apple
print(second)  # 출력: banana
print(third)   # 출력: cherry
```

## 7. 리스트와 튜플 변환
리스트와 튜플은 서로 변환이 가능합니다.

```python
# 리스트를 튜플로 변환
fruits_list = ["apple", "banana", "cherry"]
fruits_tuple = tuple(fruits_list)
print(fruits_tuple)  # 출력: ('apple', 'banana', 'cherry')

# 튜플을 리스트로 변환
fruits_tuple = ("apple", "banana", "cherry")
fruits_list = list(fruits_tuple)
print(fruits_list)  # 출력: ['apple', 'banana', 'cherry']
```