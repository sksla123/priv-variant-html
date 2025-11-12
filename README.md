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