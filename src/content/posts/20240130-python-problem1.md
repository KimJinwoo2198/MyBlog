---
title: "[ Python 강의 ] 중간점검 ( 문제 풀기 )"
published: 2024-01-30
description: 파이썬을 잘 이해했는지 문제를 풀어보아요.
# image: ./cover.jpg
tags: [강의, 파이썬]
category: 파이썬강의
draft: false
---


# 시험
이번 글에서는 앞에서 배웠던 내용을 실제로 활용해서 문제를 풀어보는 시간을 가지겠습니다.


## 문제 - 1
`Hello World` 문자열에서 `World`를 `Python`으로 변경하세요.<br>
**작동 예시**
```
Python World
```
<details>
<summary>해답 보기</summary>
<div markdown="1">

### 모범 답안
```python
text = "Hello World"
new_text = text.replace("World", "Python")
print(new_text)
```
</div>
</details>

## 문제 - 2
문자열 `Python programming is fun.`에서 `programming`이라는 단어의 시작 인덱스와 끝 인덱스를 찾는 코드를 작성하세요.<br>
**작동 예시**
```
시작 인덱스 : 7 끝 인덱스 : 17
```
<details>
<summary>해답 보기</summary>
<div markdown="1">

### 모범 답안
```python
s = "Python programming is fun."
start_index = s.find("programming")
end_index = start_index + len("programming") - 1
print("시작 인덱스 : ", start_index, "끝 인덱스", end_index)
```
</div>
</details>

## 문제 - 3
사용자로부터 두 개의 정수를 입력받아, 두 숫자의 합을 출력하는 코드를 작성하세요.<br>
**작동 예시**
```
숫자 2개를 입력하세요: 5 3
답: 8
```
<details>
<summary>해답 보기</summary>
<div markdown="1">

### 모범 답안
```python
# 숫자 두 개를 입력받음
num1, num2 = map(int, input("숫자 2개를 입력하세요: ").split()) # 해당 문법을 쓰면 띄워쓰기가 있어도 숫자가 각각 분리됨.
product = num1 + num2
print("답:", product)
```
</div>
</details>

## 문제 - 4
문자열 `안녕하세요. 저는 파이썬 강의를 진행중인 김진우라고 합니다.` 에서 모든 공백을 제거하는 코드를 작성하세요.<br>
**작동 예시**
```
안녕하세요.저는파이썬강의를진행중인김진우라고합니다.
```
<details>
<summary>해답 보기</summary>
<div markdown="1">

### 모범 답안
```python
string = "안녕하세요. 저는 파이썬 강의를 진행중인 김진우라고 합니다."
string_no_spaces = string.replace(" ", "")
print(string_no_spaces)
```
</div>
</details>

## 문제 - 5
입력받은 문자열을 거꾸로 출력하는 코드를 작성하세요.<br>
**작동 예시**
```
문자열을 입력하세요 : Hello World
dlroW olleH
```
<details>
<summary>해답 보기</summary>
<div markdown="1">

### 모범 답안
```python
input_string = input("문자열을 입력하세요 : ")
reversed_string = input_string[::-1]
print(reversed_string)
```
</div>
</details>

## 문제 - 6
문자열 `Python`을 문자 `P`만 대문자이고 나머지는 소문자인 `pYTHON`으로 변환하는 코드를 작성하세요.<br>
**작동 예시**
```
pYTHON
```
<details>
<summary>해답 보기</summary>
<div markdown="1">

### 모범 답안
```python
original = "Python"
modified = original[0].lower() + original[1:].upper()
print(modified)
```
</div>
</details>

문제 풀이를 보고도 이해가 안되신다면 댓글로 알려주세요.
틀린 문제는 반드시 이해하고 넘어가시기 바랍니다.
