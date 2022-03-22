# :pushpin: MyBatis

### 마이바티스 설정
- 필요 라이브러리 설치
    - mybatis-x.x.x.jar
    - ojdbcX.jar
- 마이바티스 설정파일 작성 (XML파일 작성)
    - mybatis configuration 파일을 작성한다
    - 마이바티스 접속 설정을 적어두는 XML파일을 작성한다
    - 유저가이드에서 복사하고 수정하여 사용한다
- 마이바티스 Connection Factory 클래스 작성하기
	-마이바티스를 이용한 DB연결객체를 생성하는 클래 (싱글톤 적용됨)
    - SqlSessionFactory 클래스의 인스턴스를 싱글톤으로 생성하고 관리한다
    - SqlSession 클래스: SQL쿼리를 수행하는 객체, 마이바티스 실행 객체
    - SqlSessionFactory 클래스: Configuration 설정 항목을 적용하여 SqlSession객체를 생성하는 객체
    - SqlSessionFactoryBuilder 클래스: Configuration 설정 항목을 읽어들여 SqlSessionFactory 객체를 생성하는 객체
- DAO 파일 작성 (interface)
    - 마이바티스 프레임워크와 연결되는 자바 객체
- Mapper 파일 작성 (XML 파일)
	- 마이바티스에 적용할 SQL쿼리를 저장해놓는 XML파일
- DTO 파일 작성 (class)
	- 테이블의 정보를 전달하거나 전달받을 때 사용하는 DTO객체 (모델 객체)
- Controller파일 작성 (실행 클래스, main())
    - SqlSessionFactory클래스를 이용하여 SqlSession 객체를 생성한다
    - SqlSession객체를 이용하여 DB쿼리를 수행한다
    - 마이바티스 프레임워크를 실행시킨다(동작시킨다)

### 마이바티스 <resultMap> 태그
- 마이바티스 Mapper XML에서 사용할 수 있는 태그 중 하나
- SELECT쿼리로 조회된 결과(Result Set)의 컬럼명과 결과를 대입할 DTO의 멤버필드명이 다를 때 resultMap태그를 이용하여 매핑되도록 조율한다
- 조회된 컬럼명과 멤버필드명이 같을 때에는 자동으로 매핑되므로 필수로 적용하지 않아도 된다
- 이름이 다를 때에는 <id>, <result>태그를 이용하여 설정해준다
- <id>태그는 PK컬럼을 적용할 때 사용한다
- <result>태그는 PK컬럼 이외의 항목을 적용할 때 사용한다
- <select>태그에서 resultType속성이 아닌 resultMap속성으로 적용해야한다
    - <resultMap>태그의 id속성값을 이용하여 적용한다

### <resultMap> 태그의 속성
- id속성: 생성될 resultMap의 이름을 지정하는 속성
    - (주로 DTO클래스의 이름을 사용한다)
	- (풀네임에서 패키지만 제외한 클래스 이름을 많이 사용함)
- type속성: resultMap과 매핑될 실제 존재하는 DTO클래스를 지정하는 속성
	- (패키지까지 포함한 풀네임으로 클래스 이름을 사용한다)

### <resultMap>태그의 자식 태그들
- <id>태그: 기본키(PK)에 해당하는 컬럼을 지정할 때 사용한다
- <result>태그: 기본키 이외의 컬럼을 지정할 때 사용한다
    - 기본키 컬럼도 <result>태그로 적용해도 된다
    - 두 태그 모두 column속성으로 컬럼명, property속성으로 필드명을 명시하여 사용한다

### 마이바티스 TypeAlias
- 매퍼XML에서 사용하는 태그의 속성으로 parameterType, resultType을 사용할 때 속성값으로 DTO클래스의 패키지명까지 포함한 풀네임을 적용해야 한다
- 패키지의 길이가 길어질 경우 속성값이 너무 길어져 불편함이 있다
- TypeAlias를 이용하여 클래스의 별칭을 적용해서 사용할 수 있다
    - 오히려 유지보수성을 떨어뜨리는 경우가 있다
	- 조심해서 사용할 것

### TypeAlias를 적용하는 방법 2가지
- 두 가지 방법 모두 마이바티스 Configuration XML의 <settings>태그 밑에 작성한다

    1. 클래스 단위로 별칭을 적용하는 방법
        - type속성에 클래스의 풀네임을 적용한다
        - alias속성에 클래스의 별칭을 적용한다
    ```java
    <typeAlias>
        <typeAlias type="dto.Emp" alias="Emp" />
    </typeAlias>
    ```
    2. 패키지 단위로 별칭을 적용하는 방법
        - 등록된 패키지의 DTO클래스의 정의코드 바로 위에 @Alias("별칭")을 이용하여 개별적으로 별칭을 설정할 수 있다
        - 별도의 별칭을 적용하지 않으면 클래스 이름이 별칭으로 적용된다
    ```java
    <typeAlias>
        <package name="dto" />
    </typeAlias>
    ```

