# :pushpin: Javascript

### 자바스크립트, Javascript
- HTML문서에서 요소들의 동작을 제어하는 언어
	> ex) button 태그를 클릭했을 때 발생할 동작 정의
- HTML문서 head 태그 안에 script 태그를 작성하여 자바스크립트 코드를 작성함
- 브라우저 자바스트립트엔진에 의해서 인터프리트방식으로 실행된다
- 자바스크립트 파일(.js)을 HTML문서 외부에 두고 로드해서 사용하기도 한다
- 브라우저가 코드를 해석하고 실행한다
	- 브라우저(클라이언트)에 자바스크립트 코드가 그대로 전달된다
	- 민감한 정보나 핵심 코드를 노출시키지 않도록 조심해야 한다

### JS 형변환
- 자동 형변환
    ```js
	String타입과 +연산을 하면 문자열로 변환된다

	Number + String -> String
	String + Number -> String

	Boolean + String -> String
	String + Boolean -> String

	-----------------------------------------------------

	Boolean타입을 Number타입과 +연산 하면 Boolean을 숫자로 취급한다

	true == 1, false == 0

	Boolean + Number -> Number
	Number + Boolean -> Number
    ```
- 강제 형변환
    ```js
	문자 -> 숫자

	parseInt("숫자형식의 문자")	-> 정수값으로 변환
	parseFloat("숫자형식의 문자")	-> 실수값으로 변환
	Number("숫자형식의 문자")	-> 정수, 실수 다 가능

	-------------------------------------------

	숫자 -> 문자

	숫자데이터.toString(n)		-> 진법을 지정하여 문자로 변환
	숫자데이터.toFixed(n)		-> 소수점 자릿수를 지정하여 문자로 변환
	String(숫자)			-> 원본형식으로 변환
    ```

### JS 데이터 타입
- Number : 숫자	(보라색)
- String : 문자	(검은색)
- Boolean : 논리	(파란색)
- Object : 객체	{객체}
	- {키1:값1, 키2:값2, ...}
- Array : 배열	[배열]
	- [요소1, 요소2, ...]
- null
	- 참조 대상이 없음을 나타내는 키워드
	- Object타입
- undefined
	- 값이 정의되지 않은 상태를 표현하는 키워드
	- (변수도 만들어지지 않음, 값이 생성되지 않음)
	- undefined타입 (값이면서 데이터타입, 고유 키워드)
- NaN, Not a Number의 약자
	- Number타입의 특수 키워드
	- Number타입으로 사용되어야하는 상황에서 Number가 아닌
	데이터를 사용할 경우 반환되는 키워드
- Infinity
	- 무한대를 뜻하는 키워드
	- Number타입의 특수 키워드
	- 특정 숫자를 0으로 나누었을 때 표현되는 특수 데이터
	- Infinity - 양의 무한대
	- -Infinity - 음의 무한대

### =, ==, === 연산자
- =연산자, 대입 연산자
	- 변수에 값을 대입할 때 사용
- ==연산자, 추상 동등 비교 연산자(Abstract Equality Comparison)
	- 동등 비교 규칙이 따로 정해져있는 비교 연산자
- ===연산자, 강력 동등 비교 연산자(Strict Equality Comparison)
	- 데이터타입을 먼저 비교한 후 같은 타입일 때에만 비교하는 연산자

### JS 변수 선언 키워드
- var
	- 기본 변수 선언 키워드
	- 같은 이름의 변수를 여러 번 선언해도 에러없이 처리된다
	    - 하나의 변수로 취급한다
- let
	- 추가된 변수 선언 키워드 (ECMAScript 6(ES6)에서 추가됨 - 2015년)
	- 같은 이름으로 여러 번 선언할 수 없다
- const
	- 추가된 변수 선언 키워드 (ECMAScript 6(ES6)에서 추가됨 - 2015년)
	- let과 동작이 비슷하다
	- 자바의 final변수와 유사함. 상수
	- 변수값의 초기화가 필수이지만 초기화 이후 대입이 되지 않는 변수

### 적용되는 스코프
- var : function scope
- let, const : function scope, block scope

### 호이스팅 적용
- var, let, const 모두 호이스팅이 발생한다
- var는 선언코드 이전에 변수에 대한 접근이 가능하다
- let, const는 선언코드 이전에 접근할 수 없도록 금지되어있다 (에러남)

### 자바스크립트의 핵심 요소 4가지
1. 자바스크립트 코어(Core, 핵심) 문법
	- 기본 문법
	- 데이터타입, 변수, 제어문, 함수, ...
	- 클래스, 객체, 프로토타입, ...
	- 내장 객체(Built-in Object)
	- String, Number, Math, Date, Timer, ...
