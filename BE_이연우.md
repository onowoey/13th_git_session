# 13th_git_session

## GIT vs GITHUB

- git 이란 컴퓨터 내에서 버전 관리를 하는 프로그램 자체를 말함
- github 는 그 git을 온라인으로 공유할 수 있는 플랫폼

## 초기 세팅

git config --global [user.name](http://user.name/) 본인 깃허브 아이디
git config --global user.email 본인 깃허브 이메일

: 아이디나 이메일을 변하게 하지 않으려면 처음에만 하면된다. 한 번만 설정하면 이후에 새로 생성하거나 클론한 모든 Git 저장소에서 자동으로 해당 설정이 적용된다. 특정 파일에서만 하려면 —local 사용.

## 개인 레포지토리 관리

- [README.md](http://README.md) : 프로젝트 소개, 사용법, 설치방법들을 보여주는 문서
- .gitignore: git이 add 명령어에 의해 commit 될 때 커밋 대상자에서 제외되는 파일
    - 예를들어 개인정보가 들어있는 파일은 제외되어야함.
- License: 프로젝트의 다른 사람들이 어떻게 사용할 수 있는지

### 과정(연결&불러오기)

1. git init: git 이 해당 폴더를 저장소로 변환
    1. 해당 폴더 내에 .git 이라는 숨김폴더가 생김. 
    2. 그 폴더 내에는 git 이 관리하는데 필요한 정보 저장됨
2. git remote add origin 내 레포지토리 주소 : 저장할 곳 연결
git remote -v : 원격 저장소 연결 확인
git branch -M main : 기본 브랜치 이름을 master 에서 main으로 변경
3. git pull origin main: 연결한 레포지토리의 main 브랜치의 최신 사항을 불러옴.

### 과정(수정사항 올리기)

1. git add . : 현재 디렉토리(.) 아래의 모든 변경 파일을 git 이 추적
2. git commit -m “커밋메세지” : 추적한 파일들을 실제 git 이력에 기록함.(커밋 메세지로)
3. git push origin main:  컴퓨터의 커밋 내용을 원격 저장소 (origin에 적었던 저장소의 main branch)로 올림.

## 협업 레포지토리 관리

- fork 란? 
다른 사람의 레포지토리를 내 github 계정으로 복사해오는 것!
- branch 란?
작업을 나누어하기 위해 기존 코드 (main) 에서 갈라져 나온 독립적인 작업공간.
즉, main 에 merge 하기 전 개인이 만드는 초안 느낌. main branch 는 항상 안정적이어야 한다.
    - git branch : branch 목록 확인
    - git branch 새 브랜치 이름 : 새 브랜치 생성
    - git switch 브랜치 이름 : 브랜치 이동
    - git branch -d 브랜치 이름 : 해당 브랜치 삭제

### 과정(연결&불러오기)

1.  git init: git 이 해당 폴더를 저장소로 변환
2. git remote add origin 내 레포지토리 주소 
git remote add upstream 중앙 레포지토리 주소(내가 fork 해 온 곳)
git remote -v 
git branch -M main
3. git pull upstream main : 중앙 레포지토리의 main branch 의 최신사항 불러옴.
4. git branch 브랜치명
git switch 브랜치명

### 과정(수정사항 올리기)

1. git add .
2. git commit -m “커밋메세지”
3. git pull upstream main : push 하기 전 꼭 pull 해주기.
git push origin 현재 브랜치명
4. 내 레포지토리로 이동해서 compare & pull request 클릭
5. Add a title : 수정한 내용에 대한 제목
Add a description : 수정한 내용에 대한 자세한 설명 추가.
스크롤 해서 밑에 수정한 부분을 확인하고, 문제 없다면 create
6. 중앙 레포지토리에 가서 코드에 문제가 없다면 merge
7. git switch main
git pull upstream main
git branch -d 사용한 브랜치명 : main branch 에 merge 시킨 후에는 사용한 브랜치를 꼭 삭제하기.
