# :pushpin: Front-end 준비하기

* [HTML]()
* [CSS]()
* [Javascript]()
* [jQuery]()

### 이클립스 JEE ( Java Enterprise Edition) 다운 받기
- https://www.eclipse.org/ 접속
- 우측 상단의 Download 버튼 클릭
- Download Packages 링크 클릭 (** Download x86_64 클릭하지 말고, 밑에 있는 링크 클릭할 것!)
- 우측 중단쯤에서 MORE DOWNLOAD 항목 확인
- Eclipse 2020-06 (4.16) 링크 클릭
- Eclipse IDE for Enterprise Java Developers 항목에서 OS에 맞게 다운로드
    - Windows x86_64 링크 클릭
- Download 클릭 (다운로드가 느리면 미러 서버를 국내로 변경해서 다운로드받는다)
- 다운 받은 zip 파일을 압축 풀고 사용한다

### Apahce Tomcat 웹서버 다운로드
- 아파치 톰캣
- http://tomcat.apache.org/ 접속
- 왼쪽 Download항목에서 Tomcat 9 링크 클릭
- 하단에 9.0.52 항목 확인
- Binary Distributions 섹션에서
	- Core : zip 파일 다운로드
- 압축 해제

### 이클립스에 서버 환경(Server Runtime) 추가하기
- 이클립스에 서버 실행환경을 인식시키는 작업
- 서버를 설치하는 것은 아님!
- Window 메뉴의 Preferences 항목 선택
- 왼쪽 카테고리창에서 Server - Runtime Environments 항목 선택
- Add 버튼
- Apache Tomcat v9.0 항목 선택하고 Next버튼
- Tomcat installation directory 입력 창 오른쪽에 있는 Browse 버튼 클릭
- Apache-Tomcat 9.0 압축해제한 폴더 선택하고 Finish
- Apply and Close

### 이클립스에서 사용할 파일들의 한글 인코딩 설정하기
- UTF-8로 설정한다
- Window메뉴의 Preferences 항목에서 작업할 것!
1. General 항목 - Workspace 메뉴
	- Text file encoding 항목을
	- Other: UTF-8 로 선택한다
	- Apply 버튼 클릭
2. Web 항목
    - CSS Files
    - HTML Files
    - JSP Files
    - 세 가지 메뉴에서 Encoding설정 항목을 변경한다
    - ISO 10646/Unicode(UTF-8) 선택
    - 각각 Apply 버튼 클릭
3. 모두 설정이 끝나면 Apply And Close로 닫는다

### 서버에 배포될 프로젝트(모듈) 설정하기
- Servers탭에 추가된 서버 항목에서 오른쪽 버튼 클릭
- Add and Remove 선택
- 왼쪽 Available : 개발된 프로젝트(아직 웹서버에 모듈로 업로드되지 않은 상태)
- 오른쪽 Configured : 배포된 프로젝트(웹서버의 모듈로 업로드된 상태)
- 업로드할 프로젝트를 오른쪽으로 옮기고 Finish클릭
- 서버를 재시작하면 완료
- 접속 가능한 상태가 된다

### URL, Uniform Resource Locator
- 인터넷 상의 정보(자원, Resource)가 어디있는지 표현하는 방법
- 규칙에 맞춰 작성하여 인터넷의 자원이 어디에 위치하는지 표현한다
- URL 형식
    - 프로토콜://인터넷주소[:포트번호][/디렉토리][/파일이름]

### 기본 테스트 URL의 구조
- http://localhost:8088/Front/test/hello.html
- 프로토콜
	- http
    - 통신 방식(서비스 형식) - 웹(Web) 통신을 나타낸다
- 인터넷주소(도메인주소, Domain)
    - localhost
	- 서버의 위치 - IP 또는 HOST를 이용하여 표현한다
- 포트번호
	- 8088
	- 서비스의 위치 - 컴퓨터에서 어떤 프로그램인지 표현한다
- 컨텍스트 패스
	- /Front
	- 웹서버에 등록된 모듈의 이름
	- 일반적으로 서버에 배포된 프로젝트의 이름을 사용한다
	- 여러 개의 프로젝트(모듈)이 배포되었을 때 구분하기 위한 이름으로 사용한다
	- 모듈이 하나밖에 없을 땐 '/'로 제거하고 사용한다
- 자원의 경로
	- /test/hello.html
	- 클라이언트가 서버로부터 받을 자원의 경로
	- Dynamic Web Project에서는 WebContent의 내부 경로가 된다

### 웹프로젝트가 톰캣 서버에 배포되는 위치
- 웹 모듈이 저장되는 곳이다
- 웹 서버는 이곳에 모듈로 업로드된 파일을 이용해서 웹 어플리케이션을 작동시킨다
- 톰캣서버 배포 경로
    - {workspace}\.metadata\.plugins\org.eclipse.wst.server.core\tmp0\wtpwebapps\{프로젝트명}

### 화면 구현의 구성요소
- Front End : 클라이언트(브라우저)에 보이는 부분
- HTML : 웹 화면의 구조(골격)을 구성하는 언어
- CSS : 화면의 스타일(모양)을 지정하는 언어
- Javascript : 화면의 동작을 정의하는 언어
