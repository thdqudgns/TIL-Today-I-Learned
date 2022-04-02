# :pushpin: DB 준비

### :bulb: 오라클 DB 설치하기 (윈도우)
- 오라클 Database 11g R2 Express Edition 사용
- [직접 URL](https://www.oracle.com/database/technologies/xe-prior-release-downloads.html)
- Oracle Database 11gR2 Express Edition for Windows x64의 Download 클릭   
![설치이미지](https://i.imgur.com/Fk3nq2h.png)
- 로그인 필요 (회원가입하세요!)
- 로그인하면 다운로드 시작
- 다운로드완료하면 설치 (DISK1 폴더의 setup 파일)
- 중요!! 설치하면서 비밀번호 1234 로 입력할 것!!

### :bulb: 오라클 SQL Developer 설치하기
- www.oracle.com 접속
- Resources 메뉴 - Downloads 클릭 - SQL Developer 링크 찾아서 클릭   
![찾기](https://imgur.com/3NCRcmU.png)
- [직접 URL](https://www.oracle.com/tools/downloads/sqldev-downloads.html)   
- Windows 64-bit with JDK 8 included 항목 다운로드   
![설치 이미지](https://imgur.com/vEbEzvH.png)
![다운로드](https://imgur.com/DxyPy5k.png)
- 압축 해제
- sqldeveloper.exe 실행

### :bulb: scott.sql 파일 위치
- C:\oraclexe\app\oracle\product\11.2.0\server\rdbms\admin
- (맥 OS - @$ORACLE_HOME/rdbms/admin/)

### :bulb: scott.sql 적용하기 (scott.sql : 테스트용 데이터 파일)
- 윈도우 콘솔창(cmd창) 열기
- sqlplus /nolog 입력
- conn system/1234;
- @ 만 타이핑 해둔 상태로 다음 진행
- 찾아둔 scott.sql 파일을 드래그&드랍, 엔터 -> 파일의 경로가 자동으로 입력 된다
- ALTER USER scott IDENTIFIED BY tiger; 입력 (본인은 예전에 변경해놔서 생략.)
- conn scott/tiger;
- show user; -> USER is "SCOTT" 으로 나오면 성공
- SELECT * FROM dept; -> 테스트용 부서 정보가 조회됨   
![콘솔창](https://imgur.com/OnrSQiA.png)

### :bulb: SQL Developer에서 데이터베이스 접속
- 파일 메뉴 - 새로만들기
- General - 접속선택
- 데이터베이스 접속 선택 - 확인
- 접속 이름 : 아무거나해도 됨 (ex. WEB)
- 사용자 이름 : scott
- 비밀번호 : tiger
- 비밀번호 저장 체크
- 테스트 -> "상태:성공" 뜨는 거 확인 - 접속
- 다음부터는 접속탭에서 "WEB" 더블클릭만 하면 접속됨 -> 우클릭 메뉴에도 있음   
![접속](https://i.imgur.com/rm8zUXZ.png)

### :bulb: 비밀번호 바꾸는 코드
- conn system/1234
- ALTER USER [계정명] IDENTIFIED BY [비밀번호];
```sql
    ex)	ALTER USER scott IDENTIFIED BY tiger;
```

### :bulb: LOCK 걸린 계정 풀기
- 비밀번호를 여러 번 틀리면 계정 LOCK걸림
- conn system/1234
- ALTER USER [계정명] ACCOUNT UNLOCK;
```sql
	ex) ALTER USER scott ACCOUNT UNLOCK;
```
![락 해제](https://imgur.com/MJVyK16.png)

### :bulb: 컴퓨터 부팅할 때 서비스 자동으로 켜지지않게 만들기
- win키 + r (실행) 열기
- services.msc 입력 (또는 시작 메뉴에서 "서비스" 입력)
- 윈도우 서비스 확인 설정창
    - OracleServiceXE
    - OracleXETNSListener
- 위 두 서비스 항목의 시작유형을 "수동"으로 변경 -> 컴퓨터 부팅할 때 자동으로 실행 안 됨
- 부팅 이후에 시작메뉴에서 "Start Database" 프로그램을 이용해 수동으로 직접 오라클을 켜야 사용 가능

### :bulb: 리스너 설정 파일 위치
- 작업 전에 .ora 파일들 백업 필수!
- C:\oraclexe\app\oracle\product\11.2.0\server\network\ADMIN
  > listener.ora   
	하단의 HOST 항목 확인   
	컴퓨터 호스트네임과 일치해야함 (변경)    
  > tnsnames.ora   
	상단의 HOST 항목 확인   
	컴퓨터 호스트네임과 일치해야함 (변경)   
- 호스트네임 확인은 cmd창(콘솔)에서 hostname 입력 ex) DESKTOP-7H5UIAM
- 호스트 항목 변경 후에는 오라클 서비스 종료, 재시작 필요

### :bulb: SqlDeveloper 글꼴 바꾸기
- 도구 - 환경설정 메뉴
- 코드 편집기 항목 - 글꼴   
![글꼴](https://i.imgur.com/aTkb0oi.png)

### :bulb: 오라클 클라이언트 툴(Tool)
- 오라클 데이터베이스 서버에 접속하여 DB에 대한 작업을 수행하는 도구 (프로그램)
1. SQL*Plus
	- Oracle 데이터베이스에느 제공하는 기본 Tool
	- 별도의 **설치가 필요없다**
	- CLI 환경 (Commnad Line Interface)
	- 콘솔창에서 sqlplus라고 입력하여 실행할 수 있다
	- 시작 메뉴에서 'Run SQL Command Line'을 실행한다
2. SQL*Developer
	- Oracle에서 제공하는 추가적인 클라이언트 Tool
	- 별도의 **설치가 필요하다**
	- GUI 환경 (Graphical User Interface)

### :bulb: AQUERY TOOL 사이트
- 데이터베이스 모델링(설계) 웹 툴
- [이동](https://aquerytool.com/)

### :bulb: 코멘트, Comment
- 테이블이나 컬럼에 설명을 적어주는 객체
- 작성된 주석(코멘트)는 자료사전을 이용하여 확인한다
#### 테이블 코멘트
	```sql
	COMMENT ON TABLE tablename IS '코멘트';
	```
#### 컬럼 코멘트
	```sql
	COMMENT ON COLUMN tablename.columnname IS '코멘트';
	```
#### 자료사전
- USER_TAB_COMMENTS -테이블코멘트
- USER_COL_COMMENTS -컬럼코멘트
#### 코멘트 삭제
- 삭제 코드는 별도로 존재하지 않으며, 코멘트 내용을 ''로 다시 작성하면 된다
