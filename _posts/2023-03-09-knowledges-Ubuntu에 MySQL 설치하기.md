---
title: "Ubuntu에 MySQL 설치하기"
excerpt: "Ubuntu에 MySQL을 설치하는 방법을 살펴보겠습니다."
categories: 
- knowledges
tags:
- Database
toc: true
toc_sticky: true
date: 2023-03-09
last_modified_at: 2023-03-09
---
**_<제가 공부하며 그때그때 필요한 지식들을 적어놓는 knowledges 카테고리이며,_**  
**_지속적으로 update될 작성글입니다.>_**

MySQL은 세계에서 많이 쓰이는 오픈소스 관계형 데이터베이스 중 하나입니다.   
Ubuntu에 MySQL 서버를 설치하는 방법을 살펴보도록 하겠습니다.  

1. 설치가능한 패키지 리스트를 업데이트합니다.
```
sudo apt-get update
```

2. MySQL Server를 설치합니다.
```
sudo apt-get install mysql-server
```

3. MySQL을 시작합니다.
```
sudo systemctl start mysql
```

4. Ubuntu 서버가 재시작될 때 MySQL이 자동으로 실행되도록 합니다.
```
sudo systemctl enable mysql
```