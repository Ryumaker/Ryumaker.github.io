---
title: "Index에 대하여"
excerpt: "Index에 대하여 알아보겠습니다."
categories: 
- database
tags:
- Database
toc: true
toc_sticky: true
date: 2024-08-29
last_modified_at: 2024-08-29
---

Index는 RDB에서 빠질 수 없는 중요한 요소입니다.  
이번 포스팅에서는 Index에 대해서 전체적으로 폭넓게 알아보도록 하겠습니다.

## Index
Index란  
:pencil2:  
**_추가적인 쓰기 작업과 저장 공간을 활용하여 데이터베이스 Table의 검색 속도를 향상시키기 위한 자료구조_**  
입니다.  
흔히 보는 책들을 생각하면 특정 주요 Keyword들에 대해 색인을 만들어 찾고자 하는 페이지를 빠르게 찾아가도록 돕듯이,   
Table에서 Data를 좀 더 빠르게 찾을 수 있도록 도와주는 일종의 **_'색인'_** 이라고 생각하면 좋습니다.  

### Index의 장단점
Index를 사용하면 Data를 빠르게 찾을 수 있어서 좋다고만 생각할 수 있는데 반드시 그런 것만은 아닙니다.  
Index 사용에도 장단점이 각각 존재합니다.    
:arrow_right: 장점
- Query로 Data를 빠르게 찾을 수 있습니다. 특히, 대량의 Data에서 검색 성능을 크게 향상시킬 수 있습니다.
- Data 정렬 및 그룹화 작업을 효율적으로 수행할 수 있습니다.  

:arrow_right: 단점
- Index도 결국에는 무언가를 저장해두는 자료 구조이므로 추가적인 저장 공간을 사용해야 합니다.  
- Insert, Delete, Update 시 Index도 같이 갱신되어야 하므로, 추가적인 overhead가 발생하여 성능에 영향을 미칠 수 있습니다.  

따라서, Table에 Index를 많이 설정한다고 해서 무조건 좋은 것도 아니므로   
Query 성능을 테스트하며 적절히 사용하는 것이 좋습니다.  

## Index의 종류
### Clustering Index vs Non-Clustering Index
- Search Key들이 File의 Sequential Order와 같으면 Clustering Index, 다르면 Non-Clustering Index 입니다.  
    - 즉, Table의 Data가 Index의 순서대로 물리적으로 정렬됩니다.

### Dense Index vs Sparse Index 
:pencil2: Dense Index
- Dense Index는 File에 있는 모든 Search Key에 대해 Index Record가 존재합니다.
- 추가적인 저장 공간이 필요할 수 있지만 조회가 빠릅니다.  

:pencil2: Sparse Index
- Sparse Index는 전부가 아니라 일부 몇 개의 Search Key에 대해서만 Index Record가 존재합니다. 
- Record들이 정렬되어 있을 때만 사용 가능합니다.  
- 저장 공간은 절약할 수 있지만 조회가 상대적으로 느립니다. 

## Covering Index
특정 Query를 수행할 때 필요한 모든 정보를 Index에서 직접 바로 얻을 수 있도록 설계된 Index입니다.  
실제 Table을 조회하지 않고 Index 자체만으로 원하는 결과값을 얻을 수 있어서, 성능이 크게 향상될 수 있습니다.

## B-Tree and B+Tree
B-Tree 와 B+Tree 는 Index를 '구현'할 때 사용되는 중요한 자료 구조입니다.  
B-Tree 는 Data와 Key가 모두 포함될 수 있는 반면,  
B+Tree 는 모든 Data가 Leaf Node에 저장되고 그러한 Leaf Node들이 서로서로 연결되어 있어 Range Query와 같은 작업에 적합합니다.

Index는 성능 개선과 직결된 요소이므로 꼭 학습하고 넘어가야 하는 부분 중 하나라고 생각합니다.  
이것으로 Index에 대한 이번 포스팅을 마치도록 하겠습니다.  