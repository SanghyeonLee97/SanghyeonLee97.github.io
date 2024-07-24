---
layout: single
title:  "[Python] 자료형 - 리스트"
categories: 
    - python-datatypes
toc: true
toc_sticky: true
toc_label: "Table of Contents"
comments: true
author_profile: false
---



리스트는 파이썬에서 가장 많이 사용되는 자료형 중 하나로, 여러 개의 값을 하나의 변수에 저장할 수 있는 자료형입니다. 리스트는 대괄호 `[]` 로 감싸서 정의하며, 다양한 연산과 메서드를 통해 쉽게 조작할 수 있습니다.

## 1. 리스트 생성하기

리스트는 대괄호 `[]`  안에 값을 쉼표 `,` 로 구분하여 생성할 수 있습니다.


```python
# 빈 리스트 생성
empty_list = []

# 숫자 리스트 생성
numbers = [1, 2, 3, 4, 5]

# 문자열 리스트 생성
strings = ["apple", "banana", "cherry"]

# 다양한 자료형을 포함하는 리스트 생성
mixed = [1, "apple", 3.5, True]

print(empty_list)  # 출력: []
print(numbers)     # 출력: [1, 2, 3, 4, 5]
print(strings)     # 출력: ['apple', 'banana', 'cherry']
print(mixed)       # 출력: [1, 'apple', 3.5, True]
```

## 2. 리스트 인덱싱과 슬라이싱
리스트는 인덱싱과 슬라이싱을 통해 개별 요소나 부분 리스트를 추출할 수 있습니다.

### 인덱싱
```python
fruits = ["apple", "banana", "cherry"]

# 첫 번째 요소
print(fruits[0])  # 출력: apple

# 마지막 요소
print(fruits[-1])  # 출력: cherry
```

### 슬라이싱
```python
fruits = ["apple", "banana", "cherry", "date", "elderberry"]

# 첫 번째부터 세 번째 요소까지
print(fruits[0:3])  # 출력: ['apple', 'banana', 'cherry']

# 두 번째부터 끝까지
print(fruits[1:])   # 출력: ['banana', 'cherry', 'date', 'elderberry']

# 처음부터 네 번째 요소까지
print(fruits[:4])   # 출력: ['apple', 'banana', 'cherry', 'date']

# 모든 요소
print(fruits[:])    # 출력: ['apple', 'banana', 'cherry', 'date', 'elderberry']
```

## 3. 리스트 연산
리스트는 덧셈 `+` 과 곱셈 `*`  연산을 지원합니다.

```python
# 리스트 덧셈
list1 = [1, 2, 3]
list2 = [4, 5, 6]
combined = list1 + list2
print(combined)  # 출력: [1, 2, 3, 4, 5, 6]

# 리스트 곱셈
repeat = list1 * 3
print(repeat)    # 출력: [1, 2, 3, 1, 2, 3, 1, 2, 3]
```

## 4. 리스트 수정
리스트의 특정 요소를 수정하거나, 새로운 요소를 추가 및 제거할 수 있습니다.

### 요소 수정
```python
fruits = ["apple", "banana", "cherry"]
fruits[1] = "blueberry"
print(fruits)  # 출력: ['apple', 'blueberry', 'cherry']
```
### 요소 추가
```python
# append() 메서드 사용
fruits.append("date")
print(fruits)  # 출력: ['apple', 'blueberry', 'cherry', 'date']

# insert() 메서드 사용
fruits.insert(1, "banana")
print(fruits)  # 출력: ['apple', 'banana', 'blueberry', 'cherry', 'date']
```
### 요소 제거
```python
# remove() 메서드 사용
fruits.remove("banana")
print(fruits)  # 출력: ['apple', 'blueberry', 'cherry', 'date']

# pop() 메서드 사용
fruits.pop()
print(fruits)  # 출력: ['apple', 'blueberry', 'cherry']
```


## 5. 리스트 관련 함수와 메서드
리스트 자료형은 다양한 함수와 메서드를 제공합니다.

### 길이 구하기
```python
fruits = ["apple", "banana", "cherry"]
print(len(fruits))  # 출력: 3
```

### 요소 존재 여부 확인
```python
fruits = ["apple", "banana", "cherry"]
print("banana" in fruits)  # 출력: True
print("grape" in fruits)   # 출력: False
```

### 리스트 정렬
```python
numbers = [3, 1, 4, 1, 5, 9, 2, 6, 5]
numbers.sort()
print(numbers)  # 출력: [1, 1, 2, 3, 4, 5, 5, 6, 9]

# 내림차순 정렬
numbers.sort(reverse=True)
print(numbers)  # 출력: [9, 6, 5, 5, 4, 3, 2, 1, 1]
```

### 리스트 뒤집기
```python
fruits = ["apple", "banana", "cherry"]
fruits.reverse()
print(fruits)  # 출력: ['cherry', 'banana', 'apple']
```

### 리스트 복사
```python
fruits = ["apple", "banana", "cherry"]
copy_fruits = fruits.copy()
print(copy_fruits)  # 출력: ['apple', 'banana', 'cherry']
```


## 6. 리스트 내포
리스트 내포(List Comprehension)를 사용하면 리스트를 쉽고 간결하게 생성할 수 있습니다.

```python
# 0부터 9까지의 제곱수를 포함하는 리스트
squares = [x**2 for x in range(10)]
print(squares)  # 출력: [0, 1, 4, 9, 16, 25, 36, 49, 64, 81]
```