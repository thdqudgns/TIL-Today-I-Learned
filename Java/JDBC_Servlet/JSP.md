# :pushpin: JSP

### JSP, Java Server Page
- 자바코드를 이용해서 **서버 페이지를 작성**하는 문법(문서)
- Servlet/JSP 컨테이너에 의해서 JSP코드는 Servlet코드로 변환된다
- Serlvet은 Java코드 안에 HTML코드를 작성하는 형태
```js
ex)	resp.getWriter().append("<h1>하이</h1>");
```
- **JSP는 HTML코드 안에 Java코드를 작성하는 형태**
```js
ex)	<h1><%=emp.getEname() %></h1>
```
- Servlet코드의 응답으로 HTML코드를 작성하는 것이 너무 힘들다
- JPS코드는 HTTP응답으로 사용되는 HTML문서를 좀 더 쉽게 작성하려고 사용한다

### JSP 기본 태그
1. 스크립트릿, Scriptlet	<%	%>
2. 선언, Declaration		<%!	%>
3. 표현식, Expression		<%=	%>
4. 지시자, Directive		<%@	%>
5. 주석, Comment		<%--	--%>

### JSP 기본 태그 1 - 스크립트릿 <%	%>
- JSP파일(문서)에서 자바 코드를 작성하기 위해 지정하는 태그영역
- 서블릿의 doGet(), doPost() 메소드 안에 작성하는 것처럼 자바코드를 작성한다
- 제어문, 메소드호출, 연산 등의 수행코드를 작성할 수 있다
- 접근제한자를 적용하는 변수 선언, 메소드를 정의하는 코드는 작성할 수 없다

### JSP 기본 태그 2 - 선언 <%!	%>
- JSP페이지에서 사용할 변수(멤버필드), 메소드를 정의할 때 사용하는 영역
- 변환된 서블릿의 멤버필드, 멤버메소드로 만들어진다
- 수행코드를 작성하면 안된다

### JSP 기본 태그 3 - 표현식 <%=	%>
- HTML문서에 표현될(출력될) 내용을 작성하는 영역
- 스크립트릿을 이용하여 out.print() 메소드를 사용한 것과 같다
```js
	ex)	<%="HIHI" %>

		->	<% out.print("HIHI"); %> 와 동일하다
```
- 자바 데이터(변수, 상수, 객체 등)를 HTML문서에 간편한게 출력할 수 있다

### JSP 기본 태그 4 - 주석 <%--	--%>
- **JSP코드의 클라이언트(브라우저) 주석**
```js
  - HTML 주석		<!-- -->
	브라우저가 HTML코드(태그)를 해석하지 못하게 한다

  - CSS 주석		/* */
	브라우저가 CSS를 해석하지 못하게 한다
	<style>태그 안에서 사용한다

  - Javascript 주석	/* */ 또는 //
	브라우저가 JS를 해석하지 못하게 한다
	<scritp>태그 안에서 사용한다
```
- **JSP코드의 서버(Tomcat, WAS) 주석**
```jsp
  - JSP 주석		<%-- --%>
	브라우저로 주석코드를 보내지 않는다
	서블릿코드로 변환되지 않는다

	JSP코드에 대한 설명을 적을 때 사용한다

  - Java 주석		/* */ 또는 //
	브라우저로 주석코드를 보내지 않는다
	서블릿코드로 변환되지만 실행은 되지 않는다

	스크립트릿태그 안에서 사용한다
```

### JSP 기본 태그 5 - 지시자 <%@	%>
- Servlet/JSP 컨테이너에게 메시지를 보내기 위한 영역
- JSP가 해석되고 변환되어 실행될 때까지 필요한 설정값을 작성하는 태그
- 서버에서 해석되기 때문에 브라우저에는 전달되지 않는다

### JSP 지시자 작성법
```jsp
<%@ 지시자종류 속성종류1="값1" 속성종류2="값2" ... %>
```
- 지시자 종류에 따라 속성 항목도 달라진다

