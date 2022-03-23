# :pushpin: JDBC

### JDBC, Java DataBase Connectivity
- 자바 프로그램으로 데이터베이스에 접속/관리할 수 있게 해주는 드라이버(API)
- 자바로 작성된 프로그램에서 DB와 관련된 작업을 수행할 수 있도록 제공되는 기능(코드, 클래스)들을 모아놓은 것

### OJDBC, Oracle JDBC
오라클 데이터베이스를 관리할 수 있도록 해주는 JDBC
```java
	OJDBC버전	요구 JDK버전	DB버전
    ---------------------------------
	OJDBC 6		JDK 6이상	11gR2
	OJDBC 5		JDK 5이상
	OJDBC 14	JDK 1.4이상
	OJDBC 13	JDK 1.3이상
	OJDBC 12	JDK 1.2이상
```

### OJDBC라이브러리 파일
- C:\oraclexe\app\oracle\product\11.2.0\server\jdbc\lib 폴더
- ojdbc6.jar 파일

### 자바 프로젝트에 OJDBC 설치/적용하기
1. 방법1. Dynamic Web Project에서 ojdbc6.jar파일을 복사하여 추가하기
    - WebContent/WEB-INF/lib/ 폴더에 복사/붙여넣기 한다
	- 프로젝트에 자동으로 라이브러리가 연결된다
2. 방법2. 자바 프로젝트에서 라이브러리로 odjbc6.jar파일얼 선택하여 추가하기
	- 프로젝트 이름 우클릭
	- Build Path - Configure Build Path... 클릭
	- (좌측 메뉴에서 Java Build Path 메뉴가 선택된 상태)
	- Libraries 탭 선택
	- 오른쪽 버튼 중에서 ADD JARs 버튼 클릭 - 프로젝트 내부 파일 또는 오른쪽 버튼 중에서 ADD External JARs 버튼 클릭 - 프로젝트 외부 파일
	- 라이브러리 파일 찾아서 선택, Apply
	- (되도록 프로젝트 내에 JAR파일을 두고 ADD JARs를 사용할 것)

### execute 메소드의 종류 3가지
- SQL구문을 수행하는 API 메소드
- 매개변수로 SQL구문을 적용하고 DB에 전달한다(DB에서 실행됨)
- 메소드의 유형에 따라서 반환값이 다르다
1. ResultSet executeQuery(String sql);
	- SELECT쿼리의 결과를 ResultSet으로 반환한다
	- ResultSet에는 조회 결과의 모든 행을 참조할 수 있게 되어있다
	- ResultSet객체.next() 메소드를 호출하여 각 행을 순차적으로 참조한다
	- 다음으로 참조할 행이 존재하면 true반환, 아니면 false반환
2. int executeUpdate(String sql);
	- SQL를 수행했을 때 영향받은 행의 수를 반환한다
	- 주로 INSERT, UPDATE, DELETE를 수행할 때 사용한다
3. boolean execute(String sql);
	- true - ResultSet객체를 반환하는 SQL이 수행되었을 때(SELECT일 때)
	- false - ResultSet객체를 반환하지 않는 SQL을 수행했을 때(SELECT아닐 때)
- SELECT수행		-> executeQuery 사용
- INSERT, UPDATE, DELETE 수행	-> executeUpdate 사용
- DDL, DCL수행	-> execute 사용
- -> DDL = CREATE, ALTER, DROP
- -> DCL = GRANT, REVOKE

### SQL 수행 객체
- Statement 객체
	- Connection객체를 통해서 createStatement()메소드를 이용해서 생성한다
	- SQL쿼리를 execute할 때 매개변수로 전달한다
- PreparedStatement 객체
	- Connection객체를 통해서 prepareStatement()메소드를 이용해서 생성한다
	- SQL쿼리를 PreparedStatement객체를 생성할 때 전달한다
	- exeucte하기 전에 SQL쿼리에서 작성한 ?에 대한 값을 전부 채워야한다

