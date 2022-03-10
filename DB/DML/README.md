# :pushpin: DML

### :bulb: INSERT
- 테이블에 새로운 데이터(행)을 추가할 때 사용하는 SQL
- 구문 형식
    ```sql
	1.
	--지정한 컬럼에 맞는 데이터를 삽입한다
	INSERT INTO tablename ( col1, col2, col3, ... )
	VALUES ( data1, data2, data3, ... )

	2.
	--컬럼을 따로 지정하지 않고 모든 컬럼에 삽입한다
	-- -> VALUES절에서 모든 컬럼의 값을 다 입력한다
	INSERT INTO tablename
	VALUES ( data1, data2, data3, ... )
	
	3.
	--VALUES절을 대신하여 SELECT구문을 이용하여 조회된 값을 삽입한다
	-- -> SELECT쿼리의 Result Set을 테이블에 삽입한다
	INSERT INTO tablename ( col1, col2, col3, ... )
	SELECT 절
    ```

### :bulb: INSERT ALL
- **한 번에 여러 행을 삽입**할 수 있게 해주는 DML 쿼리
- SELECT구문의 결과를 조건에 따라서 INSERT되도록 해주는 구문
- 여러 개의 INSERT구문으로 작성해야할 쿼리를 하나로 합칠 수 있다
- 구문 형식
    ```sql
	INSERT ALL
	WHEN 조건절
		THEN INTO tablename ( columns )
		VALUES ( datalist )
	[WHEN 반복]
	SELECT절;

	** THEN INTO 절에서 컬럼명 생략 가능 -> 전체 컬럼에 값 삽입

	** VALUES절 생략 가능 -> SELECT절에서 조회된 모든 행(데이터)을 삽입한다
    ```

### :bulb: DELETE
- 테이블의 데이터(행)을 삭제할 때 사용하는 구문
- 구문 형식
    ```sql
	DELETE (FROM) tablename
	WHERE 조건절 --삭제할 행 지정하기

	** FROM키워드 생략 가능
	** WHERE절 없이 사용하면 테이블 전체 삭제
    ```

### :bulb: UPDATE
- 테이블의 데이터(행)을 수정하는 구문
- 특정 행의 컬럼값을 변경할 수 있다
- 구문 형식
    ```sql
	UPDATE tablename
	SET 컬럼명1 = 변경값1, 컬럼명2 = 변경값2, ...
	WHERE 조건절

	** WHERE절 없이 사용하면 모든 행의 데이터가 변경된다
    ```

### :bulb: MERGE
- 오라클 전용 구문
- SELECT 수행 결과에 따라 UPDATE 또는 DELETE 또는 INSERT를 수행한다
- SELECT**조회 결과가 존재하지 않으면 INSERT** 수행
- SELECT**조회 결과가 존재한다면 UPDATE 또는 DELETE** 수행
- 구문 형식
    ```sql
	MERGE INTO tablename
	USING (
	  SELECT절
	)
	ON ( 조건절 )
	WHEN MATCHED THEN 추가구문
	WHEN NOT MATCHED THEN 추가구문;

	-> INTO : 삽입,갱신,삭제 가 이루어지는 테이블 지정
	-> USING : 조건 비교할 소스테이블 또는 서브쿼리(인라인 뷰)
	-> ON : WHEN 절에서 반응하는 조건을 부여한다
	-> WHEN MATCHED
		ON 조건절에 부합하는 USING 테이블의 데이터가 존재하면 수행한다
		UPDATE 또는 DELETE 를 작성한다
	-> WHEN NOT MATCHED
		ON 조건절에 부합하는 USING 테이블의 데이터가 없으면 수행한다
		INSERT 를 작성한다
    ```