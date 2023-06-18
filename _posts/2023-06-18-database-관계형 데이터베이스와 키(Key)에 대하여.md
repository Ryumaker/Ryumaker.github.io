---
title: "관계형 데이터베이스와 키(Key)에 대하여"
excerpt: "관계형 데이터베이스와 키(Key)의 개념들에 대해 살펴봅니다."
categories: 
- database
tags:
- Database
toc: true
toc_sticky: true
date: 2023-06-18
last_modified_at: 2023-06-18
---

## 관계형 데이터베이스란
- 관계형 데이터베이스는 데이터들을 테이블 형태로 저장합니다.  
- 각각의 테이블은 unique한 이름이 붙여져 구별됩니다.  
- 데이터의 종속성을 관계(relationship)로 표현합니다.  

- ex. 학생 테이블
- 
|ID|Name|Dept|Year|
|----|--------|--------|--------|
|1|Kevin|History|4|
|2|Kyle|Comp.Sci.|3|
|3|Lee|Mathematics|2|
|4|Albert|Music|1|

## 용어 설명
1. tuple (or row)
    * 서로 관계가 있는 데이터의 모음입니다.
    * 테이블에서 각 데이터 항목을 저장하는 하나의 가로줄입니다.
2. attribute (or column)
    * 각 항목의 속성을 표시합니다.
    * 데이터의 타입이 정해져있습니다.
    * 테이블에서 각각의 세로줄을 의미합니다.
3. domain
    * 각 속성에서 domain이란 해당 속성에 부합할 수 있는 값들의 set입니다.
    * 즉, 각 속성에 들어갈 수 있는 값들의 모임!
    * **_null_**은 모든 domain에 들어갈 수 있는 요소입니다.
    * domain의 각 값들은 **_atomic_**, 즉 더 이상 분리되지 않는 값이어야 합니다. 
    ```
    예를 들어, 위 예시 학생 테이블에서 Year가 (4, 3)처럼 복합적인 값이 될 수 없습니다.
    ```
    * Atomic한 타입에는 Integer, real, char, varchar 등이 있으며 Non-Atomic한 타입에는 set, list, bag 등이 있습니다.
    * 각각의 domain들을 D<sub>1</sub>, D<sub>2</sub>, ... , D<sub>n</sub>이라 할때,  
    D<sub>1</sub> x D<sub>2</sub> x ... x D<sub>n</sub>의 subset을 **_relation_** 이라고 합니다.
    * 즉, relation은 (a<sub>1</sub>, a<sub>2</sub>, a<sub>3</sub>, ... , a<sub>n</sub>) 형태의 tuple 들의 집합입니다. (a<sub>i</sub> ∈ D<sub>i</sub>)
4.  relation과 relationship의 비교
    * relation은 n-tuples의 집합이며, 서로 다른 속성으로 구성된 테이블 혹은 개체
    * relationship은 두 개의 테이블들 혹은 개체들이 어떻게 연결되었는지 그 방식을 나타내는 것
5. schema
    * 데이터베이스의 구조와 제약 조건 등 logical한 design 방법을 전반적으로 명시한 것
6. relation schema
    * r(A<sub>1</sub>, A<sub>2</sub>, ... , A<sub>n</sub>) 식으로 해당 relation에 어떤 속성의 정보가 담길지를 정의하는 일종의 '틀'
    * 이때, r은 테이블 혹은 relation 이름이며 A<sub>1</sub>, A<sub>2</sub>, ... , A<sub>n</sub>은 attribute를 의미합니다.  

:pencil2: 각각의 테이블에서 tuple이 어떤 순서로 나열되어 있는지는 중요하지 않습니다.

## 속성
1. 유일성
    * 하나의 키값으로 tuple을 유일하게 식별할 수 있는 특성
2. 최소성
    * 키를 구성하는 속성들 중에서 꼭 필요한 최소한의 속성들로만 키를 구성하는 특성

## Key의 개념에 대하여
1. Super Key 슈퍼키
    * 테이블에서 각 tuple을 유일하게 식별할 수 있는 **_'하나 혹은 그 이상'_**의 속성들의 집합
    * ex. 학생 테이블에서 {ID}, {ID, Name} 둘 다 Superkey입니다.
    * 유일성 O, 최소성 X
2. Candidate Key 후보키
    * 테이블에서 각 tuple을 유일하게 식별할 수 있는 **_'최소한'_**의 속성들의 집합
    * 어떤 SuperKey K가 'minimal'하다면 Candidate Key입니다.
    * 유일성 O, 최소성 O
3. Primary key 기본키
    * 후보키 중에서 특별히 선정된 '하나'의 키
    * 테이블에서 기본키는 오직 1개
    * 기본키는 null 값을 절대 가질 수 없고, 중복된 값도 가져서는 안됩니다.
