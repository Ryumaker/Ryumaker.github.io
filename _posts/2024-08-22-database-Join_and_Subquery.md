---
title: "Join과 Subquery에 대하여"
excerpt: "Join과 Subquery의 개념에 대하여 살펴보겠습니다."
categories: 
- database
tags:
- Database
toc: true
toc_sticky: true
date: 2024-08-22
last_modified_at: 2024-08-22
---

관계형 데이터베이스를 사용함에 있어서 빠질 수 없는 요소는 바로 Join입니다.  
관계형 데이터베이스는 Data의 중복을 줄이고 일관성 등을 확보하기 위해서   
Data를 수많은 Table로 분리하여 관리합니다.  
이러한 특징 때문에 RDB에서는 여러 Table들을 엮는 Join이 필수입니다.  
이번 포스팅에서는 Join에 대해 정리하고 SubQuery에 대해서도 간단하게 알아보겠습니다.  

## Join
여러 Table들을 서로 결합해서 하나의 검색 결과를 도출해내는 것을 Join이라 합니다.  

### 1. Cross Join
- 한쪽 Table의 모든 Row와 다른 쪽 Table의 모든 Row를 조합하는 Join  
- 각 Table Row들의 모든 조합을 생성하므로 결과 Row 수는 두 Table의 Row 수를 곱한 것과 같습니다.  
- 말 그대로, Cartesian Product와 같습니다.  

### 2. Equi / Non-Equi Join 
- Equi Join 등가 조인
    - Join 조건으로 '=' 연산자를 사용하는 Join
    - 즉, 동등 비교를 사용하는 Join
    - 두 Table 간의 Column 값이 같은 Row들만을 결합합니다.
- Non-Equi Join 비등가 조인
    - 동등 비교를 사용하지 않는 Join
    - 부등호나 Between 등을 비교에 사용

### 3. Inner Join 
- 두 Table에서 Join 조건을 만족하는 Row들만 합쳐서 결과에 포함시키는 Join 방식 
- Cross Join한 결과에서 Join 조건을 추가하면 Inner Join과 같은 결과를 얻을 수 있습니다.  
- 그냥 단순히 Join이라 하면 Inner Join을 말합니다.  
:surprise: Inner Join은 Equi Join뿐만 아니라 다양한 조건 연산자를 사용할 수 있습니다.  
Equi Join은 Inner Join의 한 형태로 볼 수 있습니다.  
**_<u>모든 Equi Join은 Inner Join이지만, 모든 Inner Join이 Equi Join은 아닙니다.</u>_**

### 4. Outer Join
- 조건에 일치하는 Data와 일치하지 않는 Data 모두를 가져오는 Join
- **_'어떤 Table을 중심으로 삼을 것인가?'_** 에 따라 3가지로 나뉩니다.  
:surprise: 본 설명에서 언급되는 왼쪽, 오른쪽 총 2개의 Table을 각각 Table A, Table B라 하겠습니다.  
    - Left Outer Join
        - Table A의 모든 Row와, Join 조건에 맞는 Table B의 Row를 매칭하여 반환합니다. 
        - 만약 Join 조건에 맞는 Row가 Table B에 없으면, Table B의 Column은 null로 표시됩니다. 
    - Right Outer Join
        - Table B의 모든 Row와, Join 조건에 맞는 Table A의 Row를 매칭하여 반환합니다. 
        - 만약 Join 조건에 맞는 Row가 Table A에 없으면, Table A의 Column은 null로 표시됩니다.
    - Full Outer Join
        - Table A와 Table B의 모든 Row들을 반환합니다. 
        - Join 조건에 맞는 경우는 두 Table의 Data가 결합되어 나타나고, 조건에 맞지 않는 경우는 null로 표시됩니다.

:arrow_right: Inner Join과 Outer Join의 차이  
Inner Join은 두 Table 모두에서 Join 조건을 만족하는 Row들만을 결과로 반환합니다.  
반면 Outer Join은 왼쪽, 오른쪽, 양쪽 3가지 어느 경우가 되어도  
Join 조건에 부합하지 않는 Row도 결과에 포함시켜, 기준으로 삼은 Table의 모든 Row를 반환합니다.  

### 5. Natural Join
- Equi Join의 한 유형으로, 동일한 이름과 타입을 가진 Column을 대상으로 수행되는 Join 
- 같은 이름을 가진 Column은 1번만 추출됩니다.  
- 동일한 이름을 가지는 Column은 모두 Join 되기 때문에 의도치 않은 Join으로 예상과는 다른 결과가 나올 수 있습니다.  
    - 이것을 방지하기 위해 Using을 사용합니다!  
    - Using
        - using (Column 명) 식으로 Join에 사용될 Column을 사용자가 지정합니다.  
        - 'natural' 과는 같이 사용될 수 없습니다.  
        - Column은 반드시 괄호로 묶어서 표현해야 합니다.  
        :arrow_right: 즉, 공통된 Column이 1개면 natural과 using 중에서 어느 것을 사용해도 상관 없지만 2개 이상이면 결과가 달라질 수 있습니다.  

## Subquery
단어 자체가 sub + query 라서 상대적으로 이해하기 쉽죠?  
말 그대로 다른 SQL Query의 내부에 포함된 Query 입니다.  
Subquery는 Select, From, Where 등에서 사용 가능하며,  
외부 Query에서 또다른 조건으로 참조될 수 있는 결과를 반환합니다.  
좀 더 복잡한 Data의 처리에 있어서 도움을 받을 수 있는 유용한 구조입니다.   