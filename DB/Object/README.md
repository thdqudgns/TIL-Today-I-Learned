# :pushpin: Object

### :bulb: 데이터베이스 객체(Object)
- [테이블]()
- 사용자
- 인덱스
- 뷰
- 시퀀스

### :bulb: 사용자
#### 관리자 계정
- DBA계정, DataBase Administrator
- 데이터베이스의 모든 객체들의 생성과 관리를 담당하는 계정
- 모든 권한, 모든 책임을 가지는 계정
- 오라클 DB의 기본 관리자 계정은 SYS, SYSTEM이 있다
	- SYS - 자료사전의 소유자(OWNER), DB생성 권한이 있음
	- SYSTEM - DB생성 권한이 없음
#### 일반 사용자 계정
- 데이터베이스의 객체들에 대한 조회, 갱신, 데이터 작업 등을 수행하는 일반 계정
- 소유자로써의 객체들을 다루는 게 일반적이다
- 추가 권한을 부여받으면 추가적으로 객체를 관리할 수도 있다
- 권한을 최소화하여 사용하는 것이 원칙이다
- 테스트용으로 제공되는 사용자 계정 : SCOTT, HR

### :bulb: 권한, Privilege
- DB객체에 대한 접근 또는 객체에 사용할 수 있는 SQL구문에 대한 제한을 부여하는 것
- 사용자 계정마다 권한을 부여해서 사용한다
- 보안성이 확보된다
- 시스템 권한, 객체 권한이 있다
#### 시스템 권한
- DB시스템 작업에 대한 권한
- 사용자계정 생성, 변경, 제거
- DB에 대한 접속 권한
- 객체(테이블) 생성, 변경, 제거 등등
- 대표적인 시스템 권한
	- CREATE SESSION	데이터베이스에 대한 접근(접속)
	- CREATE TABLE	테이블 생성 권한
	- ALTER TABLE	테이블 변경 권한
	- DROP TABLE	테이블 삭제 권한
	- CREATE(ALTER, DROP) USER	사용자 계정에 대한 작업 권한
#### 시스템 권한을 부여하는 구문
    ```sql
	GRANT 권한종류
	TO 사용자계정
	[ WITH ADMIN OPTION ]

	** WITH ADMIN OPTION
	 부여받은 권한을 다른 사용자 계정에 부여할 수 있는 능력이 생긴다

	 부여받은 권한에 대해서 관리자계정급으로 인정받는다
    ```
#### 시스템 권한을 회수하는 구문
- REVOKE 권한종류 FROM 사용자계정
#### 시스템 권한 관련 자료사전
- user_sys_privs	--일반사용자계정으로 부여한 시스템권한
- dba_sys_privs	--관리자계정으로 부여한 시스템권한
#### 롤, Role
- 권한들을 모아놓은 객체
- 권한 집합
- 사용자계정에 권한을 부여하는 것처럼 롤 객체에 권한을 부여한다
- 롤을 사용자에게 부여하면 롤에 적용된 모든 권한을 한번에 부여할 수 있다
#### 롤 관련 자료사전
- dba_role_privs	--관리자계정으로 생성한 롤
- user_role_privs	--사용자계정으로 생성한 롤
#### 객체 권한
- DB객체에 대한 작업(CRUD)을 수행할 수 있도록 설정하는 권한
- 객체의 소유자(OWNER)는 해당 객체에 대한 모든 작업 권한을 가지고 있다 -> 다른 소유자의 객체에 함부로 접근할 수 없다
#### 대표적인 객체 권한
- SELECT	객체에 대한 조회 권한
- INSERT	객체에 대한 삽입 권한
- UPDATE	객체에 대한 수정 권한
- DELETE	객체에 대한 삭제 권한
- RENAME	객체의 이름 변경 권한
#### 객체 권한 부여 구문
- GRANT 객체 권한
- ON 대상 객체
- TO 사용자계정;
#### 객체 권한 회수 구문
- REVOKE 객체 권한
- ON 대상 객체
- FROM 사용자계정;
#### 객체 권한 관련 자료사전
- dba_tab_privs	--관리자계정이 부여한 객체 권한
- user_tab_privs	--일반 사용자 계정이 부여한 객체 권한

### :bulb: 인덱스, Index
- 테이블의 검색속도 향상을 위한 데이터베이스 객체
- 테이블의 컬럼을 기준으로 적용한다
- 한번에 여러 개의 컬럼을 묶어서 적용할 수도 있다
- 테이블의 컬럼에 의존적이지만 테이블과는 독립적으로 생성되는 객체이다
> Unique Key(유일키), Primary Key(기본키) 제약 사항이 걸린 컬럼은 자동으로 인덱스를 생성한다

#### 인덱스 종류
- Non-Unique INDEX : 중복값을 허용 인덱스
	```sql
    CREATE INDEX 인덱스명 ON 테이블명 ( 컬럼 );
    ```
- Unique INDEX : 중복값을 허용하지 않는 인덱스
    ```sql
	CREATE UNIQUE INDEX 인덱스명 ON 테이블명 ( 컬럼 );
    ```
