다음은 Git과 GitHub에서 자주 사용되는 명령어들을 Markdown 형식으로 정리한 것입니다.


# Git 및 GitHub 명령어 정리

## 1. 기본 Git 명령어

### Git 설정 관련

```bash
git config --global user.name "Your Name"    # 사용자 이름 설정
git config --global user.email "your_email@example.com"    # 사용자 이메일 설정
git config --global core.editor "code --wait"  # 기본 텍스트 에디터 설정 (예: VSCode)
git config --list   # 현재 설정된 Git 정보 확인
```

### 리포지토리 초기화 및 상태 확인

```bash
git init        # 새로운 Git 리포지토리 생성
git clone <URL>    # 원격 리포지토리 복제
git status     # 작업 디렉토리 상태 확인
git log        # 커밋 로그 확인
git show <commit>    # 특정 커밋의 변경 사항 보기
```

### 스테이징 및 커밋

```bash
git add <파일명>    # 특정 파일을 스테이징
git add .        # 현재 디렉토리의 모든 변경 사항을 스테이징
git commit -m "커밋 메시지"    # 스테이징된 파일 커밋
git commit --amend -m "수정된 메시지"    # 마지막 커밋 메시지 수정
git diff        # 변경 사항 확인 (스테이지되지 않은 파일)
git diff --staged    # 스테이지된 변경 사항 확인
```

### 브랜치 관련 명령어

```bash
git branch        # 브랜치 목록 확인
git branch <브랜치명>    # 새 브랜치 생성
git checkout <브랜치명>    # 다른 브랜치로 전환
git checkout -b <브랜치명>    # 브랜치를 만들고 바로 전환
git merge <브랜치명>    # 특정 브랜치를 현재 브랜치로 병합
git branch -d <브랜치명>    # 브랜치 삭제
git branch -D <브랜치명>    # 강제 브랜치 삭제
```

### 원격 저장소 관련 명령어

```bash
git remote add origin <URL>    # 원격 리포지토리 추가
git remote -v    # 설정된 원격 저장소 확인
git push origin <브랜치명>    # 변경 사항을 원격 저장소에 푸시
git pull origin <브랜치명>    # 원격 저장소로부터 변경 사항 가져오기
git fetch        # 원격 저장소의 최신 커밋 가져오기
```

### 원격 저장소와의 동기화

```bash
git push        # 현재 브랜치를 원격 저장소에 푸시
git pull        # 원격 저장소의 최신 상태를 가져와 병합
git push origin --delete <브랜치명>    # 원격 저장소의 브랜치 삭제
```

### 태그 관련 명령어

```bash
git tag <태그명>                      # 태그 생성
git tag -a <태그명> -m "태그 설명"    # 주석이 달린 태그 생성
git show <태그명>                     # 특정 태그의 정보 보기
git push origin <태그명>              # 원격 저장소에 태그 푸시
git push origin --tags                # 모든 태그를 원격 저장소에 푸시
```

### 기타 유용한 명령어

```bash
git stash                       # 변경 사항 임시 저장
git stash list                  # 저장된 stash 목록 보기
git stash apply                 # 가장 최근 stash 적용
git stash drop                  # 가장 최근 stash 삭제
git rebase <브랜치명>           # 브랜치 재정렬
git reset --hard <커밋 해시>    # 특정 커밋 상태로 강제 되돌림
```

## 2. GitHub 관련 명령어

### GitHub에서 리포지토리 생성 및 관리

1. GitHub 웹사이트에서 리포지토리 생성
2. 로컬 Git 프로젝트에서 다음 명령어 실행:
```bash
git remote add origin <GitHub_저장소_URL>    # 원격 저장소 추가
git push -u origin master                    # 원격 저장소에 처음으로 푸시
```

### GitHub에서 포크된 프로젝트에 기여하기

```bash
git clone <포크된_저장소_URL>                  # 포크된 리포지토리 복제
git checkout -b <새로운_기능_브랜치>           # 새 브랜치 생성
git add . && git commit -m "변경 사항 커밋"    # 변경 사항 커밋
git push origin <새로운_기능_브랜치>           # 새 브랜치를 원격 저장소에 푸시
```
---

### GitHub Pull Request (PR) 보내기

1. GitHub에서 푸시된 브랜치로 이동
2. "New Pull Request" 버튼 클릭
3. PR 생성 후 리뷰 요청

### 원본 리포지토리와 동기화하기

```bash
git remote add upstream <원본_저장소_URL>    # 원본 리포지토리 추가
git fetch upstream                           # 원본 저장소로부터 최신 변경 사항 가져오기
git merge upstream/master                    # 변경 사항 병합
```

## 3. Git Reset 및 Revert 관련 명령어

### Git Reset

```bash
git reset <파일명>    # 특정 파일을 스테이징에서 제거
git reset --soft <커밋 해시>    # 커밋을 취소하되, 변경 사항은 유지
git reset --mixed <커밋 해시>    # 커밋 및 스테이징 취소, 파일은 작업 디렉토리에 남김
git reset --hard <커밋 해시>    # 커밋, 스테이징, 작업 디렉토리까지 모두 초기화
```

### Git Revert

```bash
git revert <커밋 해시>    # 이전 커밋을 되돌리는 새로운 커밋 생성
```

### Git Clean (비추적 파일 삭제)

```bash
git clean -f    # 추적되지 않은 파일 삭제
git clean -fd   # 추적되지 않은 파일 및 폴더 삭제
git clean -n    # 삭제될 파일 목록 미리 보기
```

## 4. Git Squash (커밋 합치기)

### 기본적인 Squash 명령어

```bash
git rebase -i HEAD~<n>    # 마지막 n개의 커밋을 대상으로 상호작용형 리베이스 시작
git rebase --continue    # 충돌 해결 후 리베이스 계속 진행
git rebase --abort    # 리베이스 중단 및 원래 상태로 돌아가기
```

- rebase 중 `pick`을 `squash`로 변경하여 커밋을 합칠 수 있습니다.

## 5. Git Log 및 커밋 기록 관리

### 커밋 기록 보기

```bash
git log        # 기본 로그 보기
git log --oneline    # 한 줄로 요약된 로그 보기
git log --graph    # 그래프 형태로 로그 보기
git log --stat    # 커밋에 포함된 변경 파일과 함께 로그 보기
git log -p    # 각 커밋의 구체적인 변경 사항도 함께 보기
```

### 특정 파일의 히스토리 보기

```bash
git log -- <파일명>    # 특정 파일의 변경 기록 보기
git blame <파일명>    # 각 줄이 마지막으로 변경된 커밋과 작성자 보기
```

### 커밋 메시지 변경

```bash
git commit --amend    # 마지막 커밋 메시지 수정
```

## 6. Gitignore

- `.gitignore` 파일에 제외하고 싶은 파일이나 폴더를 작성하여 Git이 추적하지 않도록 설정할 수 있습니다.
  
예시:
```
# 임시 파일
*.log
*.tmp

# 특정 디렉토리 제외
node_modules/
```
