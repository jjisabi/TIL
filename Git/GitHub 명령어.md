# `Git 명령어`

<br>

### 1. git --version 

- Git 버전 확인

    <img src="https://github.com/jjisabi/TIL/assets/158115388/c2cf1a2a-d887-4ee2-97c4-01f036115b25">

<br>

### 2. git init 

- 빈 저장소를 생성하거나 기존의 저장소를 다시 초기화 하는 명령어이다.

<br>

### 3. git add

- 파일이 Tracked 상태이면서 커밋에 추가될 Staged 상태를 만들어 준다.   (변경되거나 새로운 파일을 추적함)

    ```
    git add 파일이름 (하나의 파일만을 add)
    git add 파일명1 파일명2 (파일명1, 파일명2 여러 개 파일 지정해서 add)
    git add . (.을 사용하면 변경된 모든 파일을 add)
    ```
<br>

### 4. git commit 
- git add 명령어로 staging 한 파일을 repository에 commit 하는 명령어이다.

    <br>

    #### `용어 정리: staging area & repository`
    <img src="https://github.com/jjisabi/TIL/assets/158115388/d13a55e0-a248-4d99-be04-ed36e5cb5b8e">

    <br>

    1. staging area: commit 하기 전에 commit할 파일들을 골라놓는 영역이다.

    - staging area에 파일넣는 행위를 staging이라고 한다.

    - git add 명령어로 staging 할 수 있다.

    <br>

    2. repository: commit 된 파일의 버전들을 모아놓는 영역이다.

    - git이 파일버전을 저장해두는 장소

    - 작업 폴더 안에 숨겨져 있는 .git 폴더 => `local repository`

    - 실제 작업하는 공간(실제 파일이 위치하는 곳)

    <br>

     `git add`를 통해서 `staging area`으로 파일들을 올리고 스테이지에 없는 파일들은 `절대 commit 되지 않는다 ! ! ! `


<br>

## 다른 명령어들
### 1. git status

```
git status
```

- 파일의 상태 확인하는 명령어이다.
- 현재 변경된 파일, 스테이징된 파일 등 확인 가능 => 뭐하는 지 까먹었을 때 입력 !

<br>

### 2. git restore
```
git restore --staged 파일명
```

- 스테이징 된 파일 취소하는 명령어이다.

<br>

### 3. git log

```
git log --all --oneline
git log --all --oneline --graph
```

- commit 기록을 한 눈에 파악할 수 있는 명령어이다.
- graph 옵션을 넣으면 그래프로 확인 가능하다.<br><br>
<img width=500px, src="https://github.com/jjisabi/TIL/assets/158115388/50f0d51b-d4b9-4930-bfca-25f6b4fda42a"> 
<br>(보잘 것 없는 그래프,,,)

- 입력 후엔 Vim 에디터가 켜진다. j, k 키로 위아래 스크롤, q 키로 종료 <br>


<br>
<br>


## Github 사용 명령어
### 1. git branch -M main
```
git branch -M main
```

- 기본 branch 명 변경하는 명령어 이다. (master -> main)

```
github.com은 기본 branch 이름을 master가 아니라 main으로 사용해야 한다.
그래서 로컬 작업폴더에 있는 기본 branch 이름을 main으로 변경해주어야 한다.
위의 명령어를 입력하면 기본 브랜치 branch 변경된다.(안해도 될 수 있다.)
```

### 2. git push
```
git push -u https://github.com/jjisabi/TIL.git main
```
- 로컬 저장소의 main 브랜치를 원격 저장소에 올리는 명령어이다.
- `-u 옵션` : 방금 입력한 주소 저장 (다음부터 git push만 입력하면 된다.)
<br><br>

    <img src="https://github.com/jjisabi/TIL/assets/158115388/644b52bc-0338-488e-9e14-0f7e934ac703">

    ```
    원격 repository 주소는 https:// 부터 시작해서 .git으로 끝남
    위의 이미지와 같이 주소창 그대로 복사해와서 .git만 뒤에 붙이면 원격 repository 접속 url이다.
    ```
<br>

### 3. git remote add 변수명 저장소 주소

```
git remote add origin https://github.com/jjisabi/TIL.git
```

- 저장소 주소가 필요할 때 마다 origin 이라는 변수명을 쓸 수 있는 명령어이다.

```

<br><br>
git push -u https://github.com/jjisabi/TIL.git main
git push -u origin main
```