### DTO, Data Transmission Object
- 데이터 전송 객체
- 프로그램 계층(Layer) 간에 데이터 교환을 위해 작성되는 자바 클래스
- 하나의 객체로 표현되는 데이터들을 하나의 클래스로 저장할 수 있게 만든다
- 테이블의 한 행을 하나의 객체로 표현할 수 있다

### DTO 클래스를 작성하는 규칙
- 멤버 필드는 모두 private 접근 제한자를 적용한다
- 메소드는 getter, setter, toString만 작성한다
- 추가적인 기능을 가진 일반 메소드는 작성하지 않는다
	- 데이터처리 이외의 추가 기능을 넣지 않고 데이터에 집중한다
- DTO클래스 이름을 DB의 테이블 이름으로 작성하는 것이 좋다
- DTO클래스의 멤버필드명을 테이블의 컬럼명으로 작성하는 것이 좋다

### VO, Value Object
- 데이터(값)을 저장하기 위해 작성되는 자바 클래스
- DTO == VO, 완전 같은 개념은 아니지만 구성 형태와 사용 방법이 비슷하다

### DAO, Data Access Object
- 데이터베이스의 데이터에 접근하기 위해 작성되는 클래스
- JDBC라이브러리를 이용해 구현되는 DB접속(연결), SQL수행, 결과처리 등을 담당하는 객체로 작성한다
- interface와 class로 나누어서 작성하면 좋다
	- interface에서 메소드 전체 목록을 간편히 확인할 수 있다
	- interface의 메소드마다 기능에 대한 요약을 주석으로 작성하는 것이 좋다
	- 메소드의 전체적인 개요를 한눈에 파악할 수 있게 된다
	- class에는 실제 구현된 코드를 작성하도록 한다

### Javadoc Generation에서 VM option으로 다음 내용을 추가한다
- -locale ko_KR -encoding UTF-8 -charset UTF-8 -docencoding UTF-8

### 홈페이지에서 ODJBC 라이브러리 찾기
- 홈페이지에서 다운받기
- (www.oracle.com) 접속
- Resources 메뉴 - Software Downloads 클릭
- Drivers and Utilities섹션 확인
- JDBC Drivers 링크 클릭
- Central Maven Repository 링크 클릭
- jdbc/ 링크 클릭
- ojdbc/ 링크 클릭
- 11.2.0.4/ 링크 클릭
- ojdbc6-11.2.0.4.jar 다운 받아서 사용

### 프로그래밍 아키텍쳐, Programming Architecture
- 프로그램을 작성하는(구성하는) 구조
- 프로그램의 코드를 기능별, 목적별로 분류해서 작업(구현)한다
- 프로그램을 설계하고 구현할 때 사용되는 패턴과 기술들을 뜻한다
- MODEL 1 방식
	- 비지니스 로직과 프레젠테이션 로직을 하나로 합쳐놓은 구조
- MODEL 2 방식
	- 비지니스 로직과 프레젠테이션 로직을 둘 이상으로 분리해놓은 구조

### 비지니스 로직, Business Logic
- 사용자(클라이언트)에게 보이지 않는 부분
- 데이터를 처리(가공)하는 응용프로그램의 일부 영역
- 주로 데이터베이스 처리 작업을 수행한다
> ex) 로그인 ID, PW를 확인하는 작업   
ex)	게시글 조회한 결과를 가져오는 작업

### 프레젠테이션 로직, Presentation Logic
- 사용자(클라이언트)에게 보이는 부분
- 출력될 화면을 구성하는 응용프로그램의 일부 영역
> ex) 로그인 처리 결과를 보여주는 작업   
ex)	게시글 검색 결과를 보여주는 작업

### 모델 1 아키텍쳐, MODEL 1
- 비지니스 로직 + 프레젠테이션 로직을 하나의 묶음(파일, 클래스)로 구현한다
> ex) main()메소드 하나로 데이터 가공, 출력 다 하는 것

- 장점
	- 프로그램을 구성하는 파일의 구조가 단순해서 직관적이다
	- 초기 개발이 쉽다
	- 중소형 프로젝트에 잘 어울린다
