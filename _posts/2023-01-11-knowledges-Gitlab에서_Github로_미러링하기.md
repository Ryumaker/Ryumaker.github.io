---
title: "Gitlab에서 GitHub로 미러링하기"
excerpt: "Gitlab에서 작업한 결과물을 Github로 옮겨와야 하는 경우가 종종 발생합니다."
categories: 
- knowledges
tags:
- Git
toc: true
toc_sticky: true
date: 2023-01-11
last_modified_at: 2023-01-11
---
**_<제가 공부하며 그때그때 필요한 지식들을 적어놓는 Knowledges 카테고리이며,_**  
**_지속적으로 update될 작성글입니다.>_**

Gitlab에서 작업한 결과물을 Github로 옮겨와야 하는 경우가 종종 발생합니다.  
이때, 커밋 로그를 유지하며 옮겨오는 하나의 방법은 다음과 같습니다.  

## 옮기는 방법

1. Github로 옮길 원본 repo의 주소를 clone합니다.  
```
$ git clone --mirror '원본 repo의 주소'
```

2. git 폴더로 진입합니다.  
```
$ cd '원본 저장소 git 폴더 이름'.git
```

3. Github에 옮겨놓을 repo를 새로 하나 만들고 그 주소를 입력합니다.  
```
$ git remote set-url --push origin '옮겨놓을 원격 Github repo 주소'
```

4. push 합니다.  
```
$ git push --mirror
```


