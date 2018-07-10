
출처 : 소셜 코딩으로 이끄는 GitHub 실천기술

저자 : 오오츠카 히로키 지음/윤인성 옮김

출판사 : 제이펍

# 코드 공개

### ● 생성된 리포지토리 clone하는 방법

> $ git clone URL

### ● commit하는 방법
생성한 파일이 버전 관리 시스템의 관리를 받도록 해야 합니다. 이렇게 설정해야 이후의 변경 내용등이 Git에 유지됩니다.

> $ git add 파일

> $ git commit -m "Add description"

### ● push하는 방법
이어서 다음과 같이 push하면 GitHub에 있는 리포지토리가 갱신됩니다.

> $ git push

이렇게 하고 나면 GitHub에 코드가 공개됩니다.

# 기본적인 사용 방법

### git init: 리포지토리 초기화
Git으로 버전 관리를 하려면 리포지토리를 초기화해야 합니다. Git에서는 'git init'명령어로 초기화를 수행합니다. 실제로 폴더를 생성하고 리포지토리를 초기화해 봅시다.

<img width="490" alt="git_init" src="https://user-images.githubusercontent.com/35086306/42491672-c2df05bc-8450-11e8-9080-467ee51329f5.png">

초기화가 성공적으로 완료되면 git init 명령어를 실행한 폴더에 '.git'이라는 이름의 폴더가 만들어집니다. 이 .git이라는 폴더에 현재 폴더와 관련된 리포지토리 관리 정보가 저장됩니다.

Git에는 이 디렉토리 이하의 내용을 해당 리포지토리와 관련된 'working tree'라고 부릅니다. working tree에서는 파일 준비 등이 이루어지며, 이후에 리포지토리에 등록된 파일 변경 내역을 관리하게 됩니다. 파일을 이전 상태로 되돌리고 싶은 경우, 리포지토리로부터 이전 파일 상태를 확인하고 working tree에 전개합니다. 이러한 기능을 수행하는 명령어는 뒤에서 차근차근 설명하겠습니다.

### git status: 리포지토리 상태 확인

'git status' 명령어는 Git 리포지토리의 상태를 표시하는 명령어 입니다. 자주 사용하는 명령어이므로 반드시 기억하기 바랍니다.

working tree 또는 리포지토리에 대응되는 조작을 하면 상태가 차례대로 변경됩니다. git status 명령어로 현재 상태를 확인하면서 Git의 명령어를 하나하나 입력하는 것이 기본 중의 기본입니다.

<img width="247" alt="git_status1" src="https://user-images.githubusercontent.com/35086306/42492121-c3ad9e66-8452-11e8-84b8-45e5f44c1fb7.png">

현재 master라는 이름을 가진 브랜치(branch)에 있는 것이 표시됩니다. 이어서 출력 결과로 commit이 없었다는 것도 확인할 수 있습니다. commit이란, working tree에 있는 모든 파일의 특정 시점 상태를 기록한 것입니다. 또한, commit이 없는 것은 지금 작성한 리포지토리에 어떤 파일의 상태도 기록되어 있지 않다는 의미입니다. 따라서 commit하기 위해 간단하게 README.md 파일을 작성하겠습니다.

<img width="248" alt="git_status2" src="https://user-images.githubusercontent.com/35086306/42492133-d14df354-8452-11e8-9399-75feee39d4dd.png">

README.md 파일이 Untracked files에 표시되는 것을 확인할 수 있습니다.

### git add: 스테이지 영역에 파일 추가

Git 리포지토리의 working tree 파일을 작성한 것만으로는 Git 리포지토리의 버전 관리 대응 시스템 파일이 등록되지 않습니다. git status 명령어로 확인하면, README.md 파일은 'Untracked files'로 출력됩니다.

파일을 Git 리포지토리에서 관리도록 하려면 git add 명령어로 스테이지 영역이라 불리는 장소에 파일을 등록해야 합니다. 스테이지 영역이란 commit하기 전의 임시 영역입니다.

<img width="489" alt="git_add" src="https://user-images.githubusercontent.com/35086306/42492140-db458df4-8452-11e8-8e05-c21f57fb940a.png">

README.md 파일을 스테이지 영역에 등록하면, git status 명령어를 사용할 때의 출력이 변경됩니다. 'Changes to be commited'에 README.md 파일이 표시되는 것을 확인할 수 있습니다.

### git commit: 리포지토리 변경 내용을 기록
git commit 명령어는 스테이지 영역에 기록된 시점의 파일들을 실제 리포지토리의 변경 내역에 반영하는 것입니다. 이러한 기록을 기반으로 파일을 working tree에 복원하는 것이 가능합니다.

#### ● 한 줄의 commit 메시지를 기록하는 방법

<img width="257" alt="git_commit1" src="https://user-images.githubusercontent.com/35086306/42492157-ea60b084-8452-11e8-9cf4-e0e79dd9c211.png">

-m 옵션으로 "First commit"이라는 글자를 넣었습니다. 이는 commit 메시지라고 부르는 것으로, 해당 commit과 관련된 필요한 내용을 기록하는 기능입니다.

#### ● commit을 중지하는 방법

에디터가 이미 실행된 상태에서 commit을 중지하고 싶을 때는 아무것도 입력하지 말고 에디터를 종료해 주세요. 이렇게 하면 commit이 이루어지지 않습니다.

#### ● commit하고 나서 상태 확인

<img width="275" alt="git_commit2" src="https://user-images.githubusercontent.com/35086306/42492171-f977032a-8452-11e8-9f85-cd10a30d4c67.png">

현재 working tree의 상태는 commit이 된 최신 상태입니다. 변경 내역이 이미 반영되었으므로 새로운 변겨 내역이 없다는 것을 확인할 수 있습니다.

### git commit: 리포지토리 변경 내용을 기록

<img width="491" alt="git_log" src="https://user-images.githubusercontent.com/35086306/42492173-014f953a-8453-11e8-9bb0-3d8008f3dfa0.png">

git log 명령어는 리포지토리에 commit된 로그를 확인할 수 있는 명령어입니다. 누가 언제 commit또는 merge를 했는지, 어떤 변경이 발생했는지 등을 확인할 수 있습니다.
