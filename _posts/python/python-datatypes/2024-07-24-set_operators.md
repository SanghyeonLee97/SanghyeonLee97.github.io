---
layout: single
title:  "[Python] 자료형 - 집합"
categories: 
    - python-datatypes
sidebar: false
toc: true
toc_sticky: true
toc_label: "Table of Contents"
comments: true
---

집합(Set)은 **중복을 허용하지 않고, 순서가 없는 데이터 타입**입니다. 집합은 수학에서의 집합과 같은 특성을 가지며, 중괄호 `{}` 를 사용하여 정의합니다.

## 1. 집합 생성하기

집합은 중괄호 `{}` 를 사용하여 생성하거나, `set()` 함수를 사용하여 생성할 수 있습니다.

```python
# 빈 집합 생성
empty_set = set()

# 값이 있는 집합 생성
fruits = {"apple", "banana", "cherry"}

print(empty_set)  # 출력: set()
print(fruits)     # 출력: {'apple', 'banana', 'cherry'}
```

## 2. 집합에 값 추가하기, 집합에서 값 제거하기
### 값 추가하기
```python
fruits = {"apple", "banana"}
fruits.add("cherry")
print(fruits)  # 출력: {'apple', 'banana', 'cherry'}
```
### 값 제거하기
```python
fruits = {"apple", "banana", "cherry"}
fruits.remove("banana")
print(fruits)  # 출력: {'apple', 'cherry'}

# 요소가 집합에 없는 경우 KeyError 발생
# fruits.remove("grape")  # KeyError 발생

# discard() 메서드는 요소가 집합에 없는 경우에도 에러가 발생하지 않음
fruits.discard("grape")
print(fruits)  # 출력: {'apple', 'cherry'}
```


## 3. 집합 연산
집합은 합집합, 교집합, 차집합, 대칭차집합 등의 연산을 지원합니다.

### 합집합
두 집합의 **모든 요소를 포함**하는 새로운 집합을 반환합니다.
```python
set1 = {"apple", "banana", "cherry"}
set2 = {"cherry", "date", "elderberry"}
union_set = set1.union(set2)
print(union_set)  # 출력: {'apple', 'banana', 'cherry', 'date', 'elderberry'}
```
### 교집합
두 집합에 **모두 존재하는 요소만 포함**하는 새로운 집합을 반환합니다.
```python
set1 = {"apple", "banana", "cherry"}
set2 = {"cherry", "date", "elderberry"}
intersection_set = set1.intersection(set2)
print(intersection_set)  # 출력: {'cherry'}
```
### 차집합
**첫 번째 집합에는 존재**하지만, **두 번째 집합에는 존재하지 않는 요소만 포함**하는 새로운 집합을 반환합니다.
```python
set1 = {"apple", "banana", "cherry"}
set2 = {"cherry", "date", "elderberry"}
difference_set = set1.difference(set2)
print(difference_set)  # 출력: {'apple', 'banana'}
```
### 대칭차집합
두 집합 중 **한 집합에만 존재하는 요소들을 포함**하는 새로운 집합을 반환합니다.
```python
set1 = {"apple", "banana", "cherry"}
set2 = {"cherry", "date", "elderberry"}
symmetric_difference_set = set1.symmetric_difference(set2)
print(symmetric_difference_set)  # 출력: {'apple', 'banana', 'date', 'elderberry'}
```

## 4. 집합 관련 함수와 메서드
### 집합 길이 구하기
```python
fruits = {"apple", "banana", "cherry"}
print(len(fruits))  # 출력: 3
```
### 요소 존재 여부 확인
```python
fruits = {"apple", "banana", "cherry"}
print("banana" in fruits)  # 출력: True
print("grape" in fruits)   # 출력: False
```
### 집합 복사
```python
fruits = {"apple", "banana", "cherry"}
copy_fruits = fruits.copy()
print(copy_fruits)  # 출력: {'apple', 'banana', 'cherry'}
```
### 집합 모든 요소 삭제
```python
fruits = {"apple", "banana", "cherry"}
fruits.clear()
print(fruits)  # 출력: set()
```


## 5. 집합의 특성
- **중복을 허용하지 않음**: 집합 내에 같은 값이 여러 번 있을 수 없습니다.
- **순서가 없음**: 집합은 순서가 없기 때문에 인덱싱으로 특정 요소에 접근할 수 없습니다.

```python
# 중복된 값을 가지는 집합
fruits = {"apple", "banana", "cherry", "apple"}
print(fruits)  # 출력: {'apple', 'banana', 'cherry'}

# 집합은 순서가 없으므로 인덱싱이 불가능
# print(fruits[0])  # TypeError 발생
```