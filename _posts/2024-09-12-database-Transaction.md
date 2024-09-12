---
title: "Transaction"
excerpt: "Transaction에 대하여 알아보겠습니다."
categories: 
- database
tags:
- Database
toc: true
toc_sticky: true
date: 2024-09-12
last_modified_at: 2024-09-12
---

## Transaction
데이터베이스에서 일련의 연산을 하나의 논리적 단위로 묶어서 처리하는 개념입니다.  

## ACID    

## Transaction Isolation Level
### Read Uncommitted
Transaction이 아직 commit되지 않은 데이터를 읽을 수 있습니다.      

### Read Committed
Transaction이 commit된 데이터만 읽을 수 있습니다. 

### Repeatable Read
Transaction이 시작된 시점의 데이터 스냅샷을 사용하여 모든 Read 작업을 수행합니다.   

### Serializable
Transaction이 완료될 때까지 다른 Transaction이 접근할 수 없도록 Lock이 걸립니다.
  
## Redo & Undo
Redo 는 데이터베이스의 commit된 Transaction의 변경 사항을 재적용하여 시스템이 commit된 상태로 복구하는 과정을 의미합니다.  
Undo 는 Transaction이 실패했거나 롤백되었을 때, 해당 Transaction이 수행한 변경 사항을 취소하여 데이터베이스를 Transaction이 시작되기 전 상태로 되돌리는 과정을 의미합니다.  