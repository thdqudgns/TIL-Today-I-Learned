# :pushpin: 그 외 다른 것들..

### 파일 업로드
- 클라이언트(브라우저)가 전송한 파일을 웹 어플리케이션이 받아들여 처리하는 것
- 서버에서 파일 업로드 라이브러리를 이용하여 업로드된 파일을 처리할 수 있다
	1. commons-fileupload 라이브러리
	2. COS 라이브러리
- 클라이언트에서 form 태그의 인코딩형식(enctype)을 multipart/form-data로 설정해야 한다
- form 태그의 enctype속성
    - 전달 파라미터의 인코딩 방식을 지정한다
    - multipart/form-data 방식
	    - 전송할 각 전달데이터를 boundary(경계선문자)를 이용해서 구분한다
	    - 각 데이터는 2진 데이터 형식으로 전달한다
	    - -> 파일의 본문내용을 전송할 수 있게 해준다
    - application/x-www-form-urlencoded 방식 (기본값)
	    - 전달파라미터를 쿼리스트링으로 인코딩한다

### Commons Fileupload 라이브러리 다운받기
1. http://www.apache.org/ 접속
2. Projects 링크 클릭 - Proejct List 선택
3. Commons 링크 찾아서 클릭
4. Fileupload 링크 찾아서 클릭 (http://commons.apache.org/proper/commons-fileupload/)
5. 왼쪽 메뉴에서 Download 클릭
6. Binaries에서 commons-fileupload-1.4-bin.zip 파일 다운
7. 압축 해제
8. commons-fileupload-1.4.jar 파일 사용

### application/x-www-form-urlencoded 인코딩
```jsp
<< Request Message Body >>
title=Banana&data1=hihihi&data2=1234&upfile=[원본 파일의 이름]
```

### multipart/form-data 인코딩
```jsp
<< Request Message Body >>
title=Banana
----WebKitFormBoundaryiRXBqIIvqw1JBt54
data1=hihihi
----WebKitFormBoundaryiRXBqIIvqw1JBt54
data2=1234
----WebKitFormBoundaryiRXBqIIvqw1JBt54
upfile=[원본 파일의 내용 전부]
----WebKitFormBoundaryiRXBqIIvqw1JBt54
```

### Commons-IO 라이브러리 다운받기
- commons-fileupload 라이브러리는 commons-io 라이브러리에 의존적이다
	- -> commons-fileupload 라이브러리를 구현하기 위해 commons-io라이브러리를 사용하고 있다
1. http://www.apache.org/ 접속
2. Projects 링크 - Project List 클릭
3. Commons링크 찾아서 클릭
4. IO 링크 찾아서 클릭
5. 왼쪽 DOWNLOAD 메뉴 클릭
6. Binaries 섹션에서 commons-io-2.11.0-bin.zip 파일 다운로드
7. 압축 해제
8. commons-io-2.11.0.jar 파일 사용

### COS 라이브러리 다운
- http://www.servlets.com/ 접속
- 왼쪽 메뉴에서 COS File Upload Library 클릭
- 밑에 Download 섹션 확인
- cos-20.08.zip 다운로드
- 압축 해제
- lib폴더에서 cos.jar 파일 사용

### COS 파일 업로드 라이브러리
- com.oreilly.servlet.MultipartRequest 클래스를 이용한다
- 객체의 생성자를 통해서 업로드 설정과 수행을 쉽게 해결할 수 있다

### MultipartRequest 클래스의 생성자
```jsp
  public MultipartRequest (

	HttpServletRequest request	//전달파라미터를 가진 요청정보객체

	, String saveDirectory		//업로드 파일 저장 경로(위치)

	, int maxPostSize		//업로드 제한 크기

	, String encoding		//인코딩(한글 UTF-8)

	, FileRenamePolicy policy	//중복된 파일이름을 처리하는 정책

  );

  ** 객체를 생성할 때 파일 업로드도 같이 수행된다
```

### MultipartRequest 주요 메소드
- String getParameter(String name);
	- 전달 파라미터를 얻어온다
- String[] getParameterValues(String name);
	- 같은 이름으로 전달된 파라미터들을 배열로 반환한다
- File getFile(String name);
	- 업로드된 파일 객체 얻기
- String getFilesystemName(String name);
	- 업로드된 파일의 저장된 이름 반환
- String getOriginalFileName(String name);
	- 업로드된 파일의 원본 이름 반환
- String getContentType(String name);
	- 업로드된 파일의 형식(MIME타입)

### 서블릿 필터, Servlet Filter
- 클라이언트의 요청정보, 서버(서블릿)의 응답정보를 필터링할 때 사용하는 기술
- 서블릿이 실행되기 전, 실행된 이후에 필터클래스의 기능이 수행된다
- javax.servlet.Filter 인터페이스를 상속받아 기능을 구현한다

### 서블릿 필터의 주요 메소드
- doFilter(ServletRequest, ServletResponse, FilterChain)
	- 요청을 처리하고 다음으로 넘길 때마다 호출되는 메소드
	- -> 서블릿의 요청과 응답에 추가 작업을 수행할 때 사용한다
	- FilterChain을 이용한 doFilter()를 호출하지 않으면 서블릿 클래스로 요청이 전달되지 않는다

### 주로 사용하는 필터의 기능
- 전달 파라미터 인코딩 설정
- 사용자의 인증 관리(세션정보 검증 기능)
- 이미지의 변환 및 압축 처리
- 암호화 처리

### 무상태 프로토콜, Stateless Protocol
- 통신 상황에 대한 상태 정보를 저장하지 않는 프로토콜을 뜻한다
- 통신 상태 정보 : 서버-클라이언트 간 통신 이력(정보)
- 이전 통신과 다음 통신 상태에 대한 연결점이 없는 프로토콜
- 요청이 발생하면 서버는 이전에 요청해 왔던 사용자인지 새로운 사용자인지 구분할 수 없다
- 프로토콜만으로는 동일 사용자의 연속된 요청인지 판단할 수 없다
- HTTP프로토콜(WEB)은 무상태 포로토콜이다
    - -> 상태 관리 매커니즘(기술)이 필요하다

### 상태관리 매커니즘
- 사용자(클라이언트)의 정보를 유지하는 기술
- 쿠키, Cookie
	- 서버의 정보(데이터)를 클라이언트에 저장하는 기술
- 세션, Session
	- 서버-클라이언트 연결 상태를 유지하는 기술

### 쿠키, Cookie
- 웹 서버가 클라이언트에 정보(데이터)를 저장하는 기술
- 웹 서버는 필요할 때 쿠키 정보를 사용할 수 있게 된다
- javax.servlet.http.Cookie 클래스를 이용하여 관리한다
- 쿠키 정보는 name=value 쌍으로 이루어진 정보이다
- 여러 개의 쿠키를 저장할 수 있다
- 브라우저는 쿠키를 도메인별로 저장하고 관리한다
- 쿠키는 유지시간(MaxAge)을 가지고 있다
	- 쿠키를 보관하고 유지하는 시간
	- 기본값은 무한으로 설정되어있음
	- 초 단위로 설정 가능하다

### 쿠키의 기본 동작 흐름
1. 클라이언트(브라우저)는 서버에 요청을 보낼 때 항상 쿠키 정보를 포함하여 전달한다
	- 요청정보(요청메시지)에 포함하여 전달한다
	- 없으면 보내지 않는다
2. 서버는 클라이언트의 요청데이터에서 쿠키 정보를 확인할 수 있다
3. 서버는 클라이언트로 응답할 때 쿠키를 저장하도록 지정할 수 있다

### 세션, Session
- 서버가 클라이언트의 요청을 식별하기위해 사용하는 기술
- javax.servlet.http.HttpSession 클래스의 객체를 사용한다
- 서블릿에서는 요청객체(request)를 통해서 HttpSession 객체를 얻어와 사용한다
    > ex)	HttpSession session = req.getSession();
