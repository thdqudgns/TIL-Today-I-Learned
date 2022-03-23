# :pushpin: Spring

### STS, Spring Tool Suite
- 스프링 프레임워크로 프로그램을 개발하기 위해 만들어진 IDE툴

### STS 설치 방법
1. STS Tool을 다운받아 한번에 설치하기 (https://spring.io/)
2. 이클립스EE 에 플래그인 형태의 STS를 추가설치하기

### 이클립스에 STS플러그인 설치하기
1. 이클립스 Help메뉴 - Eclipse Marketplace 선택
2. Find창에서 sts 검색
3. Spring Tool 3 (Standalone Edition) 3.9.14.RELEASE 항목 확인
4. Install 버튼 클릭
5. Confirm 버튼 클릭
6. 다운로드 완료 후 라이센스 accept선택하고 Finish
    - 별도의 창이 뜬다면 Install Anyway 선택
	- 선택 창이 뜬다면 Select All하고 Accept selected
    - 설치 완료 후에 Restart Now 선택

### 스프링 프로젝트 만들기
1. File메뉴 - New - Other
2. Spring폴더 - Spring Legacy Project 선택 - Next
3. Project Name 입력 (ex. Simple)
4. Templates: 항목중에서 Spring MVC Project 선택 - Next
5. top-level Package 입력 (ex. com.test.www, a.b.c)
6. Finish

### 스프링 레거시 프로젝트에 적용된 스프링프레임워크 버전 바꾸기
- 프로젝트 내에서 pom.xml 파일 열기
- <properties>태그 확인
- <org.springframework-version> 항목의 값을 변경한 후 저장한다
- 스프링프레임워크 documentation에서 찾아서 입력한다 (https://spring.io/projects/spring-framework#learn)
- 지금 최신 GA버전은 5.3.12
    - 버전 정보를 변경하고 pom.xml파일을 저장하면 이클립스에서 곧바로 라이브러리를 다운받아서 적용한다
    - 잘못된 버전, 존재하지 않는 버전을 입력하면 버그발생할 수 있음
    - 오타없는지 다시 확인하고 저장할 것!

### 스프링 레거시 프로젝트에 적용된 JDK 버전 바꾸기
- 프로젝트 폴더 우클릭
- Properties 항목 선택
- 왼쪽 메뉴 중에서 Project Facets 선택
- Java 항목에서 1.6으로 되어있는 걸 1.8로 변경
- Apply
- =====================================
- 왼쪽 메뉴 중에서 Java Build Path 선택
- Libraries 탭 선택
- JRE System Library 항목 선택
- 우측에 Edit... 버튼 클릭
- Alternate JRE: 항목 중에서 맞는 버전(openjdk 1.8)을 선택
- Apply

### 이클립스에 Package Explorer 뷰(탭) 추가하기
- Window메뉴 - Show View - Other... 선택
- "package explorer" 검색
- Java폴더항목에 있는 Package Explorer 선택
    - Project Explorer보다 자바코드(JSP포함)에 집중할 수 있다

### MAVEN, 메이븐
- 빌드(build) 관리 (자동화)도구
- 프로젝트가 빌드될 때 필요한 라이브러리 파일(.jar)들을 관리한다
- 메이븐 저장소 URL (https://mvnrepository.com/)
- 프로그램 라이프 사이클
	- 소스코드 작성 -> 컴파일 -> 바이트코드 -> 빌드 -> 실행
- 빌드, build
	- 개발자가 작성한 소스코드의 바이트코드와 API라이브러리 코드의 바이트코드를 결합하여 실행 가능한 완성 코드를 만드는 작업
- pom.xml 파일
	- 메이븐이 관리해야하는 라이브러리들의 정보를 기록하는 설정 파일
	- 메이븐이 pom.xml파일을 읽어 프로젝트를 빌드할 수 있게 해준다

### 메이븐 충돌(오류) 발생한 상황 처리하기
- 서버를 시작하면 이클립스 콘솔의 예외 메시지가 뜬다
- invalid LOC header 문구가 떠있는 예외가 발견된다
    - pom.xml에 설정한 <dependency>의 라이브러리를 제대로 다운받지 못한 상황
- 해결 방법
    1. 이클립스를 끈다
    2. C:\Users\user1\.m2\repository\ 폴더를 삭제한다 (맥OS: 터미널에서 "open ~/.m2" 입력)
    3. 이클립스를 켠다
    4. Progress탭을 확인하고 작업이 완료될 때까지 기다린다 -> 메이븐 환경이 다시 구축되는 과정
    5. 해결! -> 해결되지 않으면 다른 원인을 찾아본다

### 의존성, Dependency
- 객체가 작동하기위해서 필요한 외부 객체와의 연결
    ```java
	ex)
	public class EmpController {

	  //EmpController객체는 EmpService객체에 의존적이다
	  private EmpService empService = new EmpService();

	}
    ```

### 의존성 주입, Dependency Injection, DI
- 객체가 의존성을 직접 발생시키지 않고 외부(프레임워크)의 도움을 받아 의존성이 주입되는 현상
    - 생성자 의존성 주입(Constructor DI)
    - Setter 의존성 주입(Setter DI)

### IoC, Inversion of Control
- 제어의 역전
- 프로그램 진행 흐름의 제어권이 역전되었다는 뜻
- 프로그램의 흐름 제어를 스프링 프레임워크가 담당한다

### @Autowired의 바인딩 전략
- 바인딩 : 실행코드와 정의코드가 연결되는 것 (주로 메소드 호출코드와 메소드 정의코드의 연결을 뜻한다)
- @Autowired에 의해 객체변수와 스프링 빈이 연결되는 것을 뜻한다(DI)
1. byType
    - 등록된 스프링 빈의 이름에 상관없이 같은 타입의 스프링 빈을 바인딩한다
    - 같은 타입으로 등록된 빈이 2개 이상이면 예외가 발생한다
2. byName
	- 같은 타입으로 등록된 빈이 여러 개 있어도 이름이 같은 스프링 빈을 바인딩한다
    - 등록된 빈의 ID 속성값과 변수의 이름으로 판단한다

### DI 어노테이션
- @Autowired
	- 패키지: org.springframework.beans.factory.annotation.Autowired
	- 스프링에서 제공하는 DI 어노테이션
	- 적용가능 위치: 멤버필드, 생성자, 파라미터가 존재하는 메소드
	- 바인딩 전략: byType 먼저, byName 다음
- @Resource
	- 패키지: javax.annotation.Resource
	- 자바 표준으로 제공하는 DI 어노테이션
	- 적용가능 위치: 멤버필드, 파라미터가 1개인 setter
	- 바인딩 전략: byName 먼저, byType 다음
- @Inject
	- 패키지: javax.inject.Inject
	- 자바 표준으로 제공하는 DI 어노테이션
	- @Autowired와 동일한 기능을 가진다 (스프링에서는 3.0이상부터 사용 가능)
	- @Resource의 강화 버전
    - 별도의 라이브러리 파일이 필요하다
- @Quilifier("beanName")
	- DI 어노테이션의 보조 기능을 제공한다
    - 바인딩 될 beanName을 직접 지정할 수 있게 해준다

### 스프링 Controller 클래스 만들기
1. 일반 클래스를 생성한다
2. 클래스 정의 앞에 @Controller 어노테이션 붙이기
    - servlet-context.xml의 설정을 기반으로 적용된다
    ```java
	<annotation-driven>
	// 어노테이션을 이용하여 컴포넌트를 등록할 수 있도록 설정한다 (컨트롤러, 서비스 - @Controller, @Service)

	<component-scan>
	// 스프링빈으로 등록할 컴포넌트들의 위치를 패키지 단위로 설정한다

	// ** 여러 개의 패키지를 등록할 땐 ',' 로 구분한다
    ```
3. 일반 메소드를 작성한다
4. 메소드 정의 앞에 @RequestMapping 어노테이션 붙이기
    - @RequestMapping(value="url패턴", method=RequestMethod.메소드형식)
	- value에는 요청을 받을 url-pattern을 작성한다
	- value는 반드시 '/'로 시작해야한다
	- method는 RequestMethod열거체의 필드값으로 적용한다
	- RequestMethod.GET 또는 RequestMethod.POST 를 사용한다

### Log4J 라이브러리
- Logging For Java
- 자바 프로그램을 위한 로깅 라이브러리

### 로그 레벨
- FATAL
    - 심각한 에러 레벨
	- 시스템으로도 문제가 번질 정도로 문제있는 상황
- ERROR
	- 에러 레벨
	- 프로그램이 중단될 정도의 문제 상황
- WARN
	- 경고 레벨
	- 정상 처리 가능하지만 확인이 필요한 정도의 상황
- INFO
	- 정보 레벨
	- 상태 변경과 같은 정보 메시지
	- 일반적인 메시지
- DEBUG
	- 디버깅 레벨
	- 프로그램 디버깅한 메시지
- TRACE
	- 추적 레벨
	- 프로그램의 동작을 모두 다 확인할 때 사용하는 메시지

### 로그 레벨 등급 차이
- FATAL > ERROR > WARN > INFO > DEBUG > TRACE
    > ex) 로그레벨을 DEBUG로 설정하면 FATAL ~ DEBUG까지 모두 출력된다

	> ex) 로그레벨을 INFO로 설정하면 FATAL ~ INFO까지 모두 출력된다

### 로그 출력하는 패턴 옵션
- %p - 로그레벨
- %c - 카테고리, 패키지 + 클래스 + 메소드명
- %m - 로그메시지 출력
- %n - 개행문자
    > ex)	%-5p: %c - %m%n
    >       %-5p	-> 5자리로 왼쪽정렬하며 로그레벨을 출력한다

