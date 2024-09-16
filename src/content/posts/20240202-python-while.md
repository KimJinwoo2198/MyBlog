---
title: "[ Python 강의 ] 9. While"
published: 2024-02-02
description: 파이썬에서 While 문 사용방법을 알아보아요.
# image: ./cover.jpg
tags: [강의, 파이썬]
category: 파이썬강의
draft: false
---

# While 문

## 1. While 문이란?

`while` 문은 조건이 참(True)인 동안, 즉 조건식이 `False`를 반환할 때까지 코드 블록을 반복 실행하는 반복문입니다. 이는 특정 조건이 만족되는 동안 계속해서 작업을 반복하고자 할 때 유용합니다.

## 2. 기본 구조

파이썬에서 `while` 문의 기본 구조는 다음과 같습니다.

```python
while 조건:
    # 조건이 참인 동안 실행할 코드
```

- 조건: 반복을 계속할지 결정하는 데 사용되는 표현식입니다. 이 조건이 `False`가 되면, 반복이 종료됩니다.

## 3. 예시 코드

다음은 `while` 문을 사용하는 간단한 예시입니다.

```python
count = 0
while count < 5:
    print("count는 현재", count, "입니다.")
    count += 1  # count를 1씩 증가시킵니다.
```

이 코드는 `count` 변수가 5보다 작은 동안 "count는 현재 X입니다."를 출력하고, `count`를 1씩 증가시킵니다. `count`가 5에 도달하면 조건이 `False`가 되어 반복이 종료됩니다.

## 4. 주의사항

`while` 문을 사용할 때는 반복문이 영원히 실행되지 않도록 주의해야 합니다. 이를 **무한 루프**라고 합니다. 반복문 내에서 조건이 결국 `False`가 되도록 만드는 로직을 반드시 포함시켜야 합니다.

## 5. While 문의 활용

`while` 문은 사용자 입력을 처리하거나, 파일의 끝에 도달할 때까지 데이터를 읽는 등 다양한 상황에서 유용하게 사용될 수 있습니다. 예를 들어, 사용자가 'quit'을 입력할 때까지 입력을 계속 받는 프로그램은 다음과 같이 작성할 수 있습니다.

```python
user_input = ""
while user_input != "quit":
    user_input = input("명령을 입력하세요 (프로그램을 종료하려면 'quit'을 입력): ")
    print("입력된 명령:", user_input)
```

이 코드는 사용자가 'quit'을 입력할 때까지 사용자의 입력을 받아 출력합니다.
