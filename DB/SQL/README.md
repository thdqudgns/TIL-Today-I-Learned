# :pushpin: DB SQL

### :bulb: DBMS, DataBase Management System
- 데이터베이스 관리 시스템
- Oracle DB, MS-SQL, MySql, MongoDB, SQLite, CUBRID 등등

### :bulb: 데이터베이스, Database, DB
- 데이터 저장소
- 체계적인 데이터를 저장하는 시스템
- 여러 종류의 클라이언트들이 공유하면서 사용할 목적으로 관리되는 데이터의 통합 정보 관리 시스템
- 데이터베이스 내부에 테이블(Table)들을 만들어서 데이터를 관리한다

### :bulb: 내가 사용하는 오라클 DB 상황
- 버전: Oracle Database 11g Release 2
- 제품군: Express Edition (Standard Edition, Enterprise Edition, Standard One Edition도 존재)
- Express Edition(XE)에는 데이터베이스가 한 개만 존재한다
- SID(DB이름) : xe
- Standard Edition에도 DB가 한 개
- SID : orcl
- Enterprise Edition에는 DB가 여러 개

### :bulb: 테이블, Table, TB
- DB 내에서 실제 데이터를 저장하고 관리하는 단위
- 표 형식으로 데이터를 관리한다
- 테이블은 소유자(Owner)를 가지고 있다
    > 소유자(Owner) - 해당 객체를 생성한 사용자 계정 (ex. scott)   
    > ex) scott.dept -> scott계정으로 생성한 dept 테이블
- 소유자는 자식이 생성한 테이블에 대한 모든 권한(privilege)을 가지고 있다
- DBA계정(시스템 계정, 관리자 계정)은 권한에 상관없이 소유권에 상관없이 모든 객체를 관리할 수 있다 -> 최대한 사용하지 않도록 한다
- 오라클DB의 기본 DBA계정 : SYS, SYSTEM (DBA, DataBase Administrator)