### 컨트롤러 메소드의 매개변수
- 요청파라미터와 관련이 있다
- 메소드 내에서 필요한 객체를 매개변수로 선언할 수 있다
- 별도의 new연산자 사용없이 객체를 생성해준다
	- 자주 사용되는 객체 또는 웹어플리케이션 동작에 필요한 객체를 스프링이 자동으로 생성해준다

> HttpServletRequest : 요청 정보 객체
> HttpServletResponse : 응답 정보 객체

> Reader : 요청객체 입력스트림 (req.getReader())
> Writer : 응답객체 출력스트림 (resp.getWriter())

> HttpSession : 세션 정보 객체

> Locale : 언어권 정보 객체

> Model, ModelAndView, ModelMap : 모델값 처리 객체

- 요청 파라미터를 받아들이는 변수
	- @RequestParam 어노테이션을 붙인 매개변수를 사용한다
	- @RequestParam 생략 가능하다
- 커맨드 객체, Command Object
	- 요청 파라미터를 받아들이는 DTO객체
	- @ModelAttribute 어노테이션을 붙여서 사용한다
	- @ModelAttribute 생략 가능하다

### @RequestParam 어노테이션 사용법
- 컨트롤러 메소드에서 요청 파라미터를 처리하는 방식을 지정할 때 사용하는 어노테이션이다
- value, required, defaultValue 등의 속성으로 설정값을 적용한다
- @RequestParam String name
	- name이라는 이름의 요청 파라미터 값을 name변수에 저장한다
	- @RequestParam을 생략할 수 있다
	- @RequestParam을 생략하면 required=false로 적용된다
	- @RequestParam을 적용하면 required=true로 적용된다