### JSP 지시자의 종류
- page
	- JSP페이지의 전반적인 환경설정을 부여한다
- include
	- 다른 파일(JSP파일)의 내용을 현재 JSP페이지 내에 삽입할 때 사용한다
- taglib
	- 태그 라이브러리 기능을 사용할 수 있도록 설정한다(활성화 시킨다)

### include 지시자
- file속성을 이용하여 삽입될 내용이나 HTML문서를 지정한다
```jsp
<%@ include file="추가할파일경로" %>
```

### page 지시자
- language
	- JSP페이지에서 사용할 서버사이드 스크립트의 언어형식을 지정한다
	- 스크립트릿(Scriptlet)에서 사용할 언어를 지정하는 속성
	- 기본값: java
	- 사용가능한 값: java
- contentType
	- JSP를 통해서 생성되는 응답데이터의 형식을 지정하는 속성
	- 브라우저가 응답데이터를 받고 지정된 형식을 참고하여 해석하고 활용한다
	- (HTML로 지정되어있으면 화면에 렌더링)
	- (PDF로 지정되어있으면 PDF Reader를 통해 읽기)
	- (일반 파일로 지정되어있으면 파일 다운로드)
	- 형식은 MIME타입을 사용하여 지정한다
- pageEncoding
	- JSP파일이 작성된 인코딩 방식
	- JSP파일 자체의 한글인코딩을 지정할 때 사용한다
- import
	- JSP페이지에서 사용할 외부 클래스를 import하는 속성
    ```jsp
	<%@ page import="java.util.List" %>
	<%@ page import="dto.Emp" %>
    ```
- errorPage
	- JSP에서 에러(예외)가 발생하면 이동될 페이지를 지정하는 속성
- isErrorPage
    - 해당 JSP페이지를 예외처리 전용 페이지로 설정한단
	- true/false (기본값: false) 로 설정한다
	- exception키워드를 사용할 수 있게 된다
	- exception키워드에는 발생한 예외 정보를 담고 있다

### MIME타입, Multipurpose Internet Mail Extension
- 전송하는 문서(데이터)의 형식을 상대방에게 알려주기 위해 사용하는 표현방식
- 웹 문서의 올바른 해석방법을 브라우저에게 알리기위해 Content-Type으로 설정할 때 사용한다
```js
	text/html; charset=UTF-8
		텍스트기반의 HTML문서, 한글인코딩은 UTF-8을 이용했다

	text/plain
		단순 텍스트

	image/jpeg
	image/png
		이미지파일, 압축(표현)방식에 따라 보조타입을 적는다

	application/json
		JSON 형태의 데이터

	application/octet-stream
		바이너리파일, 이진파일
		모든 파일에 대응하는 형식
```

### JSP 내장 객체, Built-in Object
- JSP페이지에서 **객체 생성없이 바로 사용**할 수 있는 객체
- JSP를 서블릿으로 변환할 때 자동으로 생성해준다

### 내장 객체의 종류
- 입출력(요청,응답) 관련 객체
	- request : HTTP요청 정보 객체(HttpServletRequest)
	- response : HTTP응답 정보 객체(HttpServletResponse)
	- out : 응답 출력 스트림 ( PrintWriter, response.getWriter() )
- 서블릿 관련 객체 (JSP가 추후에 변환될 서블릿을 뜻한다)
	- page : 서블릿으로 변환된 자기 자신 객체 (Object타입)
	- (서블릿 클래스에서 this라고 쓴 것과 같다)
	- config : 서블릿의 정보를 저장하고 있는 객체 (ServletConfig 타입)
