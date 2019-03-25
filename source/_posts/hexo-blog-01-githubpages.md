---
title: Hexo + GitHub Pages 로 블로그 시작하기(1/3)
date: 2019-03-25 23:46:46
tags:
 - hexo
 - github pages
---

# GitHub Pages 시작하기

* [GitHub Pages?](#sec1)
* [GitHub Pages 접속 주소 결정하기](#sec2)
* [GitHub Pages 용 Repository 생성하기](#sec3)
* [GitHub Pages 에 파일 푸시](#sec4)
* [GitHub Pages 확인](#sec5)
* [정리](#sec6)
* [참고](#sec7)

## <a id="sec1"></a>GitHub Pages?
```
GitHub Pages is a static site hosting service designed to host your personal, organization, or project pages directly from a GitHub repository.
```

* html, js, css 등 정적 파일을 호스팅 해주는 서비스이다.  

github 계정이 있으니 블로그용 repository 하나 생성하고, 적절한? 설정만 해주면 내가 만든 웹페이지를 브라우저에서 바로 볼 수 있다.


## <a id="sec2"></a>GitHub Pages 접속 주소 결정하기
git repository 이름에 따라에 아래 두가지 형태의 URL 을 사용할 수 있다. (rule)

|URL pattern | repository | 결과 | 비고 |
| ---------  | :--------: | :--: | --- |
| https://{id}.github.io | jfreshik.github.io | https://jfreshik.github.io | master 브랜치만 퍼블리시용으로 사용 |
| https://{id}.github.io/{repository}/ | blog | https://jfreshik.github.io/blog | 설정에 따라 퍼블리시 브랜치를 gh-pages,master 둘 중 하나 선택 |

## <a id="sec3"></a>GitHub Pages 용 Repository 생성하기
퍼블리시 결과 뿐만 아니라 post,plugin,theme 도 같이 관리하기 위해 "blog" 리포지토리를 사용
https://jfreshik.github.io/blog/  

repository screenshot

## <a id="sec4"></a>GitHub Pages 에 파일 푸시
```bash
# 로컬 작업 directory 생성 및 이동
$ mkdir blog
$ cd blog

# index.html 생성
$ echo "Hello GitHub Pages" >> index.html

# local repository
$ git init
$ git add .
$ git commit -m "init commit"

# github 저장소 추가
$ git remote add origin https://github.com/jfreshik/blog.git

# github 저장소로 master push
$ git push -u origin master
```

## <a id="sec5"></a>GitHub Pages 확인

### 페이지 접속 확인
https://jfreshik.github.io/blog/


### Source 설정
> GitHub blog repository > Settings > GitHub Pages

* master 로 푸시 했으니 source 설정을 "master branch" 로 선택  
* source 설정을 "gh-pages" 로 선택하면, master 브랜치에는 hexo 서버 소스(post, plugin, theme)를 푸시하고, publish 결과물을 gh-pages 브랜치로 푸시해 하나의 repository 로 관리할 수 있다.

### 재확인
https://jfreshik.github.io/blog/  
혹시 404 not found 가 다시 노출 되면 url 경로 마지막에 '/' 가 빠지지 않았는지 확인!!


## <a id="sec6"></a>정리
* 파일을 업로드 하기 위해 ftp 등의 서버접속을 할 필요가 없어 아주아주 편리하다.
* repository 설정에서 서비스 운영에 적합한 GitHub Pages "Source" 를 선택하자.


## <a id="sec7"></a>참고
* https://pages.github.com/  
* https://help.github.com/en/articles/configuring-a-publishing-source-for-github-pages