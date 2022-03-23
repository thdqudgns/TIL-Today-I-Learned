# :pushpin: HTML

### HTML, HyperText Markup Language
- HyperText
	- 하이퍼링크가 적용된 문서(텍스트)
	- 다른 문서와 링크로 연결된 문서(웹 문서)
- Makup Language
	- 태그(tag) 요소를 사용하여 문서 또는 데이터의 구조를 표현하는 언어
- 웹페이지의 정적인 구조(골격)을 표현하는 언어이다
- 웹 UI 레이아웃(Layout)을 구성한다
- 태그(tag)를 이용하여 개발한다

### HTML 태그, Tag
- HTML문서에서 사용하는 문법 요소
- 여는태그 와 닫는태그 두 개를 한 쌍으로 구성된다
    ```html
	ex)	<button> </button>
		<div> </div>
		<a> </a>
		<html> </html>
    ```
- HTML문서의 기본 태그 : 
    ```html
    <html>, <head>, <body>
    ```
- 기본 태그 3가지는 HTML문서에 반드시 포함되어있어야한다
- 태그들은 계층적(hierarchy)으로 작성된다
- 부모태그 - 자식태그 구조로 이루어져있다

### 기본 태그들의 형식
```html
	<html>

	  <head>
	  </head>

	  <body>
	  </body>

	</html>
```
- html 태그는 html문서에서 최상위 부모 태그이다
- html 태그는 head, body 태그를 자식 태그로 가진다
- html 태그
	- HTML문서의 최상위 태그
	- 문서 내의 모든 태그를 감싸고 있다
- head태그
	- HTML문서의 정보를 입력하는 태그
	- HTML문서 자체에 대한 정보 또는 설정값들을 입력한다
- body 태그
	- 화면에 보여질 내용을 작성하는 곳

### Front End 레퍼런스
https://www.w3schools.com/

### HTML 태그 레퍼런스
https://www.w3schools.com/tags/default.asp

### DTD, Document Type Definition
- DOCTYPE
- 문서 유형 정의
- 브라우저가 문서를 해석할 때 어떤 유형의 문법으로 작성되어있는지 알리는 문장(태그)
- 브라우저가 DTD를 확인하고 문서를 검사한다
- DTD에 적용된 버전에 맞게 문법 검사(유효성 검사)를 할 수 있게 해준다
- HTML 문서에서는 <!DOCTYPE>태그로 적용한다

### DTD유형
- HTML 4.01
- HTML 5
- XHTML 1.0
- XML
    - XML, eXtensible Markup Language
        - 확장 가능한 태그사용 문서
        - 표준 태그가 정해져있지 않고 문서를 작성하는 사람이 임의로 작성 가능한 형태
        - 특정 DTD를 적용하여 태그 문법이 DTD를 따르도록 적용할 수 있다

### 태그의 기본 레이아웃 속성
- 레이아웃 : 시각적으로 어떻게 배치(구성)되는지를 나타냄
- block 요소
	- 화면의 일부 영역을 차지하면서 구역 설정할 때 사용한다
	- 공간을 만들어내는 요소들
	- 화면의 전체적인 구조를 구성할 때 사용한다
	- 한 줄을 전부 차지하는 특성을 가지고 있다
    ```html
	<div>, <h1>~<h6>, <p>, <ol>, <ul>, ...
    ```
- inline 요소
	- 내용물(컨텐츠)의 영역을 감싸는 속성
	- 블록(block)요소의 내부에 포함하여 작성한다
	- 태그없이 사용된 단순 텍스트도 inline요소처럼 취급한다
    ```html
	<span>, <a>, <img>, ...
    ```

### 글자 관련 태그
- h1~h6, hn, hx
	- Heading 태그
	- 제목을 표현하는 태그
	- h1이 큰 텍스트, h6로 갈수록 점점 작아진다
