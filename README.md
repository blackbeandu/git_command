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

자기가 올릴 파일이 있는 상위 폴더에 마우스 오른쪽 버튼 클릭 후 git bash here 클릭  

처음 시작하면 맨 끝에 (master) 이런게 없음  
git을 사용하기 위해 git init으로 .git 폴더 생성 (쉽게 말하면 git 생성자 클래스라할까..)  

이거 만들면서 git 다시 해봤는데 빈 폴더는 push를 할 수 없다.  
애초에 add가 안됨. 폴더 안에 파일이 1개라도 있어야함. 그래서 test2.txt를 넣었더니 git status에 test_folder가 보인다.  