2. BOM, Browser Object Model, 브라우저 객체 모델
    - 웹 브라우저 윈도우(창)와 자바스크립트가 상호작용하기 위한 수단으로 제공되는 객체들
	- window객체
	    - BOM 객체들의 최상위 객체
	    - 브라우저의 전반적인 기능을 관리한다
	    - 자바스크립트 코드의 정의한 모든 전역 변수, 함수, 객체들을 window객체의 프로퍼티(property, 속성, 멤버 필드)로 가지고 있다
	    - window. 을 생략하고 사용할 수 있다
	- navigator객체
	    - 브라우저의 정보, 운영체제의 정보를 제공하는 객체
	- location객체
	    - URL과 관련된 인터넷 주소 정보 객체
	- history객체
	    - 사용자의 인터넷 방문기록 관련 객체
	    - 인터넷 사용기록을 이용할 수 있는 객체
	- screen객체
	    - 사용자의 모니터 정보 관련 객체
	- document객체
	    - 웹 문서 관련 객체
	    - 웹 문서 == 웹페이지
	    - body 태그에 작성된 내용(태그)을 관리하는 객체
3. DOM, Document Object Model, 문서 객체 모델
    - document객체를 이용한 문서 객체 모델
	- 화면에 보여지는 모든 태그 요소를 객체로 만들어서 관리한다
4. Event, 이벤트
	- 사용자의 입력을 받아 상호작용하는 코드

### DOM, Document Object Model
- 문서 객체 모델
- window객체의 내장 객체 중 하나인 document를 통해서 웹 문서를 관리하는 것을 말한다
- HTML문서의 body 태그의 내용물들을 객체(Object)로 만들어서 제공한다
- 자바스크립트 코드로 HTML 문서의 요소(태그)들에 접근하고 관리할 수 있다

### DOM 관련 용어
- 요소(Element)
	- HTML문서의 태그
	- 태그 : 열기, 닫기로 표현되는 문법
	- 요소 : 태그를 브라우저가 해석하여 화면에 표현한 것
- 문서 객체(Document Object)
	- 자바스크립트 코드로 요소에 접근할 수 있도록 객체화한 것
	- HTML태그요소와 자바스크립트코드의 연결 지점
- DOM 트리(tree)
	- HTML문서의 모든 문서 객체를 트리 구조로 표현한 것
	- 계층적 구조로 문서 객체를 정리하여 저장한 것
- 노드(Node)
	- DOM트리의 구성 요소
	- 요소 노드	- 태그를 객체화한 것
	- 텍스트 노드	- 태그가 감싸고 있는 텍스트를 객체화한 것
    ```html
	ex)	<h1>Hello</h1>

		<h1>	- 요소노드
		"Hello"	- 텍스트노드
    ```

### DOM객체(document객체)를 사용하는 코드를 적용하는 방법
- document객체는 DOM트리가 완성된 이후에 사용할 수 있다
- DOM트리에는 <body>태그의 모든 계층구조(태그들)를 파악하여 작성되어있다
- DOM트리가 완성되는 시점까지 document객체를 사용하는 코드가 실행되지 않도록 코드 실행 시점을 미루어야한다
- 방법1.
    - /body 닫는 태그 바로 위에 script>태그 작성 후 사용한다
- 방법2.
    - head 태그 내 script 태그를 작성하고, window.onload코드에 함수로 적용한다
- 방법3.
   - 일반 함수로 document객체를 사용하는 코드를 작성한다
   - 해당 함수를 태그 요소의 이벤트처리코드로 사용한다

### DOM 객체 이용 함수, DOM API
- document객체를 이용하여 DOM객체를 사용(관리)하는 내장 함수들
- HTML태그 요소들을 관리할 수 있는 API함수들이다

### 노드(Node) 생성
- document.createElement("tagName")
	- 요소노드 만들기
	- HTML표준태그가 아니어도 생성은 할 수 있음
- document.createTextNode("text")
	- 텍스트노드 만들기

### 노드(Node) 추가하기
- DOM객체.appendChild( 대상객체 )
    - DOM객체의 자식으로 대상객체를 추가한다(연결한다)

### 요소(Element)의 속성(Attribute)값 다루기
- 표준속성값 가져오기
	- DOM객체.표준속성
- 표준속성값 설정하기
	- DOM객체.표준속성 = "속성값"
- 일반속성값 가져오기
	- DOM객체.getAttribute("속성명")
- 일반속성값 설정하기
	- DOM객체.setAttribute("속성명", "속성값")

