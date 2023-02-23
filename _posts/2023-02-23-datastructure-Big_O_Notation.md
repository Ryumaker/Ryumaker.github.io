---
title: "Big-Oh Notation에 대하여"
excerpt: "Big-Oh Notation에 대하여 공부해보겠습니다."
categories: 
- datastructure
tags:
- datastructure
toc: true
toc_sticky: true
date: 2023-02-23
last_modified_at: 2023-02-23
---
**_<제가 공부하며 그때그때 필요한 지식들을 적어놓는 datastructure 카테고리이며,_**  
**_지속적으로 update될 작성글입니다.>_**

## 복잡도
알고리즘을 공부하는 데에 있어서 중요한 척도입니다.  
얼마만큼의 **_'효율성'_** 이 있느냐를 나타내는 것으로 생각하면 쉬우며,  
'시간 복잡도' 와 '공간 복잡도' 로 나뉩니다.

## Running Time에 대하여
- 보통 일반적인 알고리즘은 input이 주어지면  
문제 조건에 맞는 output으로 변환하여 출력하는 과정을 수행합니다.  

- 하지만, input 데이터의 사이즈가 늘어나면 늘어날수록  
수행되는 running time도 필연적으로 늘어나기 때문에  
모든 상황에서 항상 최선의 경우만을 단정 짓고 수행하기 어렵습니다.  

- 그래서, **_worst case_** 에 주로 집중합니다. :arrow_right: 상대적으로 분석하기 용이하기 때문!

## Big-Oh Notation
시간 복잡도와 공간 복잡도를 나타나는데에 사용되는데,  
메모리 제한을 특별히 생각하지 않는 한 대부분 '시간 복잡도'에 큰 의미를 두기 때문에  
해석할 때도 이에 맞추어 생각하면 됩니다.

### Big-Oh
함수 f(n)과 g(n)이 주어졌을때, n >= n<sub>0</sub>인 모든 n에 대하여 f(n) <= c * g(n)인  
양수 n<sub>0</sub>와 c가 존재하면 f(n)을 O(g(n))이라 표현합니다.  

- 예시  
1. 8n - 3 은 O(n)
2. 4n<sup>3</sup> + 20n<sup>2</sup> + 7 은 O(n<sup>3</sup>)
3. 2logn + 5 은 O(logn)

:bulb: Big-Oh Notation은 주어진 함수 실행의 **_'상한'_** 을 표현해줍니다.

## Big-Oh Notation의 규칙
1. 만약 f(n)이 d차 다항식일 경우, 빅오 표기법으로는  
:arrow_right: 낮은 차수의 항은 무시하고  
:arrow_right: 상수항도 무시하고  
가장 높은 차수인 d차 항만 생각하여 O(n<sup>d</sup>)로 표시합니다.   

2. 가능한 가장 작은 notation을 사용합니다.  
:arrow_right: 2n은 논리상 O(n<sup>2</sup>)도 가능하기는 하지만  
가능한 가장 작은 notation인 O(n)으로 표시합니다.  

3. 가능한 가장 간단한 notation을 사용합니다.  
:arrow_right: 3n + 5는 O(3n)보다는 O(n)으로 표시합니다.  

:bulb: 빅오 표기법은 데이터 입력값의 크기가 충분히 크다고 가정하고 있어  
효율성 또한 데이터 입력값의 크기에 따라 영향을 받기 때문에  
낮은 차수의 항과 상수항 같은 부분은 영향력이 상대적으로 '사소' 하므로 무시하고 표기합니다. 

## Big-Omega 와 Big-Theta
1. Big-Omega  
함수 f(n)과 g(n)이 주어졌을때, n >= n<sub>0</sub>인 모든 n에 대하여 f(n) >= c * g(n)인  
상수 c > 0와 정수 n<sub>0</sub> >= 1가 존재하면 f(n)을 Ω(g(n))이라 표현합니다.  

2. Big-Theta  
함수 f(n)과 g(n)이 주어졌을때, n >= n<sub>0</sub>인 모든 n에 대하여  
c<sub>0</sub> * g(n) <= f(n) <= c<sub>1</sub> * g(n)인    
상수 c<sub>0</sub> > 0와 c<sub>1</sub> > 0, 그리고 정수 n<sub>0</sub> >= 1가 존재하면 f(n)을 Θ(g(n))이라 표현합니다. 

## 정리하면  
- Big-Oh : f(n) is asymptotically **_'less than or equal'_** to g(n)  
- Big-Omega :  f(n) is asymptotically **_'greater than or equal'_** to g(n)
- Big-Theta :  f(n) is asymptotically **_'equal'_** to g(n)

