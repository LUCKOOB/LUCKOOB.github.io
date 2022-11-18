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