- 정보 전달 객체
	- JSP 컨텍스트영역(Context Scope)에 정보를 저장하거나 꺼내올 수 있도록 만들어진 객체
	- 컨텍스트 정보 전달 객체
	- pageContext : page스코프의 컨텍스트 정보에 접근할 수 있는 객체
	- request : request스코프의 컨텍스트 정보에 접근할 수 있는 객체
	- session : session스코프의 컨텍스트 정보에 접근할 수 있는 객체
	- application : application스코프의 컨텍스트 정보에 접근할 수 있는 객체
- 예외 처리 객체
	- exception : JSP페이지에서 예외 정보를 확인할 수 있도록 해주는 객체

### 컨텍스트, Context
- 단어의 뜻 : 문맥, 전후 사정
- 프로그램에서 사용하고 있는 전반적인 **설정값, 속성값, 상황** 등을 표현하는 용어
- 프로그램과 연관된 모든 정보 -> 프로그램이 실행될 때 메모리에 로드된 모든 요소

### 컨텍스트 영역의 유효범위(Scope)
- 웹 어플리케이션에서 컨텍스트정보(컨텍스트변수)를 저장하고 사용할 수 있도록 구분한 범위
- **page 영역**
	- **JSP파일 하나**가 처리되는 동안 유지되는 영역
- **request 영역**
	- **하나의 요청**(request)이 처리되는 동안 유지되는 영역
	- HTTP요청을 받아 HTTP응답이 이루어질 때까지 영역이 유지된다
	    - Controller에서 요청을 받고 MODEL값을 View에 전달하고 View가 응답될 때까지 유지된다
- **session 영역**
	- 연결된 하나의 클라이언트(브라우저)에게 **서비스하는 동안** 유지되는 영역
	- **페이지 이동이나 새로고침에도 영역이 유지된다**
	- 세션 컨텍스트정보를 이용하여 **로그인 유지**에 사용한다
- **application 영역**
	- 어플리케이션이 구동되는 동안 유지되는 영역
	    - 톰캣서버가 켜지고 꺼질 때까지 유지
	- 클라이언트들의 정보 보다는 서버 자체에 대한 정보를 저장한다

### JSP 액션 태그, Action Tag
- JSP의 문법 요소 중 하나
- JSP페이지에서 수행할 특정 동작들을 태그로 만들어놓은 것

### 형식
```jsp
<jsp:수행명령 속성="속성값"></jsp:수행명령>
```
- ==================================================

