---
title: "Implementation And BruteForce - 구현과 브루트포스에 대하여"
excerpt: "구현과 브루트포스 알고리즘에 대하여 공부해보겠습니다."
categories: 
- algorithm
tags:
- algorithm
toc: true
toc_sticky: true
date: 2023-01-16
last_modified_at: 2023-01-16
---
**_<제가 공부하며 그때그때 필요한 지식들을 적어놓는 algorithm 카테고리이며,_**  
**_지속적으로 update될 작성글입니다.>_**

## 구현 (Implementation)
- 어떻게 하면 문제를 해결할 수 있을지에 대해 생각한 일련의 logic 절차를 소스코드로 옮기는 것을 말합니다.  
:arrow_right: 풀이를 떠올리는 것은 쉽지만, 코드로 옮기기는 어려울 수도 있습니다.  
:arrow_right: 사용하는 프로그래밍 언어에 따라 문제의 난이도와 소스코드 길이가 달라질 수 있습니다.  
:bulb: 라이브러리 사용법을 많이 알수록 좋습니다!

## 구현 문제를 풀 때 주의해야 할 점들
```
시간 제한 : 1초
메모리 제한 : 256 MB
```
문제 풀이를 할 때, 위와 같은 제약들이 걸려있는 것을 흔하게 볼 수 있습니다.  

### 1. 메모리 제약  
Python의 경우, 드물게 리스트의 개수가 많고 크기가 1000만 이상인 리스트가 존재한다면  
**_메모리 초과_**가 될 수 있습니다. 이 점에 주의합시다.  

### 2. 시간 복잡도
**_시간 초과_**는 흔히 볼 수 있는 오답 사유 중 하나입니다.  
적절한 알고리즘으로 최대한 효율적인 시간 복잡도를 찾아보도록 합시다.  

### 3. 프로그래밍 언어
Python은 C/C++에 비해 동작 속도가 느립니다.  
Python으로는 대략 1초에 2000만 번의 연산을 수행한다고 가정하고 문제 풀이에 임하면 수월합니다.  

## 브루트포스 알고리즘 (Brute-Force)
- 완전 탐색이며, 가능한 경우의 수를 **_"모두" "일일이"_** 확인해보는 알고리즘입니다.  
:arrow_right: 모든 경우의 수를 다 살피기 때문에 100% 정답만을 가져올 수 있습니다.  

## 브루트포스의 장점
- 복잡한 특정 알고리즘 없이도 쉽고 빠르게 구현할 수 있습니다.  

## 브루트포스의 단점
- 모든 경우의 수를 살피기 때문에 실행 시간이 매우 오래 걸릴 수밖에 없습니다.
- 메모리 효율 측면에서 비효율적입니다.  

## 브루트포스의 종류
- 선형 구조 : 순차 탐색
- 비선형 구조 : 백트래킹, DFS, BFS

참고할만한 백준 문제들은 다음에서 볼 수 있습니다.  
문제 : [백준 알고리즘 분류하기 - 구현](https://www.acmicpc.net/problemset?sort=ac_desc&algo=102)  
문제 : [백준 알고리즘 분류하기 - 브루트포스 알고리즘](https://www.acmicpc.net/problemset?sort=ac_desc&algo=125)