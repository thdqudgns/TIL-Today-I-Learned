# DB SQL

### DBMS, DataBase Management System
- 데이터베이스 관리 시스템
- Oracle DB, MS-SQL, MySql, MongoDB, SQLite, CUBRID 등등

### 데이터베이스, Database, DB
- 데이터 저장소
- 체계적인 데이터를 저장하는 시스템
- 여러 종류의 클라이언트들이 공유하면서 사용할 목적으로 관리되는 데이터의 통합 정보 관리 시스템
- 데이터베이스 내부에 테이블(Table)들을 만들어서 데이터를 관리한다

### 내가 사용하는 오라클 DB 상황
- 버전: Oracle Database 11g Release 2
- 제품군: Express Edition (Standard Edition, Enterprise Edition, Standard One Edition도 존재)
- Express Edition(XE)에는 데이터베이스가 한 개만 존재한다
- SID(DB이름) : xe
- Standard Edition에도 DB가 한 개
- SID : orcl
- Enterprise Edition에는 DB가 여러 개

### 테이블, Table, TB
- DB 내에서 실제 데이터를 저장하고 관리하는 단위
- 표 형식으로 데이터를 관리한다
- 테이블은 소유자(Owner)를 가지고 있다
    > 소유자(Owner) - 해당 객체를 생성한 사용자 계정 (ex. scott)   
    > ex) scott.dept -> scott계정으로 생성한 dept 테이블
- 소유자는 자식이 생성한 테이블에 대한 모든 권한(privilege)을 가지고 있다
- DBA계정(시스템 계정, 관리자 계정)은 권한에 상관없이 소유권에 상관없이 모든 객체를 관리할 수 있다 -> 최대한 사용하지 않도록 한다
- 오라클DB의 기본 DBA계정 : SYS, SYSTEM (DBA, DataBase Administrator)

### SQL, Structured Query Language
- 구조적 질의 언어
- 자료의 검색(조회), 관리, DB객체 생성, 수정, 관리, 삭제 등을 수행하는 언어
- 주로 CRUD작업을 수행하는 명령어들이다 (Create, Read, Update, Delete)
- 스크립트 언어이다
	- 코드를 읽어서 곧바로 실행된다
	- 인터프리트 언어

### SQL의 용도에 따른 분류
#### 1. DML, Data Manipulation Langauge
- 데이터 조작어
- 테이블의 데이터를 조작(CRUD, 조회, 삽입, 변경, 삭제)하는 명령어
- 데이터를 처리할 때 사용하는 SQL
- **SELECT, INSERT, UPDATE, DELETE**

#### 2. DDL, Data Definition Language
- 데이터 정의어
- 데이터베이스의 구조를 정의, 조작하는 SQL
- **CREATE, ALTER, DROP**
- 조회(Read)에 해당하는 구문이 없다 -> 데이터사전을 SELECT하여 확인해야 한다
    > **데이터 사전, Data Dictionary, 자료 사전**   
    데이터베이스의 모든 정보를 기록해둔 특수한 테이블이다   
    SYS 계정이 소유자이다   
	DDL을 수행할 때마다 DBMS가 알아서 알맞는 정보를 데이터 사전에 반영한다   
	데이터베이스에 설정된 모든 정보들을 확인할 수 있다   

#### 3. DCL, Data Control Language
- 데이터 제어어
- 데이터베이스에 제한사항을 적용하거나 해제할 때 사용하는 SQL
- 보안성, 데이터의 무결성, 병행 작업, 수행 제어, 권한 등을 정의하는 SQL
- DBA가 데이터베이스를 관리하는 목적으로 사용된다
- 권한 관련 명령어 - **GRANT, REVOKE**
- 트랜잭션 관련 명령어 - **COMMIT, ROLLBACK**
- TCL, Transaction Control Language