### 마이바티스 <sql>, <include> 태그
- SQL구문의 재사용성을 높이기 위해 Mapper XML에서 사용하는 태그
- 반복적으로 사용되는 SQL구문을 <sql>태그에 저장하여 사용한다
- <include>태그를 이용하여 DML태그에서 <sql>태그에 저장된 구문을 불러온다
- <sql>태그를 이용할 때에는 적용된 코드들이 다 함께 영향을 받는다는 걸 주의한다
	- 한쪽 SQL코드만 변경하려고 할 때 오히려 역효과를 불러온다
- <sql>태그의 id속성을 반드시 작성해야 한다

### 마이바티스 SQL쿼리 수행 태그
- DML 태그
- <select>, <insert>, <update>, <delete>
- 수행하려는 SQL 구문에 맞게 태그를 골라 작성한다
- 수행하는 SQL구문과 맞지 않는 태그를 이용해도 실행은 된다
- 하지만, 사용할 수 있는 기능에 제약이 생길 수 있고 가독성을 해치므로 SQL쿼리와 맞는 태그를 사용하는 것이 좋다

### 공통 속성
- id
    - 매퍼 파일(XML)에서 유일한 값으로 태그의 이름을 설정한다. 네임스페이스 내에서 식별값으로 사용된다
	- DAO인터페이스의 추상메소드의 이름과 같은 값으로 설정한다
- parameterType
	- SQL쿼리를 수행할 때 필요한 파라미터(전달값)의 데이터타입을 적는다
	- 기본 데이터타입을 지칭하는 키워드로 사용할 수 있다
	DTO클래스(객체)는 패키지까지 포함한 풀네임으로 사용한다
- parameterMap	[사용하지 않는 속성]
- flushCache
	- SQL구문을 사용(호출)할 때 사용될 캐시에 대한 자동 처리여부 설정
	- 기본값은 false다. true로 설정하면 SQL구문이 호출될 때마다 캐시를 지우게된다
- timeout
	- 데이터베이스의 처리 결과를 기다리는 최대 시간을 설정한다
- statementType
	- SQL쿼리를 수행하는 방식(객체)에 대한 설정
	- Statement, PreparedStatement(기본값), Callable 중 골라서 설정한다
	- Callable은 마이바티스로 PL/SQL을 사용할 때 적용한다

### <select>태그의 전용 속성
- resultType
	- SELECT쿼리의 수행 결과(ResultSet)를 처리할 데이터타입을 설정한다
	- 실제 존재하는 데이터타입으로 작성한다
	- TypeAlias를 적용할 수 있다
- resultMap
	- <resultMap>태그를 이용하여 생성한 항목을 사용한다
	- <resultMap>태그의 id속성값을 적용한다
	- resultType속성을 대신하여 사용한다
- useCache
	- SELECT구문의 조회 결과를 생성할 때 캐시를 사용할 것인지 설정한다
	- 기본값은 true
- fetchSize
	- SELECT구문의 조회 결과를 한번에 가져올 크기를 설정하는 속성
	- 기본값은 10
	- 대용량 조회 처리가 필요하면 1000개 정도를 설정하는 편이다
- resultSetType
	- 조회 결과값을 읽어들이는 동작을 설정하는 속성
	- DBMS의 커서의 동작하는 방식을 설정한다
	- FOWARD_ONLY : 커서가 앞쪽(다음데이터)으로만 이동한다
	- SCROLL_INSENSITIVE : 커서가 뒤쪽으로도 이동 가능하다, 데이터의 변화(변경)에 민감하지 않다	
    - SCROLL_SENSITIVE : 커서가 뒤쪽으로도 이동 가능하다, 데이터의 변화(변경)에 민감하다
    - 오라클DBMS는 SCROLL_SENSITIVE를 지원하지 않는다

### 데이터타입을 나타내는 키워드
- 매퍼XML에서 resultType이나 parameterType에서 특정 데이터타입을 표현할 때 사용하는 키워드
- org.apache.ibatis.type.TypeAliasRegistry 클래스에 명시되어있다

    ```java
	키워드		자바 타입
	--------	--------
	string		java.lang.String
	date		java.util.Date

	map		java.util.Map
	hashmap		java.util.HashMap
	list		java.util.List
	arraylist	java.util.ArrayList

	ResultSet	java.sql.ResultSet

	--------	--------
	int		java.lang.Integer	(wrapper 클래스)
	integer		java.lang.Integer

	_int		int			(기본 데이터타입)
	_integer	int

	int[]		Integer[]

	_int[]		int[]
    ```
