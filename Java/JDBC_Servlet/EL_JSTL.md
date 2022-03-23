# :pushpin: EL_JSTL

### EL, Expression Language, 표현 언어
- JSP에서 값을 출력하는 코드를 쉽게 사용할 수 있도록 만들어진 문법
- 표현식(Expression Tag, <%= %>)태그와 비슷한 역할을 담당한다
- 주로 컨텍스트 정보를 다룰 때 사용한다
- JSTL 태그 라이브러리와 함께 사용하기에 적합하다

### EL 구문 형식
```jsp
	${ }

	ex)	${10 + 20 }
		 -> <%=10 + 20 %>

		 -> 브라우저에 30 이 출력된다
```

### EL 연산자
- 산술 : +, -, *, /, div, %, mod
- 관계 : ==, eq, !=, ne, <, lt, >, gt, <=, le, >=, ge
- 논리 : &&, and, ||, or, !, not
- 조건 : (조건식)? 참일 때 반환: 거짓일 때 반환
- null검사 : empty 대상
```jsp
	ex)	${empty obj }
		 ->obj객체가 null이라면 true 반환

	ex)	${not empty obj }
		 ->obj객체가 null이 아니라면 true 반환
```

### EL 내장 객체
- **pageContext:** JSP내장객체인 pageContext와 동일
    - pageScope
    - requestScope
    - sessionScope
    - applicationScope
	- 각 컨텍스트 영역의 정보에 접근할 수 있는 객체
    ```jsp
	ex)	<%=request.getAttribute("data") %>
		-> ${requestScope.data }

		**EL의 Scope객체들은 생략가능하다

		${requestScope.data }
		-> ${data }

		**스코프를 지정하지 않고 컨텍스트 정보를 사용하면
		 page->request->session->application 순으로 찾아서 사용한다
    ```
- **param:** 전달파라미터에 접근할 수 있는 객체
    ```jsp
	ex)	<%=request.getParameter("data") %>
		-> ${param.data }
    ```
- **paramValues:** request.getParameterValues("name")의 기능을 수행하는 객체
    ```jsp
	ex)	<% String[] genres = request.getParameterValues("genre"); %>
		<%=genres[0] %>
		<%=genres[1] %>

		-> ${paramValues.genre[0] }
		-> ${paramValues.genre[1] }
    ```
- **header:** 요청 Header정보에 접근할 수 있는 객체
    ```jsp
	ex)	<%=request.getHeader("host") %>
		-> ${header.host }
    ```
- **headerValues:** 같은 이름의 Header정보에 접근할 수 있는 객체
    ```jsp
	ex)	<% String[] datas = request.getHeaderValues("data"); %>
		<%=datas[0] %>
		<%=datas[1] %>

		-> ${headerValues.data[0] }
		-> ${headerValues.data[1] }
    ```
- **cookie:** request.getCookie() 로 반환받은 Cookie[] 데이터를 Map으로 사용할 수 있도록 제공하는 객체
- **initParam:** application.getInitParam("name")의 기능을 제공하는 객체
    - 초기화 파라미터, Initial Parameter
	- 웹 어플리케이션에 설정된 기본 파라미터(변수, 설정값)

### JSTL, JSP Standard Tag Library
- JSP에서 사용 가능한 표준 태그 라이브러리
- JSP코드의 가독성이 좋아진다
- 자바코드로 작성해야하는 상황을 최소화시켜준다
- 추가 라이브러리 파일이 필요하다
- JSP페이지에서 taglib지시자를 이용하여 태그라이브러리를 활성화해야 한다

### 다운 URL
- http://archive.apache.org/dist/jakarta/taglibs/standard/binaries/
- jakarta-taglibs-standard-1.1.2.zip 파일 다운 & 압축 해제
- lib폴더의 jstl.jar, standard.jar 두 파일 사용

### JSTL에서 제공하는 5가지 커스텀 태그
- **Core**
	- 논리 판단(조건문), 반복문 들의 제어문 기능을 지원하는 태그
	- 다른 JSP페이지를 호출하는 기능도 제공한다
- **Format**
	- 날짜, 숫자, 시간 데이터의 서식을 지정하는 태그
- **Sql**
	- 데이터베이스 처리
- **Xml**
	- XML문서에 대한 처리
- **Functions**
	- 문자열 처리함수를 사용할 수 있게 해주는 태그
	- 단독으로 태그만 사용할 수 없고 EL과 함 께 사용해야 한다

