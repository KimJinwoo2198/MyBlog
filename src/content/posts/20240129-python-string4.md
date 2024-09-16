---
title: "[ Python 강의 ] 6-4. 자료형 변환"
published: 2024-01-29
description: 파이썬에서 자료형 변환에 대해서 알아보아요.
# image: ./cover.jpg
tags: [강의, 파이썬]
category: 파이썬강의
draft: false
---

# 파이썬 문자열 이해하기 - Part 4: 자료형 변환

프로그래밍을 할 때 자주 마주치는 상황 중 하나는 서로 다른 자료형 간의 변환이 필요할 때입니다. 파이썬에서는 이러한 변환을 쉽고 직관적으로 할 수 있는 다양한 방법을 제공합니다. 이번 글에서는 파이썬에서 자주 사용되는 자료형 변환 방법에 대해 알아보겠습니다.

## 기본 자료형과 변환

파이썬에서는 다양한 자료형을 지원합니다. 가장 기본적인 자료형은 정수(int), 실수(float), 문자열(str) 등이 있습니다. 

### 1. 정수형으로 변환: `int()`

문자열이나 실수를 정수형으로 변환할 수 있습니다. 이는 데이터를 처리하거나 계산할 때 유용하게 사용됩니다.

```python
number_str = "10"
number_int = int(number_str)
print(number_int, type(number_int))  # 출력: 10 <class 'int'>
```

### 2. 실수형으로 변환: `float()`

문자열이나 정수를 실수형으로 변환할 때 사용합니다. 이는 소수점이 포함된 계산이 필요할 때 필요합니다.

```python
number_str = "3.14"
number_float = float(number_str)
print(number_float, type(number_float))  # 출력: 3.14 <class 'float'>
```

### 3. 문자열로 변환: `str()`

정수, 실수 등 다른 자료형을 문자열로 변환할 때 사용합니다. 이는 데이터를 출력하거나 사용자와의 상호작용에서 자주 쓰입니다.

```python
number_int = 500
number_str = str(number_int)
print(number_str, type(number_str))  # 출력: 500 <class 'str'>
```