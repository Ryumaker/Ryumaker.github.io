---
title: "DFS와 BFS - 대표적인 그래프 탐색에 대하여"
excerpt: "DFS와 BFS에 대하여 공부해보겠습니다."
categories: 
- algorithm
tags:
- algorithm
toc: true
toc_sticky: true
date: 2023-03-03
last_modified_at: 2023-03-03
---
**_<제가 공부하며 그때그때 필요한 지식들을 적어놓는 algorithm 카테고리이며,_**  
**_지속적으로 update될 작성글입니다.>_**

## 그래프
- 정점(vertex)과 간선(edge)으로 이루어진 자료구조

:bulb: 대표적인 그래프 탐색 알고리즘으로 DFS, BFS 2가지가 있습니다.  

## DFS (Depth-First Search)
- 깊이 우선 탐색  
- 최대한 '깊이' 내려간 후에 더 이상 갈 곳이 없으면 그때 옆으로 이동하는 방법  
- 임의의 노드에서 탐색을 시작해서 다음 branch로 넘어가기 전에 해당 branch를 끝까지 탐색하는 방법  
- 스택 혹은 재귀를 사용하여 구현  

![DFS 순서 설명](/assets/images/DFS_graph.gif){:style="border-radius: 15px;"}

<center> DFS 방문 순서 (기준: 번호가 낮은 노드부터 탐색) </center>  

### DFS의 실행 과정
1. 탐색을 시작할 노드를 스택에 삽입하고 방문 처리
2. 스택의 top 노드에 아직 방문하지 않은 인접 노드가 있으면 그 노드를 스택에 넣고 방문 처리하고,  
없으면 스택에서 top 노드를 꺼내기
3. 2번을 더 이상 수행할 수 없을 때까지 반복하기

:bulb: 위 그림의 그래프 탐색 예시 코드
<script src="https://gist.github.com/Ryumaker/fc5e29603700996df385c51249ceec76.js"></script>

실행 결과 : 1 2 5 3 6 9 7 4 8

## BFS (Breadth-First Search)
- 너비 우선 탐색
- 최대한 '넓게' 이동한 후에 더 이상 갈 곳이 없으면 그때 아래로 이동하는 방법
- 임의의 노드에서 탐색을 시작해서 인접한 노드들을 먼저 탐색하는 방법
- 큐를 사용하여 구현
- 주로 두 노드 사이의 **_최단 경로_**를 찾고자 할때 사용

![BFS 순서 설명](/assets/images/BFS_graph.gif){:style="border-radius: 15px;"}

<center> BFS 방문 순서 (기준: 번호가 낮은 노드부터 탐색) </center> 

### BFS의 실행 과정
1. 탐색을 시작할 노드를 큐에 삽입하고 방문 처리
2. 큐에서 노드를 꺼내서 해당 노드의 인접 노드 중에서 아직 방문하지 않은 노드를  
전부 큐에 넣고 방문 처리
3. 2번을 더 이상 수행할 수 없을 때까지 반복하기

:bulb: 위 그림의 그래프 탐색 예시 코드
<script src="https://gist.github.com/Ryumaker/c36bb3114561faeb9c152eb9c9c9dbce.js"></script>

실행 결과 : 1 2 3 4 5 6 7 8 9

## 시간 복잡도
N을 노드의 수, E를 간선의 수라고 가정했을 때

그래프를  
- 인접 리스트로 표현할 시 : O(N + E)
- 인접 행렬로 표현할 시 : O(N<sup>2</sup>)

참고할만한 백준 문제들은 다음에서 볼 수 있습니다.  
문제 : [백준 알고리즘 분류하기 - DFS](https://www.acmicpc.net/problemset?sort=ac_desc&algo=127)  
문제 : [백준 알고리즘 분류하기 - BFS](https://www.acmicpc.net/problemset?sort=ac_desc&algo=126) 