- p
	- Paragraph 태그
	- 문단을 표현하는 태그
	- 공백문자(띄어쓰기, 탭, 개행)이 개별적으로 적용되지 않는다 -> 공백문자 전체를 한 개의 띄어쓰기로 대체하여 표현한다
	- 개행	 -> br 태그 사용
	- 띄어쓰기 -> &nbsp; 키워드 사용
	- 수평탭	 -> 없음
	- ** br : line BReak
	- ** nbsp : No Break SPace

- pre
    - PREformatted text
	- 입력한 문단의 서식형태 그대로 브라우저에 표현하는 태그
	- 공백문자를 작성한 문장을 그대로 화면에 표현한다
	- 스타일(모양)을 직접 지정해야하는 일이 많아져서 잘 사용하지 않는다
	- 프로그래밍 소스코드 같은 형태를 표현하기에 적절하다

### 목록 태그, list
```html
 <ul>, <ol>, <li>
```
- ul : Unordered List, 순서없는 리스트(목록)
- ol : Ordered List, 순서있는 리스트(목록)
- li : List Item, 리스트의 항목, 목록에 들어가는 항목
- ul태그와 ol태그의 자식태그로 li태그를 사용할 수 있다
- 중첩된 목록을 생성할 수 있다
	- 중첩된 목록은 들여쓰기되며 항목스타일이 달라 질 수 있다
- 스타일(CSS)을 적절히 조절하여 웹 화면의 메뉴를 구성할 때에도 사용된다

### 정의 목록 태그
```html
 <dl>, <dt>, <dd>
```     
- dl : Description List, 정의(설명) 목록
- dt : Description Terms, 정의 용어의 이름
- dd : Description Descripe, 정의 용어의 설명
- 용어에 대한 설명, 정의에 대한 목록을 구성하는 태그
- dt 와 dd 가 한 쌍으로 하나의 용어를 설명한다

### 하이퍼링크 태그
```html
 <a>
```
- Anchor 태그, 닻
    - 클릭 시 다른 페이지로 이동하는 하이퍼링크를 적용하는 태그
    - 글자나 문단뿐만 아니라 이미지(그림)나 다른 태그들을 이용하여 적용할 수 있다
- href 속성
	- a 태그가 링크될 URL을 지정한다
	- 같은 도메인, 다른 도메인, 같은 페이지 내부 링크 가능하다
	- 절대경로URL을 이용하여 "다른 도메인" 페이지로 링크를 건다
	- 상대경로URL을 이용하여 "같은 도메인" 페이지로 링크를 건다
    - 속성값(id)을 이용하여 "같은 페이지"에 링크를 건다
- target 속성
	- 링크된 페이지가 열리는 위치(방식)을 조절한다
	- _self - 현재 창(기본값)
	- _blank - 새 창 또는 새 탭

### 이미지 태그
```html
 <img>
```
- 화면에 이미지를 추가할 때 사용한다
- src속성
	- 보여질 이미지의 URL을 지정하는 속성
- alt속성
	- 이미지 경로가 잘못되었거나 파일이 손상되었을 때 대체할 텍스트 지정
- width속성
	- 이미지의 너비 (픽셀에 해당하는 수치로 정수값으로 적는다)
- height속성
	- 이미지의 높이 (픽셀에 해당하는 수치로 정수값으로 적는다)

### 테이블 태그
- 표를 표현하는 태그
```html
    <table>
    <tr>, <th>, <td>
    <caption>, <thead>, <tbody>, <tfoot>
```
- table : 표를 만들 때 사용하는 태그
    - 자식 요소들로 행과 열을 표현한다
- tr : Table Row
	- 테이블의 각 행을 표현한다
	- table 태그의 자식 요소로 사용한다
- th : Table Head - 테이블의 제목을 나타내는 셀(cell, 칸)을 표현한다
- td : Table Data - 테이블의 데이터을 나타내는 셀(cell, 칸)을 표현한다
- th, td 태그는 tr 태그의 자식요소로 사용한다
```html
  ** 테이블의 기본 태그
	<table>
	  <tr>
	    <th></th>
	    <th></th>
	  </tr>
	  <tr>
	    <td></td>
	    <td></td>
	  </tr>
	</table>
```
- thead : Table HEADer - 테이블의 최상단행으로 고정
- tfoot : Table FOOTer - 테이블의 최하단행으로 고정
- tbody : Table BODY - thead, tfoot 사이에 배치
- caption : 테이블의 이름 - 테이블의 상단 바깥쪽에 위치한다