- 사용자의 상태 정보를 유지하기 위해 사용한다
	> ex)	로그인 상태
- 쿠키 정보는 클라이언트에 저장하고, 언제든 지워질 위험이 있다
- 세션 정보는 서버가 관리한다
- 서버는 클라이언트마다 따로 세션 정보를 관리한다
- 세션 정보는 기본적으로 서버의 메모리에 저장된다 (DB를 이용해서 세션 정보를 관리할 수도 있다)

### 세션의 동작 원리
- 클라이언트의 첫 요청(접속)이 들어오면 서버는 SESSION ID를 생성한다
- 서버는 SESSION ID를 저장해놓는다
- 서버가 응답하면서 Set-Cookie 헤더값을 이용하여 SESSION ID를 클라이언트에게 전달한다
- 클라이언트는 쿠키로 SESSION ID를 저장한다
- 클라이언트는 다음 요청부터 SESSION ID를 쿠키값으로 서버에 전송한다
- 서버는 SESSION ID별로 세션정보를 저장할 공간을 생성/관리한다 (세션 컨텍스트 영역)
- 클라이언트가 종료되면 세션 정보는 지워진다(자동)
- 아파치 톰캣 서버는 기본적으노 JSESSIONID라는 이름으로 SESSION ID를 발급하고 관리한다

