# Code Reviewer Flow

## 1단계 레파지토리 받기 

작업할 프로젝트 Fork 를 누른다. 

// 내 로컬로 복사하는 과정

```git clone -b {본인_아이디} --single-branch https://github.com/{본인_아이디}/{저장소 아이디}```

// 새로운 기능 구현을 위한 브랜치 생성

```git checkout -b step1```


## 2단계 Pull Request/리뷰 요청

// 변경된 파일 확인
```git status ```

// 변경된 전체파일을 한번에 반영 가능, 나같은경우는 commit 할 파일만 따로 함
```git add -A (또는 .) ```

// 커밋
```git commit -m "메시지"```

// 원격브랜치로 보냄
```git push origin 브랜치 이름```

pull Request 요청을 하고 리뷰요청을한다.




## 3단계 미션이 완료하여 다음 단계로 넘어가야할 때 

```git checkout mkkim90 (본인_아이디)```

```git branch -D step1 (작업완료한 브랜치인 경우 삭제)```


// 합(merge)한 원격 저장소와 동기화하기 위해 원격 저장소 추가

```git remote add upstream https://github.com/next-step/java-racingcar.git```

// 저장소 추가한 후 목록 확인

```git remote -v ```


// 저장소에서 자기 브랜치 가져오기 (또는 갱신)

```git fetch upstream mkkim(본인아이디)```

```git branch -a``` 를 통해 확인 ( remotes/upstream/mkkim90와 같은 브랜치 확인


// 원격 저장소 브랜치와 동기화하기

```git rebase upstream/mkkim90```

// 새로운 미션을 진행하기 위한 브랜치 생성

```git checkout -b step2 (다음 단계 브랜치 이름)```



## 충돌을 해결하려면 어떻게 해야 하나요?

rebase 안하고 브랜치 생성하면 충돌이 일어날 수 있음 그럴때 해결 방법으로 

```
git checkout mkkim90
git reset --hard upstream/mkkim90
git checkout 기능_브랜치(예: git checkout step2)
git merge 본인_아이디(예: git merge javajigi)
```
