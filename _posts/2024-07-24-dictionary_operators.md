---
layout: single
title:  "[Python] 자료형 - 딕셔너리"
toc: true
toc_sticky: true
toc_label: "Table of Contents"
---

# 딕셔너리 자료형

딕셔너리(Dictionary)는 키(key)와 값(value)의 쌍을 저장하는데 사용되는 자료형입니다. 중괄호 `{}` 를 사용하여 정의하며, 키와 값은 콜론 `:` 으로 구분합니다. 키는 유일하며, 변경 불가능한 데이터 타입이어야 합니다.
<br><br>

## 1. 딕셔너리 생성하기

딕셔너리는 중괄호 `{}` 안에 키-값 쌍을 콜론 `:` 으로 구분하여 생성합니다.

```python
# 빈 딕셔너리 생성
empty_dict = {}

# 키-값 쌍을 가진 딕셔너리 생성
person = {"name": "Lee", "age": 25, "city": "Incheon"}

print(empty_dict)  # 출력: {}
print(person)      # 출력: {'name': 'Lee', 'age': 25, 'city': 'Incheon'}
```

## 2. 딕셔너리 쌍 추가하기, 딕셔너리 요소 삭제

### 딕셔너리 쌍 추가하기

```python
person = {"name": "Lee", "age": 25}
person["city"] = "Incheon"
print(person)  # 출력: {'name': 'Lee', 'age': 25, 'city': 'Incheon'}
```

### 딕셔너리 요소 삭제

```python
person = {"name": "Lee", "age": 25, "city": "Incheon"}
del person["age"]
print(person)  # 출력: {'name': 'Lee', 'city': 'Incheon'}
```

## 3. 딕셔너리에서 Key를 사용해 Value 얻기

```python
person = {"name": "Lee", "age": 25, "city": "Incheon"}
name = person["name"]
print(name)  # 출력: Lee
```

## 4. 딕셔너리 만들 때 주의할 사항
- 키는 유일해야 하며, 변경 불가능한 데이터 타입이어야 합니다. 예를 들어, 문자열, 숫자, 튜플을 키로 사용할 수 있습니다.
- 값은 어떤 데이터 타입도 가능합니다.

```python
# 유효한 키
valid_dict = {
    "name": "Lee",
    1: [2, 4, 3],
    (2, 3): "tuple as a key"
}

# 유효하지 않은 키 (리스트는 변경 가능하므로 키로 사용할 수 없습니다)
# invalid_dict = {[1, 2]: "list as a key"}  # TypeError 발생
```

## 5. Key 리스트 만들기 - keys

```python
person = {"name": "Lee", "age": 25, "city": "Incheon"}
keys = person.keys()
print(keys)  # 출력: dict_keys(['name', 'age', 'city'])
```

## 6. Value 리스트 만들기 - values

```python
person = {"name": "Lee", "age": 25, "city": "Incheon"}
values = person.values()
print(values)  # 출력: dict_values(['Lee', 25, 'Incheon'])
```

## 7. Key, Value 쌍 얻기 - items

```python
person = {"name": "Lee", "age": 25, "city": "Incheon"}
items = person.items()
print(items)  # 출력: dict_items([('name', 'Lee'), ('age', 25), ('city', 'Incheon')])
```

## 8. Key: Value 쌍 모두 지우기 - clear

```python
person = {"name": "Lee", "age": 25, "city": "Incheon"}
person.clear()
print(person)  # 출력: {}
```

## 9. Key로 Value 얻기 - get

```python
person = {"name": "Lee", "age": 25, "city": "Incheon"}
age = person.get("age")
print(age)  # 출력: 25

# 존재하지 않는 키를 요청할 경우 None 반환
country = person.get("country")
print(country)  # 출력: None

# 존재하지 않는 키를 요청할 경우 기본 값 반환
country = person.get("country", "South Korea")
print(country)  # 출력: South Korea
```

## 10. 해당 Key가 딕셔너리 안에 있는지 조사하기 - in

```python
person = {"name": "Lee", "age": 25, "city": "Incheon"}
print("name" in person)  # 출력: True
print("country" in person)  # 출력: False
```