# HTML 배포용 레포
여러 목표로 제작한 html을 배포하기 위한 레포지토리

## algorithm-visualizer
특정한 알고리즘을 시각화한 웹페이지

### Linked-List Intersect 알고리즘 시각화
정보 검색 Inverted-Index에서 자주 쓰이는 알고리즘
**의사코드**
```
Intersect(P1, P2)

answer <- []

while 
    P_1 is not empty and P_2 is not empty 
do 
    if docID(P_1) = docID(P_2) then 
        ADD(answer, docID(P_1))
        P_1 <- next(P_1)
        P_2 <- next(P_2)

    else if docId(P_1) < docID(P_2) then
        P_1 <- next(P_1)
        
    else
        P_2 <- next(P_2)

return answer
```

### Linked-List Intersect with Skip Pointer 알고리즘 시각화
정보 검색 Inverted-Index에서 교집합 계산 효율성을 높이기 위해 skip pointer를 추가한 알고리즘

(보통 IR에서 다루는 문서 집합의 크기는 매우 크기 때문에, Skip Pointer를 사용해 더 빠르게 처리하게 하는 것이 보통이다.)
**의사코드**
```
IntersectWithSkips(P1, P2)

answer <- []

while 
    P_1 is not empty and P_2 is not empty 
do 
    if docID(P_1) = docID(P_2) then 
        ADD(answer, docID(P_1))
        P_1 <- next(P_1)
        P_2 <- next(P_2)
    
    else if docID(P_1) < docID(P_2) then
        if hasSkip(P_1) AND (docID(skip(P_1)) <= docID(P_2)) then
            P_1 <- skip(P_1)
        else
            P_1 <- next(P_1)
    
    else
        if hasSkip(P_2) AND (docID(skip(P_2)) <= docID(P_1)) then
            P_2 <- skip(P_2)
        else
            P_2 <- next(P_2)

return answer
```