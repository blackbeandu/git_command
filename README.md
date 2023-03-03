# git_command


## Git Bash를 이용해 repository에 파일 및 폴더 올리기

windows git 테스트</br>


연결할 레파지토리의 url을 복사한 후
git remote add origin url  
origin에 내 url(사이트 주소 말고 copy에 나오는 주소) 정보가 담겨 있음.  
origin은 변수명이라고 생각하면된다. 다른 이름으로도 가능하나 가장 상위(즉 디폴트)는 통념상 origin으로 한다. </br>
참고) 일단 내 것 말고 원본 레파지토리로 연결해놓으면 PR이 가능한 것을 확인했다.  
  여기서 2가지 경우의 수를 생각해볼 수 있다.  
   1. fork뜬 것은 원본에 remote를 걸어야 한다.</br>
   2. 내 레이어(내가 원본)는 내 주소로 remote하면 PR이 가능하다.(지금 말 정리가 안된다;;) </br>
복사하기 : ctrl + insert (참고로 그냥 인터넷에서 복사할 때는 ctrl + c 로 복사후 git  bash해서 붙여넣기 방식으로 하면 붙여넣어진다. </br>
붙여넣기 : shift + insert  

기존 orign 삭제  
git remote remove origin

레파지토리 연결된거 확인  
git remote -v  

내 레파지토리의 clone을 생성  
git clone url  
git bash의 경로에 해당 레파지토리 폴더가 생긴다. 이렇게 하는 것이 code클릭 후 zip파일을 다운받는 것보다 더 쉽고 빠르다.  \
url은 진짜 경로여야 한다. origin으로 썼더니 안된다.  

자기가 올릴 파일이 있는 상위 폴더에 마우스 오른쪽 버튼 클릭 후 git bash here 클릭  

처음 시작하면 맨 끝에 (master) 이런게 없음  
git을 사용하기 위해 git init으로 .git 폴더 생성 (쉽게 말하면 git 생성자 클래스라할까..)  
이것은 기존 레파지토리를 사용하지 않고(clone뜨지 않고 할 경우) 할 때고 보통 git bash에서 git clone뜨면 저절러 .git 생성된다.</br>

git --global user.name git 닉네임  
git --global user.email git로그인 이메일  
git config --global --list : global config list  
git config --local --list : local config list  
git config --list : all config list  
삭제 : git config --global --unset 해당cfg변수  
  --global이 없으면 --local이 default로 되어있는 듯하다.

이거 만들면서 git 다시 해봤는데 빈 폴더는 push를 할 수 없다.  
애초에 add가 안됨. 폴더 안에 파일이 1개라도 있어야함. 그래서 test2.txt를 넣었더니 git status에 test_folder가 보인다.  

add한거 commit하기 
git commit -m "설명"
근데 메시지 안쓰고 싶으면?
git commit --allow-empty-message -m "" (당연히 git commit -m "" 은 안되기 때문)

add와 commit 동시에 하기
git commit -am "설명"  

이미 clone을 생성 했는데 레파지토리에 다른 파일이 누군가에 의해서(또는 내가 직접 파일을 웹에서 올렸을 경우)  
git pull  
하면 업로드된 파일들 가져온다.  
git fetch 도 pull과 같은 역할인데 pull은 가져오는 코드가 더 최신이면 내 코드와 merge하지만 fetch는 단순히 로그만 가져온다고 생각하면 된다.</br>
즉 어디어디가 지금 너가 가지고 있는것과 달라졌다고 알려주는데 이게 FETCH_HEAD라는 branch에 담긴다.</br>
fetch는 내가 pull한 파일과 fetch로 가져올 때 파일이 서로 다르면 안된다.</br>
ex) 1. 내가 파일 A를 pull함. A가 수정됨. git fetch시 FETCH_HEAD branch가 생기며 checkout가능하다. ((fealllc...))로 변경됨.</br>
이때 수정된 파일을 가진채로 새로운 branch를 만드는 방법까지 알려준다. git switch -c <new-branch-name> </br>
2. 내가 파일 A를 pull함. pull한 파일 중 수정 파일 존재. A가 수정됨. git fetch시 정상작동 안함. </br>


새로운 branch를 만드는 방법  
git branch 새로만들 branch 이름  

branch 전환  
git checkout 전환할 branch 이름  

새로운 branch를 만들고 그 branch로 전환하기  
git checkout -b 새로만들 branch 이름  

새로운 branch를 만들고 그 branch를 깃헙에 만드려면
git push --set-upstream origin 새로운 branch 이름  
해석하자면 origin(remote)에 내가 만든 branch(local)를 push하겠다!  
(이거 지금 작동을 안함..)  
->정상 작동 한다면 새로운 branch가 위 코드 필요 없이 자동으로 만들어짐. 즉 protect된 branch에 직접 push를 하지 않으면 됨.</br>

한번도 commit을 하지 않고 branch를 만들면  
fatal: not a valid object name: 'mater'이라고 에러 문구가 뜬다.  
그럼 여기서 강제로 git checkout -b test 를 입력하면 branch가 switch 되는데,  
이는 새로운 branch가 만들어 진것이 아니라 기존 branch이름이 변경된 것이다(master -> test).  

branch list 확인  
git brach -a  

branch 삭제
git branch -D 삭제할 branch 이름

git bash을 통해 텍스트 파일에 진입시
vim test.txt
후 i나 a를 눌러 편집모드로 들어감. write 가능.<br> 
다 수정후 Esc누른후 :wq 누르면 저장하고 종료 <br>

git bash에서 새로운 branch를 만들면 main을 기반으로 새롭게 만들어진다. </br>
git checkout <branch name>으로 이동하면 당연히 파일 내용이 바뀐다. </br>
원본에서 git pull을 해 내 로컬에 파일을 업데이트 하려면 같은 branch 선상에 있어야 한다.</br>
ex)git pull origin main 이라고 하면 내 git bash에 branch도 main에 있어야 한다. </br>

git add . 할 때 특정 파일을 제외하고 싶은 경우(숨겨진 폴더중 .vs는 업로드가 어려운데(불가) 이거 하나만 빼주고 싶을 때)  
git bash에서 vi gitignore 입력 후  
폴더의 경우  
#folder  
.vs/  

파일의 경우  
#file  
*.apk  
동시도 가능  

원격 저장소의 branch확인하기</br>
git remote show origin </br>

*수정이 필요함</br>
stash는 임시저장으로 아직 add와 commit을 하고 싶지는 않지만 다른 branch로 이동해 작업해야 할 때 사용한다.</br>
git stash save로 stash가 저장되며 git stash list로  stash목록을 확인할 수 있다.</br>
특정 stash를 적용시키려면 list를 확인한 뒤 git stash apply <stash이름> . stash이름 ex) stash@{0} </br>
추가 사항은 참고에 사이트 확인</br>

git diff : 두 branch의 차이를 보여주는 명령어</br>
git diff origin/amster origin/test </br>


참고<br>
https://www.zerocho.com/category/Git/post/580f633046f4fe09815b72a5 (git 명령 간단 설명)  
https://wayhome25.github.io/git/2017/07/08/git-first-pull-request-story/ (PR 관련)  
https://gmlwjd9405.github.io/2018/05/18/git-stash.html (stash 관련)  
https://dreamaz.tistory.com/540 (add시 특정 파일(폴더) 제외시키기)  