### 오라클 11gR2 SQL 레퍼런스
[URL](https://docs.oracle.com/cd/E11882_01/server.112/e41084/toc.htm)

### SELECT 구문 - DML, DQL(Data Query Language)
- 테이블에 저장된 데이터를 조회할 때 사용하는 명령어
- 반드시 FROM절이 뒤에 따라 와야한다
    #### 구문 형식
    ```sql
        SELECT * FROM tablename;
        -> 테이블의 모든 컬럼을 이용하여 전체 데이터(모든 행)을 조회한다

        SELECT col1, col2, ... FROM tablename;
        -> 지정한 컬럼만 이용하여 전체 데이터를 조회한다
    ```
    #### FROM 절
    - 조회하려는 대상을 지정하는 절
    - 테이블, TABLE
    - 뷰, VIEW
    - 인라인뷰, Inline View (서브쿼리)
    #### SELECT 구문에서의 Alias, 별칭
    - 조회하려는 컬럼명, 테이블명 등의 이름에 별칭을 붙일 수 있다
    - 컬럼에 AS 키워드를 붙이고 별명을 붙이거나, 그냥 별칭을 바로 옆에 사용한다
    ```sql
        ex)	empno AS "사원번호"
        ex)	empno "사번"
    ```
    - 테이블명 옆에 별칭을 붙여 사용한다
    ```sql
        ex)	FROM emp "사원정보"
    ```
    - ""큰따옴표로 묶어서 되고 ""큰따옴표없이 사용해도되지만 숫자나 기호가 포함되면 ""로 묶어야 한다
    - 한글, 영어, 숫자 전부 사용 가능하다
    - 컬럼명과 테이블명을 단순화하거나 명확하게할 때 사용한다

### WHERE 절
- 조건절, 조건에 만족하는 데이터만(행) 조회되거나 처리되도록 설정한다
- SELECT, UPDATE, DELETE 구문에서 사용된다
- 형식
```sql
WHERE [조건절]
WHERE 컬럼명 연산자 조건값
    ex)	WHERE sal < 2000
    ex)	WHERE ename = 'SMITH'
```

### 연산자
- **비교(관계) 연산자**
```sql
	=	같다
	!=	같지 않다 ( <>  ^= )

	<	작다
	>	크다

	<=	작거나 같다
	>=	크거나 같다
```
- **논리 연산자**
	- AND	두 조건이 모두 만족할 때 TRUE
	- OR	두 조건 중 하나라도 만족할 때 TRUE
	- NOT	논리 부정
- **기타 연산자**
	- **BETWEEN a AND b** : a 와 b 사이의 데이터라면 TRUE (a, b 포함)
    ```sql
	ex)	WHERE deptno BETWEEN 10 AND 20
	ex)	WHERE sal BETWEEN 1000 AND 2000
	ex)	WHERE sal >= 1000 AND sal <= 2000
	ex)	WHERE (sal >= 1000) AND (sal <= 2000)
    ---
	부정문 : NOT BETWEEN a AND b
    ```
	- **IN ( list )** : list에 해당하는 값 중 하나라도 일치하면 TRUE
    ```sql
	ex)	deptno IN ( 10, 20 )
		(deptno = 10 OR deptno = 20)
    ---
	부정문 : NOT IN ( list )
    ```
	- **LIKE** : 지정된 형식의 문자열 포맷(서식)으로 일치하는 조건
    ```sql
	% : 여러 개의 문자, 또는 문자가 없는 경우
	_ : 단일 문자, 반드시 한 글자가 존재하는 경우
	ex)	ename LIKE 'B%' -> B로 시작하는 모든 문자
	ex)	ename LIKE '%B%' -> B를 포함하는 모든 문자
	ex)	ename LIKE '_B%' -> 두 번째 문자가 B인 모든 문자
	ex)	ename LIKE '%B' -> B로 끝나는 모든 문자
	ex)	SELECT * FROM board --게시판
		WHERE title LIKE '%검색어%'; --게시글 제목
    ---
	부정문 : NOT LIKE
    ```
	- **IS NULL** : 컬럼의 값이 NULL인지 검사하는 연산자
    ```sql
	ex)	WHERE mgr IS NULL

	** 테이블의 데이터 중에서 (null) 값은 데이터가 없음을 나타낸다
	** WHERE mgr = null 같은 형식의 조건식은 데이터가 존재하지 않는 공간(mgr)과 null값을 비교하는 구문이 된다
	** 데이터가 존재하지 않는 공간(행)은 아예 조회(검색) 대상에서 제외된다
    ---
	부정문 : IS NOT NULL
	ex)	comm IS NOT NULL
    ```

### DB 조회(탐색) 방법, Scan
#### 전체 탐색, Full Scan
- 테이블의 처음부터 끝까지 전부 확인하며 탐색하는 방법
- 시간이 오래걸린다
- DB의 성능을 높이려면 풀 스캔되는 상황을 줄여야한다
#### 인덱스 탐색, Index Scan
- 인덱스를 우선 확인하고 인덱스에 연결된 데이터(행을) 찾아가서 탐색하는 방법
- 인덱스에서 찾을 수 없는 데이터라면 풀스캔한다
- **인덱스, Index**
    - 테이블의 대표컬럼을 지정하여 테이블과 별개로 작성한 객체
    - 테이블의 데이터를 빠르게 찾을 수 있도록 도와준다





