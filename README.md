# git 명령어

#### git add
- 기록할 파일 고르기 명령어 (staging area에 놓기)
- 명령어 : git add app.txt

#### git commit
- 고른 파일을 저장소에 저장 명령어
- 명령어 : git commit -m '메시지입력'
![image](https://github.com/wjdwodnr5452/git-study/assets/90361061/dd615ba5-3db3-45d4-9270-dca7fc3d353b)

#### git status
- staging area에 있는 파일 확인

#### git log
- 커밋한 로그 확인

#### git diff
- 소스 수정 전 후를 알려줌

#### git difftool
- 소스 수정 전 후를 에디터로 알려줌
![image](https://github.com/wjdwodnr5452/git-study/assets/90361061/89da5775-dfab-41c6-ac42-76fa6a3e9de7)
- ###### 커밋 아이디로 통해 수정 전 후를 알 수 있음 - git difftool 커밋 id
- ###### git diff, git difftool는 사용이 불편하기 때문에 에디터로 이용해서 보는게 좋음 (git graph)


# git 브랜치
- 새로운 기능을 개발 할 때 main 브랜치에 개발 하면 위험성이 있다. 그래서 브랜치를 통해 복사본을 만들어가 개발을 진행한다.
  ![image](https://github.com/wjdwodnr5452/git-study/assets/90361061/66744c50-56b6-4d69-9e6a-5a3ea39a3a69)

#### 브랜치 생성
- 명령어 : git branch 브랜치명

#### 브랜치 전환
- 명령어 : git switch 브랜치명

##### [참고] 각 브랜치에서 커밋한 그래프
![image](https://github.com/wjdwodnr5452/git-study/assets/90361061/a02a0e11-b05e-443f-b9f2-96a138f07222)

#### 브랜치 머지
- 개발이 완료되서 버그 없이 잘돌아가면 main 브랜치와 합치는 작업
- 명령어 : git merge 브랜치명
- 머지를 할시 성공적으로 머지가 되는 경우도 있지만 서로 같은 파일을 수정 하게 되면 충돌 날 수가 있다.

##### [참고] 브런치 머지
![image](https://github.com/wjdwodnr5452/git-study/assets/90361061/5a2099b7-1d82-4dcf-8755-253eb466e7c9)

##### [참고] 브런치 머지 충돌
![image](https://github.com/wjdwodnr5452/git-study/assets/90361061/e813d79f-7c29-44a6-871b-b0f5b76134f5)

##### 충돌날 경우 직접 소스를 고쳐야 함!

##### 브랜치 머지 방법

- 3 way merge (각 브랜치에 신규 commit이 있는 경우)
![image](https://github.com/wjdwodnr5452/git-study/assets/90361061/5a2099b7-1d82-4dcf-8755-253eb466e7c9)

- fast-forward merge (기준 브랜치에 신규 commit이 없는 경우)
  
  - [beafore merge]
    
   ![image](https://github.com/wjdwodnr5452/git-study/assets/90361061/21074470-7fab-46d4-b5c3-059e063ad3fc)

  - [fast-foward merge]
    
   ![image](https://github.com/wjdwodnr5452/git-study/assets/90361061/01ed555d-2283-4702-bd8f-4db469b3b4a9)


- git rebase & merge
  - rebase 쓰는 이유 : 간단하고 짧은 브랜치들은 rebase 쓰면 깔끌 해보임
  - rebase 단점 : conflict가 많이 남


- squash and merge
3 way merge를 하게 되면 로그에서 깔끔하게 안보임 그래서 squash and merge를 해서 로그 상 선이 안겹치게 하는 머지 방법
  























