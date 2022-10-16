# Git Stash
**stash** 뜻은 '넣어 두다'이다.

깃 공식 문서에 따르면 **Git Stash**를 다음과 같이 말하고 있다.
> Stash the changes in a dirty working directory awway

말 그대로 작업물의 수정 내용을 넣어둔다(커밋하지 않고)는 의미인 것 같다.

## 개요
깃 공식 문서에 따르면 `git stash`에 대해사 다음과 같이 설명하고 있다.
> Use `git stash` when you want to record the current state of the working directory and the index,
> but want to go back to a clean working directory. The command saves your local modifications away and reverts the workig directory to match the `HEAD` commit.

여기서는 `git stash`를 어떤 상황에서 왜 써야하는지를 명시하고 있다.
`git statsh`를 사용할 때는 현재 작업하고 있는 부분을 기록하며 수정 전의 작업물로 돌아갈 때 사용하라고 이야기하고 있다.

## 사용 예시
### 1. Pulling into a dirty tree
내가 깃을 통해 협업을 진행한다고 가정해보자.
예를들어 내가 작업하고 있는 브랜치는 `feature/login`이고 이 브랜치는 `develop`에서 나오게 되었다.
작업하던 중 다른 팀원의 작업 내용이 `develop`에 합쳐지게 되었고, 작업 내용이 내가 개발중인 로그인 부분에도 영향이 있는 것이다.
만약 내가 작업한 부분이 `develop`에서 변경된 작업과 충돌될 부분이 없다면 간단하게 `git pull`을 수행하면 된다.

하지만 내가 작업한 부분이 `develop`에서의 변경된 작업과 충돌되는 부분이 있다면 `git pull`을 한다고 해도 **conflict**가 발생하고 쉽게 병합되지 않을 것이다.
이런 경우에 **stash**를 이용하여 아래와 같이 수행하면 쉽게 해결할 수 있다.

``` powershell
$ git pull
 ...
file foobar not up to date, cannot merge.
$ git stash -m "my stash message..."
$ git pull
$ git stash pop
```

위의 흐름을 가볍게 살펴보자.
- `git pull`하는 과정에서 병합 실패!
- `git stash`를 통해서 `develop`과 충돌이 발생할 수 있는 부분을 임시 저장. (`-m "..."`: 스태시 메시지는 옵션)
- `git pull`를 통해 다시 최신 버전의 `develop`과 병합
- 병합 성공한 후, 임시 저장되어 있는 기존 작업내용 `git stash pop`을 통해 가져오기.

### 2. Interrupted workflow
이 경우는 내가 회사에서 일하면서 가장 많이 겪은 경우이다.
만약 내가 맡은 작업을 진행하던 중, **핫 픽스** 이슈가 들어오거나 **QA 검수 중 이슈** 또는 **앱 심사**와 같은 급히 처리해야할 일들이 발생한다면 작업중인 내용은 우선순위가 밀리게된다. 그냥 커밋 후, 다른 작업을 진행하면 되지만 커밋하기에는 내용이 정리되어 있지 않고 오류를 포함한 코드들이 있을 수 있기에 커밋하기가 꺼려진다.

이런 경우에도 **stash**를 이용하여 아래와 같이 수행하면 커밋하지 않고 처리할 수 있다.
``` powershell
$ git stash -m "Stash Login to resolve hotfix"
$ resolve hotfix...
$ git commit -m "Fix in a hurry"
$ git stash pop
```

위의 흐름을 가볍게 살펴보자
 - `git stash`를 통해서 기존 작업 내용을 임시저장하고 기존의 클린한 코드로 돌아가서 **핫 픽스**를 대응할 상태를 만든다.
 - **핫 픽스**를 대응 후, `git commit -m "Fix in a hurry"` 작업 내용을 커밋한다.
 - 이후에 다시 임시 저장되어 있던 기존 작업내용을 `git stash pop`을 통해 가져온다.

### 3. Testing partial commits

### 4. Saving unrelated changes for future use

### 5. Recovering stash entries that were cleared/droppped erroneously


<!-- 
## 개요

Stash는 작업하고 있던 내용을 커밋을 통해 남기지 않고 **임시**로 저장할 때 사용된다.

나같은 경우는 회사에서 업무 중 **핫픽스** 이슈가 들어온 경우 현재 작업이 완료된 상황이 아니라서 커밋을 남기기 어려워서 **Stash**를 이용해
임의로 저장 후, 핫 픽스 이슈를 해결하고 다시 돌아와서 **Stash**를 통해 저장된 내용을 다시 **Pop**해서 이전 작업을 이어간다.

항상 작업이 순차적으로 완료되면서 commit으로 작업을 마무리하며 진행하고 싶지만 현실은 그렇지 못하다.
위와 같이 다른 기능 개발 작업 중 핫픽스 이슈가 들어오거나, QA 검수 중 이슈가 발생하거나, 앱 심사 거절을 통해 급하게 처리해야할 일들이
생가보다 발생한다. 이때 필요한게 **Stash**이다.

### Git Stash 란
> 아직 마무리하지 않은 작업을 스택에 잠시 저장할 수 있도록 하는 명령어이다. 
> 이를 통해 아직 완료하지 않은 일을 commit 하지 않고 나중에 다시 꺼내와서 마무리 할 수 있다.

- git stash 명령어를 사용하면 워킹 디렉토리에서 수정한 파일들만 저장한다.
- stash란 아래에 해당하는 파일들을 보관해두는 장소이다.
 - `Modified`이면서 `Tracked` 상태인 파일
    - `Tracked` 상태인 파일을 수정한 경우


-->
[참고](https://gmlwjd9405.github.io/2018/05/18/git-stash.html)

[공식문서](https://git-scm.com/docs/git-stash)
