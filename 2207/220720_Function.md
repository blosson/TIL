# 220720 :: Python 제어문 및 함수

## 제어문

- 조건문
    - 중첩 조건문
    
   
    → 중첩 조건문에서 **else: 는 마지막에 하나만 써줘도 됨** **(즉, 하부 if 문의 else: 를 일일이 써줄 필요가 없음!))**
    
    - 조건 표현식 (Conditional Expression)
        - 삼항 연산자 (Ternary Operator)로 부르기도 함
        
        ```python
        true인 경우 값 if 조건 else false인 경우 값
        
        # 왼참 (왼쪽 참) <if 조건 else> 오거 (오른쪽 거짓)
        ```
        
        ```python
        
        # 삼항연산자 예시
        num = 1
        result = '홀수입니다.' if num % 2 == 1 else '짝수입니다.'
        print(result)
        
        ---
        # 삼항연산자 -> if 문 (사실 이게 더 가독성 좋고 직관적인듯..)
        num = 1
        if num % 2 == 1:
        	print('홀수입니다.')
        else:
        	print('짝수입니다.')
        ```
        
    
- 반복문
    - while 문
        - **종료 조건에 해당하는 코드**를 통해 반복문을 종료시켜야 함 ex) 쿠키런
    - for 문
        - 반복 가능한 객체를 모두 순회하면 종료 **(별도의 종료 조건이 필요 없음)** ex) 피라미드 별찍기
    - 반복 제어
        - break, continue, for-else
    
    > While 문
    > 
    - 조건식이 참인 경우 반복적으로 코드를 실행 `while 조건:`
        - 조건이 참인 경우 들여쓰기 되어 있는 코드 블럭이 실행됨
        - 코드 블럭이 모두 실행되고, 다시 조건식을 검사하며 반복적으로 실행됨
        - while문은 **무한 루프를 하지 않도록** 반드시 **종료 조건이 필요**
        
        ```python
        a = 0
        while a < 5: # 종료조건!!!
        	print(a)
        	a += 1
        print('끝')
        ```
        
        ★ **꿀팁 : Python Tutor** : Python의 code 과정을 시각화해서 보여줌
        
        [visualize.html#mode=edit](https://pythontutor.com/visualize.html#mode=edit)
        
        - 복합 연산자 (In-Place Operator) `a += 1` `a += a`
    
    > for 문
    > 
    - 시퀀스 (String, tuple, list, range)를 포함한 **순회 가능한 객체(iterable)**의 요소를 모두 순회 `for 변수명 in iterable:`
        - 처음부터 끝까지 모두 순회하므로 별도의 **종료 조건이 필요하지 않음**
    - **iterable**
        - 순회할 수 있는 자료형 (string, list, dict, tuple, range, set 등)
        - 순회형 함수 (range, enumerate)
        
    - 딕셔너리 (Dictionary) 순회
        - 딕셔너리는 기본적으로 **key를 순회**하며, key를 통해 값을 활용
        
        ```python
        grades = {'john' : 80, 'eric' :90}
        for students in grades:
        	print(student)
        '''
        john
        eric
        '''
        
        **#** **value 값도 출력하고 싶을 때** 
        
        grades = {'john' : 80, 'eric' :90}
        for student in grades:
        	print(student, **grades[student]**)
        '''
        john 80
        eric 90
        '''
        ```
        
        - 추가 메서드를 활용하여 순회할 수 있음
            - keys() : key로 구성된 결과
            - values() : value로 구성된 결과
            - items() : (key, value)의 튜플로 구성된 결과
        
        ```python
        grades = {'john' : 80, 'eric' :90}
        print(grades.keys())
        print(grades.values())
        print(grades.items())
        '''
        dic_keys {['john', 'eric']}
        dic_values {[80, 90]}
        dic_items {[('john', 80), ('eric', 90)]}
        '''
        
        ---
        grades = {'john' : 80, 'eric' :90}
        for student, grade in grades.items():
        	print(student, grade)
        ```
        
    - **enumerate 순회 (★★★)**
        - 인덱스와 객체를 쌍으로 담은 열거형 (enumerate) 객체 반환
            - (index, value) 형태의 **tuple**로 구성된 열거 객체를 반환
        
        ```python
        members = ['민수', '영희', '철수']
        
        for idx, member in enumerate(members):
        	print(idx, member)
        
        '''
        0 민수
        1 영희
        2 철수
        '''
        
        # 기본값은 0이나 start를 지정하면 해당 값부터 순차적으로 증가
        
        print(list(enumerate(members, start=1))) # [(1, '민수'), (2, '영희'), (3, '철수')]
        # start=숫자 말고 그냥 바로 숫자 써도 적용됨
        ```
        
    - **List Comprehension (엄청 자주 쓰임)**
        - 표현식과 제어문을 통해 특정한 값을 가진 리스트를 간결하게 생성하는 방법
        
        `[code for 변수 in iterable]`  `[code for 변수 in iterable if 조건식]`
        
        ```python
        # e.g) 1~3의 세제곱 리스트 만들기
        
        # 1번 방법
        cubic_list = []
        for number in range(1, 4):
        	cubic_list.appnd(number ** 3)
        print(cubic_list)
        
        # [1, 8 ,27]
        
        # 2번 방법
        cubic_list = [number ** 3 for number in range(1,4)]
        print(cubic_list)
        
        # [1, 8 ,27]
        ```
        
    - Dictionary Comprehension
        - 표현식과 제어문을 통해 특정한 값을 가진 딕셔너리를 간결하게 생성하는 방법
        
        `{key: value for 변수 in iterable}`  `{key : value for 변수 in iterable if 조건식}`
        
        ```python
        # e.g) 1~3의 세제곱 리스트 만들기
        
        # 1번 방법
        cubic_dict = {}
        for number in range(1, 4):
        	cubic_dict[number] = number ** 3
        print(cubic_dic)
        
        # {1: 1, 2: 8, 3: 27}
        
        # 2번 방법
        cubic_dict = {number ** 3 for number in range(1,4)}
        print(cubic_dict)
        
        # {1: 1, 2: 8, 3: 27}
        ```
        
    
    > 반복문 제어
    > 
    - break
        - 반복문을 종료
    - continue (실행해야하는 코드를 건너뛰기)
        - continue 이후의 코드 블럭은 수행하지 않고, **다음 반복을 수행**
    - for-else
        - 끝까지 반복물을 실행한 이후에 else문 실행
            - break를 통해 중간에 종료되는 경우 else 문은 실행되지 않음
    - pass
        - 아무것도 하지 않음 (문법적으로 필요하지만 할 일이 없을 때 사용)
        - 보통 구조 잡을 때 많이 쓰임
        - **반복문 아니어도 사용 가능**
        

## 함수

- 함수를 사용하는 이유? → 분해 (Decomposition) and 추상화 (Abstraction)  - 재사용성과 가독성!

- 함수의 종류
    - 내장함수
        - 파이썬에 기본적으로 포함된 함수 (파이썬 개발자가 만든, 자동설치되어있는 함수)
    - **외장함수**
        - **import 문을 통해 사용**하며, 외부 라이브러리에서 제공하는 함수 (다른 개발자가 만든 함수)
    - 사용자 정의 함수
        - 사용자가 직접 만드는 함수 (내가 만든 함수)
        
        print vs return
        
        2개 이상 return 원할 때 tuple 활용
        
        palindrome
        
        parameter (선언, 정의할 때)  vs argument (호출할 때)
        
        positional (x=2 , y= 2 이거 어려움)
        
        **가변인자 *asterisk(args)** 
        
        패킹 vs 언패킹(언패킹시 요소 개수가 같아야 함)
        
        **가변키워드인자 **kwargs**
        
        scope : built in(파이썬이 실행) global (내가 작성한 코드 어디에서든) vs local (함수 내부에서만)
        
        variable : global vs local
        
        abc 예시 이해하기
        
        global a 변수 설정
        
        global 이해하기 
        
        내장함수 - map, filter, zip, 
        
        lamda 함수
        
        재귀함수 (recursive function) e.g) 팩토리얼
        
        모듈 - 다양한 기능을 하나의 파일로(.py)
        
        패키지 - 다양한 파일을 하나의 폴더로, 특정 기능과 관련된 여러 모듈의 집합
        
        라이브러리 - 다양한 패키지를 하나의 묶음으로
        
        라이브러리 (도구, 삽 - 주도권이 나한테 있음) vs 프레임워크 (포크레인 - 주도건이 나한테 없음)
        
        pip - 이것들을 관리하는 곳(파이썬 패키지 관리자)
        
        가상환경 - 패키지의 활용 공간
        

## 교수님 꿀팁

- **enumerate( )**
    - **literable**은 다 enumerate에 들어갈 수 있다!
    - **start 값**을 줘서 시작값을 제어할 수 있다!
- for문을 한 줄 로 만드는 게 성능에 대단히 향상되지 않음. **오히려 2차원 배열에 대한 이해가 훨씬 더 중요함.**
    
    → 한 줄씩 디버그 하는 게 더 중요하기 때문에, 가독성을 위해
    
- 함수 생성할 때 ( )를 매개변수라고 하고, 출력할 때  ( )에 넣는 값을 인자값이라고 함
- 귀찮더라도 len( ), sum( ), sort ( ) 함수를 안 쓰고 **직접 만들어서 써보길**
- comprehension도 좋지만 그냥 2차원 for문으로 하길
- dict도 순회가 가능하다는 걸 까먹지 말아라!!

- 재귀함수는 진짜 많이 해봐야 익숙해진다.
- S