---
title: "Ubuntu에 MySQL 설치 후 외부에서 Workbench로 접속하기"
excerpt: "MySQL Workbench로 외부에서 접속하는 방법을 살펴보겠습니다."
categories: 
- tips
tags:
- Database
toc: true
toc_sticky: true
date: 2023-03-08
last_modified_at: 2023-03-08
---
**_<제가 공부하며 그때그때 필요한 지식들을 적어놓는 tips 카테고리이며,_**  
**_지속적으로 update될 작성글입니다.>_**

MySQL Workbench는 MySQL을 다루기 위한 GUI 기반 툴입니다.  
서버에 MySQL을 설치한 후에 '외부'에서 MySQL Workbench 등을 사용하여 접속을 시도하면 오류가 발생하는데    
그 이유는 MySQL은 설치 시 기본적으로 현재 사용중인 로컬에서만 접속할 수 있도록 되어있기 때문입니다.  

따라서, 외부에서 접속을 하기 위해서는 몇 가지 추가적인 설정이 필요합니다.  

본 게시물은 Ubuntu 20.04, MySQL 8.0.32 버전을 기준으로 작성되었습니다.

## 접속하는 과정
### :pencil2: cnf 파일 수정하기
```
cd /etc/mysql/mysql.conf.d
```
위 명령어를 입력하여 디렉토리를 이동한 후에
```
sudo vi mysqld.cnf
```
위 명령어를 입력하여 mysqld.cnf 파일을 엽니다.  
bind-address = 127. 0. 0. 1 이라 되어 있는 부분을 #으로 주석처리 해주면 됩니다.  
(만약 되지 않는다면, mysqlx-bind-address = 127. 0. 0. 1 까지 주석처리해주면 됩니다.)

### :pencil2: MySQL 접속하여 사용자 생성하기
```
sudo mysql -u root -p
```
위 명령어를 통해 MySQL에 접속해줍니다.  
(만약 되지 않는다면, sudo /usr/bin/mysql -u root -p 로 경로를 명시해주면 됩니다.)  

외부접속을 허용할 사용자를 생성해줍니다.  
```
mysql> create user 'username'@'%' identified by 'password';
mysql> grant all privileges on *.* to 'username'@'%' with grant option;
```
username에는 생성하고자 하는 사용자의 이름을 입력하고  
password에는 해당 사용자 계정에 대한 비밀번호를 설정해주시면 됩니다. (자신이 원하는 비밀번호를 입력)  

%는 모든 곳에서 오는 접속을 허용한다는 뜻입니다.  
:bulb: INSERT, DELETE, UPDATE와 같은 SQL문을 사용하지 않고 바로 grant 명령어를 사용하여 작업하였다면  
굳이 FLUSH PRIVILEGES를 실행할 필요가 없습니다.

모든 과정을 마치면
```
mysql> exit
Bye
```
exit를 입력하여 MySQL을 빠져나옵니다.  

### :pencil2: 방화벽 설정 후 MySQL 재시작
```
sudo ufw allow mysql
```
외부에서 접속할 수 있도록 MySQL 포트 3306번을 열어주어야 하기 때문에 위 명령어를 입력합니다.  
명령어 입력 후에 Rules updated가 뜨면 정상적으로 실행된 것입니다.  
```
sudo service mysql restart
```
위 명령어를 입력하여 MySQL을 재시작해줍니다.

### :pencil2: (Optional) 클라우드 사용할 시
aws, naver cloud, nhn cloud 등 클라우드 플랫폼을 이용할 시에  
해당 플랫폼의 인스턴스 보안그룹 규칙에 포트번호 3306을 추가해줍니다.  

### :pencil2: MySQL Workbench 실행하기
MySQL Workbench를 실행합니다.  
![MySQL connection 설명](/assets/images/mysql_connections.png){:style="border-radius: 15px;"}  

빨간색 상자로 체크된 버튼을 클릭합니다.  

- 일반적인 TCP/IP 접속인 경우
![TCP/IP connection 설명](/assets/images/tcp_ip_connection.png){:style="border-radius: 15px;"} 

Connection Name : Workbench에 해당 연결을 어떤 이름으로 해놓을 것인지 작성  
Hostname : Putty로 서버에 접속할 때 사용하는 IP주소 (퍼블릭 IP 등) 작성   
Username : MySQL 유저 이름 작성  
Password : 해당 MySQL 유저를 생성할 때 설정한 비밀번호 작성  

- SSH 접속인 경우
![SSH connection 설명](/assets/images/ssh_connection.png){:style="border-radius: 15px;"}

Connection Name : Workbench에 해당 연결을 어떤 이름으로 해놓을 것인지 작성  
SSH Hostname : Putty로 서버에 접속할 때 사용하는 IP주소 (퍼블릭 IP 등) 및 해당 서버의 포트번호 작성  
SSH Username : 연결하고자 하는 SSH 유저 이름 (일반적으로는 root이나 별도 설정된 경우 입력 필요) 작성  
SSH Password : 서버에 접속할 때 입력하는 비밀번호 작성  
MySQL Hostname : localhost 혹은 '127. 0. 0. 1' 작성  
MySQL Server Port : MySQL의 포트번호 (일반적으로는 3306이나 별도 설정된 경우 입력 필요) 작성  
Username : MySQL 유저 이름 작성  
Password : 해당 MySQL 유저를 생성할 때 설정한 비밀번호 작성  

:bulb: Username과 Password에는 위에서 '%' 로 생성한 User를 입력하면 됩니다.

## 접속 완료
위 과정을 모두 완료하면  
![연결 성공 이미지](/assets/images/mysql_connection_success.png){:style="border-radius: 15px;"}

성공적으로 연결된 것을 확인할 수 있습니다.  