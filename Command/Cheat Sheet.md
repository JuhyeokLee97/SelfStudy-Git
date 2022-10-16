# Git 명령어 치팅 시트
> Git is the free and open source distributed version control system that's responsible for everything
> GitHub related thate happens locally on your computer. This cheat sheet features the most important
> and commonly used Git commands for easy reference.

## 용어 정리
- **메인 저장소**:
- **리모트**
- **origin**:
- **local**:

## SET UP
Configuring user information used across all local repositories

#### `명령어`가 들어가고 아래에서 설명과 사용 예시가 들어가면 좋을 것 같다.
[참고 자료](https://education.github.com/git-cheat-sheet-education.pdf)

#### 이름 설정
이름은 이후에 히스토리를 확인 할 때, 작업자를 확인 할 떄 구분이 필요함으로 본인을 명시할 수 있는 이름으로 한다.
``` cmd
git config --global user.name "[firstname lastname]"
```

#### 이메일 설정

``` cmd
git config --global user.email "[valid-email]"
```

#### 명령어 컬러 설정

``` cmd
git config --global color.ui auto
```

## SET UP & INIT
Configuring user information, initializing and cloning repositories

#### 깃 레파지토리 등록
현재 존재하는 디렉토리를 **깃 레파지토리**로 등록한다.

``` cmd
git init
```

#### 외부 레파지토리 복사
외부에 호스팅 되고 있는 레파지토리를 URL을 통해 로컬로 복사한다.

``` cmd
git clone [url]
```

## STAGE & SNAP SHOP
Working with snapshots and the Git staging area

#### 상태 확인
작업 중인 디렉토리에서 수정된 파일 목록을 확인할 수 있다.
``` cmd
git status
```

#### 깃에 파일 등록
다음 커밋에 등록될 수 있도록 해당 파일을 깃에 등록한다.(stage)

``` cmd
git add [file]
```

#### 깃 리셋 파일
> unstage a file while retaining the changes in working directory

``` cmd
git reset [file]
```

#### 
