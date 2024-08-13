---
layout: single
title:  "[Python] 파일 읽고 쓰기 (심화편)"
categories: 
    - python-io
sidebar: false
toc: true
toc_sticky: true
toc_label: "Table of Contents"
comments: true
---

Python을 사용하여 `JSON`, `CSV`, `Excel`, `XML`, `SQLite` 파일을 읽고 쓰는 방법에 대한 예제를 알아보겠습니다.

## 1. JSON 파일 처리
**JSON (JavaScript Object Notation)** 은 데이터 교환 형식으로 널리 사용됩니다. Python에서는 `json` 모듈을 사용하여 JSON 데이터를 읽고 쓸 수 있습니다.

### JSON 파일 읽기
```python
import json

# JSON 파일 읽기
with open('user.json', 'r', encoding='utf-8') as f:
    data = json.load(f)

# json.load() 함수는 파일 객체를 받아 JSON 데이터를 Python 딕셔너리로 변환합니다.
# 'user.json' 파일의 내용을 읽어서 data 변수에 저장합니다.
```
`user.json` 파일을 열어 JSON 데이터를 Python의 딕셔너리 형태로 읽어오는 예제입니다. `encoding='utf-8'`을 지정하여 파일의 인코딩 문제를 방지할 수 있습니다.

### JSON 파일 쓰기
```python
import json

# JSON 데이터
user = {
    "name": "홍길동",
    "id": 152352,
    "history": [
        {"date": "2015-03-11", "item": "iPhone"},
        {"date": "2016-02-23", "item": "Monitor"}
    ]
}

# JSON 파일로 저장
with open('member.json', 'w', encoding='utf-8') as f:
    json.dump(user, f, ensure_ascii=False, indent=4)

# json.dump() 함수는 Python 객체를 JSON 형식으로 파일에 기록합니다.
# ensure_ascii=False는 한글 등 비 ASCII 문자를 그대로 저장하도록 합니다.
# indent=4는 JSON 데이터를 4칸 들여쓰기하여 읽기 쉽게 포맷팅합니다.
```
`user`라는 딕셔너리를 `member.json` 파일에 JSON 형식으로 저장하는 예제입니다. `ensure_ascii=False`를 사용하여 JSON 파일에 한글을 정상적으로 저장할 수 있습니다.



## 2. CSV 파일 처리
**CSV (Comma-Separated Values)** 는 데이터를 간단한 텍스트 형식으로 저장하는 방법입니다. Python에서는 `csv` 모듈을 사용하여 CSV 파일을 읽고 쓸 수 있습니다.

### CSV 파일 작성
```python
import csv

# CSV 파일 작성
with open('user.csv', 'w', encoding='utf-8', newline='') as f:
    writer = csv.writer(f)
    writer.writerow(['ID', '이름'])
    writer.writerow(['001', '뽀로로'])
    writer.writerow(['002', '크롱'])

# csv.writer()를 사용하여 CSV 파일에 데이터를 기록합니다.
# writerow() 메서드는 리스트 형태의 데이터를 한 행씩 추가합니다.
# newline=''는 각 행 사이에 빈 줄이 추가되는 것을 방지합니다.
```
`user.csv` 파일에 헤더와 두 개의 데이터 행을 작성하는 예제입니다. `newline=''`을 지정하여 Windows에서 빈 줄이 추가되는 문제를 방지합니다.

### CSV 파일 읽기
```python
import csv

# CSV 파일 읽기
with open('user.csv', 'r', encoding='utf-8') as f:
    reader = csv.reader(f)
    next(reader)  # 헤더 건너뛰기
    for row in reader:
        print(row)

# csv.reader()를 사용하여 CSV 파일에서 데이터를 읽습니다.
# next(reader)는 첫 번째 행(헤더)을 건너뛰도록 합니다.
# 반복문을 사용하여 각 행을 출력합니다.
```
`user.csv` 파일에서 데이터를 읽고 출력하는 예제입니다. `next(reader)`를 사용하여 헤더를 건너뛰고 실제 데이터만 처리합니다.

### CSV 파일에 추가
```python
import csv

# CSV 파일에 데이터 추가
with open('user.csv', 'a', encoding='utf-8', newline='') as f:
    writer = csv.writer(f)
    writer.writerow(['003', '에디'])

# 'a' 모드는 파일을 추가 모드로 열어 기존 데이터 뒤에 새로운 데이터를 추가합니다.
```