- Composite INDEX : 복합 컬럼 인덱스
    ```sql
	CREATE [UNIQUE] INDEX 인덱스명 ON 테이블명 ( 컬럼1, 컬럼2, ... );
    ```
	- 여러 개의 컬럼을 묶어서 인덱스로 지정한다
	- 지정한 컬럼을 순서대로 모두 이용하여 조회할 때 인덱스 스캔을 한다
#### 인덱스 재생성(재구성)
    ```sql
	ALTER INDEX 인덱스명 REBUILD;
    ```
#### 인덱스 삭제
    ```sql
	DROP INDEX 인덱스명;
    ```
#### 인덱스의 장점
- 테이블에 대한 전체 탐색(Full Scan)을 줄여준다
#### 인덱스의 단점
- 인덱스 객체를 생성하는데 시간이 필요하다
- 인덱스 객체를 생성하는데 별도의 공간이 필요하다
- 검색 기능의 성능은 향상시키지만 추가, 삭제, 수정에는 도움이 되지 않는다 -> 추가, 삭제, 수정이 발생하면 인덱스를 재구축해야한다
#### 인덱스 생성이 불필요한 경우
- 데이터가 적을 때 (수 천 건 이하)
- 해당 테이블에 SELECT보다 INSERT, UPDATE, DELETE가 빈번한 경우
- 인덱스탐색으로 조회되는 결과가 전체 행의 상당 부분을 차지할 경우(약 15%)
#### 인덱스 생성이 필요한 경우
- WHERE 구문에서 조건으로 특정 컬럼을 비교하는 연산을 많이 수행하는 경우
- JOIN구문에서 조인조건으로 사용되는 특정 컬럼이 존재할 때

### :bulb: 뷰, VIEW
- 목적 : 복잡한 쿼리를 간단한 이름으로 지정해서 사용하는 것
- VIEW객체에는 SELECT 쿼리를 저장하고 있다
- 뷰를 이용하여 조회 구문을 사용하면 서브쿼리처럼 동작한다
- 자료사전들은 대부분 VIEW이다
- 부가 효과: 조회 가능한 컬럼이나 조건을 제한할 수 있다
#### 뷰 생성 구문
```sql
	CREATE [OR REPLACE] VIEW viewname
	AS 서브쿼리
	[ WITH CHECK OPTION [CONSTRAINT 제약조건명] ]
	[ WITH READ ONLY ]
```
- **CREATE VIEW** : 뷰 생성 전용 구문
- **CREATE OR REPLACE VIEW** : 뷰를 생성하거나 서브쿼리를 변경하는 구문 -> 존재하는 뷰라면 쿼리수정, 없는 뷰라면 생성
- **WITH CHECK OPTION**
	- 설정된 제약조건에 맞는 데이터만 삽입, 수정 가능하도록 하는 옵션
    - CONSTRAINT가 없으면 서브쿼리의 WHERE에 만족하는 데이터만 가능
	- CONSTRAINT가 있으면 지정한 제약조건을 만족하는 데이터만 가능
- **WITH READ ONLY** : 조회 전용 뷰로 설정하는 옵션
#### 뷰관련 자료 사전
- user_views

### :bulb: 시퀀스, Sequence
- 연속된 숫자를 생성하는 객체
- 정수값으로 생성한다
- 테이블에서 사용할 유일한 숫자를 자동으로 생성할 때 쓰이는 객체 -> PRIMARY KEY의 값으로 사용한다
- 테이블마다 각각의 시퀀스를 생성하여 사용하게 된다
#### 시퀀스 생성 구문
    ```sql
	CREATE SEQUENCE 시퀀스명;
	 -> 1부터 1씩 증가하는 시퀀스를 생성한다

	CREATE SEQUENCE 시퀀스명
	[ START WITH n ]		--시작값 설정
	[ INCREMENT BY n ]		--증가 단위 설정
	[ MAXVALUE n | NOMAXVALUE ]	--최대값
	[ MINVALUE n | NOMINVALUE ]	--최소값
	[ CYCLE | NOCYCLE ]		--순환 구조 여부
	[ CACHE | NOCACHE ]		--미리 생성할 숫자의 개수(캐시)
    ```
#### 시퀀스 변경 구문 (옵션을 변경한다)
    ```sql
	ALTER SEQUENCE 시퀀스명
	[ INCREMENT BY n ]		--증가 단위 설정
	[ MAXVALUE n | NOMAXVALUE ]	--최대값
	[ MINVALUE n | NOMINVALUE ]	--최소값
	[ CYCLE | NOCYCLE ]		--순환 구조 여부
	[ CACHE | NOCACHE ]		--미리 생성할 숫자의 개수(캐시)

	** CREATE SEQUENCE에서 사용하는 옵션 중에서 START WITH를
	 제외하고 모두 사용 가능하다
    ```
#### 시퀀스 사용 방법
- 시퀀스명.nextval --다음 시퀀스 값
- 시퀀스명.currval --현재 시퀀스 값
#### 시퀀스 삭제
- DROP SEQUENCE 시퀀스명;
#### 시퀀스 관련 자료사전
- user_sequences