### AJAX, Asynchronous JAvascript with Xml
- (XML을 이용한) 비동기식 자바스크립트 통신
- 자바스크립트 코드를 이용하여 HTTP통신을 비동기식으로 수행하는 기술
- 자바스크립트 코드로 HTTP요청을 보내고 XML파일 형식으로 응답을 받는다 (비동기적으로 응답을 받는다)
- 요즘에는 응답데이터의 형식으로 JSON을 많이 사용한다
- 보고있는 웹페이지 화면의 페이지이동(화면전환)없이 서버에 HTTP요청을 보내고 응답을 받아 사용할 수 있다
    - -> 화면은 그대로 두고 서버의 DB 정보가 필요할 때 사용한다
```jsp
  ex) 웹 어플리케이션 활용 예시
	게시글의 댓글창 새로고침

	SNS에서의 좋아요

	회원가입의 아이디 중복검사
```

### XHR 객체
- XMLHttpRequest 객체를 줄여서 XHR로 부른다
- AJAX통신을 하기 위해 준비되어있는 자바스크립트 기본 내장 객체
- IE 예전 버전(6이전)에서는 AJAX기술이 ActiveX를 이용하여 구현되어있다
	- -> 크로스브라우징 처리가 필요하다

### XHR 객체 속성(property)
- readyState
	- XHR 객체는 AJAX통신에 따라 준비-전송-완료 단계를 거친다 (LifeCycle)
	- readyState는 각 단계를 표현하는 값을 저장하고 있다
    ```jsp
	0 : UNSENT		- XHR객체를 생성만 한 단계 ( open() 호출 전 )
	1 : OPENED		- 서버와 연결하는 단계 ( open() 호출 후 )
	2 : HEADERS_RECEIVED	- AJAX요청 후 응답을 받기 전까지의 단계
				 ( send() 호출 후 )
	3 : LOADING		- 응답메시지를 받는 중
	4 : DONE		- XHR동작이 완료된 상태
    ```
- onreadystatechange
    - readyState가 변경될 때마다 실행되는 이벤트 리스너 속성
	- callback함수로 값을 지정한다
- status
	- HTTP 응답 상태코드
- statusText
	- HTTP 응답 상태 메시지
    - 상태코드(status)는 번호로 표기된다(200, 400, 404, 405, 500, ...)
	- 상태메시지(statusText)는 코드에 해당하는 설명을 문자열로 표현한다
- responseText
	- 응답 데이터를 문자열로 파싱(추출)해놓은 값
- responseXML
	- 응답 데이터를 XML 형식으로 파싱(추출)해놓은 값
	
### XHR 객체 메소드
- void open(String method, String url [, boolean asynch])
	- AJAX요청 정보를 초기화하는 함수
	- 요청 정보에 맞에 설정하여 호출한다
	- method	- HTTP 요청 메소드를 지정한다
	- url	- HTTP 요청 URL을 지정한다
	- asynch	- true:비동기식, false:동기식 (기본값 true)
	- asynch속성을 동기식(false)으로 설정하고 요청을 보내고 응답이 완료될 때까지 브라우저는 대기상태(BLOCKED)가 된다
