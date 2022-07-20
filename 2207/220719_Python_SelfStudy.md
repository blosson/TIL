- 단축평가
    - Point!
        - 해당 문자가 vowel 안에 있는지 어떻게 확인할건지?
        - `'a' and 'b'` 와 `'b' and 'a'` 의 차이점을 알아야 함 (단축평가)

```python
vowels = 'aeiou'

print('a' and 'b' in vowels) # False
print('b' and 'a' in vowels) # True

# find로 풀이
print(vowels.find('a')) # 0 (find 함수는 위치를 나타내주기 때문)
print(vowels.find('b')) # -1 (b가 존재하지 않기 때문에 -1을 출력)
```