---
title: "정규화에 대하여"
excerpt: "정규화에 대하여 알아보겠습니다."
categories: 
- database
tags:
- Database
toc: true
toc_sticky: true
date: 2024-09-05
last_modified_at: 2024-09-05
---

## Anomaly
데이터베이스의 무결성이나 일관성을 해치는 비정상적인 상황을 의미합니다.  

## 정규화
Data의 중복과 Anomaly를 최소화하기 위한 일련의 과정입니다.    

## 정규화 단계
### 1NF
Table의 모든 column 값들은 Atomic해야 한다.    

### 2NF
모든 Non-prime Attribute들은 모든 Key에 완전 함수적 종속을 가져야 한다.    

### 3NF
모든 Non-prime Attribute들은 어떤 Key에도 이행적 함수적 종속을 가지면 안 된다.   

### BCNF
모든 결정자가 Super Key여야 한다.    