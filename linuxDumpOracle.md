# 리눅스 서버에서 오라클 데이터베이스 덤프 및 로컬 DB로 가져오기

## 1. 리눅스 서버에서 Oracle DB 덤프 생성

### 1-1. Docker 오라클 컨테이너 접속
```bash
# Docker Oracle 컨테이너에 접속
docker exec -it --user=oracle oracle18c bash

# 컨테이너 내에서 Oracle DB 접속
sqlplus
system/oracle
1-2. 디렉토리 생성 및 권한 부여
sql
복사
편집
-- 오라클 서버 내에서 덤프 파일을 저장할 디렉토리 생성
CREATE OR REPLACE DIRECTORY BLUE AS '/home/oracle';

-- 해당 디렉토리에 읽기 및 쓰기 권한 부여
GRANT READ, WRITE ON DIRECTORY BLUE TO blue;
1-3. 데이터 덤프 파일 생성
bash
복사
편집
# 현재 실행 중인 Docker 컨테이너 상태 확인
docker ps

# expdp 명령어를 사용하여 데이터 덤프 파일 생성
expdp blue/blue DIRECTORY=BLUE DUMPFILE=BLUE_FINISH.DMP LOGFILE=export.log
1-4. 생성된 덤프 파일 로컬로 복사
bash
복사
편집
# Docker 컨테이너에서 덤프 파일을 로컬 디렉토리로 복사
docker cp [컨테이너_ID]:/home/oracle/BLUE_FINISH.DMP /home/server2
2. 로컬 DB로 덤프 파일 가져오기
2-1. 로컬 디렉토리 생성 및 권한 부여
sql
복사
편집
-- 로컬 환경에서 덤프 파일을 저장할 디렉토리 생성
CREATE OR REPLACE DIRECTORY BLUE AS 'C:\tools';

-- 해당 디렉토리에 읽기 및 쓰기 권한 부여
GRANT READ, WRITE ON DIRECTORY BLUE TO blue;
요약
1단계: Docker 컨테이너에 접속하여 오라클 DB의 데이터를 덤프 파일로 생성.
2단계: Docker 컨테이너에서 생성된 덤프 파일을 로컬 환경으로 복사.
3단계: 로컬 DB에서 덤프 파일을 이용해 데이터 복원 작업 수행.
