## Git
<a name="readme=top"></a>
####버전 관리 시스템
      원하는 시점(버전)으로 이동할 수 있으며,
      각 버전별로 여러 개발자가 협업할 수 있는 최적의 환경을 제공하는 시스템(체계, 약속)
####SVN
      작업 내역 커밋시, 변경사항과 히스토리가 즉시 서버로 전송되기 때문에 편하다.
      또한 간단한 설치와 사용 방법으로 별도의 교육 없이도 초보자도 쉽게 사용할 수 있다.
      하지만 원격 저장소(SVN 서버)를 필요로 하며, 서버간 버전 관리 및 복구가 힘들다.
####Git
      SVN이 가지고 있던 클라이언트와 서버 간의 버전 관리 문제를 많이 보완해준 시스템.
      서버 뿐만 아니라 로컬에서도 버전 관리가 가능하며, 로컬이 서버가 될 수도 있도,
      서버가 로컬이 될 수도 있다. 브랜치라는 개념을 사용하여 개발자 마음대로
      로컬 환경에서 커밋과 버전 관리가 가능하다. 이를 git-flow라고 한다.
      git-flow는 회사마다, 프로젝트 마다 다르기 때문에 입사 후 담당 PL/PM분과 상의하기로 한다.
<br>

####저장소의 종류
       - 로컬 저장소(local): 개인 전용
       - 원격 저장소(remote): 서버 전용
<p align="right">(<a href="#readme-top">back to top</a>)</p>

####[초기 설정]
       git config --global user.name "이름"
       git config --global user.email "이메일"
       git config --list (스크롤 형태가 나온다면 q로 나가기)
       git config --global -e
####[VIM editor]
       i (INSERT MODE)
       내용 작성
       esc
       :wq
       git config --global --list
####[로컬 작업]
      git init
      작업 진행
      git status
      git add .
      git commit
      ※ 만약 기존 파일 수정 혹은 삭제일 경우 git commit -am 옵션으로 add와 commit을 한 번에 할 수 있다.
      git status
      git log --pretty=oneline
      git log --oneline
####[버전 이동]
      git log --oneline
      git checkout [커밋 ID]
      ※ 버전을 이동한 다음 작업은 절대 불가, 만약 해당 버전에서 작업하고 싶다면, 브랜치를 따서 이동 후 작업
####[브랜치 생성 및 이동]
     git checkout -b [브랜치명] : 새롭게 만들고 이동
     git checkout [브랜치명] : 기존에 있는 브랜치로 이동
####[병합]
     받을 곳으로 이동해서 가져올 브랜치를 작성한다. 
     git merge [가져올 브랜치명]
   1. fast-forward
      하나의 브랜치에서만 작업(커밋)하면, fast-forward이다.

   2. merger
      각 브랜치에서 각자 작업(커밋)하면, 일반 merge(새로운 버전으로 생성)이다.
      
   3. conflict
      각자 같은 파일을 수정하고 merge하면 충돌 발생.
      되돌릴 때에는 git merge --abort
      해결하고자 할 때에는 충돌난 파일 열어서 1가지 선택 후 commit
<p align="right">(<a href="#readme-top">back to top</a>)</p>

####[원격 서버 연결]
     git remote [이름] [URL]
     git remote -v
     작업
     git add .
     git commit -m ""
     git push -u [이름] [브랜치명]
     git branch -vv
     서버 작업 불러오기
     ***
     git fetch
     git diff --stat origin/master
     git merge origin/master
     ***
     * fetch + merge는 pull로 사용하자
     git pull origin master
<p align="right">(<a href="#readme-top">back to top</a>)</p>

####[입사 첫 날]
     git clone -b [브랜치명] [URL] [clone 받을 경로]
     예) git clone -b master [URL] .
     예) git clone [URL] .
####[.gitignore]
     개인 설정 파일 및 개인 보안 파일 등은 협업에 사용하지 않도록
     .gitignore 파일에 기재하여 감지되지 않게 막아준다.
####   * 경로
   /a   : 현재 경로에 있는 a파일 혹은 a폴더
   a   : 모든 경로에 있는 a파일 혹은 a폴더
   /a/   : 현재 경로에 있는 a폴더
   a/   : 모든 경로에 있는 a폴더
   *.class   : 모든 경로에 있는 class확장자를 가진 파일
   /*.class   : 현재 경로에 있는 class확장자를 가진 파일
####[Organization]
   [팀장]
   Organization 레포지토리 생성
   작업
   push
   팀원 초대

   전원 fork

   [팀원]
   clone
   작업
   add
   commit
   push
   PR(Pull Request)

   [팀장]
   merge

   [PR 요청자 제외 전원]
   sync
   pull (다른 사람이 작업한 것들 받기)