### td, th 테이블 셀 태그의 확장 속성
- colspan : 열(column)을 확장하는 속성, 셀이 차지할 칸 수를 지정한다
- rowspan : 행(row)을 확장하는 속성, 셀이 차지할 행 수를 지정한다

### HTTP 통신 과정 ( WEB 통신 )
```java
	웹 클라이언트			웹 서버
	(브라우저)			(Apache Tomcat)

			   HTTP
	1. URL요청	---REQUEST--->	2. 요청 받기
					3. 요청 처리
					(요청에 적절한 작업을 수행한다)

			   HTTP
	5. 응답받기	<--RESPONSE---	4. 응답 생성
					(요청에 적절한 응답으로 생성한다)
					(주로 HTML파일 형식으로 생성된다)

	6. 응답데이터 처리

	7. 응답데이터해석 및 보여주기
	(브라우저 화면으로 HTML파일을 해석하여 보여주기)
```

- HTTP REQUEST, HTTP RESPONSE 메시지에는 각각 HEADER영역, BODY영역으로 구성되어있다
    - HEADER영역 : 메시지의 속성, 설정 정보를 담고 있는 영역
    - BODY영역 : 메시지의 내용물(본문, 컨텐츠)를 담고 있는 영역

### form 태그
- 클라이언트(브라우저)가 서버로 HTTP요청을 보낼 때 데이터를 포함해서 전달할 수 있도록 만들어주는 태그
- 요청데이터를 입력할 수 있도록 만들어주는 태그
	- 요청 데이터 : HTTP요청메시지에 포함시키는 데이터
		- 요청 파라미터
		- 전달 파라미터
		- 전달 데이터
- input, textarea, select 등의 특정 자식태그들을 이용하여 전달될 데이터를 입력할 수 있도록 한다
- form 태그에는 action속성, method속성을 필수로 적용해야 한다
    - action속성 : 요청URL을 지정하는 속성
    - method속성 : 요청방식(요청메소드)을 지정하는 속성 ( get | post )

### HTTP의 요청 방식(Request Method, 요청 메소드)
- HTTP Request(HTTP요청) 메시지를 서버로 보낼 때 요청 데이터를 전달하는 방식을 나타낸다
- 요청 메시지에는 반드시 요청 메소드가 지정되어있어야한다
- 따로 지정하지 않으면 기본값으로 GET방식을 사용한다
- GET방식, POST방식을 주로 사용한다

### GET방식(GET Method)
- 요청데이터를 쿼리스트링 형태로 URL의 마지막에 ?를 붙이고 그 뒤에 포함한다
> ex)	http://localhost:8088/search?keyword=JAVA

- 쿼리스트링, QueryString
    - HTTP통신(웹 통신)에서 전달데이터의 변수명과 값을 표현하는 방식
	- '변수명=값' 쌍의 형태로 표현된다
	- 여러 개의 변수를 나타낼 때에는 각 데이터쌍 사이에 & 를 적어서 구분한다
> ex)	id=abc&pass123   
ex)	keyword=JAVA&type=all

### POST방식(POST Method)
- 전달데이터를 쿼리스트링 형태로 요청 메시지의 BODY영역에 포함시켜 전달한다
- GET방식과는 다르에 URL에 전달하려는 데이터가 보이지 않는다
- GET방식은 주로 서버의 데이터(DB데이터)를 조회하려고할 때 사용한다 -> SELECT
- POST방식은 주로 서버의 데이터(DB데이터)를 삽입/갱신/삭제하려고 할 때 사용한다 -> INSERT, UPDATE, DELETE
- GET방식은 데이터가 없을 때, 짧을 때 사용한다
- POST방식은 데이터가 길 때 사용한다
- 민감데이터일 경우 POST방식을 사용한다 (ex. 비밀번호)
