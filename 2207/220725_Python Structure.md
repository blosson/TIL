# 데이터 구조

- 메서드는 클래스 내부에 정의한 함수, 사실상 함수와 동일
- **데이터구조.메서드()** 형태로 활용. **주어.동사()** 라고 쉽게 생각
    - ex) string.split(), list.append(10)
- 파이썬 공식 문서의 표기법 (배커스-나우르 표기법)
    - ex) str.replace(old, new [,count]  : old, new는 필수 / [,count]는 선택적 인자를 뜻함
    

## 순서가  있는 데이터 구조 (문자열, 리스트, 튜플)

### 문자열 (String)

- 모든 문자는 str 타입 (변경 불가능한 **immutable**)

- 문자열 조회/탐색 및 검증 메서드
    
    ![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/9298d41a-baaa-4d6f-9cf1-89d7be352d30/Untitled.png)
    
    - .find(x) : x의 첫 번째 위치를 반환. 없으면 -1을 반환함.
    
    ```python
    print('apple'.find('p')) # 1
    
    print('apple'.find('k')) # -1
    ```
    
    - .index(x) : x의 첫 번째 위치를 반환. 없으면 오류 발생
    
    ```python
    print('apple'.index('p')) # 1
    
    print('apple'.index('k')) # ValueError: substring not found
    ```
    
    - 문자열 관련 검증 메서드
    
    ```python
    print('abc'.isalpha()) # True
    print('ㄱㄴㄷ'.isalpha()) # True
    print('Ab'.isupper()) # False
    print('ab'.islower()) # True
    print('Title Title!'.istitle()) 
    # True (문자열 띄어쓰기 기준으로 각 단어의 첫 글자가 대문자인지 검증)
    ```
    
- 문자열 변경 메서드
    
    ![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/24f1d139-9230-4367-8c75-6c955215c1bf/Untitled.png)
    
    - .find(x) : x의 첫 번째 위치를 반환. 없으면 -1을 반환함.
        - .find(x) : x의 첫 번째 위치를 반환. 없으면 -1을 반환함.

### 리스트 (List)

### 튜플 (Tuple)

## 비시퀀스형 데이터 구조 (셋, 딕셔너리)

### 셋 (Set)

### 딕셔너리 (Dictionary)

## 얕은 복사와 깊은 복사

- 할당
    - 대입 연산자 (=)
        - 대입 연산자(=)를 통한 복사는 해당 객체에 대한 참조를 복사 (= 같이 쓰는 사물함을 바꾸는 것임) 그래서 한꺼번에 바뀌어벌임…
        
- 얕은 복사 (Shallow Copy) - 1차원만 해결 가능
    - 할당 문제를 해결하기 위해 사용 (1차원)
    
    ```python
    original_list = [1, 2, 3]
    copy_list = **original_list[:]**
    print(original_list, copy_list)
    
    copy_list[0] = 'hi'
    print(original_list, copy_list)
    ```
    
    - (주의) 1차원에서만 사용 가능, 2차원 리스트에서는 못 막음 - 또 주소를 참조하기 때문에
    
- 깊은 복사 (Deep Copy) = 모든 문제 해결 가능
    
    ```python
    import copy
    
    a = [1, 2, ['a', 'b']]
    b = copy.deepcopy(a)
    
    print(a, b) # [1, 2, ['a', 'b']] [1, 2, ['a', 'b']]
    b[2][0] = 0
    print(a, b) # [1, 2, ['a', 'b']] [1, 2, [0, 'b']]
    ```
    

join, split 매우 중요!! 제발 공부하자