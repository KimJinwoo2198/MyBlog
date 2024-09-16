---
title: "[ Python 강의 ] 7. input()"
published: 2024-01-31
description: 파이썬에서 input 을 받는 방법에 대해서 알아보아요.
# image: ./cover.jpg
tags: [강의, 파이썬]
category: 파이썬강의
draft: false
---

# `input()` 함수

파이썬 프로그래밍에서 사용자와의 상호작용은 매우 중요한 부분을 차지합니다. `input()` 함수는 사용자로부터 직접 입력을 받는 기본적인 방법을 제공합니다. 이 글에서는 `input()` 함수의 사용법과 활용 예시에 대해 알아보겠습니다.

## `input()` 함수의 기본

`input()` 함수는 사용자에게 입력을 요청하고, 사용자가 입력한 값을 문자열로 반환합니다.

```python
user_input = input("Enter your name: ") # 화면에 Enter your name: 출력 및 사용자 입력 요청
print("Hello, " + user_input + "!")
```

이 코드는 사용자에게 이름을 입력하라는 메시지를 보여주고, 입력된 이름을 화면에 인사와 함께 출력합니다.

## `input()`과 자료형 변환

`input()`으로 받은 입력은 기본적으로 문자열(`str`) 형태입니다. 때로는 이를 다른 자료형으로 변환해야 할 필요가 있습니다.

### 예시: 숫자로 변환하기

사용자로부터 숫자를 입력받아 계산에 사용하는 경우, 입력값을 정수나 실수로 변환해야 합니다.

```python
age = input("Enter your age: ")
age = int(age)  # 문자열을 정수로 변환
print("Next year, you will be " + str(age + 1) + " years old.")
```

이 예제에서는 입력받은 나이를 정수로 변환한 후, 1년 후의 나이를 계산하여 출력합니다.