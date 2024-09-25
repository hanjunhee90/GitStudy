# Git&Github 명령어
---
1. 기본 Git 명령어

### 설정 관련

```bash
    git config --global user.name "이름"      # 사용자 이름설정
    git config --gloval user.email "이메일"   # 사용자 이메일(깃허브 계정)
    git config --list
```
### 레포지토리 초기화 및 상태 확인
```bash
    git init        # 상태확인
    git clone<URL>  # 원격 레포지토리 복제
    git status      # 작업 디렉토리 상태 확인
    git log         # 커밋 로그 확인
```
### 스테이징 및 커밋
```bash
    git add <파일명>      # 특정파일 스테이징
    git add .             # 현재 디렉토리의 모든 변경 사항을 스테이징
    git commit -m "커밋 메세지"  # 스테이징된 파일 커밋
    git diff                    # 변경 사항 확인(스테이징되지 않은 파일)
    git diff --staged           # 스테이지된 변경 사항 확인
```
### 원격 저장소 관련
```bash
    git remote add origin <URL>   # 원격 레포지토리 추가
    git remote -v                 # 설정된 원격 저장소 확인
    git remote remove origin      # 설정된 원격 저장소 제거
    git push origin main          # 변경 사항을 원격 저장소에 올리기(main은 브렌치명)
    git pull origin main          # 원격 저장소로 부터 변경 사항 가져오기
    git fetch                     # 원격 저장소의 최신 커밋장보 가져오기
```