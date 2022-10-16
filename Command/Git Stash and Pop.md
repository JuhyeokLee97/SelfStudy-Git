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



[참고](https://gmlwjd9405.github.io/2018/05/18/git-stash.html)