---
title: "Greedy Algorithm - 그리디 알고리즘에 대하여"
excerpt: "그리디 알고리즘에 대하여 공부해보겠습니다."
categories: 
- algorithm
tags:
- algorithm
toc: true
toc_sticky: true
date: 2023-01-15
last_modified_at: 2023-01-15
---
**_<제가 공부하며 그때그때 필요한 지식들을 적어놓는 algorithm 카테고리이며,_**  
**_지속적으로 update될 작성글입니다.>_**

## Greedy Algorithm
- **_Greedy_**는 '탐욕스러운'이라는 뜻을 가진 영단어입니다.  
- **_어떠한 상황에서 그때그때 가장 좋은 선택을 하는 방법_**  
:arrow_right: '지금 당장 좋은 게 뭘까??' 를 고민하는 알고리즘입니다!
- 일반적으로는, Greedy Algorithm이 항상 **_최적의 해를 보장하지는 않습니다._**  
:arrow_right: 최적의 해에 가까운 근삿값을 구하는 용도로 사용됩니다.  
- '정렬' 알고리즘과도 짝을 이뤄 출제되기도 합니다.  

:bulb: **_Tip_** 코테 등에 나오는 문제들은 지역적으로 최적이면서 전역적으로도 최적인 문제가 대부분입니다.  

## 문제를 해결하는 방법
그리디 알고리즘으로 문제를 푸는 일련의 절차는 다음과 같습니다.

### 1. 선택 절차 (Selection Procedure)
현재 상태에서의 최적의 해를 선택합니다.  
### 2. 정당성 검사 (Feasibility Check)
문제의 조건에 맞는 해인지를 체크합니다.
### 3. 해 검사 (Solution Check)
원래의 문제가 해결되었는지 확인하고, 해결되지 않았다면 다시 돌아가서 위의 과정을 반복합니다.

## Greedy Algorithm을 적용하기 위한 2가지 조건  
항상 최적해가 보장되지는 않는다는 특징 때문에 아래와 같은 2가지 조건이 성립되어야 합니다.  
### 1. 탐욕적 선택 속성 (Greedy Choice Property)
앞에서 했던 선택이 이후에 할 선택에 영향을 주지 않습니다.  
### 2. 최적 부분 구조 (Optional Substructure) 
각각의 상황들에 대한 local optimum (부분 최적해)들이 모여 global optimum (전체 최적해)을 구성합니다. 

위의 조건이 성립되지 않으면 '최적해'는 구할 수 없지만, 근삿값을 구하는 알고리즘으로 사용할 수 있습니다.  

참고할만한 백준 문제들은 다음에서 볼 수 있습니다.  
문제 : [백준 알고리즘 분류하기 - 그리디 알고리즘](https://www.acmicpc.net/problemset?sort=ac_desc&algo=33)
