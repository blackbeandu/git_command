# git_command


## Git Bash를 이용해 repository에 파일 및 폴더 올리기



연결할 레파지토리의 url을 복사한 후
git remote add origin url  
origin에 내 url 정보가 담겨 있음.  
origin은 변수명이라고 생각하면된다. 다른 이름으로도 가능하나 가장 상위(즉 디폴트)는 통념상 origin으로 한다.

레파지토리 연결된거 확인  
git remote -v  

내 레파지토리의 clone을 생성  
git clone origin  
git bash의 경로에 해당 레파지토리 폴더가 생긴다. 이렇게 하는 것이 code클릭 후 zip파일을 다운받는 것보다 더 쉽고 빠르다.

자기가 올릴 파일이 있는 상위 폴더에 마우스 오른쪽 버튼 클릭 후 git bash here 클릭  

처음 시작하면 맨 끝에 (master) 이런게 없음  
git을 사용하기 위해 git init으로 .git 폴더 생성 (쉽게 말하면 git 생성자 클래스라할까..)  

이거 만들면서 git 다시 해봤는데 빈 폴더는 push를 할 수 없다.  
애초에 add가 안됨. 폴더 안에 파일이 1개라도 있어야함. 그래서 test2.txt를 넣었더니 git status에 test_folder가 보인다.  

이미 clone을 생성 했는데 레파지토리에 다른 파일이 누군가에 의해서(또는 내가 직접 파일을 웹에서 올렸을 경우)  
git pull  
하면 업로드된 파일들 가져온다.  

새로운 branch를 만드는 방법  
git branch 새로만들 branch 이름  

branch 전환  
git checkout 전환할 branch 이름  

새로운 branch를 만들고 그 branch로 전환하기  
git checkout -b 새로만들 branch 이름  











