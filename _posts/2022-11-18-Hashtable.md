---
layout: post
tags: [overview, moonwalk]
---

## 해시 테이빌(Hash Table)
- 굉장히 강력한 자료구조
- 평균적적인 시간이 상수 시간의 평균,삽입,삭제,탐색연산을 제공
 
## 딕셔너리디
딕셔너리 함수로 (key,Values)로 구성한다
```py
D={} # 빈사전
D=['2000820']="오영복"
D=['2019209']="홍길동"
-------------------------------
D={2019209:"홍길동",2000820:"오영복"}
```
- 2019209 : 학번 : key, 신찬수:vlaue 
- `key`: 문자,숫자로 `key`값을 설정할수 있다
- `vlaue` : 하나 또는 하나이상의 리스트 값으로 만들수 있다

### 해시 테이블

예시
```py
D = {}
D['2019317'] = "신찬수"
D['2019209'] = "홍길동"
D = { 2019317: "신찬수", 2019209: "홍길동" }
```
- "key: 2019317, value: "신창수""를 받으면 2019317 % 10의 위치에 저장
- "key: 2019209, value: "홍길동""을 받으면 2019209 % 10의 위치에 저장

"%10"은 열 칸 중에 하나에 저장하기 위해서임. 10칸은 임의의 예시.

만약 "2019235"를 찾으면 2019235 % 10 위치에 찾아가 확인한 후, 없음을 반환한다.

### 해쉬함수 

저장하는 장소를 정할 때 key 값을 index 로 매핑한다. 이 매핑 과정에서 함수(여기서는 나머지 연산)가 쓰인다. 이 함수를 해시 함수라고 부른다.
새로 들어온 값을 저장하려 할 때, 그 곳에 기존의 값이 있으면 충돌(collistion) 발생. 이를 해결하는 걸 충돌 해결(collision resolustion)이라고 부르며 이 해결함수를 충돌 해결 방법이라고 부른다.

```txt
   maping
kry ---> index 
    f(key) = key 값이 저장될 인덱스를 계산
```
- f(key)= key % m(hash Table 사이즈)

세가지 주요 요소
- 1.Table : list
- 2.Hash function 
- 3.Collision resolution method (충돌이 일어 날때 어떻게 처리 할건지)


H, (H) = m # m은 slots 개수

division hash function
f(k) = (k%P(소수)%m #충돌이 많이 생긴다

perfect hash function : ideal hash function 비현실적이다
```txt
key ----> slot
    1:1
```
universal hush function  : 충돌이 일어날 확률이 1/m 인 해쉬함수
```py
pr(f(x)==f(y)) = 1/m
```

C-universal hush function : 충돌이 일어날 확률이 c/m인 해쉬 함수
```py
pr(f(x)==f(y)) = C/m
```

여러 종류의 해쉬 함수
- Divsion
- Multiplication
- Folding
- Mid-squares
- Extraction

### 키값이 문자열일 경우

- Addictive :key[i] 번째 문자를 전부 더해서 m으로 나머지 연산
- Rotating: 값 h를 계산하는데 initial_value를 임의로 준 후 for문으로 키값 문자열의 길이만큼 h = (h << 4) ^ (h >> 28) ^ key[i]한후 h%P%m을 반환 
```py
h = initial_value
for i in range(len(key)):
   h = (h << 4) ^ (h >> 28) ^ key[i]
return h%p%m
```
- Universa : C++ STL 해시 함수로 사용되고 있음. 자바에서도 활용. a= 임이의 값이다
```py
h = ((h*a) + key[i])%p
return e%n
```

좋은 hash function
Less collision
Fast computation
이 두 가지는 트레이드오프인 측면이 있다. 적절하게 만드는 게 중요하다.