- 단점
	- 프로그램의 코드가 한 곳에 섞여있어 유지보수가 어렵다
	- 프로젝트 적응력이 떨어진다
	- 프로젝트 변화에 즉각 반응하기 어렵다
	- 코드 재사용성이 떨어진다
	- 분업이 힘들다
	- 대형 프로젝트에 어울리지 않는다

### 모델 2 아키텍처, MODEL 2
- 비지니스 로직과 프레젠테이션 로직을 서로 다른 파일로 분리한 형태
- 장점
    - 분업하기에 적절하며 대형 프로젝트에 잘 어울린다
    - 코드 재사용성을 올려서 개발하게 된다
- 단점    
    - MODEL 2 개발 방식에 대한 이해가 있어야 하고
    - 기본 지식의 요구 수준이 높은 편이다

### 디자인 패턴, Design Pattern
- 잘 알려진 알고리즘의 해결법을 정리한 것
- 프로그램을 구현하거나 설계할 때 발생하는 문제점(issue, 이슈)에 대한 해답을 문서화한 것 -> 자주 마주치는 프로그래밍 문제들을 해결하기 위한 노하우
- 재사용성을 높여 작성된 프로그래밍 솔루션(해결책)

### MVC 패턴
- 프로그램을 크게 세 가지 파트(역할)로 구분하여 개발하는 방법
- Model, View, Controller 의 약자
- 우리는 MODEL 2 기반의 MVC패턴을 이용하여 개발한다

### Model 파트
- 데이터베이스(데이터저장소)의 데이터를 처리하는 파트
- DB데이터를 관리하는 역할
- DAO, DTO가 해당된다

### View 파트
- 사용자에게 보여지는 화면을 구성하는 파트

### Controller 파트
- 사용자의 입력을 처리하고, 프로그램의 흐름을 제어하는 파트
- 주로 사용자와 상호작용을 하는 파트이다

### MVC패턴의 각 계층 요약
- Controller
	- 사용자의 입력처리
	- 보여질 화면(View) 선택
- Service
	- 데이터의 가공(DB데이터에 대한 추가적인 작업 수행)
	- 단순 DB데이터를 프로그램에 쓸모있는 정보로 변경하는 작업
- DAO
	- DB접속 및 DB데이터 단순처리(CRUD)
- View
	- 프로그램 수행 결과
	- 화면 구성
- DTO
	- 각 계층들이 주고받는 데이터를 저장하는 객체
```java

  예시)	사용자가 게시판의 7번 페이지를 클릭한다 ( 사용자의 입력 )
	-> 웹서버는 게시글들의 7번째 페이지를 보여준다

	( 게시글이 2750개, 한 페이지에 게시글을 30개씩 보여준다 )
	( 7번째 페이지에는 2570~2541 게시글을 보여준다 )
	------------------------------------------------------------
	[사용자의 입력]
		7 페이지를 클릭
	[Controller]
		7번 페이지를 클릭한 걸 입력으로 받아들인다
	[Service]
		DAO에서 DB 조회에 필요한 데이터를 가공한다
		총 게시글 수 == 2750개
		한 페이지 게시글 수 == 30개
		최근 작성글에서 210번째부터 30개 == 2570~2541번
	[DAO]
		Service가 요청한 항목의 데이터를 조회(SELECT)해서 반환한다
	[Service]
		조회결과를 Controller에 반환한다
	[Controller]
		조회 결과를 가지고 View를 선택한다
	[View]
		Controller가 전달해준 정보를 이용하여 화면을 구성한다
```

### 싱글톤 패턴, Singleton
- 특정 객체를 여러 번 생성하려고 시도할 때 매번 새로운 객체를 만들지 않고 하나의 인스턴스(객체)가 유지하도록 만든 패턴
- 객체를 생성할 때 필요한 자원의 요구 정도가 높을 때 사용한다
- 객체를 빈번히 생성하지 않고 딱 한 번 만들어두고 계속 사용하기 위해 적용한다

### 싱글톤 패턴이 적용되는 상황
1. 리소스를 많이 사용하는 자원을 로드할 때
2. 해당 자원이 지속적으로 사용될 때
    - JDBC 드라이버 로드 객체
    - 로그(log) 객체

