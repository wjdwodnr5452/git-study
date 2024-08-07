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

#### 1. 3 way merge (각 브랜치에 신규 commit이 있는 경우)
  
![image](https://github.com/wjdwodnr5452/git-study/assets/90361061/5a2099b7-1d82-4dcf-8755-253eb466e7c9)

  - 3 way merge (그래프)
    
   ![image](https://github.com/wjdwodnr5452/git-study/assets/90361061/2d6585cf-7438-495b-9fea-20547ef6d197)



#### 2. fast-forward merge (기준 브랜치에 신규 commit이 없는 경우)
  - main 브랜치에 커밋이 없고 새로운 브랜치에 커밋이 있을 경 우 merge 할때 자동으로 fast-forward merge 가 됨
  
  - [beafore merge]
    
   ![image](https://github.com/wjdwodnr5452/git-study/assets/90361061/21074470-7fab-46d4-b5c3-059e063ad3fc)

  - [fast-foward merge]
    
   ![image](https://github.com/wjdwodnr5452/git-study/assets/90361061/01ed555d-2283-4702-bd8f-4db469b3b4a9)
  
  - fast-forward merge 그래프
    
   ![image](https://github.com/wjdwodnr5452/git-study/assets/90361061/6a0f4dc7-fa31-4ed5-bfd5-42dd8b27f6ff)



#### 3. git rebase & merge
  - 신규브랜치의 시작점을 main 브랜치 최근 commit으로 옮긴 다음 fast-forward-merge 하는 것
  - rebase 쓰는 이유 : 간단하고 짧은 브랜치들은 rebase 쓰면 깔끔 해보임
  - rebase 단점 : conflict가 많이 남
    
  ![image](https://github.com/wjdwodnr5452/git-study/assets/90361061/9682681e-c206-438d-b1ac-9dee4f529268)
  
  - git rebase & merge(그래프)
    - 새 브런치에 있는 커밋들이 main으로 옮겨짐
      
   ![image](https://github.com/wjdwodnr5452/git-study/assets/90361061/ab7b4c60-4c1f-4f33-9dd5-0339eca1e5c3)

   ```
    git switch 새브랜치이름
    git rebase main

    git switch main
    git merge 새브랜치이름
   ```


    

#### 4. squash and merge
  - 새브런치에서 변경된 소스들을 main 브런치로 내용을 붙여줌
  - 3 way merge를 하게 되면 로그에서 깔끔하게 안보임 그래서 squash and merge를 해서 로그 상 선이 안겹치게 하는 머지 방법
    
    ![image](https://github.com/wjdwodnr5452/git-study/assets/90361061/8f0eedc0-b205-41a1-8c69-80d1c9a1bd76)

  - squash and merge (그래프)
    - 변경된 소스 파일을 main에 붙여주고 main을 재 커밋
      
  ![image](https://github.com/wjdwodnr5452/git-study/assets/90361061/59d0dc75-449b-43ed-a8f5-13d4356f54d4)

   ```
    git switch main
    git merge --sqush 새브랜치이름
    git commit -m '메세지'
   ```

  

