- @RequestParam(value="n") String name
	- n이라는 이름의 요청 파라미터 값을 name변수에 저장한다
	- String name = req.getParameter("n"); 과 같은 동작
- @RequestParam(defaultValue="abc") String name
	- 요청파라미터의 데이터가 없으면 "abc"를 name변수에 저장한다 -> 요청파라미터의 기본값을 설정하는 효과를 준다
	```java
     ex) @RequestParam(defaultValue="0") int curPage(int타입 변수로 사용할 값도 문자열 형태로 설정해야 한다)
     ```
- @RequestParam(required=true) String name
	- required=true 요청파라미터가 존재하지 않으면 에러 발생(기본값)
	- required=false 요청파라미터가 존재하지 않아도 정상 동작한다
	- true설정은 파라미터가 아예 존재하지 않아야 에러가 발생한다
    ```java
	 ex)	@RequestParam(required=true) String test
		 /param/required			-> 에러 발생
	
    	 /param/required?test=		-> 에러 발생하지 않음
		 /param/required?test=123	-> 에러 발생하지 않음
    ```
- @RequestParam HashMap<String, String> map
	- 전달 파라미터를 map의 key, value쌍으로 받아들인다
	    - DTO가 필요없다
	    - 요청 파라미터에 어떤 이름을 가진 값이 전달되는지 상관없이 서버에서 데이터를 받아들인다
	- ** Map을 사용할 때에는 @RequestParam 어노테이션을 생략하면 안 된다
	- ** @RequestParam 어노테이션을 생략하면 Map에 전달파라미터가 저장되지 않는다