- void send(null)
	- GET메소드로 요청을 보내는 함수
	- 전달파라미터는 open()함수의 매개변수로 URL에 쿼리스트링으로 포함한다
- void send(params)
	- POST메소드로 요청을 보내는 함수
	- 전달파라미터는 쿼리스트링 형식의 문자열로 params 매개변수로 포함한다

### JSON, JavaScript Object Notation
- 자바스크립트 객체 표기법
- https://www.json.org/json-ko.html
- 통신을 할 때 데이터를 전달하기 위한 데이터 표기법으로 사용한다
- 통신에 참여하는 시스템들이 사용하는 언어가 달라서 서로 데이터를 곧바로 주고받을 수 없다 -> 상대방의 데이터형식을 읽을 수 없다
- 공통적으로 이해할 수 있는 데이터타입 표기법으로 자바스크립트 표기법인 JSON을 사용한다 -> XML데이터를 사용하기도 한다

### JSON의 데이터 표현 방식
- 객체, Object
	- 클래스, Map, HashTable, 구조체 등을 표현할 때 사용한다
	- { }중괄호로 감싸서 데이터를 표현한다
	- name은 문자열로 표현하고 value는 어떤 타입이든지 허용된다
	- name=value 쌍을 프로퍼티(property)로 사용한다
	- 여러 개의 프로퍼티를 표현할 때에는 ,콤마로 구분한다
- 배열, Array
	- 배열, ArrayList, List, Vector, Sequence 등을 표현할 때 사용한다
	- [ ]대괄호로 감싸서 데이터를 표현한다
	- key값없이 인덱스가 자동으로 부여된 요소(element)를 나열하여 표현한다
- 문자열, String
	- "data"
- 숫자, Number
	- data
- true, false, null

### 마샬링, Marshalling
- 데이터를 전달하기 위해서 특정 표기법으로 변환하는 것
    - 클라이언트 : Javascript데이터 -> JSON표기법
	- 서버 : Java데이터 -> JSON표기법

### 언마샬링, Unmarshalling
- 마샬링되어 전달된 데이터를 자신의 시스템(프로그래밍 언어)에 맞게 복원한다
    - 클라이언트 : JSON텍스트 -> Javascript데이터
    - 서버 : JSON텍스트 -> Java데이터

### 직렬화, Serialization
- 스트림을 통해서 데이터를 전송하기 위해 1바이트 단위로 잘게 나누는 것

### 역직렬화, Deserialization
- 스트림을 통해서 데이터를 수신하기 위해 1바이트 단위로 데이터들을 원본 형태로 복원하는 것

### 원본데이터 -> 마샬링(JSON) -> 직렬화 -> 송신 -> 수신 -> 역직렬화 -> 언마샬링(사용 가능한 타입) -> 복원데이터

### GSON API 라이브러리
- 구글에서 제공하는 JSON 관련 자바 라이브러리
- JAVA데이터 <-> JSON 변환을 도와준다
- JAVA 언어의 데이터를 JSON으로 마샬링, 언마샬링할 수 있도록 해준다

### GSON 라이브러리 다운받기
- https://mvnrepository.com/ 접속 (메이븐 저장소)
- gons 검색
- gson 항목 클릭 ( 구글 마크 있는 것 )
- 2.8.8 클릭
- Files항목에 있는 jar 버튼 클릭
- gson-2.8.8.jar 사용

### jQuery를 이용한 Ajax
- XHR객체를 이용한 순수 JS Ajax코드는 크로스브라우징이 필요하다
	- -> XHR객체를 생성하는 코드를 작성할 때 불편하다
- jQuery Ajax API는 크로스브라우징을 지원한다
	- -> 브라우저에 따라서 코드가 바뀌지 않는다
- 응답 데이터를 처리하는 jQuery DOM를 이용하면 손쉽게 결과처리 가능하다

