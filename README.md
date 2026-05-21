# HTML 배포용 레포
여러 목표로 제작한 html을 배포하기 위한 레포지토리

## 접속 방법

`main` 브랜치에 push되면 GitHub Actions가 `docs` 폴더를 스캔해서 `docs/index.html`을 자동 생성하고 GitHub Pages에 배포한다.

- 목록 페이지: https://sksla123.github.io/priv-variant-html/
- 개별 HTML 링크 규칙: `https://sksla123.github.io/priv-variant-html/<docs 아래 경로>`
- 예시: https://sksla123.github.io/priv-variant-html/algorithm-visualizer/linked_list_intersect_algorithm.html

자동 생성되는 `docs/index.html`은 배포 워크플로우 안에서 만들어지므로 로컬 파일 목록에는 없을 수 있다. 로컬에서 바로 확인하려면 `docs/algorithm-visualizer/*.html` 파일을 브라우저로 열면 된다.

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
