---
title: Hexo + GitHub Pages 로 블로그 시작하기(2/3)
date: 2019-03-25 23:46:59
tags:
 - hexo
 - github pages
---

# HEXO

* [HEXO?](#sec1)
* [HEXO 설치](#sec2)
* [웹사이트 생성 및 확인](#sec3)
* [새 글 작성](#sec4)
* [GitHub Pages 준비](#sec5)
* [웹사이트 배포](#sec6)
* [테마 적용하기](#sec7)
* [GitHub 로 Push](#sec8)
* [정리](#sec9)
* [참고](#sec10)

## <a id="sec1"/></a>HEXO?
* 빠르고 간단하고 강력한 블로그 프레임워크
* 정적 사이트 생성기
* 가이드 문서: https://hexo.io/ko/index.html


Markdown 으로 작성한 포스트를 테마가 적용된 정적 파일로 생성해준다.  


## <a id="sec2"/></a>HEXO 설치
npm 을 이용하기 위해 node.js 가 미리 설치되어야 함


```bash
# hexo-cli 를 '전역'으로 설치
$ npm install -g hexo-cli

# hexo 버전 확인
$ hexo version
hexo-cli: 1.1.0
...(생략)

```

## <a id="sec3"/></a>웹사이트 생성 및 확인
이름은 원하는 이름으로 생성하면 되지만, git repository 이름(blog)으로 맞추도록 하겠다.

### 로컬 웹사이트 생성
```bash
# "blog" 폴더에 hexo 프레임워크 설치

$ hexo init blog
$ cd blog

# hexo 서버를 실행하기 위한 패키지 설치
$ npm install

```

### 디렉토리 구조 확인
```
.
├── _config.yml
├── package.json
├── scaffolds
├── source
|   ├── _drafts
|   └── _posts
└── themes
```

* _config.yml: 환경설정 파일
* source
  * _posts: 노출 될 post 를 markdown 파일로 저장하는 디렉토리
  * _drafts: post 초안 파일을 저장하는 디렉토리
* themes: 테마 패키지들이 저장 된 디렉토리

### 로컬 웹사이트 실행
```bash
$ hexo server
```

### 블로그 확인
http://localhost:4000 으로 접속


## <a id="sec4"/></a>새 글 작성
```bash
# 새 post markdown 파일 생성
$ hexo new post "first post"
# 생성 된 markdown 파일 이름 확인
$ ls source/_posts
```
> NOTE: _config.yml 에 new post 로 생성하는 파일명 규칙을 지정할 수 있다.

사용하기 편한 마크다운 에디터를 이용해 파일에 내용을 추가하고 저장한다.
* [visual studio code](https://code.visualstudio.com)
  > 마켓플레이스에서 markdown 확장을 추가 설치해 주어야 함
* [stackedit.io](https://stackedit.io)
  > 설치가 필요 없이 웹에서 바로 작성.

hexo 서버가 실행 중이면 브라우저를 refresh 해 추가 된 포스트 확인.

## <a id="sec5"/></a>GitHub Pages 준비
github repository 생성 blog  
hexo deploy 대상이 git 이면 publish 결과물은 gh-pages 브랜치로 푸시 된다.
리포지토리만 만들어 두고, 배포 한 후에 설정 확인해보자.

## <a id="sec6"/></a>웹사이트 배포
### git 으로 배포하기 위한 plugin 설치
```bash
$ npm install hexo-deployer-git --save
```

### _config.yml 설정
```yaml
# _config.yml
# 접속 경로 설정. 
url: https://jfreshik.github.io
root: /blog/
```
> NOTE: 로컬에서는 잘 보이는데, github pages 로 배포하면 페이지를 찾을 수 없다고 나오는 경우 URL과 root 설정값을 확인해 보자.  

```yaml
# _config.yml
# deploy 설정.
# repo에 GitHub Pages 를 위해 만든 git repository 주소를 적어주자.
deploy:
  type: git
  repo: https://github.com/jfreshik/blog.git
  branch: gh-pages

```
> NOTE: deploy branch 는 "gh-pages" 가 default 이다. master 로 배포하려면 branch 값을 꼭 설정해 주자.

### 배포!
markdown 을 정적파일로 생성해 github 로 푸시하는 과정이다.
```bash
$ hexo clean
$ hexo generate
$ hexo deploy

or

$ hexo clean
$ hexo deploy --generate
```

> NOTE: 간혹 변경 사항이 업데이트 안되어 deploy 되는 경우가 있다. 이 때에는 'clean' 후에 generate,deploy 해주면 된다.

### 배포 결과 확인:
* https://jfreshik.github.io/blog/


## <a id="sec7"/></a>테마 적용하기

마음에 드는 테마를 찾아보자.
테마를 다운로드 받는다.

## <a id="sec8"/></a>GitHub 로 Push
.gitignore 파일 추가
master 로 푸시

## <a id="sec9"/></a>정리


## <a id="sec10"/></a>참고
* https://hexo.io/ko/docs/
