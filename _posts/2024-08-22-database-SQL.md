---
title: "자주 사용하는 SQL 기본 문법 총정리"
excerpt: "SQL의 기본 개념과 자주 사용하는 구문들에 대해서 알아보겠습니다."
categories: 
- database
tags:
- Database
toc: true
toc_sticky: true
date: 2024-08-22
last_modified_at: 2024-08-22
---

SQL에 대해서 많이들 들어보셨을 것이라 생각합니다.  
관계형 데이터베이스를 사용하면 빠질 수 없는 것이 바로 SQL에 대한 공부인데요.  
이번 포스팅에서는 SQL의 기본 개념과 자주 사용하는 구문들에 대해서 알아보겠습니다.  

## 절차적 vs 비절차적 언어
SQL에 대해 알아보기 전에 먼저 **_절차적 vs 비절차적_** 언어의 개념에 대해서 학습해야 합니다.  

:pencil2:
절차적 언어는 원하는 결과 Data를 얻기 위해서 어떤 연산을 수행해야 할지에 대한  
처리 방법 및 절차를 작성해야 합니다.

:pencil2:
비절차적 언어는 어떤 Data를 원하는지만 작성하면 됩니다. 

다시 말하면, 비절차적 언어는 '무엇을 해야 하는지' 를 정의하고 '어떻게' 수행할지를 명시하지 않는 언어입니다.  
반면, 절차적 언어는 '어떻게' 해야 하는지까지 명시합니다.  
잘 생각해보면 우리는 '원하는 Data가 이것이다' 까지만 명시하고   
SQL Query의 실제 실행과 최적화는 데이터베이스 엔진이 알아서 처리합니다.   
바로 이 점이 SQL의 비절차적 특징이라고 말할 수 있으며,   
C언어와 같은 프로그래밍 언어와 차이점을 보인다고 할 수 있습니다.  

## SQL
그렇다면 SQL은 과연 무엇일까요?  
SQL은 Structured Query Language를 줄인 말로,  
관계형 데이터베이스에 정보를 저장하고 처리하기 위한 언어를 말합니다.  
NoSQL에서도 SQL과 유사한 Query 언어나 SQL을 기반으로 한 시스템을 제공하는 경우가 있기는 하지만,  
주로 관계형 데이터베이스에서 사용되므로 RDB를 기준으로 설명해보겠습니다.  

### SQL의 실행 과정
우리가 작성한 SQL은 어떤 과정을 통해서 실행될까요?  
크게 다음과 같이 나눠볼 수 있습니다.  

- Parsing and Translation
    - Syntax 체크 : '문법적 오류' 가 없는지를 확인 
        - ex. 사용할 수 없는 Keyword를 사용했는가?  
    - Semantic 체크 : '의미상 오류' 가 없는지를 확인 
	    - ex1. Table에 존재하지 않는 Column을 사용했는가?
        - ex2. 사용하려는 오브젝트에 대한 권한이 없는가?  
	- 이 과정에서 Parse Tree가 생성됩니다.
        - 문장을 Tree 구조로 분석한 것을 Parse Tree라 합니다.   
- Optimization
    - 주어진 Query를 처리할 수 있는 수많은 실행 계획 중에서 가장 효율적인 것을 선택하는 과정 
- Evaluation
    - 실행해서 결과를 가져오는 과정 

## DML, DDL, DCL, TCL 
목적과 기능에 따라서 크게 4가지로 나눠볼 수 있습니다.  

1. DML
    - Data Manipulation Language  
    - 데이터베이스에 있는 Data를 검색하거나 어떠한 조작을 가하기 위해 사용   
    :arrow_right: select / insert, update, delete

2. DDL
    - Data Definition Language
    - Table과 같은 Data의 구조를 정의하기 위해 사용
    - 'Table 자체' 와 관련된 기능들이라 생각!  
    :arrow_right: create, alter, drop, rename

3. DCL
    - Data Control Language
    - DB 접근을 제어하거나, 특정 작업에 대한 권한을 주고 회수할 때 사용  
    :arrow_right: grant, revoke

4. TCL
    - Transaction Control Language
    - Transaction을 제어하기 위해 사용  
    :arrow_right: commit, rollback 

## 참조 무결성과 Cascade
데이터베이스에 저장된 Data들의 정확성, 일관성, 유효성 등을 보장하기 위해 무언가 변경이 일어날 때 이를 제약하기 위한 조건이 바로 무결성 제약 조건이었죠.  
그 중 하나가 바로 **_참조 무결성_** 이었습니다.  
:pencil2:
**_참조 무결성 : foreign key 값은 null이거나 참조하는 테이블의 primary key 값과 동일해야 합니다_**  
    - Primary key와 Foreign Key 사이의 관계가 항상 유지되도록 보장합니다. 

조금 더 쉽게 말하자면,  
하나의 속성이 다른 Table의 속성을 참조하고 있으면 참조한 해당 속성값이 필히 존재해야 한다는 것입니다.  
즉, **_<u>'다른 Table에서 이거 참조하고 있으니까 함부로 변경하거나 삭제할 수 없어'</u>_** 라는 의미가 되겠죠.  
그러면 바꿀 방법이 아예 없는 것일까요? 당연히 이때를 위한 기능이 있겠죠!  
바로, Cascade를 사용하는 것입니다.  

### Cascade
Cascade를 사용하면 해당 값을 참조하고 있는 Record 또한 종속적으로 수정 및 삭제를 가능하게 해줍니다.  

- on update cascade
    - 어떤 Table의 특정 Record가 변경될 때, 해당 Record를 외래 키로 참조하는 다른 모든 Table의 관련 Record들도 함께 업데이트  
- on delete cascade
    - 어떤 Table의 특정 Record가 삭제될 때, 해당 Record를 외래 키로 참조하는 다른 모든 Table의 관련 Record들도 함께 삭제 

## SQL 처리 순서
Query 내에 다양한 Keyword가 들어갈 수 있는데, 기본적인 처리 순서는 다음과 같습니다.  
- from, on, join :arrow_right: where :arrow_right: group by :arrow_right: having :arrow_right: select :arrow_right: distinct :arrow_right: order by :arrow_right: limit

    - from : Query의 대상이 되는 Table 확인
    - on : Join 조건 확인
    - join : Table Join
    - where : Data 추출 조건 확인
    - group by : 특정 Column에 대해 그룹화
    - having : 그룹화 이후 Data 추출 조건 
    - select : 조회할 Column 선택
    - distinct : 중복 제거
    - order by : 순서 정렬
    - limit : 결과 제한

이것으로 이번 SQL의 기초에 대한 포스팅을 마치겠습니다.  