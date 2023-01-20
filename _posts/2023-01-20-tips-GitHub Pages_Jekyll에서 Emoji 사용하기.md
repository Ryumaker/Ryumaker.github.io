---
title: "GitHub Pages - Jekyll에서 Emoji 사용하기"
excerpt: "GitHub Pages에서 Emoji 감정표현을 사용해봅시다."
categories: 
- tips
tags:
- Github-Pages
toc: true
toc_sticky: true
date: 2023-01-20
last_modified_at: 2023-01-20
---
**_<제가 공부하며 그때그때 필요한 지식들을 적어놓는 tips 카테고리이며,_**  
**_지속적으로 update될 작성글입니다.>_**

Github Pages는 사용자 마음대로 커스텀할 수 있는 자유도가 높아  
많은 사람들이 찾는 블로그 서비스 중 하나입니다.  
이때, Emoji를 사용하면 자칫 밋밋해보일 수 있는 게시물에  
풍부한 감정표현을 추가함으로써 훨씬 다채롭게 꾸밀 수 있습니다.  

본 방법은 minimal-mistakes 테마 기준으로 작성되었습니다.  

## Emoji를 사용하는 방법
### 1. _config.yml 수정하기
```
plugins:
- jekyll-feed
- jekyll-paginate
- jemoji
```
_config.yml 파일에서 plugins 항목을 찾아 jemoji를 위 코드와 같은 형식으로 추가해줍니다.  
서버를 실행한 후에 이상이 없으면 바로 사용할 수 있습니다.  

### 2. 에러가 발생했을 경우
```
Dependency Error: Yikes! It looks like you don't have jemoji or one of its dependencies installed. In order to use Jekyll as currently configured, you'll need to install this gem. The full error message from Ruby is: 'cannot load such file -- jemoji'
```
local Server에서 먼저 확인하고자 서버를 실행하였을 때, 위와 같은 오류가 발생했습니다.  
로컬에 github-pages gem을 설치해봅시다.  

#### 2-1. Gemfile 수정하기
```
gem "github-pages", group: :jekyll_plugins
```
Gemfile에 위의 코드를 추가한 후에
```
bundle install
```
위 코드로 install해줍니다.

#### 2-2. 버전 문제
```
Bundler could not find compatible versions for gem ~~~
```
2-1까지 수행했더니 위와 같은 오류가 발생하였습니다.  
gem이나 jekyll 버전이 맞지 않을 수 있으니 아래의 코드를 수행합니다.  
```
bundle update
```
#### 2-3. API 문제
여기까지 수행하였는데도 다음과 같은 오류가 발생하였습니다.
```
"No GitHub API authentication" error
```
이때는, _config.yml 파일에 아래와 같은 코드를 추가해줍니다.
```
github: [metadata]
```

저는 위의 과정을 모두 거쳐서 emoji를 사용할 수 있게 되었습니다.  
중간에 오류가 더 이상 발생하지 않고 잘 출력된다면, 바로 사용하셔도 무방합니다. :thumbsup:


