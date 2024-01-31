
GitHub 계정을 새로 만든 후, 로컬 Git에서 push 했을 때 에러 발생

<에러 메세지>
remote: Invalid username or password.
fatal: Authentication failed for 'https://github.com/jjisabi/JavaScript-Mini-Project.git/'

-> GitHub계정 정보가 바뀌어 git과 github간의 계정 정보가 맞지 않는다는 생각이 들어 해결방법 검색

<해결>
1. 계정 정보 확인
git config user.name
git config user.email 
-> user name과 email이 다른 것을 가리키고 있음 확인

2. 로컬 Git의 이메일과 사용자 이름 새로 설정
git config --global user.name 사용자 이름
git config --global user.email 사용자 이메일


GitHub에서는 커밋에 기록된 이메일 정보를 보고, GitHub 사용자를 찾아 커밋 작성자로 자동으로 연결해준다. 따라서 github 계정 변경 시 git도 변경 필요