### JSTL taglib 지시자
- JSTL 태그 라이브러리를 활성화시키는 지시자가 필요하다
- 형태
```jsp
<%@ taglib prefix="접두어" uri="라이브러리식별값" %>
```
- **Core**
```jsp
<%@ taglib prefix="c" uri="http://java.sun.com/jsp/jstl/core" %>
```
- **Format**
```jsp
<%@ taglib prefix="fmt" uri="http://java.sun.com/jsp/jstl/fmt" %>
```
- **Sql**
```jsp
<%@ taglib prefix="sql" uri="http://java.sun.com/jsp/jstl/sql" %>
```
- **Xml**
```jsp
<%@ taglib prefix="x" uri="http://java.sun.com/jsp/jstl/xml" %>
```
- **Functions**
```jsp
<%@ taglib prefix="fn" uri="http://java.sun.com/jsp/jstl/functions" %>
```

### JSTL Core 라이브러리
- **c:out : JSP Writer를 이용한 브라우저 출력**
```jsp
  <c:out value="출력할 데이터"
	default="value값이 null일 때 대체되어 출력할 값"
	escapeXml="true|false" />

	** escapeXml 속성
	 true - < > & " ' 를 기호문자 그래도 출력(기본값)
	 false - 태그로 반영되어 출력
```
- **c:set : JSP변수 등록, 설정(컨텍스트 영역에 등록된다)**
```jsp
  <c:set var="변수명" value="값" [scope="영역"] />

  <c:set var="변수명" [scope="영역"]>
	값
  </c:set>

	**scope: page(기본값) | request | session | application
```
- **c:remove : JSP변수 제거**
```jsp
  <c:remove var="변수명" [scope="영역"] />

	**scope를 지정하지 않으면 모든 컨텍스트 영역의 해당 변수를 제거한다
```
- **c:if : 조건문**
```jsp
  <c:if test="조건식">
	//조건식 결과가 true일 때 수행할 코드 작성영역
  </c:if>
```
- **c:choose : 다중 조건문(else if구문)**
```jsp
  <c:choose>
	<c:when test="조건식1">
	</c:when>

	<c:when test="조건식2">
	</c:when>

	...

	<c:otherwise>
	</c:otherwise>

  </c:choose>
```
- **c:forEach : 반복문, 컬렉션이나 맵의 Iterator**
```jsp
  <c:forEach var="변수"
	begin="시작값" end="끝값" step="증가값"

	items="반복될객체"

	varStatus="반복정보를 저장할 객체">

    <%-- ${var}변수를 이용한 반복코드 작성 --%>

  </c:forEach>
```
- **c:import : 자원 삽입(페이지 삽입)**
```jsp
  <c:import url="삽입할 페이지" />

  <c:import url="삽입할 페이지">
	<c:param name="키" value="값" />
  </c:import>

  ** <jsp:include>와 같은 기능을 수행한다
  ** 전달 파라미터를 전달하고 처리할 수 있다 (동적 처리 가능)
```

### JSTL Format 태그
```jsp
  <%@ taglib prefix="fmt" uri="http://java.sun.com/jsp/jstl/fmt" %>
```
- **formatNumber : 숫자형식으로 서식화하여 출력하는 태그**
```jsp 
  <fmt:formatNumber
	value="값"

	type="숫자의 표현방식"
	pattern="서식패턴 지정"

	currencySymbol="통화심볼"
	currencyCode="통화코드"

	groupingUsed="true|false"

	var="변수"
	scope="컨텍스트영역" />


	**type		number(기본값) | currency | percent

	**pattern	데이터의 출력 서식을 직접 지정한다
		# - 유효숫자가 존재하면 숫자를 표시한다
		0 - 자리수만큼 표현하고 빈자리는 0으로 채운다

		(java.text.DecimalFormat에 정의된 패턴을 사용한다)

	**currencyCode	ISO 4217에 지정된 표준을 사용한다

	**var,scope를 이용하여 변수에 저장하면 화면에 출력하지 않는다
```
- **formatDate : 날짜형식으로 서식화하여 출력하는 태그.** java.util.Date타입의 데이터를 사용한다
```jsp
  <fmt:formatDate
	value="값"

	dateStyle="날짜표현방식"
	timeStyle="시간표현방식"

	pattern="패턴지정문자"

	var="변수"
	scope="컨텍스트영역" />

	**type		date(기본값) | time | both

	**dateStyle, timeStyle
		default | short | medium | long | full

	**pattern
		yy, MM, dd, hh, mm, ss

		a, HH, hh, KK, kk, z, Z, X, S


		MM - 월 (대문자 M)
		mm - 분 (소문자 m)

		HH - 24시간기준 시 (자정이 00시, 대문자 H)
		hh - 12시간기준 시 (자정이 12시, 소문자 h) 14시가 02시로 나온다

		kk - 24시간기준 시 (자정이 00시, 소문자 k)
		KK - 12시간기준 시 (자정이 12시, 대문자 K) 14시가 02시로 나온다

		S - 밀리초

		a - 오전/오후

		z, Z, X - time zone(시간대)
```