### innerHTML 프로퍼티
- 객체의 자식요소를 HTML문장으로 처리하는 속성
- DOM객체.innerHTML
	- 자식요소를 얻어온다
- DOM객체.innerHTML = "HTML양식의 문장"
	- 자식요소를 설정한다

### innerText 프로퍼티
- 객체의 자식요소를 단순 텍스트 문장으로 처리하는 속성
- DOM객체.innerText
	- 자식요소를 얻어온다
- DOM객체.innerText = "단순 텍스트 문장"
	- 자식요소를 설정한다

### 요소노드 객체 얻어오기 (DOM객체 얻기)
- document.getElementById("ID속성값")
	- 지정된 ID값을 가진 요소 반환
- document.getElementsByTagName("TAG이름")
	- 지정된 태그들을 배열로 반환
- document.getElementsByName("NAME속성값")
	- 지정된 NAME값을 가진 태그들을 배열로 반환

### 노드요소 제거하기
- DOM객체.remove()
	- DOM객체를 DOM트리에서 제거한다
- DOM객체.removeChild( 대상 )
	- DOM객체의 자식노드 중에서 대상노드를 제거한다
- **둘 다 화면에서 제거된다**

### DOM API사용을 줄일 수 있는 특수 규칙(축약 규칙)
1. 모든 태그들의 id는 window객체의 property로 등록된다
2. form 태그의 자식요소들의 name은 해당 form 객체의 property로 등록된다
3. form 태그의 name은 document객체의 property로 등록된다

### JS 이벤트, Event
- 사용자의 모든 입력(행위), 프로그램의 상태 변화 등을 미리 정의해놓은 객체
- 컴퓨터의 특정 사건도 포함하여 객체화시켜둔 것
- 운영체제에서 발생한 이벤트를 감지하고 해당 이벤트를 이벤트가 발생한 응용프로그램에게 전달한다
- 전달된 이벤트를 해당 응용프로그램에서 적절한 코드가 실행되도록 처리한다
    - 이벤트 기반 처리 프로그램
	- Event Driven

### JS 기본 이벤트
- 태그 요소에 별도의 이벤트 처리 코드를 작성하지 않아도 기본적으로 실행되는 이벤트
- a 요소를 클릭한다
	- 지정된 경로로 페이지를 이동시킨다
	- ( location.href = "지정경로" )
- 브라우저 화면에 마우스 우클릭
	- 메뉴 보여주기
- form 태그에서 submit버튼 클릭
	- action속성에 지정된 경로로 데이터를 전달한다
	- ( form 객체.sumbit() )

### JS 주요 이벤트
- ----- 마우스 이벤트 -----
    - click	마우스를 클릭했을 때
    - dblclick	마우스를 더블 클릭했을 때
    - mousedown	마우스의 버튼을 눌렀을 때
    - mouseup	마우스의 버튼을 뗐을 때
    - mousemove	마우스 포인터를 이동했을 때 (픽셀단위로 이벤트 발생)
    - mouseenter	마우스 포인터가 요소 위로 올라갔을 때
    - mouseleave	마우스 포인터가 요소 밖으로 나갔을 때
	- (mouseenter, mouseleave : 자식요소를 제외하고 판단)
    - mouseover	마우스 포인터가 요소 위로 올라갔을 때
    - mouseout	마우스 포인터가 요소 밖으로 나갔을 때
	- (mouseover, mouseout : 자식요소를 포함하여 판단)
- ----- 키보드 이벤트 -----
    - keydown	키보드를 눌렀을 때(한번, 눌림이 시작될 때)
    - keyup	키보드에서 손을 뗐을 때
    - keypress	키보드를 눌렀을 때(연속, 눌려져있는 상태)
	- 한 번의 키입력에서 이벤트 발생 순서
	    1. keydown
	    2. keypress
	    3. keyup
	- keypress는 alt, ctrl, shift, esc 같은 가상키에 반응하지 않음
	- keydown은 모든 키에 반응한다
- ----- 폼(form) 이벤트 -----
    - submit	폼이 제출되었을 때 (제출버튼을 눌렀을 때)
    - reset	폼이 초기화되었을 때 (초기화버튼을 눌렀을 때)
    - focus	입력 포커스가 특정 요소에 들어갔을 때
    - blur	포커스를 잃었을 때
    - change	폼 필드(폼의 자식요소)에 변화가 발생했을 때
    - select	select 태그의 항목을 선택했을 때
- ----- 윈도우(창) 이벤트 -----
    - load	HTML문서 또는 요소가 불러와졌을 때(메모리에 로드됐을 때)
    - resize	요소의 크기(윈도우의 크기)가 변경되었을 때
    - scroll	페이지 스크롤이 이동되었을 때