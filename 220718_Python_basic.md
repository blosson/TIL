## Python 기초

> 프로그래밍이란?
> 

    : 컴퓨터에게 일을 시키기 위해서 프로그램을 만드는 행위

- String Interpolation (문자열을 변수를 활용하여 만드는 법) : **f-strings**

```python
name = 'Kim'
score = 4.5

print(f'Hello, {name}! 성적은 {score}')
# Hello, Kim! 성적은 4.5

import datetime
today = datetime.datetime.now()
print(today) # 2022-07-08 16:04:15.200411

print(f'오늘은 {today:%y}년 {tdoay:%m}월 {today:%d}일')
# 오늘은 22년 07월 08일

pi = 3.141592
print(f'원주율은 {pi:.3}. 반지름이 2일 때 원의 넓이는 {pi*2*2}')
# 원주율은 3.14. 반지름이 2일 때 원의 넓이는 12.566368
```

- 기타
    - 비교연산자
        - `!=`  : 같지 않음
    - 논리연산자
        - Falsy : False는 아니지만 False로 취급되는 다양한 값
            
            : 0, 0.0, (), [], {}, “”(빈 문자열)
            
        - 논리 연산자에도 우선순위가 존재
            
            : **not, and, or 순**으로 우선순위가 높음 (and는 곱하기, or은 더하기로 생각하면 편함)
            
            ```python
            print(not True and False or not False) # True
            print(((not True) and False) or (not False)) # True
            ```
            

- 컨테이너 <br></br>
    
    > 리스트
    > 
    - 리스트는 담고 있는 요소를 변경할 수 있다. → 가변 자료형(mutable)
        
        ```python
        location = ['서울', '대전', '광주']
        location[0] = '양양'
        print(location) # ['양양', '대전', '광주']
        ```
        
    
    > 튜플
    > 
    - 여러 개의 값을 순서가 있는 구조로 저장하고 싶을 때 사용 (불변 자료형)
    - 소괄호 () 혹은 `tuple()`을 통해 생성
    - 튜플 생성 시 주의사항
        - 단일 항목의 경우
            - 하나의 항목으로 구성된 튜플은 생성 시 값 뒤에 쉼표를 붙어야 함
                
                `tuple_a = (1,)`
                
        - 복수 항목의 경우
            - 마지막 항목에 붙은 쉼표는 없어도 되지만, 넣는 것을 권장
                
                `tuple_b = (1, 2, 3,)`
                
    - 튜플 대입 (Tuple assignment)
        
        : 우변의 값을 좌변의 변수에 한 번에 할당하는 과정
        
        ```python
        x, y = 1, 2
        x, y = (1, 2) # 위와 아래는 완전히 같음
        print(x, y) # 1, 2
        ```
        
    
    > Range
    > 
    - 숫자의 시퀀스를 나타내기 위해 사용
    - 주로 반복문과 함께 사용됨
    - Range의 사용 방법
        - 기본형 : `range(n)`
            - ㅇ부터 n-1까지 숫자의 시퀀스
        - 범위 지정 : `range(n, m)
            - n부터 m-1까지의 시퀀스
        - 범위 및 스텝 지정 : range(n, m s)
            - n부터 m-1까지 s만큼 증가시키는 숫자의 시퀀스
        
        ```python
        # 0부터 특정 숫자까지
        print(list(range(3))) # [0, 1, 2]
        # 숫자의 범위
        ```
        
    
    `input()` : 사용자 데이터 입력
    
    ```python
    number = input('아무 숫자나 입력하세요.`)
    
    print(type(number)) # 숫자를 쳐도 무조건 str 자료형으로 뜸
    ```
    
     `map(int, input().split())` : 입력값을 int형으로 변환시켜주고 split은 쪼개준다는 의미
     
    
    
    ---
    