---
layout  : post
title   : 
summary : 
date    : 2020-07-25 16:57:49 +0900
updated : 2020-07-25 16:57:49 +0900
tags    : 
toc     : true
public  : true
parent  : 
latex   : false
---
* TOC
{:toc}

## Title

제목에 다음과 같은 Type을 붙인 후, :로 구분하고 제목을 쓴다.

* feat : New function 추가
* fix : Bug fix
* docs : Document 수정
* style : Code에 대해 포맷을 변경하거나, 누락된 문법 요소를 추가하는 등 코드의 직접적인 변경과 무관한 내용
* refactor : Production Code Refactoring
* test : Test 관련 (Production 코드와 무관)
* chore : Build Task Update

-----

* 제목은 대문자로 시작, 명령문을 사용한다 (과거 시제 사용 X)
* Issue에 대응하는 commit일 경우, Type #Issue - Title 형태로 작성

## Description

* 맨 뒤에 마침표를 붙이지 않으며, 50자 이내로 적는다
* Title과 Description을 한 줄 띄워서 분리한다

## commit으로 Issue 종료하기

commit message 내부에 다음 키워드를 사용하여 keyword #issue-number 형태로 적은 후 push하면 자동으로 issue 종료

* close
* closes
* closed
* fix
* fixes
* fixed
* resolve
* resolves
* resolved