### 컨트롤러 메소드의 리턴타입
- 응답할 View와 View에 전달할 MODEL과 연관이 있다
- viewName으로 지정한 문자열을 통해 View(주로 JSP)를 지정하게 만든다
- viewName은 ViewResolver에 전달되는 데이터이다
- ViewResolver는 viewName에 해당하는 View를 찾고 응답한다
- ViewResolver의 타입(유형)에 따라 viewName을 이용하는 방식이 달라진다
	- ** InternalResourceViewResolver
	    - JSP파일을 찾아서 View로 사용한다
	- ** BeanNameViewResolver
	    - 스프링Bean을 찾아서 View로 사용한다
	- ** 스프링 레거시 MVC프로젝트에서는 기본적으로 InternalResourceViewResolver를 사용하고 있다
        - servlet-context.xml에 설정되어있다
	    - prefix + viewName + suffix에 해당하는 JSP를 View로 사용한다
        - /WEB-INF/views/{viewName}.jsp

### 컨트롤러 메소드에서 사용하는 리턴타입 3가지
- void
- String
- ModelAndView
1. void 타입
    - @RequestMapping의 value로 설정한 url-pattern을 판단하여 viewName으로 사용한다
    - 처음에 오는 '/'를 제거한다
    - 폴더 구조는 유지한다
    - URL에 확장자형태를 가지면 확장자를 제거한다
    ```java
	ex)	@RequestMapping(value="/member/login.do")
		public void login() {}

		-> viewName:	member/login
		-> view:	/WEB-INF/views/member/login.jsp
    ```
2. String 타입
    - return코드에 반환한 문자열을 viewName으로 지정한다
    - return null;일 경우에는 void타입 리턴과 동일하게 동작한다
    ```java
	ex)	@RequestMapping(value="/member/login.do")
		public String login() {
		  return "strMember/strLogin";
		}

		-> viewName:	strMember/strLogin
		-> view:	/WEB-INF/views/strMember/strLogin.jsp
    ```
3. ModelAndView 타입
    - MODEL값 지정과 viewName설정을 하나의 객체로 처리한다
    - 컨트롤러 메소드의 매개변수로 선언하여 사용할 수 있다
    - 메소드 내에서 new ModelAndView()로 생성하여 사용할 수 있다
    - return값으로 선언된 변수를 이용하여 반환한다
    ```java
	ex)	@RequestMapping(value="/member/login.do")
		public ModelAndView login(ModelAndView mav) {

		  mav.addObject("key", value); //모델값 지정
		  mav.setViewName("viewName"); //뷰네임 지정

		  return mav;
		}

	ex)	@RequestMapping(value="/member/login.do")
		public ModelAndView login() {
		  ModelAndView mav = new ModelAndView();

		  mav.addObject("key", value); //모델값 지정
		  mav.setViewName("viewName"); //뷰네임 지정

		  return mav;
		}
    ```