### :bulb: SQL, Structured Query Language
- 구조적 질의 언어
- 자료의 검색(조회), 관리, DB객체 생성, 수정, 관리, 삭제 등을 수행하는 언어
- 주로 CRUD작업을 수행하는 명령어들이다 (Create, Read, Update, Delete)
- 스크립트 언어이다
	- 코드를 읽어서 곧바로 실행된다
	- [인터프리트](https://github.com/thdqudgns/TIL-Today-I-Learned/blob/main/Java/Java%EA%B0%9C%EB%85%90/%EA%B8%B0%EB%B3%B8%EA%B0%9C%EB%85%90.md#bulb-%EC%9D%B8%ED%84%B0%ED%94%84%EB%A6%AC%ED%84%B0-interpreter-interpret) 언어

### :bulb: SQL의 용도에 따른 분류
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

### :bulb: 오라클 11gR2 SQL 레퍼런스 : [URL](https://docs.oracle.com/cd/E11882_01/server.112/e41084/toc.htm)

### :bulb: SELECT 구문 - DML, DQL(Data Query Language)
- 테이블에 저장된 데이터를 조회할 때 사용하는 명령어
- **반드시 FROM절이 뒤에 따라 와야한다**
    - **구문 형식**
        ```sql
            SELECT * FROM tablename;
            -> 테이블의 모든 컬럼을 이용하여 전체 데이터(모든 행)을 조회한다

            SELECT col1, col2, ... FROM tablename;
            -> 지정한 컬럼만 이용하여 전체 데이터를 조회한다
        ```
    - **FROM 절**
        - 조회하려는 대상을 지정하는 절
        - 테이블, TABLE
        - 뷰, VIEW
        - 인라인뷰, Inline View (서브쿼리)
    - **SELECT 구문에서의 Alias, 별칭**
        - 조회하려는 컬럼명, 테이블명 등의 이름에 별칭을 붙일 수 있다
        - **컬럼**에 AS 키워드를 붙이고 별명을 붙이거나, 그냥 별칭을 바로 옆에 사용한다
        ```sql
            ex)	empno AS "사원번호"
            ex)	empno "사번"
        ```
        - **테이블명** 옆에 별칭을 붙여 사용한다
        ```sql
            ex)	FROM emp "사원정보"
        ```
        - ""큰따옴표로 묶어서 되고 ""큰따옴표없이 사용해도되지만 **숫자나 기호가 포함되면 ""로 묶어야 한다**
        - 한글, 영어, 숫자 전부 사용 가능하다
        - 컬럼명과 테이블명을 단순화하거나 명확하게할 때 사용한다

### :bulb: WHERE 절
- 조건절, 조건에 만족하는 데이터만(행) 조회되거나 처리되도록 설정한다
- **SELECT, UPDATE, DELETE** 구문에서 사용된다
- 형식
```sql
WHERE [조건절]
WHERE 컬럼명 연산자 조건값
    ex)	WHERE sal < 2000
    ex)	WHERE ename = 'SMITH'
```

### :bulb: 연산자
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

### :bulb: DB 조회(탐색) 방법, Scan
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

### :bulb: ORDER BY 절
- SELECT쿼리 결과를 **정렬**하기 위한 구문
- **WHERE절 다음에 온다**
- 기본적으로 오름차순 정렬을 한다
- ASC 기능 : 오름차순, ASCENDING의 약자, 생략가능
- DESC 기능 : 내림차순, DESCENDING의 약자
#### ORDER BY 구문 형식
- ORDER BY 기준컬럼명1, 기준컬럼명2, ...   
-> 기준컬럼마다 ASC 또는 DESC를 적용할 수 있다
#### NULL을 포함하는 컬럼에 대한 정렬
- 오름차순(ASC) 정렬일 경우 NULL이 마지막에 나온다
- 내림차순(DESC) 정렬일 경우 NULL이 처음에 나온다
- NULL 데이터의 정렬 순서를 변경하려면 NULLS 키워드를 사용한다
    - NULLS FIRST : NULL데이터를 처음에 보이도록 정렬한다
	- NULLS LAST : NULL데이터를 마지막에 보이도록 정렬한다
    ```sql
	ex)	ORDER BY comm DESC NULLS LAST
	ex)	ORDER BY comm ASC NULLS FIRST

	** DESC NULLS LAST가 주로 사용된다
    ```

### :bulb: DISTINCT 키워드
- 중복 데이터를 제거하는 키워드
- SELECT 키워드와 짝꿍으로 사용된다
    - SELECT ~ FROM 구문
    - SELECT DISTINCT ~ FROM 구문
- **조회된 데이터(행의 모든 컬럼)가 중복되었을 때 중복을 제거하고 한 개만 보여준다**
- 모든 컬럼의 값이 같아야 행을 하나로 줄여서 조회한다

### :bulb: 데이터 연결 연산자, ||
- 두 개의 데이터를 하나의 데이터(문자열)로 연결하여 표현하는 연산자
- 문자열 || 문자열
- 문자열 || 숫자
- 문자열 || 날짜

### :bulb: 오라클 내장 함수(Built-In Functions)
- 오라클 SQL Functions
- [레퍼런스 URL](https://docs.oracle.com/cd/E11882_01/server.112/e41084/functions.htm#SQLRF006)
- **[단일 행 함수](https://github.com/thdqudgns/TIL-Today-I-Learned/tree/main/DB/SQL#bulb-%EB%8B%A8%EC%9D%BC-%ED%96%89-%ED%95%A8%EC%88%98%EC%9D%98-%EC%A2%85%EB%A5%98), Single Row Functions**
    - 테이블을 조회할 때 조회되는 모든 행에 각각 함수의 결과가 반영된다
- **[그룹 함수](https://github.com/thdqudgns/TIL-Today-I-Learned/tree/main/DB/SQL#bulb-%EB%8B%A8%EC%9D%BC-%ED%96%89-%ED%95%A8%EC%88%98%EC%9D%98-%EC%A2%85%EB%A5%98), Group Functions**
    - 행들의 조회 결과를 하나의 결과로 도출하는 함수

### :bulb: DUAL 테이블
- SYS계정(관리자계정)이 소유하는 테이블
- 오라클에서 제공하는 **테스트 용 테이블**
- 조회 결과를 하나의 행으로 출력해주는 기능
- 연산의 결과, 가상 컬럼, 함수의 결과 등을 확인할 때 사용한다 -> SQL Functions를 테스트하기 위해 사용한다

### :bulb: 단일 행 함수의 종류
#### 숫자 함수, Numeric Function
- 숫자를 매개변수로 받아서 숫자를 변환
- Java의 Math클래스와 비슷한 역할을 한다
#### 문자 함수, Character Function
- 문자를 매개변수로 받아서 사용하는 함수
    1. 반환값이 문자인 함수
    2. 반환값이 숫자인 함수
#### 날짜 함수, Datetime Function
- 날짜/시간 데이터타입을 매개변수로 사용하는 함수
	> **sysdate, systimestamp**   
	현재 날짜/시간을 반환하는 함수   

	매개변수 없이 사용한다   
	()괄호도 사용하지 않는다   

	sysdate는 DATE타입이다   
	systimestamp는 TIMESTAMP타입이다
#### 변환 함수, Conversion Function
- 숫자, 문자, 날짜 사이의 형변환을 해주는 함수
- TO_CHAR : NUMBER 또는 DATE -> 원하는 서식의 VARCHAR2
- TO_NUMBER : NUMBER포맷의 VARCHAR2 -> NUMBER
- TO_DATE : DATE포맷의 VARCHAR2 -> DATE
```sql
		TO_CHAR(number)                 TO_DATE
	숫자	 ----------->	문자		---------->	날짜
	(NUMBER) <-----------	(VARCHAR2)	<----------	(DATE)
		TO_NUMBER                       TO_CHAR(date)
```
#### TO_CHAR(number)
- NUMBER -> VARCHAR2 변환
- 숫자 -> 문자
- TO_CHAR(number)
- TO_CHAR(number, 숫자서식문자)
    - **숫자 서식 문자**
        - 0 : 숫자가 들어갈 자리를 확보한다, 남은 자리를 0으로 LPAD한다
        - 9 : 숫자가 들어갈 자리를 확보한다, 남은 자리를 ' '(빈칸)으로 LPAD한다
        - , : 자릿수 구분 문자 추가
        - . : 소수점 구분 문자
        - $ : 통화기호 $ 추가
        - L : 세계 통화기호 추가 (설정된 통화를 따라감, 한국 : ￦)
#### TO_CHAR(datetime)
- DATETIME -> VARCHAR2
- 날짜시간 -> 문자
- TO_CHAR(datetime)
- TO_CHAR(datetime, 날짜서식문자)
    - **날짜형식 지정하는 문자**
        - SCC : 세기
        - YEAR, year, Year : 년도
        - YYYY, YY, YYY, Y : 숫자 년도, Y의 개수는 년도를 표현하는 자릿수를 나타냄
        - MM : 숫자 월
        - MONTH, MON : 문자 월
        - Q : 분기
        - DD : 월 기준 날짜
        - D : 주 기준 날짜(일요일부터 1, 토요일까지 7)
        - DDD : 년 기준 날짜
        - DAY : 요일
        - DY : 요일의 약자
        - HH : 12시간 표기법 시간
        - HH12 : 12시간 표기법 시간
        - HH24 : 24시간 표기법 시간
        - MI : 분
        - SS : 초
        - AM, PM, A.M., P.M. : 오전/오후
        - FF : 밀리초
            - SYSTIMESTAMP같은 밀리초를 가진 TIMESTAMP타입에서 사용 가능하다
    - **접미어 서식**
        - TH : 서수 (숫자+영문)	(ex. 31st)
        - SP : 기수 (영문)		(ex. THIRTY-ONE)
        - THSP, SPTH : 서수 (영문)	(ex. THIRTY-FIRST)
        - 접미어 앞에 오는 서식의 UPEER, LOWER, INITCAP이 적용된다
        > ex)   Ddsp -> Four   
                DDth -> 04TH   
                mmsp -> nine
#### 기타 단일행 함수
- **NVL**
    - 특정값이 NULL이면 원하는 값으로 변환하는 함수   
    ```sql
    NVL(비교데이터, 원하는 값)
    ```
- **NVL2**
    - 특정값이 NULL인지 판단하여 원하는 값으로 변환하는 함수   
    - NULL일 경우, NULL이 아닐 경우에 맞춰 원하는 값으로 변환할 수 있다   
    ```sql
    NVL2(비교데이터, NULL이 아닐 경우 반환값, NULL일 경우 반환값)
    ```
- **NULLIF**
    - 두 개의 같은 같은지 비교하고 같으면 NULL 반환   
    - 다르면 첫번째 매개변수를 반환   
    ```sql
    NULLIF(첫번째값, 두번째값)
    ```
- **DECODE**
    - 비교값을 여러 개 나열하고 비교 결과를 반환하는 함수
    - 자바의 if문, switch문과 비슷한 기능을 한다
    - 비교값과 기준값을 비교하여 반환할 값을 선택하는 함수
    ```sql
    	DECODE( 기준값,
		비교값1, 반환값1,
		비교값2, 반환값2,
		...
		default값 )

	-> 기준값과 같은 비교값을 찾으면 바로 다음에 오는 반환값을 반환한다
	-> 기준값과 같은 비교값이 없으면 default값을 반환한다
	-> default값은 생략가능하다
    ```
#### CASE 구문
- DECODE함수와 비슷한 동작을 하는 조건 구문
- CASE (-) WHEN THEN (-) END 로 구성된다
- WHEN THEN의 마지막에 ELSE 구문을 추가할 수 있다
```sql
	CASE 기준값
	  WHEN 비교값1 THEN 반환값1
	  WHEN 비교값2 THEN 반환값2
	  WHEN 비교값3 THEN 반환값3
	  ...
	  ELSE default반환값
	END

	-----------------------------

	CASE
	  WHEN 조건식1 THEN 반환값1
	  WHEN 조건식2 THEN 반환값2
	  WHEN 조건식3 THEN 반환값3
	  ...
	  ELSE default반환값
	END
```

### :bulb: 그룹 함수, Group Function
- 테이블의 특정 행들을 그룹화하여 **하나의 결과로 반환한다**
- 주로 테이블의 **통계 처리**를 수행한다
- 계산된 결과를 하나의 값으로 반환하게 된다
- 그룹마다 하나씩 여러 개의 값으로 반환하기도 한다
- COUNT : 데이터를 가지고있는 **행 수**를 반환, 데이터의 개수
    - NULL값을 무시한다
	- NULL데이터를 가진 컬럼을 조회하면 전체 행 수에 포함되지 않는다
	- count(*) vs count(1) 성능 이슈가 있지만 아무거나 써도된다
- SUM : 행들의 합계
- AVG : 행들의 평균
- MAX : 행들 중에서 가장 큰 값
- MIN : 행들 중에서 가장 작은 값
#### GROUP BY 절
- 데이터(행)들을 원하는 기준(컬럼의 조합)으로 **그룹화**할 때 사용하는 절
- 그룹함수 사용할 때 적용한다
- GROUP BY 절에 **컬럼을 명시**하고 **해당 컬럼의 값이 같은 행들을 같은 그룹으로 만들어준다**
    - SELECT절에서 그룹함수 이외에 다른 컬럼을 같이 조회하려면 GROUP BY절에 그룹함수를 제외한 모든 컬럼을 다 적어주어야 한다
```sql
GROUP BY colname1, colname2, colname3, ...
```
#### HAVING 절
- GROUP BY 절 다음에 오는 조건절
- **그룹함수를 이용한 조건을 설정**하고 싶을 때 사용한다 -> WHERE절에서는 그룹함수를 사용할 수 없다
- WHERE 대신 사용한다고 보면 된다.

### :bulb: SELECT 구문의 실행(수행) 순서
1. FROM절	- 조회하려는 대상 테이블을 설정한다
2. WHERE절	- 조회될 행을 선택하는 조건문 적용
3. GROUP BY절	- 그룹화 기준이 되는 컬럼 적용
4. HAVING절	- 그룹함수를 이용한 조건문 적용
5. SELECT절	- 조회할 컬럼을 지정한다 (DISTINCT 중복 제거 가능)
6. ORDER BY절	- 정렬
- **작성하는 순서**   
	SELECT   
	FROM   
	WHERE   
	GROUP BY   
	HAVING   
	ORDER BY
- 수행 순서에 따라 Alias(별칭)도 적용된다
	- SELECT절에서 지정한 Alias를 ORDER BY에서 사용할 수 **있다**
	- SELECT절에서 지정한 Alias를 WHERE절에서 사용할 수 **없다**

### :bulb: 조인, JOIN (08/02)