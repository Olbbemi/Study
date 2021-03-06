#3장 아키텍처
---

Mysql Server: Mysql 엔진 + 스토리지 엔진

###### Mysql 엔진
1. 클라이언트의 접속 및 쿼리 요청 처리하는 커넥션 핸들러와 SQL 파서
2. 최적화된 실행을 위한 옵티마이저

###### 스토리지 엔진 
1. 최적화 및 분석된 쿼리문을 통해 데이터를 디스크에 저장 및 로드하는 역할
2. MYSQL 서버에서 Mysql 엔진은 하나이지만 스토리지 엔진은 동시에 여러개 사용할 수 있음

###### 핸들러 API
1. Mysql 쿼리 실행기에서 읽기 또는 쓰기 데이터를 스토리지 엔진에 요청하는데 사용하는 API
2. dfs

###### 포그라운드 스레드
1. Mysql 서버에 접속된 유저 수만큼 존재
2. 각 클라이언트가 요청하는 쿼리 처리
3. 해당 쿼리 작업을 완료하면 Thread Pool 되돌아 감(만약 스레드 풀에 일정 개수 이상의 스레드가 존재하는 경우 스레드 파괴)
	- thread_cache_size 파라미터 참조
4. MyISAM 엔진은 디스크 I/O 작업까지 포그라운드에서 처리
5. InnoDB 엔진은 데이터 버퍼 및 캐시에 데이터가 있으면 포그라운드에서 처리, 없다면 백그라운드 스레드에서 처리

###### 백그라운드 스레드(InnoDB 엔진에 해당)
1. 인서트버퍼 병합
2. 로그를 디스크로 저장
3. InnoDB 버퍼 풀 디스트로 저장
4. 데드락 모니터링
	- 쓰기 스레드 개수 조정 파라미터: Innodb_write_io_threads, 읽기 스레드 개수 조정 파라미터: Innodb_read_io_threads

###### 글로벌 메모리
1. MySQL 서버가 실행되면 무조건 OS로 부터 할당
2. 스레드 수에 상관없이 하나의 메모리 공간에 할당되며 모든 스레드에 공유

###### 로컬 메모리
1. 포그라운드 스레드가 쿼리를 처리하는데 사용하는 메모리 영역으로 필요한 순간에만 할당
	- 소트 및 조인 버퍼

###### 쿼리 실행 구조(p.110)
- 파서

- 전처리기

- 옵티마이저

- 실행 엔진

- 핸들러(스토리지 엔진)