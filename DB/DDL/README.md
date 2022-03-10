# :pushpin: DDL

### :bulb: DDL, Data Definition Language, 데이터 정의어
- **DB객체(테이블, 뷰, 인덱스, 사용자계정 등등)를 생성, 변경, 삭제하는 SQL**
- **DB구조(테이블 구조)에 대한 관리 작업**을 수행한다
- DDL구문의 결과는 자료사전(Data Dictionary)에 반영된다
- 구문 종류
	- CREATE    생성
	- ALTER     변경
	- DROP      삭제

### :bulb: 테이블, Table, TB
- 데이터베이스에서 데이터를 저장하는 단위
- 행(row, record), 열(column, col, 컬럼)으로 구성된 객체
- 서로 연관있는 데이터를 하나의 테이블에 모아 구성한다
- 테이블들 여러 개 생성하여 사용한다
- 테이블끼리는 관계(Relation)를 맺어 연관성을 확보한다 ( PK - FK )
	> ** 개체, Entity == 테이블, Table   
	** 관계, Relation == 테이블 간의 연관성   
	** ER, Entity - Relation, 개체-관계   
	테이블들이 서로 연관관계를 맺고있는 형태   
	** RDB, Relation DataBase   
	관계형 데이터베이스   
	테이블들이 관계를 형성하면서 데이터베이스가 되는 형식

### :bulb: CREATE TABLE - 테이블 생성 SQL
- 테이블을 만들 때 컬럼을 지정해주어야한다
- 컬럼마다 컬럼의 이름, 자료형을 필수로 지정한다
- 기본 구문 형식
    ```sql
	CREATE TABLE 테이블명 (
	  컬럼명1 자료형1,
	  컬럼명2 자료형2,
	  컬럼명3 자료형3,
	  ...

	);

	-- SELECT조회결과로 테이블을 생성한다
	CREATE TABLE 테이블명
	AS
	SELECT구문;
    ```

### :bulb: ALTER TABLE - 테이블 변경
- 테이블의 구조(스키마, Schema)를 변경하기 위한 SQL 구문
- 테이블을 지정하고 어떤 변경사항을 적용할 것인지 추가 구문으로 작성한다
- 추가 구문은 목적에 따라 키워드 달라진다
	- ADD	    - 추가 사항 적용
	- MODIFY	- 변경 사항 적용
	- DROP	    - 제거(삭제) 사항 적용
#### ALTER TABLE tablename ADD ( 컬럼명 데이터타입 );
- 새로운 컬럼을 추가한다
- 추가된 컬럼은 마지막 컬럼으로 들어간다
#### ALTER TABLE tablename MODIFY ( 컬럼명 데이터타입 );
- 기존 컬럼의 데이터터타입을 변경한다
- 크기만 변경할 수도 있다
- 데이터타입과 함께 크기도 아예 변경할 수 있다
	> ** 컬럼에 데이터가 존재하면 동작이 달라진다   
	데이터 존재하면 데이터타입을 변경할 수 없다   
	데이터가 존재해도 크기는 가장 큰 값보다 크게 변경할 수는 있다

	> CHAR와 VARCHAR2는 데이터가 존재해도 서로 변경할 수 있다
#### ALTER TABLE tablename DROP COLUMN 컬럼명;
- 컬럼을 삭제한다
- 컬럼의 데이터도 전부 삭제된다
#### ALTER TABLE tablename SET UNUSED ( 컬럼명 );
- 컬럼을 비활성화한다
- 컬럼과 그 데이터들을 물리적으로 삭제하지는 않지만 컬럼을 사용할 수 없게 만든다

  > 테이블의 컬럼을 삭제하면 해당 테이블에 락(LOCK)이 걸린다 (LOCK : 다른 사용자의 접근을 막고 작업하는 것)

  > 테이블락 때문에 전체적인 시스템에 영향을 주거나 성능저하가 발생한다

  > 서비스 중인 DB에 DROP을 함부로 수행하지 말아야한다   
#### ALTER TABLE tablename DROP UNUSED COLUMNS;
- 비활성화해둔 컬럼을 물리적으로 삭제한다
#### ALTER TABLE tablename RENAME TO new_tablename;
- 테이블의 이름을 변경한다
#### ALTER TABLE tablename RENAME COLUMN old_columnname TO new_columnname;
- 컬럼의 이름을 변경한다
#### ALTER TABLE - 테이블의 제약조건 다루기
- ALTER TABLE tablename MODIFY 컬럼명 [데이터타입] 제약조건
    - 컬럼의 정보를 변경하며 제약사항을 반영한다
	- NOT NULL, DEFAULT 제약사항을 부여할 때 사용한다
- ALTER TABLE tablename ADD CONSTRAINT cons_name 제약조건설정
	- 테이블에 제약조건을 추가한다
- ALTER TABLE tablename DROP CONSTRAINT cons_name
	- 테이블에 제약조건을 제거한다

### :bulb: 테이블 삭제
- DELETE tablename;
    - DML
	- 테이블의 데이터(내용물)만 삭제한다
	- 지우고 난 후의 용량은 줄어들지 않는다
    - 트랜잭션에 포함된다
- TRUNCATE TABLE tablename;
	- DDL
	- 테이블의 데이터(내용물)만 삭제한다
	- 테이블의 구조를 유지한다
	- 지우고 난 후의 용량이 줄어든다
	- 트랜잭션을 종료시킨다(Auto Commit)
- DROP TABLE tablename;
	- DDL
	- 테이블의 스키마(구조)까지 포함하여 삭제한다
	- 테이블 자체가 삭제된다
