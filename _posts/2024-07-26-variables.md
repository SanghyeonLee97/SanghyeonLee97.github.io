---
layout: single
title:  "[Python] 변수(Variables)"
categories: 
    - python-datatypes
author_profile: false
sidebar: false
toc: true
toc_sticky: true
toc_label: "Table of Contents"
comments: true
---

변수는 데이터를 저장하고 참조하는 이름입니다. 파이썬에서 변수와 메모리 관리는 중요한 개념입니다. 이 글에서는 변수의 할당과 참조, 스코프와 생명주기, 얕은 복사와 깊은 복사 등을 다룹니다.


## 1. 변수의 할당과 참조

변수에 값을 할당하면, 변수는 그 값이 저장된 메모리 주소를 참조합니다. 파이썬의 변수는 객체를 가리키는 참조(reference)입니다.
```python
x = 10
y = x

print(x)  # 출력: 10
print(y)  # 출력: 10

x = 20
print(x)  # 출력: 20
print(y)  # 출력: 10
```

이 예제에서 `x` 와 `y` 는 처음에 동일한 값을 참조합니다. 하지만 `x` 의 값을 변경해도 `y` 에는 영향을 미치지 않습니다.


## 2. 변수 스코프와 생명주기
변수의 스코프(scope)는 변수의 유효 범위를 의미합니다. 파이썬에서는 변수의 스코프가 **함수 내**, **블록 내**, **전역**으로 나뉩니다.

```python
x = 10  # 전역 변수

def outer():
    x = 20  # 외부 함수의 지역 변수
    def inner():
        nonlocal x
        x = 30  # 내부 함수의 지역 변수
        print("inner x:", x)  # 출력: inner x: 30
    inner()
    print("outer x:", x)  # 출력: outer x: 30

outer()
print("global x:", x)  # 출력: global x: 10
```


## 3. 얕은 복사와 깊은 복사
복사는 객체의 값을 복사하여 새로운 객체를 만드는 과정입니다. 파이썬에서는 **얕은 복사(shallow copy)**와 **깊은 복사(deep copy)**가 있습니다.

### 얕은 복사
얕은 복사는 객체의 최상위 수준만 복사하고, 하위 객체들은 원본 객체와 동일한 참조를 가집니다. 즉, 얕은 복사는 객체를 복사하지만 그 안에 포함된 객체는 복사하지 않습니다.

```python
import copy

list1 = [1, 2, [3, 4]]
list2 = copy.copy(list1)

print(list1)  # 출력: [1, 2, [3, 4]]
print(list2)  # 출력: [1, 2, [3, 4]]
print(id(list1), id(list2))  # 서로 다른 주소

list1[2][0] = 99
print(list1)  # 출력: [1, 2, [99, 4]]
print(list2)  # 출력: [1, 2, [99, 4]]  # 얕은 복사이므로 내부 리스트는 공유됨
```

### 깊은 복사
깊은 복사는 모든 수준의 객체를 재귀적으로 복사하여, 원본 객체와 독립적인 복사본을 만듭니다. 즉, 깊은 복사는 객체와 그 안에 포함된 모든 객체를 복사합니다.

```python
import copy

list1 = [1, 2, [3, 4]]
list3 = copy.deepcopy(list1)

print(list1)  # 출력: [1, 2, [3, 4]]
print(list3)  # 출력: [1, 2, [3, 4]]
print(id(list1), id(list3))  # 서로 다른 주소

list1[2][0] = 99
print(list1)  # 출력: [1, 2, [99, 4]]
print(list3)  # 출력: [1, 2, [3, 4]]  # 깊은 복사이므로 내부 리스트도 복사됨
```

### 메모리 주소 확인
파이썬에서 객체의 메모리 주소는 `id()` 함수를 사용하여 확인할 수 있습니다. 얕은 복사와 깊은 복사의 차이를 메모리 주소를 통해 확인할 수 있습니다.

```python
import copy

list1 = [1, 2, [3, 4]]
list2 = copy.copy(list1)
list3 = copy.deepcopy(list1)

print(id(list1), id(list2), id(list3))  # 서로 다른 주소
print(id(list1[2]), id(list2[2]), id(list3[2]))  # list1과 list2는 동일, list3는 다름
```

## 5. 불변 객체와 가변 객체
파이썬의 데이터 타입은 **불변(immutable)** 객체와 **가변(mutable)** 객체로 나눌 수 있습니다. 불변 객체는 생성 후 변경할 수 없으며, 가변 객체는 변경 가능합니다.

### 불변 객체
불변 객체는 한 번 생성되면 그 값을 변경할 수 없습니다. 불변 객체에는 `숫자`, `문자열`, `튜플` 등이 포함됩니다.

```python
a = 10
b = a
print(id(a), id(b))  # 동일한 주소

a = 20
print(id(a), id(b))  # 다른 주소
print(a, b)  # 출력: 20 10
```
이 예제에서 `a`와 `b`는 처음에 동일한 값을 참조합니다. 그러나 `a`의 값을 변경하면 새로운 객체가 생성되고, `a`는 그 새로운 객체를 참조하게 됩니다. 반면 `b`는 여전히 원래의 객체를 참조합니다. 따라서 불변 객체는 값이 변경되지 않으며, 새로운 값을 할당하면 새로운 객체가 생성됩니다.

### 가변 객체
가변 객체는 생성 후 그 값을 변경할 수 있습니다. 가변 객체에는 `리스트`, `딕셔너리`, `집합` 등이 포함됩니다.

```python
x = [1, 2, 3]
y = x
print(id(x), id(y))  # 동일한 주소

x[0] = 99
print(id(x), id(y))  # 동일한 주소
print(x, y)  # 출력: [99, 2, 3] [99, 2, 3]
```
이 예제에서 `x`와 `y`는 동일한 리스트 객체를 참조합니다. 리스트의 값을 변경해도 `x`와 `y`는 여전히 동일한 객체를 참조하며, 그 값도 변경됩니다. 따라서 가변 객체는 값이 변경될 때 새로운 객체를 생성하지 않고, 기존 객체를 변경합니다.