```jsp
<jsp:useBean id="bean속성명" class="클래스명" [scope="스코프지정"]>
</jsp:useBean>
```
- [자바빈(JavaBean)](https://github.com/thdqudgns/TIL-Today-I-Learned/blob/main/Java/JDBC_Servlet/JSP.md#jsp-%EC%9E%90%EB%B0%94-%EB%B9%88-java-bean) 객체를 생성한다
- JSP에서 사용할 JavaBean객체를 생성하고 지정한 Scope영역의 컨텍스트 정보로 저장한다
- scope를 지정하지않으면 page영역에 저장된다
- scope속성값
	- page(기본값) | request | session | application
- ==================================================
```jsp
<jsp:setProperty name="bean이름" property="필드명" [value="설정값"] />
```
- JavaBean의 프로퍼티에 값을 설정한다
- DTO클래스의 setter를 실행하도록 되어있다
	- DTO클래스에 setter가 정의되어있지 않으면 에러발생한다
- ==================================================

```jsp
<jsp:getProperty name="bean이름" property="필드명" />
```
- JavaBean의 프로퍼티의 값을 불러온다
- DTO클래스의 getter를 실행하도록 되어있다
	- DTO클래스에 getter가 정의되어있지 않으면 에러발생한다 
- ==================================================

```jsp
<jsp:forward page="이동할페이지" />
```
- JSP에서 포워딩을 수행하는 태그
- ==================================================

```jsp
<jsp:param value="값" name="변수명" />
```
- 포워딩되는 페이지에 전달 파라미터를 추가할 수 있다
- 포워딩된 페이지에서 request.getParameter("name")을 이용하여 전달파라미터를 사용할 수 있다
- ==================================================

```jsp
<jsp:include page="삽입할페이지URL" />

<jsp:include page="삽입할페이지URL">
	<jsp:param value="값" name="변수명" />
</jsp:include>
```
- JSP페이지에 다른 페이지를 내용으로 추가할 때 사용한다
- include 지시자와 비슷한 기능을 수행한다
    ```jsp
	(include지시자	<%@ include file="" %>)
	(include액션	<jsp:include page="" />)
    ```
    - include지시자와 include액션의 차이점
    ```jsp
	include지시자   JSP코드를 하나의 JSP로 합치고나서 컴파일한다
	include액션 	각각의 JSP코드를 컴파일한 후 결과물로 합친다

	include지시자   전달 파라미터를 전달할 수 없다
	include액션 	전달 파라미터를 전달할 수 있다

	include지시자   정적 페이지를 포함시킬 수 있다
	include액션 	정적,동적 페이지를 포함시킬 수 있다
    ```

### JSP 자바 빈, Java Bean
- JSP에서 사용하는 자바클래스 **객체(인스턴스)**
- 컨텍스트 영역에 컨텍스트 정보로 등록된 자바 객체를 자바빈이라고 부른다
- JSP를 통해서 인스턴스화된 객체를 지칭한다 (메모리에 로드된 상태)
- **자바 빈 설계 원칙에 맞게 작성된 클래스**를 사용한다
- **DTO로 만든 클래스를 자바 빈 객체로 사용**한다

### 자바 빈 설계 원칙(규약)
- DTO 작성 방법
- 반드시 패키지가 있어야한다
- 디폴트 패키지에 작성하지 않아야한다
- **public 클래스**로 생성한다
- **멤버필드는 private** 접근제한자를 가진다
- 생성자는 디폴트 생성자가 반드시 존재해야 한다
- 매개변수있는 생성자는 작성하지 않는 것이 좋다
	- 매개변수있는 생성자는 모든 멤버필드를 초기화하는 용도로 만들기도 함
	- **아예 생성자 코드를 작성하지 않는 것이 좋다**
- **캡슐화**가 되어있어야한다
- 멤버필드에 대한 **getter, setter**를 구현한다
- getter, setter의 접근제한자를 public으로 작성한다
- getter의 반환타입이 boolean이라면 메소드명을 get대신 is로 시작할 수 있다
	- JSP에서 등록된 자바 빈의 멤버 필드를 Property(프로퍼티)라고 부른다

### POJO, Plain Old Java Object
- 객체의 규모를 줄이고, **가볍고 최소화**하여 개발한 객체
- **extends나 implements를 최소화**하여 작성한다
- 최대한 Object만 부모클래스로 가지도록 설계한다
- 간결하게 객체를 만들자는 뜻

### 페이지 이동
- 서버에서 수행하는 화면(페이지) 전환
- 클라이언트 입장에서 보면 보고있는 화면이 변경된다

- **포워드, forwarding**
	- **request스코프 영역을 유지**하며 화면을 전환하는 방식
	- 요청객체(request), 응답객체(response)가 유지된다
	- **요청 URL이 변경되지 않는다 -> 브라우저의 주소입력창이 안바뀐다**
	- Controller가 request영역에 MODEL값을 저장한다
	- View로 Forwarding을 하면 MODEL값을 유지한다
	```jsp
		ex)	req.getRequestDispatcher("페이지URL").forward( req, resp );

		ex)	<jsp:forward url="페이지URL" />
	```

- **리다이렉트, redirection**
	- 새로운 요청을 발생시켜 화면을 전환하는 방식이다
	- **request 스코프 영역이 새롭게 만들어진다**
	- 요청객체(request), 응답객체(response)가 새롭게 생성된다
	- **URL이 변경된다**(브라우저의 주소입력창이 바뀐다)
	```jsp
		ex)	response.sendRedirect("페이지URL");
	```

