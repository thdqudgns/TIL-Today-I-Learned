# :pushpin: Servlet

### 서블릿, Servlet
- Servlet = Server + Applet
- 서버에서 동작하는 애플릿 프로그램이라는 뜻을 가지고 있다
	- 애플릿, Applet
	    - 자바 언어로 개발되어 바이트코드 형태로 배포되는 프로그램
	    - JVM만 존재한다면 애플릿 프로그램을 실행할 수 있게 된다
- 서블릿은 JVM이 포함되어있는 웹 서버에서 동작하게 된다 ( Tomcat )

### 서블릿 스펙, Servlet Spec, Servlet Specification
- 웹 어플리케이션을 개발하기 위한 자바의 기술(API)
- 버전으로 표현한다
- Apache Tomcat 9버전에서는 서블릿 스펙 4.0을 지원한다
- 톰캣서버는 자바웹개발에 필요한 서블릿API, JSP API를 가지고 있다

### 서블릿 클래스, Servlet Class
- 서블릿 스펙에 맞춰 개발된 자바 클래스를 뜻한다
- javax.servlet.http.HttpServlet클래스를 상속받아 구현한 클래스
- 서블릿 클래스를 줄여서 서블릿이라고 부르기도 한다
- MVC패턴으로 웹을 구현할 때 Controller역할을 담당한다

### 서블릿 4.0 JavaDocumentation
https://javaee.github.io/javaee-spec/javadocs/index.html?javax/servlet/package-summary.html

### JSP 2.3 JavaDocumentation
https://docs.oracle.com/javaee/7/api/index.html?javax/servlet/jsp/package-summary.html

### 서블릿의 동작 원리
클라이언트 HTTP 요청 -> Apache Tomcat 서버( WEB서버 + WAS서버 ) -> 서블릿 컨테이너   
-> URL매핑을 참고함 -> 서블릿 클래스 객체 -> 서블릿객체의 service() 메소드 호출됨 (요청Method를 확인한다)   
-> 요청메소드에 따라 doGet() 또는 doPost() 메소드 호출 -> 서블릿 컨테이너 -> Apache Tomat 서버 -> 클라이언트 HTTP 응답

### 서블릿 컨테이너, Servlet Container
- 서블릿이 **동작되는 환경을 구축**하는 역할을 담담하는 소프트웨어 요소
- **서블릿 객체를 생성하고 실행**시켜주는 역할을 수행한다
- WAS서버와 서블릿 객체를 연결하는 중간다리 역할을 수행한다
- 요청URL-Pattern 과 서블릿 객체를 1:1로 매핑해놓고 클라이언트의 요청에 따라 서블릿 객체를 실행시킨다 -> 매핑 테이블
- 매핑 테이블은 web.xml(배포관리자) 또는 @WebServlet 어노테이션에 따라 작성된다
- HTTP요청 정보를 HttpServletRequest 객체로 생성한다
- HTTP응답 정보를 HttpServletResponse 객체로 생성한다
	- HttpServletRequest, HttpServletResponse객체를 서블릿 객체로 전달한다

### 서블릿 객체의 라이프 사이클(생명 주기)
```java
	객체생성	-> init() 실행	-> service() 실행	-> destroy() 실행
	(생성자 호출)	(서블릿 초기화)	(doGet(), doPost()	(서블릿 정리)
	(객체 초기화)			 반복적으로 실행)	(서버 종료)
```
- 객체 생성
	- URL요청에 따른 서블릿 객체가 처음으로 사용될 때 수행한다
- init()
	- 객체 생성이후에 곧바로 호출된다
- service()
	- URL 요청이 있을 때마다 반복적으로 호출된다
	- Request Method에 따라서 doGet() 또는 doPost()를 호출해준다
- destroy()
	- 서버가 종료되는 시점에 호출된다
- 서버가 켜질 때 서블릿객체가 같이 생성되지 않는다
- 서버가 켜진 이후에 처음으로 요청이 와서 서블릿이 사용될 때
    - 객체 생성 - init() - service() - 응답 순으로 진행된다
- 객체가 생성된 이후에 서블릿이 사용될 때 (첫번째 요청이 아닌 다음부터)
	- service() - 응답 순으로 진행된다

### WEB서버
- HTTP요청, HTTP응답을 처리하는 기능을 가진 서버
- 클라이언트의 요청을 받아서 URL에 해당하는 자원(파일)을 응답한다
	- 자원은 정적 자원을 처리할 수 있다
	- HTML, CSS, JS, Image, PDF 등등

### WAS, Web Application Server
- 동적 자원을 처리할 수 있는 WEB서버의 추가 모듈
- 동적 자원 : 프로그램 코드를 실행한 후에 만들어지는 자원(데이터)
- 웹 어플리케이션(프로그램 코드)를 해석하고 실행시키는 기능을 가진 서버
	- Servlet/JSP 코드를 해석하고 실행시킨다 (JVM기능)

### HTTP요청이 GET메소드로 전달되는 상황
- 단순히 URL만 요청했을 때 (브라우저 주소입력창에 URL입력하고 엔터!)
- form 태그에 method를 get로 설정하고 submit했을 때
- a 링크태그를 클릭했을 때
- location.href = "URL" 로 페이지 이동했을 때
- link 태그나 script 태그로 자원(파일)을 로드했을 때

### HTTP요청이 POST메소드로 전달되는 상황
- form 태그에 method를 post로 설정하고 submit했을 때

### 요청 파라미터의 한글 인코딩처리방식 설정하기
- 웹에서 사용하는 한글 인코딩은 UTF-8이다
- 요청 파라미터도 UTF-8형식으로 전달된다
- 아파치웹서버는 ISO-8859-1 (Latin 1) 인코딩을 사용한다
	- 한글을 표현하지 않는 인코딩방식
- 한글이 웹 서버를 통과할 때 한글 형태를 유지하지 못하고 깨진다
- 서블릿에서 원본 데이터형식인 UTF-8로 다시 합성해서 사용해야 한다
	- req.setCharacterEncoding("UTF-8");

### HTTP요청의 GET, POST 메소드
> GET메소드는 서버의 자원을 **조회**할 때 사용한다 (SELECT)   
POST메소드는 서버의 자원을 **삽입,수정,삭제**할 때 사용한다 (INSERT,UPDATE,DELETE)

> 전달파라미터가 **짧은(단순한)** 데이터이거나 없으면 GET방식을 사용한다   
전달파라미터가 **긴(복잡한)** 데이터이거나 **민감한** 정보라면 POST방식을 사용한다

> GET메소드는 URL뒤에 **쿼리스트링**으로 전달파라미터를 붙여서 서버로 전달하기에 URL에 전달데이터가 노출된다

> POST메소드는 **요청메시지의 BODY영역에 쿼리스트링**으로 전달파라미터를 추가해서 서버로 전달한다   
전달 데이터가 겉으로 노출되지 않는다
