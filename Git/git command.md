# Git command

> Git 명령어 정리

### 0. init

- `.git/` 폴더를 생성해준다.
- git init
- ![a](gitcommand.assets/a.png)
- `.git`폴더가 생성된 경우 로른쪽에 `master`라는 표시가 나온다

- 최초에 한번만 하면된다.

### 1. add

- `git add` <추가하고 싶은 파일>
- `git add .` : 현재 폴더의 모든 파일과 폴더를 add
- working directory > staging area로 파일 이동

### 2. config

- `git config -- grobal user.email "이메일 주소"`
  - 이메일의 경우 깃헙에 올릴 경우 잔디가 싶어지는 기준이므로 정확게 입력!
- `git config --grobal user.name "myname"`
- 최초에 한번만 하면된다

### 3. commit

- `git commit -m "메세지"`
- 스냅샷을 찍는 동작
- add 되어 있는 파일들을 하나의 묶음으로 저장
- 메세지에 들어가는 내용은 기능 단위로

### 4. remote

- `git remote add origin <주소>`
- 원격 저장소와 현재 로컬 저장소를 연결

### 5. push

- `git push origin master`
- 깃아 올려줘 origin으로 master를
- 원격저장소에 로컬 저장소의 데이터를 전송

### 6. status

- `git staus`
- 현재 git 상태를 출력



