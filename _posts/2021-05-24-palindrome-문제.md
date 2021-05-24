---
layout  : post
title   : 
summary : 
date    : 2021-05-24 22:13:06 +0900
updated : 2021-05-24 22:13:06 +0900
tags    : 
toc     : true
public  : true
parent  : 
latex   : false
---
* TOC
{:toc}

# Palindrome 문제 풀이

- Palindrome

    ```python
    class Solution:
        def isPalindrome(self, s: str) -> bool:
            strs = []
            for char in s:
                if char.isalnum():
                    strs.append(char.lower())
            while len(strs) > 1:
                if strs.pop(0) != strs.pop():
                    return False
            return True
    ```

    1. List를 활용하여 판별
        - isalnum()은 영문자, 숫자 여부를 판별하는 함수. 이를 통해 해당 문자만 리스트에 추가하고, 문제 조건이 대소문자 구분 X 이므로, lower()를 통해 모두 소문자로 변경
        - 이를 통해 첫번째 반복문에서, 모든 문자, 숫자를 각각 개별적으로 list 요소로 저장함.
        - 이후 while문은 list에 남은 비교 대상이 있는지 확인...
            - pop()은 맨 뒤의 요소, pop(0)은 맨 앞의 요소를 의미
            - 두 요소를 서로 비교하며...(조건문에 돌입하는 순간 리스트에서 제거됨), 일치하지 않을 경우 False를 return함.

    ```python
    class Solution:
        def isPalindrome(self, s: str) -> bool:
            strs: Deque = collections.deque()
            for char in s:
                if char.isalnum():
                    strs.append(char.lower())
            while len(strs) > 1:
                if strs.popleft() != strs.pop():
                    return False
            return True
    ```

    2. Deque를 사용한 최적화

    - list 선언을 deque 명시로 바꾸고,
    - pop(0) 부분을 popleft()로 변경
        - 292ms → 48ms
            - 약 5배 가량 빨라짐
            - **Why?**
                - List의 pop(0)은 O(n)
                - Deque의 popleft는 O(1)
                    - 이를 n번씩 반복하면 각각 O(n^2) VS O(n)으로 성능 차이가 극적으로 벌어짐

```python
class Solution:
    def isPalindrome(self, s: str) -> bool:
        s = s.lower()
        s = re.sub('[^a-z0-9]', '', s)
        
        return s == s[::-1]
```

3. 정규식으로 a-z, 0-9만 남기고, 이후 slicing을 이용하여 풀이.

- 2번 방법에 비해 2배 개선 → 약 28ms
