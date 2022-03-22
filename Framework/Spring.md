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
