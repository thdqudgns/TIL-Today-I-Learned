# Java 기초 개념 정리

### :pushpin: Java의 시작

* **자바(Java) 다운로드 받기**
    - Open JDK 1.8 다운로드 받아서 사용함
    - 구글에서 'openjdk github'검색
    - ojdkbuild/ojdkbuild: Community builds using source ... [링크 들어가기](https://github.com/ojdkbuild/ojdkbuild)
    - 하단 쪽에 Downloads for Windows x86_64 섹션 확인
    - 1.8.0_292-1 항목 확인
    - java-1.8.0-openjdk-1.8.0.292-1.b10.ojdkbuild.windows.x86_64.zip 링크 다운
    - 압축 해제
    - 압축 해제한 폴더 이름을 'java-1.8.0-openjdk'로 변경
    - C:\Program Files\ 폴더에 'Java' 폴더 만들기
    - C:\Program Files\Java\ 폴더에 복사한 폴더 붙여넣기

* **JDK(Java) 환경변수 설정하기**
    - 시스템 창 열기 (단축키 : Win키 + Pause/Break)
	(내컴퓨터 창에서 '내 PC' 아이콘에 우클릭 '속성' 선택)
    - 왼쪽 메뉴 중에서 '고급 시스템 설정' 클릭 (또는 하단 목록에서 찾으세요)
    - 고급 탭에서 '환경변수' 버튼 클릭
    - '새로 만들기' 버튼 클릭
	변수이름: JAVA_HOME
	변수 값: C:\Program Files\Java\java-1.8.0-openjdk
	입력하고 확인
    - Path 항목 변수를 찾아서 '편집' 버튼 클릭.
	윈10일 경우 '새로 만들기' 클릭하고
		C:\Program Files\Java\java-1.8.0-openjdk\bin 추가
		(찾아보기 버튼누르고 찾아도 됨)

	윈7, 8일 경우 기존내용 절대 지우지 말고 가장 오른쪽 끝에
		;C:\Program Files\Java\java-1.8.0-openjdk\bin 추가
		( ;세미콜론 잘 입력할 것)
    - 확인
    - 확인

* **JDK(Java) 설치 확인**
    - Win키 + r (실행창) 열기
    - 'cmd' 입력
    - 검은색 프로그램 창이 뜬다
	java -version 명령어 입력
	javac -version 명령어 입력
	-> 두 명령어의 결과가 모두 같은 버전으로 제대로 출력되어야 설치완료

* **콘솔, Console**
    - 시스템과 사용자(유저) 사이의 대화창
    - 해당 시스템에 직접적인 명령을 내릴 수 있는 환경
    - Windows Console, 윈도우 콘솔: 실행 창에서 'cmd'입력하여 실행

* **이클립스 툴 다운로드**
    - [링크접속](http://www.eclipse.org/)
    - 화면 우측 상단 Download 버튼 클릭
    - Download x86_64 누르지말고! Download Packages 링크 클릭
    - 우측 중간쯤에 MORE DOWNLOADS 항목 확인
    - Eclipse 2020-06 (4.16) 링크 클릭
    - Eclipse IDE for Java Developers 항목에서 자기 컴퓨터 OS에 맞게 다운로드
    - 압축 해제
    - 해제된 폴더 'eclipse'를 복사하여 적당한 폴더에 붙여넣기 (폴더 이름 변경해도 됨) (원본 eclipse 폴더는 백업용으로 남겨놓고 사용하면 좋음)
    - 폴더 내 eclipse.exe 파일로 실행

* **workspace(작업폴더) 지정하기**
    - 내 컴퓨터를 이용해서 D:\workspace\ 폴더 생성. (다른 폴더여도 상관없음) (위치 기억하기 쉬운 폴더로 생성할 것)
    - 이클립스 실행하고 나오는 창(workspace선택창)에서 "Browse..." 버튼 누르도 폴더 선택
    - Launch 클릭
    - workspace를 변경하고 싶다면 이클립스 File메뉴 - Switch Workspace에서 변경


* **코딩 폰트 적용하기**
    - [네이버 나눔고딕 코딩글꼴](https://github.com/naver/nanumfont)
    - Ver 2.5 (2016.10.24 배포) 링크 클릭
    - 다운 받은 압축파일 해제 (NanumGothicCoding-2.5.zip)
    - NanumGothicCoding.ttf, NanumGothicCoding-Bold.ttf 파일 두 개 확인
    - 두 파일을 C:\Windows\Fonts\ 폴더에 복사, 붙여넣기

* **이클립스 글꼴 바꾸기**
    - Window 메뉴 - Preferences 항목 선택
    - 왼쪽 메뉴 중에서 General - Apperance - Colors and Fonts
    - Text font 검색 ( Basic 항목에 있는 Text Font )
    - 항목을 선택하고 우측에 "Edit..." 버튼 클릭
    - 글꼴을 "나눔고딕코딩"으로 설정

* **프로젝트 Import 하는 방법**
    - 이클립스 File 메뉴 - import... 선택
    - General항목에서
    - Existing Projects into Workspace 선택
    - Next
    - Select root directory: 쪽에서 Browse...
    - 자기 workspace 폴더 찾아가기
    - 폴더 선택 버튼 클릭
    - Projects: 항목에서 불러올 프로젝트 체크
    - Finish

* **이클립스 자바 프로젝트 만들기**
    - **프로젝트, Project**
    프로그램 개발하기 위한 환경
    -> 개발된 소스코드를 관리하는 폴더라고 생각하면 된다
    - File - New - Java Project 선택 - 프로젝트 이름 "Test"로 작성 (프로젝트는 첫글자 대문자)
    - src폴더 우클릭, New - Package 선택 - "simple" 입력 - Finish (패키지는 첫글자 소문자)
    - simple 패키지 우클릭, New - Class 선택 - "Hello" 입력 - Finish (클래스는 첫글자 대문자)
    - 기존 코드 그대로 유지하며 아래와 같이 작성
    ```java
    package simple;

    public class Hello {

	    public static void main(String[] args) {
		
		    System.out.println("Hello Java");
	    }
		
    }
    ```
    - 저장 (단축키 ctrl + s)
    - 실행 (단축키 ctrl + F11)
    - 하단 Console뷰(탭)에서 'Hello Java' 문구 출력 확인
---

### :pushpin: 기본 개념

* **자바 프로젝트, Java Project**
    - Java 프로그램 개발을 하기 위해 만드는 환경(폴더)
    - 주로 하나의 프로그램을 개발하기 위해 프로젝트 1개를 생성하는 편이다

* **패키지, Package**
    - 프로그램을 구성하고 있는 코드들을 모아놓는 폴더(꾸러미)
    - 비슷한 기능이나 하나의 기능을 구현할 때 필요한 소스코드들을 모아놓는다
    - 자바 프로젝트에는 반드시 1개 이상의 패키지로 구성한다

* **소스 코드, Source Code**
    - 프로그램을 개발하기 위해 작성된 코드   
	**Source**: 원시의, 원본, 출처   
	**Source Code**: 프로그램의 원본이 되는 코드
    - 자바에서는 클래스(Class) 단위로 소스코드를 작성한다
    - 자바 클래스파일의 확장자는 ".java" 로 가진다

* **자바 프로그램 개발(실행) 과정**
    - 소스코드 작성 --컴파일--> 바이트코드  --실행--> JVM
	- **'.java'** --compile--> **'.class'** --run--> **'JVM'**
	- (Source Code) ----> (Byte Code) ----> (Java Virtual Machine)
    - 고급언어(Java코드)를 저급언어(바이트코드)로 번역하는 과정을 컴파일(Compile)이라고 한다
    - 컴파일러(Compiler)가 컴파일을 수행한다
    - 이클립스에서는 소스코드를 저장하면 자동으로 컴파일된다

    - 컴파일이 수행될 땐 소스코드에 대한 문법 검사도 같이 이루어진다   
	**자바 컴파일러**: javac.exe

    - 프로그램을 실행하면 JVM이 바이트코드를 읽어 실행한다   
	**실행 프로그램**: java.exe

    - **고급 언어(High Level)** -> **사람**이 이해하기 쉬운 형태의 프로그래밍 언어
    - **저급 언어(Low Level)** -> **컴퓨터**가 이해하기 쉬운 형태의 프로그래밍 언어

* **컴파일러, Compiler (compile)**
    - 코드를 실행하기 전에 미리 번역해놓는 방식
    - 사전에 번역하는 시간이 많이 필요하다
    - 실행하는 동안에는 따로 번역할 필요가 없어 빠른 반응성을 보인다

* **인터프리터, Interpreter (interpret)**
    - 코드를 미리 번역해놓지 않고 실행할 때 필요한 부분을 번역하여 실행하는 방식
    - 사전 번역 시간이 필요없다, 곧바로 실행 가능
    - 특정 기능을 실행할 때마다 번역할 시간이 필요해서 반응이 느린 편이다

* **JIT 컴파일, Just-In-Time Compiler**
    - 인터프리터 기반으로 동작한다
    - 한번 번역한 코드는 캐시(cache, 임시저장소)에 저장해놓고 사용한다
    - 인터프리트의 실행속도(반응성)가 느린 점을 보완한 방식
    - JVM은 JIT컴파일 방식으로 바이트코드를 실행한다

* **자료형, Data Type**
    - 데이터를 표현하는 정해진 방식
    - 데이터 표현법(규칙)
    - 프로그램에서 사용하는 데이터를 표현하는 방법이다

* **자바의 기본 데이터타입**
    - 자바에서 데이터를 표현하는 8가지 방식
    - 정수형 타입 (소수점 이하를 표현하지 않는 숫자 형식)   
	    1 byte (1Byte) -128 ~ 127   
	    2 short (2Bytes) -32768 ~ 32767   
	    3 **int** (4Bytes) 약 -21억 ~ 약 21억 => **(정수형 기본 데이터타입)**   
	    4 long (8Bytes)	약 -900경 ~ 약 900경
    - 실수형 타입 (소수점 이하를 표현하는 숫자 형식)   
        5 float (4Bytes)   
	    6 **double** (8Bytes) => **(실수형 기본 데이터타입)**
    - 논리형 타입   
	    7 **boolean** (1Byte) true/false => **(논리형 기본 데이터타입)**   
    (true:참, false:거짓)
    - 문자형 타입   
	    8 **char** (2Bytes) => **(문자형 기본 데이터타입)**   
	    - 문자형은 컴퓨터에서 정수형 타입으로 처리된다.
        - 코드화 시킨 문자체계(매핑표)를 적용해서 인식/사용한다.
        - 자바는 유니코드(Unicode)를 사용한다.
	- **ASCII코드 American Standard Code for Information Interchange**   
	    - 영어 대소문자, 숫자, 특수기호, 가상키를 1:1로 매핑(mapping)한 표   
	    - 한글 없음
	- **유니코드 Unicode**   
	    - ASCII로만 표현할 수 없는 전세계 문자를 매핑한 표   
	    - 유니코드는 변환과정(인코딩)을 거쳐 사용한다   
	    - 한글 인코딩 방식은 UTF-8, EUC-KR, CP949(MS949)   
	    - 주로 UTF-8을 사용한다

* **변수, Variables**
    - 변하는 값
    - 데이터(값)를 저장하는 메모리의 공간
    - 데이터를 저장하는 그릇
    - 저장할 수 있는 데이터의 형식을 자료형으로 지정하여 생성한다
    - 변수 공간에는 한 순간에 하나의 데이터만 저장할 수 있다
    - 저장된 데이터는 계속 변경할 수 있다


// 6/25일 치까지 작성.