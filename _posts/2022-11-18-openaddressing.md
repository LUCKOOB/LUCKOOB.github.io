---
layout: post
author: Abhinav Saxena
tags: [overview, moonwalk]
---

### 충동회피방법(collision resolation method)

- openaddressing : 충돌이 일어났을때 내가 넣을 위치는 데이터가 들어 있지만 주위에는 비어있을수 있기 때문에 주위빈칸을 찾아 넣는 방법
세가지 방법이 있다
- linear probing : 바로 아래의 슬롯부터 확인해서 빈칸을 발견하면 저장
- guardratic prbing
- double hashing

오픈어드레싱 랑 대비대는 chaining

claster : 비슷한 `key`값이 모여있는 단위, 클러스터 크면 삽입/삭제 하는데 시간이 걸리기 때문에 클러스터가 안생기게
분산하여 입력해야한다 

```py
set(key,value=None)
    1.key 값이 H에 있으면 vlaue를update
    2.`key` 값이 H에 없으면 (key,vlaue)를 insert
```

### SET,SEARCJ,REMOVE 연산 

```py 
find-solt(key):
    i = f(key)
    start= i 
    while (H[i]==occupiede)and (H[i].key !=key)
        i = (i+1)%m # 으로 나눈느 이유는 한바퀴 돌았을떄 다시 처음부터 시작할려고
        if i == start : retrun Full
        
set(key,value= None):
    i = find-solt(key)
    if i == Full: return None #H를 키워야함
    if H[i].is occupied:
        H[i].value = value # H가 가즉찾지만 원하는 `value`가 있기 때문에 `H[i].value`값을 업데이트한다
    else: #H도 비어있고 동일한 값이 안들어 있기 때문에 새로운 값을 입력한다
    H[i].key,H[i].value= key,vlaue
    return key
    
   
search(key)
    i = find-slot(key)
    if i == FULL : return None 
    if H[i].is occupied: # 원하는 값이 찾아서 i를 리턴한다
            return H[i].value
    else: # 찾는 값이 없으면 None 값을 리턴한다 
        return None
```
- `key`값이 있으면 `slot`번호 리턴
- `kwy`값이 없다면 `key`값이 삽이되어 `solt`번호 리턴


