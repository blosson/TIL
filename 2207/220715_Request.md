## Requests

- json이 key:value 형식이 key값을 입력해주면 value값이 출력된다.

```python
import requests

url = 'https://www.dhlottery.co.kr/common.do?method=getLottoNumber&drwNo=1021'

response = requests.get(url).json()
#print(response)

print(response.get('drwtNo1'))
print(response.get('drwtNo2'))
print(response.get('drwtNo3'))
print(response.get('drwtNo4'))
print(response.get('drwtNo5'))
print(response.get('drwtNo6'))
print(response.get('bnusNo'))
```

```python
SSAFY@DESKTOP MINGW64 ~/dev/python
$ python lotto.py
12
15
17
24
29
45
16
```

API를 request 이용해서 가져오는 서비스 (로또 추첨)