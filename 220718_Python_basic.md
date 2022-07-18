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
            

- 컨테이너
    
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
        - 범위 지정 : `range(n, m)`
            - n부터 m-1까지의 시퀀스
        - 범위 및 스텝 지정 : `range(n, m s)`
            - n부터 m-1까지 s만큼 증가시키는 숫자의 시퀀스
        
        ```python
        # 0부터 특정 숫자까지
        print(list(range(3))) # [0, 1, 2]
        # 숫자의 범위
        print(list(range(1, 5))) # [1, 2, 3, 4]
        # step 활용
        print(list(range(1, 5, 2))) # [1, 3]
        
        # 역순
        print(list(6, 1, -1))) # [6, 5, 4, 3, 2]
        print(list(6, 1, -2))) # [6, 4, 2]
        print(list(range(6, 1, 1) # []
        ```
        
    
    > 집합 (Set)
    > 
    - 데이터 중복 허용 X, 순서가 없기 때문에 인덱스를 통한 접근 불가능
    - 중괄호 {} 혹은 set()을 통해 생성  (but, 빈 중괄호는 dictionary 자료형태임)
    
    ```python
    | : 합집함, & : 교집합, - : 차집합, ^ : 대칭차집함(합집합에서 교집합 뺀 거), 여집합은 존재X
    
    A_set = {1, 2, 3, 4}
    B_set = {1, 2, 3, 'Hello', (1, 2, 3)}
    print(B_set - A_set) # {(1, 2, 3), 'Hello'}
    print(A_set ^ B_set) # {'Hello', 4, (1, 2, 3)}
    ```
    
    > 딕셔너리
    > 
    - key-value 쌍으로 이루어진 자료형
    - key
        - key는 변경 불가능한 데이터(immutable)만 활용 가능
            : str, int, float, boolean, tuple, range
            
    - value
        - 어떤 형태든 상관없음 <br></br>
        
    - 중괄호 `{}` 혹은 `dict()`을 통해 생성
    
    ```python
    # 딕셔너리는 아래와 같이 두 방법으로 만들 수 있음
    **dict_a = {'a' : 'apple', 'b' : 'banana', 'list' : [1, 2, 3]}**
    print(dict_a['list])  # [1, 2, 3]
    **dict_b = dict(a = 'apple', b = 'banana', list = [1, 2, 3])**
    print(dict_b) # {'a' : 'apple', 'b' : 'banana', 'list' : [1, 2, 3]}
    ```
    
    > 형변환
    > 
    
    : 파이썬에서 데이터 형태는 서로 변환할 수 있음
    
    - 암시적 형 변환 (implicit)
        
        : 사용자가 의도하지 않고, 파이썬 내부적으로 자료형을 변환하는 경우 (파이썬)
        
    - 명시적 형 변환 (explicit)
        
        : 사용자가 특정 함수를 활용하여 의도적으로 자료형을 변환하는 경우 (개발자)
        
    
    ---
    
    - `**input()**` : 사용자 데이터 입력
    
    ```python
    number = input('아무 숫자나 입력하세요.`)
    
    print(type(number)) # 숫자를 쳐도 무조건 str 자료형으로 뜸
    ```
    
     `**map(int, input().split())**` : 입력값을 int형으로 변환시켜주고 split은 쪼개준다는 의미