## 3. Excel 파일 처리
Excel 파일을 다루기 위해서는 `openpyxl` 모듈을 사용할 수 있습니다. 이 모듈은 Excel 2010 xlsx/xlsm/xltx/xltm 파일 포맷을 지원합니다.

```python
import openpyxl

# Excel 파일 열기
wb = openpyxl.load_workbook('cha.xlsx')
ws = wb['Sheet1']  # 시트 이름으로 접근

# 데이터 읽기
for row in ws.iter_rows(values_only=True):
    print(row[0], row[1])

# ws.iter_rows(values_only=True)는 각 행의 셀 값을 튜플 형태로 반환합니다.
# 이 튜플을 반복하여 셀의 값을 출력합니다.

# 데이터 수정
ws['B2'] = '크롱'

# 수정된 Excel 파일 저장
wb.save('cha_ver_1.2.xlsx')
```



## 4. XML 파일 처리
**XML (eXtensible Markup Language)** 은 데이터의 구조를 정의하는 마크업 언어입니다. Python에서는 `xml.etree.ElementTree` 모듈을 사용하여 XML 파일을 읽고 쓸 수 있습니다.

### XML 파일 읽기 및 수정
```python
import xml.etree.ElementTree as et

# XML 파일 읽기
tree = et.parse("user.xml")
root = tree.getroot()

# XML 데이터 조회
for item in root.findall('user'):
    print('이름:', item.find('name').text)
    print('아이디:', item.find('id').text)
    print('수준:', item.get('level'))

# XML 데이터를 수정
second_user = root.findall('user')[1]
second_user.find('name').text = '김유신'
second_user.set('level', '3')

# 수정된 XML 파일 저장
header = '<?xml version="1.0" encoding="UTF-8"?>\n'
output = et.tostring(root, encoding='UTF-8')
with open('user2.xml', 'w', encoding='UTF-8') as f:
    f.write(header + output.decode('utf-8'))

# et.parse()는 XML 파일을 파싱하여 ElementTree 객체를 반환합니다.
# ElementTree 객체에서 root를 사용하여 XML 데이터를 접근합니다.
# 수정 후 et.tostring()을 사용하여 수정된 XML을 문자열로 변환하고 파일에 저장합니다.
```
`user.xml` 파일에서 XML 데이터를 읽고 수정한 후, 수정된 내용을 새 XML 파일에 저장하는 예제입니다. XML 데이터를 문자열로 변환할 때, UTF-8 인코딩을 사용하여 저장합니다.



## 5. SQLite 데이터베이스 처리
SQLite는 가벼운 관계형 데이터베이스 관리 시스템입니다. Python에서는 `sqlite3` 모듈을 사용하여 SQLite 데이터베이스를 다룰 수 있습니다.

### 데이터 조회
```python
import sqlite3

# SQLite DB 연결
conn = sqlite3.connect('test.db')
cur = conn.cursor()

# 데이터 조회 쿼리 실행
cur.execute('SELECT * FROM customer')
rows = cur.fetchall()

# 결과 출력
for row in rows:
    print(row)

conn.close()

# sqlite3.connect()는 SQLite 데이터베이스 파일에 연결하거나 새 파일을 생성합니다.
# cursor 객체를 통해 SQL 쿼리를 실행하고, fetchall()로 모든 결과를 가져옵니다.
```

### 데이터 추가
```python
import sqlite3

# SQLite DB 연결
conn = sqlite3.connect('test.db')
cur = conn.cursor()

# 데이터 추가 쿼리
sql = 'INSERT INTO customer(name, category, region) VALUES(:name, :category, :region);'

# 데이터 삽입
cur.execute(sql, {'name': '이순신', 'category': 2, 'region': '부산'})
cur.execute(sql, {'name': '강감찬', 'category': 2, 'region': '부산'})
cur.execute(sql, {'name': '권율', 'category': 3, 'region': '인천'})

# 변경 사항 커밋
conn.commit()
conn.close()

# SQL INSERT 문을 사용하여 데이터를 삽입합니다.
# 커밋을 통해 데이터베이스에 변경 사항을 저장합니다.
```