4. Foreign Key 외래키
    * 다른 테이블의 기본키를 '참조'하는 속성의 집합
    * 테이블 간의 참조관계를 표현합니다.
    * 참조되는 테이블의 필드는 반드시 unique나 Primary Key가 설정되어 있어야 합니다.
    * 중복 데이터 제거를 위해서 테이블을 분리할 때 필요합니다.
5. Alternate Key 대체키
    * 후보키가 2개 이상인 경우 그 중에서 어느 하나를 기본키로 하고 남은 후보키들을 대체키라고 합니다.

## 절차적 언어와 비절차적 언어
- 절차적 언어는 작성하는 사람이 필요한 데이터뿐만 아니라 그걸 얻어내기 위한 처리 순서나 방법과 같은 절차를 정해주어야 하는 언어입니다.
- 반면, 비절차적 언어는 작성하는 사람이 원하는 데이터만 선언하고 내부 수행절차는 명시하지 않는 언어입니다.

## Relational Algebra
- 일반적으로 SQL은 비절차적 언어지만, 내부적으로 절차적 언어인 Relational Algebra로 변환되어 처리됩니다.
- 따라서, SQL의 이론상 기초이며 6개의 기본 연산자가 존재합니다.
위의 예시 학생 테이블을 다시 가져오겠습니다.
- ex. 학생 테이블 students
- 
|ID|Name|Dept|Year|
|----|--------|--------|--------|
|1|Kevin|History|4|
|2|Kyle|Comp.Sci.|3|
|3|Lee|Mathematics|2|
|4|Albert|Music|1|

1. Select (σ)
    * 원하는 조건의 tuple들을 추출해내는 연산입니다.
    * σ<sub>Year > 2</sub> (students) 시 결과는
    * |ID|Name|Dept|Year|
    |----|--------|--------|--------|
    |1|Kevin|History|4|
    |2|Kyle|Comp.Sci.|3|

2. Project (Π)
    * 원하는 열(column)들을 추출해내는 연산입니다.
    * Π<sub>Name, Year</sub> (students) 시 결과는  
    * |Name|Year|
    |--------|--------|
    |Kevin|4|
    |Kyle|3|
    |Lee|2|
    |Albert|1|

3. Cartesian Product (X)
    * 두 relation으로 만들 수 있는 모든 tuple 조합을 얻어냅니다.
    * ex. 테이블 r과 s가 각각 아래와 같을 때
    * |A|B|
    |----|----|
    |a|1|
    |b|2|
    * |C|D|
    |----|----|
    |c|3|
    |d|4|

    출력되는 결과는 다음과 같습니다.

    r X s
    * |A|B|C|D|
    |----|----|----|----|
    |a|1|c|3|
    |a|1|d|4|
    |b|2|c|3|
    |b|2|d|4|

4. Union (U)
    * Union하려는 두 relation은 반드시 같은 column 수를 가져야하며 필드의 Type이 같아야합니다. 즉, compatible 해야합니다.
    * ex. 테이블 r과 s가 각각 아래와 같을 때
    * |A|B|
    |----|----|
    |a|1|
    |b|2|
    * |A|B|
    |----|----|
    |a|1|
    |c|3|

    출력되는 결과는 다음과 같습니다.
    
    r U s
    * |A|B|
    |----|----|
    |a|1|
    |b|2|
    |c|3|

5. Set Difference (-)
    * Set Difference도 Union과 마찬가지로 두 relation이 compatible 해야합니다.
    * ex. 테이블 r과 s가 각각 아래와 같을 때
    * |A|B|
    |----|----|
    |a|1|
    |b|2|
    |c|3|
    * |A|B|
    |----|----|
    |a|1|
    |d|4|

    출력되는 결과는 다음과 같습니다.

    r - s
    * |A|B|
    |----|----|
    |b|2|
    |c|3|

6. Rename(ρ)
    * 데이터베이스 내의 relation과는 달리 관계 대수식의 결과는 그것을 참조할 수 있는 이름을 갖고 있지 않습니다.
    * 따라서, 이러한 결과들에 이름을 주는데에 유용하게 쓰는 것이 Rename 연산입니다.
    * ρ<sub>x</sub>(E) : 식 E의 결과를 이름 x로 돌려줍니다.  
    * ρ<sub>x\(A<sub>1</sub>, A<sub>2</sub>, ... , A<sub>n</sub>\)</sub>(E) : 식 E의 결과를 이름 x로 돌려주고, A<sub>1</sub>, A<sub>2</sub>, ... , A<sub>n</sub>로 재명명된 속성을 가집니다.