- byte, short, long, float, double, boolean도 int와 같은 형태로 사용

### 마이바티스의 내장 캐시(Cache)
- 2가지 내장 캐시를 가지고 있다
    - Local Session Cache
	- Second Level Cache (2nd Level)
- Local Session Cache
    - SqlSession객체마다 가지고 있는 객체
    - DMBS연결다마 하나씩 생성된다
    - 개발자가 임의로 기능을 해제할 수 없다
- Second Level Cache
    - Mapper에 연결된 namespace마다 존재하는 캐시
    - DAO마다 하나씩 연결된다
    - SQL쿼리 구문을 수행할 때마다 사용할 수 있다

### 마이바티스 <selectKey> 태그
- 자동 생성키(Auto Increment)를 지원하지 않는 데이터베이스에서 사용하도록 제공되는 키 생성 태그 (주로 PK를 뜻한다)
	- 오라클 DB는 Auto Increment기능이 없다
- <insert>태그의 자식 태그로 사용된다
- 생성된 키값을 자바코드 쪽으로 넘겨준다

### <selectKey> 태그의 속성
- order
	- BEFORE: insert쿼리 수행 전에 selectKey가 동작한다
	- AFTER: insert쿼리 수행 후에 selectKey가 동작한다
- resultType
	- selectKey에서 조회된 결과값의 데이터타입을 명시한다
- keyProperty
	- 결과값이 저장(매핑)될 프로퍼티명을 지정한다
	- parameterType의 멤버필드명으로 작성한다
- statmenetType
	- Statement, PreparedStatement(기본값), Callable 중에서 선택해서 작성

### 마이바티스 동적 SQL 쿼리 태그, Dynamic SQL
- 동적으로 변환되는 SQL쿼리를 작성할 수 있도록 도와주는 마이바티스 태그
- <select>, <insert>, <update>, <delete> 태그 안에서 사용한다
- <if>, <choose>, <foreach>, <trim> 태그를 제공한다

### <if> 태그
- test속성을 이용하여 조건문을 지정하는 조건문 태그
- 조건문의 결과에 따라 쿼리의 추가 여부가 결정된다
- test속성의 값은 "true" 또는 "false"가 되도록 작성한다

### <choose> 태그
- 자식태그로 <when>, <choose> 태그를 같이 사용한다
- if - else if - else 구문과 비슷한 조건문 태그
- <choose>태그에는 속성을 작성하지 않는다
- <when>태그에 test속성으로 조건문을 작성한다
- <otherwise>태그는 test속성을 작성하지 않는다
- <otherwise>태그는 <when>태그의 test속성이 모두 false일 때 적용된다

### <foreach> 태그
- SQL구문이 반복적으로 추가되면서 동적으로 바뀌는 구문을 생성할 때 사용한다
- 배열/해시맵 타입의 파라미터를 처리할 때 유용하다
- 마이바티스의 parameterType을 hashmap으로 처리하는 것이 좋다
- 배열이나 리스트를 해시맵의 요소로 저장(put)하여 사용한다
- 속성
	- collection: 반복 수행할 객체(리스트,배열)를 지정한다
	- item: 반복될 때마다 사용하는 요소의 이름을 지정한다
	- open: 구문의 첫부분에 사용할 단어(구문)을 지정한다
	- close: 구문의 끝부분에 사용할 단어(구문)을 지정한다
	- seperator: 반복되는 구문 사이사이에 추가할 단어(구문)을 지정한다
    - checkbox 선택항목에 대한 조건 처리에 유용하다

### <trim> 태그
- WHERE절에서 AND|OR의 적용, UPDATE구문에서 SET절에서 많이 사용하는 태그
- 전달파라미터의 값이 전달되지 않아 동적쿼리가 추가되지 않는 상황에서 WHERE절의 AND 또는 OR 키워드의 충돌, UPDATE구문의 SET절의 ',' 충돌을 제거할 때 사용한다
- 속성
	- prefix: 접두어, 구문의 맨 앞쪽에 반드시 추가될 문자열을 지정한다
	- prefixOverrides: 접두어 값과 겹치면 지워질 문자열을 지정한다
	- suffix: 접미어, 구문의 맨 뒤쪽에 반드시 추가될 문자열을 지정한다
	- suffixOverrides: 접미어 값과 겹치면 지워질 문자열을 지정한다
    - prefix나 suffix를 설정하지 않으면 각 Overrides는 구문의 처음, 마지막 값을 판단하여 제거한다
