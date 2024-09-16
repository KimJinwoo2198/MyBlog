---
title: "[ Python 강의 ] 6-2. 메소드"
published: 2024-01-27
description: 파이썬에서 메소드에 대해서 알아보아요.
# image: ./cover.jpg
tags: [강의, 파이썬]
category: 파이썬강의
draft: false
---
# 파이썬 문자열 이해하기 - Part 2: 메소드

프로그래밍을 처음 접하시는 분들에게 '메소드(Method)'는 다소 생소한 개념일 수 있습니다. 간단히 말해, 메소드는 특정 객체에 적용할 수 있는 '함수'의 일종입니다. 하지만, 메소드는 일반 함수와는 다르게 특정 객체와 밀접한 관련이 있으며, 그 객체의 '행동'이나 '기능'을 정의합니다.

## 메소드의 이해
1. 객체와의 연관성
메소드는 객체 지향 프로그래밍의 핵심 요소 중 하나입니다. 객체란 실세계의 사물 또는 개념을 프로그래밍적으로 표현한 것으로, 데이터(속성)와 그 데이터에 관련된 행위(메소드)를 포함합니다.

2. 메소드의 구조
파이썬에서 메소드는 주로 점(.) 표기법을 사용하여 호출됩니다. 예를 들어, string.upper()에서 upper()는 string이라는 문자열 객체에 적용되는 메소드입니다. 이 메소드는 string의 모든 문자를 대문자로 변환하는 기능을 수행합니다.

3. 메소드와 함수의 차이
메소드는 특정 객체에 종속되어 있습니다. 예를 들어, 문자열 객체의 메소드는 문자열에만 사용할 수 있습니다. 반면, 일반 함수는 보다 독립적이며, 다양한 유형의 입력에 적용될 수 있습니다.

# 메소드 예시

## 1. `len()`: 문자열 길이 구하기

`len()` 함수는 문자열의 길이를 반환합니다. 이 함수는 문자열에 포함된 문자의 개수를 세어 그 수를 알려줍니다.

```python
s = "Hello, Python!"
length = len(s)
print(length)  # 출력: 14
```

- 사용 예시: 사용자 입력의 길이 제한 검사, 텍스트 데이터 처리 등에 활용됩니다.

## 2. `str.upper()`와 `str.lower()`: 대소문자 변환

문자열의 모든 문자를 대문자(`upper()`) 또는 소문자(`lower()`)로 변환합니다. 이는 텍스트의 일관된 형식을 유지하거나, 대소문자 구분 없이 비교할 때 유용합니다.

```python
greeting = "Hello, World!"
print(greeting.upper())  # 출력: HELLO, WORLD!
print(greeting.lower())  # 출력: hello, world!
```

- 사용 예시: 사용자 입력을 표준화하거나, 대소문자 구분 없는 검색 등에 활용됩니다.

## 3. `str.strip()`, `str.lstrip()`, `str.rstrip()`: 공백 제거

`strip()` 메소드는 문자열의 앞과 뒤에 있는 공백을 제거합니다. `lstrip()`은 문자열 왼쪽의 공백을, `rstrip()`은 오른쪽의 공백을 제거합니다.

```python
text = "   Hello, Python!   "
print(text.strip())   # 양쪽 공백 제거
print(text.lstrip())  # 왼쪽 공백 제거
print(text.rstrip())  # 오른쪽 공백 제거
```

- 사용 예시: 사용자 입력의 불필요한 공백 제거, 파일 처리 시 줄바꿈 문자 제거 등에 활용됩니다.

## 4. `str.startswith()`와 `str.endswith()`: 문자열의 시작과 끝 확인

`startswith()`와 `endswith()` 메소드는 문자열이 특정 문자 또는 문자열로 시작하거나 끝나는지를 확인합니다. 이는 문자열의 특정 패턴을 검사할 때 유용합니다.

```python
filename = "report.pdf"
print(filename.endswith(".pdf"))  # 출력: True
print(filename.startswith("rep"))  # 출력: True
```

- 사용 예시: 파일 확장자 검사, 특정 패턴으로 시작하는 텍스트 필터링 등에 활용됩니다.

## 5. `str.replace()`: 문자열 내용 교체

`replace()` 메소드는 문자열 내의 특정 부분 문자열을 다른 문자열로 교체합니다. 이는 텍스트 데이터 내용을 변경할 때 유용합니다.

```python
message = "Hello, World!"
new_message = message.replace("World", "Python")
print(new_message)  # 출력: Hello, Python!
```

- 사용 예시: 텍스트 데이터 정제, 단어 교체 등에 활용됩니다.

## 6. `str.split()`: 문자열 분리

`split()` 메소드는 문자열을 지정된 구분자에 따라 분리하여 리스트로 반환합니다. 기본 구분자는 공백이지만, 다른 문자를 지정할 수도 있습니다.

```python
data = "apple, banana, cherry"
words = data.split(", ")
print(words)  # 출력: ['apple', 'banana', 'cherry']
```

- 사용 예시: CSV 파일 처리, 사용자 입력 파싱 등에 활용됩니다.

## 7. `str.join()`: 문자열 결합

`join()` 메소드는 여러 개의 문자열을 하나의 문자열로 결합합니다. 이 메소드는 문자열 리스트를 하나의 문자열로 합칠 때 주로 사용됩니다.

```python
words = ["Python", "is", "awesome"]
sentence = " ".join(words)
print(sentence)  # 출력: Python is awesome
```

- 사용 예시: 문자열 리스트를 하나의 문자열로 변환, 파일 경로 생성 등에 활용됩니다.

## 8. `str.find()`와 `str.index()`: 문자열 내 위치 찾기

`find()` 메소드는 부분 문자열의 첫 번째 인덱스를 반환하며, 해당 부분 문자열이 없는 경우 `-1`을 반환합니다. `index()`는 비슷하지만 부분 문자열이 없으면 오류를 발생시킵니다.

```python
s = "Hello, Python!"
position = s.find("Python")
print(position)  # 출력: 7
```

- 사용 예시: 특정 문자 또는 부분 문자열의 위치 확인, 텍스트 데이터 분석 등에 활용됩니다.