### 스프링 컨트롤러의 페이지 이동(화면 전환)
- 리다이렉트, redirect
	- URL이 변경되면서 페이지 이동, 새로운 요청이 발생한다
	- request객체, response객체가 새로 생성된다
	- MODEL값을 유지하지 않는다
- 포워드, forward
	- URL을 유지하면서 화면의 내용만 바뀜
    - request객체, response객체가 유지된다
	- MODEL값을 유지한다

### 스프링의 redirection
- 뷰네임 앞에 "redirect:" 을 붙여준다
    ```java
	return "redirect:요청URL";

	ex)	return "redirect:/board/list";
	ex)	return "redirect:/";
	
	ex)	return "redirect:/board/detail?board=" + boardno;
    ```

### 스프링의 forward
- 뷰네임을 전달한다
    ```java
	return "viewName";
    ```

### 스프링 마이바티스 설정
- [MAVEN 저장소 URL](https://mvnrepository.com/)
- 버전을 잘 고려하여 다운받도록 한다
1. MAVEN을 이용하여 라이브러리 설치하기
	- mybatis-spring: 스프링에서 마이바티스를 사용할 수 있도록 한다
    ```java
    <dependency>
        <groupId>org.mybatis</groupId>
        <artifactId>mybatis-spring</artifactId>
        <version>2.0.6</version>
    </dependency>
    ```
    - mybatis: 마이바티스 프레임워크
    ```java
    <dependency>
        <groupId>org.mybatis</groupId>
        <artifactId>mybatis</artifactId>
        <version>3.5.7</version>
    </dependency>
    ```
    - spring-jdbc: 스프링에서 JDBC를 사용할 수 있도록 한다
    ```java
    <dependency>
        <groupId>org.springframework</groupId>
        <artifactId>spring-jdbc</artifactId>
        <version>${org.springframework-version}</version>
    </dependency>
    ```
	- ojdbc: 오라클 DB에 자바코드로 접근할 수 있도록 한다
	    - mvnrepository에서 직접 받을 수 없음
	    - 저장소(repository)를 따로 설정해야 한다
    ```java
    <!-- ODJDBC6를 위한 추가 저장소 설정 -->
    <!-- dependencies태그와 properties태그 사이에 작성 -->
    <repositories>
        <repository>
            <id>oracle</id>
            <url>http://maven.jahia.org/maven2</url>
        </repository>
    </repositories>


    <!-- OJDBC6 -->
    <!-- dependencies태그 안에 작성
    <dependency>
        <groupId>com.oracle</groupId>
        <artifactId>ojdbc6</artifactId>
        <version>12.1.0.2</version>
    </dependency>
    ```
2. root-context.xml에 마이바티스 설정하기
- 스프링 빈으로 설정 정보를 등록한다
- dataSource: DB접속 정보 설정 객체
- SqlSessionFactory: 마이바티스 수행 객체 생성
- mapperLocations: Mapper XML 파일의 위치 설정
- MapperScannerConfigurer: DAO인터페이스의 위치 설정 (basePackage 설정)
3. 매퍼 작성하고 실행

### 마이바티스 로그 남기기
1. 로그 라이브러리 추가하기
	- pom.xml을 이용하여 log4jdbc-remix 0.2.7 추가
	- https://mvnrepository.com/artifact/org.lazyluke/log4jdbc-remix/0.2.7
    ```java
    <dependency>
        <groupId>org.lazyluke</groupId>
        <artifactId>log4jdbc-remix</artifactId>
        <version>0.2.7</version>
    </dependency>
    ```
2. root-context.xml 편집
- dataSource에 대한 설정
- dataSource의 id를 dataSourceSpied로 변경
- 새로운 dataSource를 id로 가지는 <bean> 작성
    ```java
	<!-- DB접속 정보 -->
	<bean id="dataSourceSpied" class="org.springframework.jdbc.datasource.DriverManagerDataSource">
		<property name="driverClassName" value="oracle.jdbc.driver.OracleDriver"/>
		<property name="url" value="jdbc:oracle:thin:@localhost:1521:xe"/>
		<property name="username" value="scott"/>
		<property name="password" value="tiger"/>
	</bean>

	<!-- 마이바티스 로깅 -->
	<!-- 	-> 마이바티스 dataSource의 프록시(Proxy) -->
	<bean id="dataSource" class="net.sf.log4jdbc.Log4jdbcProxyDataSource">
	
		<!-- 프록시 대상 DB DataSource설정하기 (원본 DB 정보) -->
		<constructor-arg ref="dataSourceSpied" />

		<!-- 로그 출력 양식(포맷) 설정 -->		
		<property name="logFormatter">
			<bean class="net.sf.log4jdbc.tools.Log4JdbcCustomFormatter">
				<property name="loggingType" value="MULTI_LINE" />
				<property name="sqlPrefix" value="SQL:::" />
			</bean>
		</property>
	</bean>
    ```
3. log4j.xml에 Logger설정 추가하기
- log4jdbc-remix 라이브러리가 로그를 남길 수 있도록 설정
- 추가할 Logger 목록
    ```java
	 jdbc.connection	: WARN레벨
	 jdbc.audit		: WARN레벨
	 jdbc.sqlonly		: WARN레벨
	 jdbc.sqltiming		: INFO레벨
	 jdbc.resultset		: WARN레벨
	 jdbc.resultsettable	: INFO레벨

	 org.mybatis		: WARN레벨
    ```
    ```java
	<!-- 마이바티스 Loggers -->
	<logger name="jdbc.connection">
		<level value="WARN" />
	</logger>
	
	<logger name="jdbc.audit">
		<level value="WARN" />
	</logger>
	
	<logger name="jdbc.sqlonly">
		<level value="WARN" />
	</logger>
	
	<logger name="jdbc.sqltiming">
		<level value="INFO" />
	</logger>
	
	<logger name="jdbc.resultset">
		<level value="WARN" />
	</logger>
	
	<logger name="jdbc.resultsettable">
		<level value="INFO" />
	</logger>
	
	<logger name="org.mybatis">
		<level value="WARN" />
	</logger>
    ```

### 한글 인코딩 설정 필터 : UTF-8
    ```java
	<!-- 한글 인코딩 설정 필터 : UTF-8 -->
	<!-- web.xml 파일의 첫 부분에 작성한다 -->
	<filter>
		<filter-name>encodingFilter</filter-name>
		<filter-class>org.springframework.web.filter.CharacterEncodingFilter</filter-class>
		<init-param>
			<param-name>encoding</param-name>
			<param-value>UTF-8</param-value>
		</init-param>
	</filter>
	
	<filter-mapping>
		<filter-name>encodingFilter</filter-name>
		<url-pattern>/*</url-pattern>
	</filter-mapping>
    ```

### 인터셉터, Handler Interceptor
- 컨트롤러의 처리 전, 후 끼어들어서 초가적인 작업을 수행하는 요소
- 스프링의 어플리케이션 영역에서 처리된다
- 스프링의 기능을 사용할 수 있다
- 서블릿 필터(Filter)와 비슷한 기능을 수행한다
- 서블릿 필터는 서블릿의 처리 전, 후
- 인터셉터는 스프링컨트롤러 처리 전, 후

### 핸들러 인터셉터 인터페이스
- org.springframework.web.servlet.HandlerInterceptor
- preHandle(), postHandle() 메소드를 재정의(override)하여 인터셉터 클래스를 구현하여 적용한다
- preHandle()
	- 요청을 처리하는 컨트롤러가 수행되기 전에 동작할 기능을 작성한다
	- 요청 처리 전
- postHandle()
	- 요청을 처리하는 컨트롤러가 수행된 이후에 동작할 기능을 작성한다
	- 응답 처리 후

### 스프링 파일업로드
- 스프링 파일업로드 클래스
	- org.springframework.web.multipart.commons.CommonsMultipartResolver
- Apache Commons-Fileupload 라이브러리를 이용하여 스프링 프레임워크에서 파일업로드를 수행할 수 있도록 지원하는 클래스
- 파일업로드관련 추가 설정이 필요하다
- Commons-Fileupload 라이브러리를 MAVEN로 추가하여 사용한다
```java
<!-- Apache Commons Fileupload 1.4 -->
<!--  -> Apache Commons IO도 같이 추가된다 -->
<dependency>
    <groupId>commons-fileupload</groupId>
    <artifactId>commons-fileupload</artifactId>
    <version>1.4</version>
</dependency>
```

### 스프링 파일업로드 처리 클래스 설정
- 스프링 빈으로 등록한다
- servlet-context.xml에 설정한다
- CommonsMultipartResolver클래스를 이용한다
- 스프링 빈의 id를 multipartResolver로 지정하여 등록하도록 한다

### 설정 프로퍼티
- maxInMemorySize
	- 임시 파일을 메모리로 처리할 수 있는 사이즈 설정
- maxUploadSize
	- 최대 업로드 사이즈 제한
	- 다중 업로드된 모든 파일의 사이즈 총합을 제한한다
- maxUploadSizePerFile
	- 업로드 되는 파일의 최대 사이즈 제한
	- 다중 업로드 된 각각의 파일의 사이즈를 제한한다
- uploadTempDir
	- 임시 파일을 저장할 경로 설정
- defaultEncoding
	- 업로드 파일의 기본 인코딩(기본값: ISO-8859-1)
	- 요청 객체(HttpServletRequest)에 설정된 인코딩값을 따라간다
- resolveLazily
	- 요청 정보의 파싱(추출)을 최대한 미루도록 설정한다
	- boolean형으로 설정한다, 기본값: false
- servletContext
	- 설정하고 있는 MultipartResolver가 동작할 ServletContext를 지정한다

### MultipartFile 클래스
- 패키지 : org.springframework.web.multipart
- 요청파라미터로 전달된 파일의 정보를 다루는 클래스
- enctype="multipart/form-data"를 필수로 적용해야 한다
- 컨트롤러 메소드의 매개변수로 선언하여 파일 업로드를 처리하는 객체로 사용한다

### 주요 메소드
- boolean isEmpty()
	- 전송된 파일의 존재 여부 확인
- long getSize()
	- 업로드한 파일의 크기를 반환
- String getName()
	- 요청파라미터의 이름(name)
	- 클라이언트쪽에서 전달한 name속성값
- String getOriginalFilename()
	- 업로드한 파일의 원본 이름(origin_name)
- void transferTo(File dest)
	- 파일을 저장할 때 사용하는 메소드(stored_name을 지정할 수 있다)
- byte[] getBytes()
	- 업로드한 파일을 바이트단위 스트림으로 반환받는다
	- 바이트배열 스트림
	- 오라클DB의 BLOB컬럼에 데이터를 저장할 때 사용할 수 있다

### AOP, Aspect Oriented Programming
- 관점 지향 프로그래밍
- OOP(객체지향프로그래밍)처럼 개발 방식을 의미하진 않는다
- 객체 단위로 기능이 개발된 이후에 서로 다른 객체에서 반복되는 기능(코드)를 관점(Aspect)로 정의하고 프로그래밍을 하는 것
- 기능을 구현하고 있는 객체에서 공통 코드를 추출하여 별도의 객체로 구현하는 프로그래밍 기법
- 로그 남기기, 예외 처리, 트랜잭션 관리, 권한 체크 등을 구현한다
    ```java
	ex)	로그인 기능에서 시작 로그 남기기
		게시글 작성 기능에서 시작 로그 남기기
		회원가입 기능에서 시작 로그 남기기

		 -> 모든 기능에서 "시작 로그 남기기"를 수행한다
		 -> "시작 로그 남기기"를 AOP를 통해 추출한다
		 -> 각 기능 구현에서는 "시작 로그 남기기"를 따로 작성하지 않는다
    ```

### aspectj-weaver 라이브러리 추가
- pom.xml 파일에 <dependency>항목 추가
- aspectjrt, Aspectj Runtime : aspect기능 활성화 라이브러리
- aspectjweaver, Aspectj Weaver : aspect라이브러리의 정보를 이용하여 코드를 생성해주는 라이브러리
```java
<dependency>
	<groupId>org.aspectj</groupId>
	<artifactId>aspectjweaver</artifactId>
	<version>${org.aspectj-version}</version>
</dependency>
```

### AOP 용어
- 조인포인트, Joinpoint
	- AOP를 적용할 수 있는 프로그램의 모든 코드
- 포인트컷, Pointcut
	- AOP를 적용하기 위해 지정된 조인포인트
- 어드바이스, Advice
	- 공통 기능으로 들어갈 코드
- 애스팩트, Aspect
	- 포인트컷 + 어드바이스 의 결합
	- 어드바이져(Advisor)라고도 부른다
	- 공통적으로 들어갈 기능과 어디에 적용될 것인가를 합쳐서 부르는 용어
	- @Aspect 어노테이션을 이용하여 적용할 수 있다
- 위빙, Weaving
	- 포인트컷에 어드바이스가 삽입되는 과정을 말한다
	- 애스팩트가 적용되는 과정

### aop 적용하기
- Advice클래스 작성
- @Component 어노테이션 적용
    - servlet-context.xml에 component-scan으로 패키지 등록
- @Aspect 어노테이션 적용
    - servlet-context.xml에 <aop:aspectj-autoproxy />태그 추가
	- ** xmlns:aop="http://www.springframework.org/schema/aop" 추가
	- ** schemaLocation에 http://www.springframework.org/schema/aop, https://www.springframework.org/schema/aop/spring-aop.xsd 추가

### 어드바이스 동작 시점
- Before
	- 조인포인트 전에 실행한다
- After
	- 조인포인트 후에 실행한다
- After Returning
	- 조인포인트에서 성공적인 리턴 이후 실행한다
- After Throwing
	- 실행 중 예외가 발생할 경우 실행한다 (catch코드와 비슷하게 동작한다)
- Around
	- 조인포인트의 실행 전후에 처리될 로직을 직접 조율한다

### 스프링 주요 기능
- Spring DI
	- 스프링 프레임워크에서 객체간의 의존성 관계를 설정한다
	- 의존성 주입 - xml설정파일 또는 어노테이션을 활용한다
- Spring AOP
	- 프로그램에서 공통으로 필요한 기능을 관점으로 분리해서 관리하는 것
- Spring JDBC
	- 데이터베이스처리하는 영속성 프레임워크와 연결해주는 기능
	- 영속성 프레임워크 : MyBatis, Hibernate, iBatis 등
- Spring MVC
	- Model, View, Controller 컴포넌트들 사이에서 의존 관계를 유지한다
	- MVC 디자인 패턴을 유지한다

### 마이바티스 스프링에서 적용할만한 settings
    ```java
	<settings>
		<!-- 컬럼의 Snake Case를 DTO의 Camel Case로 자동 변환하는 설정 -->
		<setting name="mapUnderscoreToCamelCase" value="true"/>
		
		<!-- SQL에서 여분(불필요한) whitespace(공백문자)를 제거한다 -->
		<setting name="shrinkWhitespacesInSql" value="true"/>
		
		<!-- JDBC타입이 명시되지않았을 때 null값을 처리하는 방법을 설정한다 -->
		<setting name="jdbcTypeForNull" value="NULL"/>
	</settings>
    ```