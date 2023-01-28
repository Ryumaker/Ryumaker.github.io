---
title: "Stack에 대하여"
excerpt: "Stack 자료구조에 대하여 공부해보겠습니다."
categories: 
- datastructure
tags:
- datastructure
toc: true
toc_sticky: true
date: 2023-01-28
last_modified_at: 2023-01-28
---
**_<제가 공부하며 그때그때 필요한 지식들을 적어놓는 datastructure 카테고리이며,_**  
**_지속적으로 update될 작성글입니다.>_**

## Stack이란?
- **_Stack_**은 '쌓다'라는 뜻을 가진 영단어입니다.   
:arrow_right: 즉, 데이터를 차곡차곡 쌓아 올린 형태의 자료구조입니다.  

## Stack의 연산
:bulb: Insertion and Deletion happen on Same End
- 삽입과 삭제 연산이 동일한 위치에서 일어납니다.  
:arrow_right: 즉, 정해진 방향으로만 데이터를 삽입 및 삭제할 수 있습니다.  

- Stack에서는 삽입 연산을 'push', 삭제 연산을 'pop'이라 하며,  
Stack의 제일 꼭대기 윗부분을 'top', 가장 아래쪽을 'bottom'이라 합니다.  
Stack의 입출력은 top을 기준으로 수행됩니다.  

```
Stack은 가장 나중에 넣은 데이터를 가장 먼저 꺼내는  
'후입 선출' (LIFO : Last In First Out) 구조입니다.
```

![Stack 연산 설명](/assets/images/Stack_pushpop.png){:style="border-radius: 15px;"}

## Stack의 사용사례
- 웹 브라우저 방문기록, 뒤로 가기  
- 후위 표기법 계산하기  
- 프로그램의 실행취소 (Undo)  
- 자료의 출력 순서가 입력의 역순이어야 할 때

참고할만한 백준 문제들은 다음에서 볼 수 있습니다. 

문제 : [백준 알고리즘 분류하기 - 스택](https://www.acmicpc.net/problemset?sort=ac_desc&algo=71)