### jQuery Ajax API
```js
- $객체.load( url [,data] [,complete] );
- $.get( url [,data] [,success] [,dataType] );
- $.post( url [,data] [,success] [,dataType] );
- $.ajax( settings );
```

### jQuery Ajax API 01 - $객체.load()
- $객체.load( url [, data ] [, complete ] );
	- url로 AJAX요청을 보내고 응답받은 데이터를 $객체에 적용한다
	- DOM객체의 콘텐츠로 반영된다
	- -> 응답 데이터의 형식을 HTML로 많이 활용한다
	- url	AJAX통신을 수행할 URL
	    - 뒤에 쿼리스트링을 붙여 GET Method통신에 사용할 수 있다
	- data	
        - AJAX통신에 사용될 전달파라미터를 지정한다
		- String타입	- GET Method 요청
		- PlainObject타입	- POST Mehotd 요청
	- complete
		- 요청/응답 완료 후에 호출되는 callback 지정
        ```js
		function(
		  String responseText //응답데이터
		  , String textStatus //응답 상태 메시지
		  , jqXHR jqXHR //jQuery객체로 변환한 XHR객체
        ```

### jQuery Ajax API 02 - $.get(), $.post()
- jQuery.get( url [, data ] [, success ] [, dataType ] )
- jQuery.post( url [, data ] [, success ] [, dataType ] )
	- url	AJAX통신을 수행할 URL
	- data	전달 파라미터
		- String타입 또는 PlainObject타입
	- success	요청완료 후 성공적인 응답일 경우 호출하는 콜백함수
        ```js
		function(
		  Object data //응답 데이터
		  , String textStatus //응답 상태 메시지
		  , jqXHR jqXHR //jQuery XHR객체
        ```
	- dataType
		- 응답받은 데이터의 데이터타입을 지정한다
		- 응답받은 데이터를 지정한 데이터타입을 파싱(추출)한다
		- "xml", "json", "script", "text", "html"
		- -> 응답데이터를 지정한 데이터타입으로 파싱할 수 없다면 에러 발생한다
		- -> 주로 "json", "html" 을 적용한다

### jQuery Ajax API 03 - $.ajax()
- $.ajax( url [,settings] )
- $.ajax( settings )
	- settings는 PlainObject타입으로 작성한다
	- settings에는 AJAX 요청/응답에 필요한 설정값을 넣는다
	- settings항목에는 url도 있으므로 url매개변수를 따로 뺄 필요는 없다

### settings 필수 옵션들
- 다음 6가지 옵션들 필수로 작성하도록 한다
- **type**
	```js
    "GET" (기본값) | "POST"
    ```
	- AJAX HTTP 요청 메소드를 지정한다
	- jQuery 1.9.0 이후부터는 method옵션으로 대체 가능하다
- **url**
	- AJAX 요청 URL
	- String 타입
- **data**
	- 요청 파라미터
	- String, PlainObject, Array 타입
- **dataType**
	- 응답 데이터를 처리하는 방식
	- "xml" | "json" | "script" | "html" | "text"
	-  success에 지정한 callback함수의 첫번째 전달인자를 지정한 옵션형식으로 파싱한다
	- 응답데이터를 파싱할 수 없는 형태로 옵션을 지정하면 에러 발생한다
- **success**
	- 요청/응답 성공 시 호출되는 콜백 함수
    ```js
	function(
	  Anything data //응답 데이터
	  , String textStatus //응답 상태 메시지
	  , jqXHR jqXHR //jQuery XHR 객체
	) 
    ```
- **error**
	- 요청/응답 실패 시 호출되는 콜백 함수
	```js
	function(
	  jqXHR jqXHR //jQuery XHR 객체
	  , String textString //응답 상태 메시지
	  , String errorThrown //에러 정보
	)
    ```

### $.ajax 메소드의 기본 작성 형태
```js
	$.ajax({
		type: ""
		, url: ""
		, data: {
		
		}
		, dataType: ""
		, success: function() {
			
		}
		, error: function() {
			
		}
	})
```