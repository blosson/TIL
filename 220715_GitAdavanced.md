# Git 심화

- git과 github은 다르다! <br>
: git은 분산 버전 관리 시스템! Github는 git을 통해 이용하는 Cloud 서비스다! <br></br>

- Git 기본 명령어
  - Local Repository를 입력할 때 : `git init`
  - File의 상태: <br>
    1. `untracked`: git이 아직 관리되고 있지 않다. (최초 생성시)
    2. `Tracked`: add 명령어를 통해서 Staging Area에 올라간 파일
   - Git status : 현재 Local Repository의 상태를 확인하는 명령어 (**습관처럼 입력해야 한다!**) <br></br>
  
- 협업과 복구 및 백업
  - 원격 저장소 연결 <Br>
    1. github에 원격 저장소를 생성합니다.
    2. 로컬 저장소 (Repository)를 생성합니다.
    3. 원격 저장소에 push 하기 전에 반드시 최소 하나 이상의 commit을 가져야 한다. <br></br>

  - 원격 저장소 연결 명령어 <br>
    >git clone url or git pull url : 가져오기 <br>

    -> 처음은 clone or pull 상관없음. BUT 이후에는 계속 pull로 가져와야 함. clone으로 가져오면 계속 새로운 폴더와 README.md 파일이 생성되기 때문이다. 즉, 로컬 repo가 원격 repo와 연결되어 있는 경우에는 pull을 쓰면 됨. 

    1. `git remote add origin URL`
    2. `git remove -v` : origin URL __(등록한 Remote Repository 정보 확인)__
    3. git push -u origin master : 로컬에서 생긴 커밋 내역을 업로드 
      - -u로 입력하면 그 다음부터는 git push 만 입력해도 커밋이 됨
    4. `git pull origin master` : 원격 저장소의 변경 사항을 __업데이트__
    5. git clone URL : 원격 저장소를 **복제**해온다 (원격→로컬) : 다운로드
       - (번외) git remote remove origin URL : 연결된 origin  삭제 <br></br>
> Gitignore
- Github에 올리면 안되는 개인정보, 비밀 같은 것들을 숨기는 기능
- 그냥 `.gitignore` 라는 파일을 만들어주면 됨.
- **.gitignore**를 README.md와 함께 Repository를 생성하자 마자 만들어야 함. Git에 한 번 푸쉬한 파일/폴더는 절대 ignore를 할 수 없음.

---

## Branch

[브랜치 생성과 삭제, 체크아웃](https://mylko72.gitbooks.io/git/content/branch/checkout.html)

- 병렬적인 작업이 가능하게 해줌
- fast-forward 방식과 3 way merge 방식이 있음 (알아만 두기)

