# :pushpin: 제약사항

### :bulb: 제약사항, Constraint
- 테이블에 부적절한 값이 입력되는 것을 방지하는 용도로 적용하는 필터(조건)
- 데이터 무결성을 유지한다
> **데이터 무결성**   
프로그램이 생명 주기(시작, 동작, 종료)를 거치며 데이터가 정확하고 일관성있는 값을 유지하고 그 값이 보장되는 성격

### :bulb: 테이블에 제약사항을 지정하는 방식
1. CREATE TABLE 구문에 컬럼과 함께 지정한다
2. 이미 생성된 테이블에 ALTER TABLE 구문을 이용하여 추가, 반영한다
> DROP CONSTRAINT 구문을 이용하연 제약사항만 제거할 수 있다

### :bulb: 제약사항의 종류
#### NOT NULL
- 컬럼의 데이터로 NULL을 허용하지 않음
- NULL값을 입력할 수 없다
- 컬럼의 데이터타입과 함께 부여되는 제약사항
- 데이터타입을 변하는 구문으로 추가/변경할 수 있다
#### UNIQUE
- 컬럼에 중복데이터를 허용하지 않는다
- 데이터의 유일성을 확보하는 제약조건
- UNIQUE 설정된 컬럼을 테이블의 UNIQUE KEY라고 부른다 (유일키, UK)
- UNIQUE KEY는 자동으로 인덱스를 생성한다
#### CHECK
- 컬럼에 들어갈 수 있는 데이터의 범위(조건)를 지정하는 제약사항
- WHERE절의 조건문을 제약조건으로 적용한다 (SEARCH_CONDITION으로 적용된다)
- NOT NULL제약조건 - IS NOT NULL조건을 사용하는 CHECK제약사항
#### DEFAULT
- 데이터를 입력하지 않고 INSERT할 때 들어갈 기본값을 지정하는 제약사항
- 제약사항 항목으로 추가되지 않고, 컬럼의 정보로 추가된다
    - user_constrains에서 확인되지 않는다
	- user_tab_columns에서 확인해야된다 (사용자 테이블 컬럼 정보 자료사전)
#### PRIMARY KEY, PK
- 기본키, 주키
- 테이블을 대표하는 컬럼에 부여하는 키 제약사항
- NOT NULL, UNIQUE제약사항이 자동으로 부여된다
- NOT NULL, UNIQUE 라는 별도의 항목이 추가되지는 않는다 (PRIMARY KEY 자체가 두 제약사항의 특성을 가지고 있다)
- PRIMARY KEY의 UNIQUE속성이 있어 인덱스가 자동으로 생성된다
- 외래키(FK)들이 참조할 수 있는 자격이 부여된다

#### FOREIGN KEY, FK
- 외래키, 보조키, 참조키
- 기본키(PK)를 참조하는 컬럼
- 참조하고 있는 컬럼(기본키)과 데이터타입이 일치해야한다
> **ON DELETE CASCADE 설정**   
참조하고 있는 PK값이 삭제되면 FK를 가진 행도 같이 삭제되도록 설정한다

> **ON DELETE SET NULL 설정**   
참조하고 있는 PK값이 삭제되면 FK의 값을 NULL로 바꾸도록 설정한다

### :bulb: 기본키 지정 방법
#### 방법 1 : 컬럼레벨로 제약조건 이름없이 지정하기
    ```sql
	CREATE TABLE tablename (
	  colname1 type1 PRIMARY KEY,
	  colname2 type2
	);
    ```
#### 방법 2 : 컬럼레벨로 제약조건의 이름을 명시하며 지정하기
    ```sql
	CREATE TABLE tablename (
	  colname1 type1 CONSTRAINT cons_name PRIMARY KEY,
	  colname2 type2
	);
    ```
#### 방법 3 : 테이블레벨로 제약조건 지정하기 (이름X)
    ```sql
	CREATE TABLE tablename (
	  colname1 type1,
	  colname2 type2,
	  PRIMARY KEY ( colname1 )
	);
    ```
#### 방법 4 : 테이블레벨로 제약조건 지정하기 (이름O)
    ```sql
	CREATE TABLE tablename (
	  colname1 type1,
	  colname2 type2,
	  CONSTRAINT cons_name PRIMARY KEY ( colname1 )
	);
    ```

### :bulb: 외래키 지정 방법
#### 방법1 : 테이블 레벨로 제약조건을 이름없이 지정하기
    ```sql
	CREATE TABLE tablename (
	  colname1 type1,
	  colname2 type2,
	  FOREIGN KEY ( colname1 )
	    REFERENCES r_tablename ( r_colname )
	);
    ```
#### 방법2 : 테이블 레벨로 제약조건의 이름을 설정하여 지정하기
    ```sql
	CREATE TABLE tablename (
	  colname1 type1,
	  colname2 type2,
	  CONSTRAINT cons_name
	    FOREIGN KEY ( colname1 )
	    REFERENCES r_tablename ( r_colname )
	);
    ```
#### 외래키의 추가 옵션
- 외래키 설정 코드의 마지막에 추가로 적용할 수 있다
> **ON DELETE CASCADE**   
참조 대상인 PK의 데이터를 삭제하면 FK키의 행(row)도 같이 삭제된다

> **ON DELETE SET NULL**   
참조 대상인 PK의 데이터를 삭제하면 FK키의 컬럼 값이 NULL로 바뀐다

### :bulb: 식별 관계
- FK가 PK역할을 동시에 수행하는 경우
- PK-FK가 중복값을 가지기 못하도록 추가적인 처리가 필요한 경우가 많다
    ```sql
	ex)	상품TB			주문TB

		> 상품번호PK	    > 상품번호PK-FK
		> 상품이름		> 구매한사람PK


		10001			10001
		Apple			Alice

		10002			10001
		Banana			Bob

		10003
		Cherry
    ```

### :bulb: 비식별 관계
- FK와 PK가 서로 직접적인 연관이 없는 경우
- FK와는 별도로 컬럼을 추가하여 PK로 지정한다
    ```sql
	ex)	상품TB			주문TB

	                            > 주문번호PK
		> 상품번호PK        > 상품번호FK
		> 상품이름          > 구매한사람


					    1 (주문번호PK)
		10001			10001 (상품번호FK)
		Apple			Alice

					    2 (주문번호PK)
		10002			10001 (상품번호FK)
		Banana			Bob

		10003
		Cherry
    ```