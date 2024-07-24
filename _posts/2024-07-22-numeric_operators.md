---
layout: single
title:  "[Python] 자료형 - 숫자형"
toc: true
toc_sticky: true
toc_label: "Table of Contents"
comments: true
---

# 숫자형 자료형
파이썬에서 숫자형 자료형은 크게 세 가지로 나뉩니다. 파이썬에서 숫자형 자료형은 크게 세 가지로 나뉩니다: 정수형, 실수형, 복소수형. 이 문서에서는 각 자료형에 대한 간단한 설명과 예제를 다룹니다.

# 1. 정수형 (Integer)
정수형은 소수점이 없는 숫자입니다. 파이썬에서는 **int** 타입으로 사용됩니다.
<hr>


```python
a = 10
b = -3
c = 0
```


```python
print(a) # 출력: 10
print(b) # 출력: -3
print(c) # 출력: 0
```

# 2. 실수형 (Float)
실수형은 소수점을 포함한 숫자입니다. 파이썬에서는 **float** 타입으로 사용됩니다.
<hr>


```python
a = 10.5
b = -3.14
c = 0.0
```


```python
print(a)  # 출력: 10.5
print(b)  # 출력: -3.14
print(c)  # 출력: 0.0
```

# 3. 복소수형 (Complex)
복소수형은 실수부와 허수부로 이루어진 숫자입니다. 파이썬에서는 **complex** 타입으로 사용됩니다.
<hr>


```python
a = 2 + 3j
b = -1 - 1j
```


```python
print(a)  # 출력: (2+3j)
print(b)  # 출력: (-1-1j)
print(a.real)  # 출력: 2.0 (실수부)
print(a.imag)  # 출력: 3.0 (허수부)
```

파이썬에서 복소수는 'a+bj' 형식으로 표현합니다. 여기서 'a'는 실수부, 'b'는 허수부를 나타내고 'j'는 허수의 단위를 의미합니다.

<br><br>

# 숫자형의 연산
파이썬에는 숫자형에 대한 다양한 연산을 지원합니다. 기본적인 산술 연산자로는 `+`, `-`, `*`, `/`, `//`, `%`, `**` 등이 있습니다.


```python
a = 10
b = 3
```


```python
print(a + b)  # 출력: 13
print(a - b)  # 출력: 7
print(a * b)  # 출력: 30
print(a / b)  # 출력: 3.3333333333333335
print(a // b) # 출력: 3 (정수 나눗셈)
print(a % b)  # 출력: 1 (나머지)
print(a ** b) # 출력: 1000 (거듭제곱)
```
