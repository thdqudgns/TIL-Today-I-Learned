# :pushpin: Framework

* [MyBatis](https://github.com/thdqudgns/TIL-Today-I-Learned/blob/main/Framework/MyBatis.md)
* [Spring](https://github.com/thdqudgns/TIL-Today-I-Learned/blob/main/Framework/Spring.md)

### 프레임워크, Framework
- 뼈대, 기반 구조, 체계
- 프로그램을 개발하기 위한 여러 요소들(클래스 + 인터페이스 등)과 개발 절차(규칙)를 제공하는 것
- 프로그램 개발의 밑바탕이 되고 (사용 형식이 정해져 있는) 클래스와 인터페이스의 집합

### 라이브러리 vs 프레임워크
- 라이브러리와 달리 프레임워크는 API들의 사용 절차(개발 절차)까지 포함하는 경우가 많다
- **라이브러리는 응용프로그램의 흐름(의존성)을 코드로 개발자가 직접 제어한다**
- **프레임워크는 프레임워크에 의해서 프로그램의 흐름이 제어된다**
- 프로그램을 구성하는 API(컴포넌트)들을 
    - 직접 호출해서 사용하면 라이브러리
    - 만들어 놓은 코드(클래스)들을 가져가서 동작되도록 하면 프레임워크
	- IoC, Inversion of Control, (프로그램 흐름)제어의 역전

### 스프링 프레임워크, Spring Framework
- MVC패턴을 이용한 Java 프로그램 개발을 위한 프레임워크

### 마이바티스 프레임워크, MyBatis Framework
- 퍼시스턴스 계층 프레임워크 ( Persistence Layer )
    * Persistence, 영속성 : 특정 상태가 꾸준히 유지되는 속성
	* Persistence Layer : 데이터베이스 계층
- JDBC관련 개발을 편하게 만들어 준다
- JDBC 프레임워크, 데이터베이스 관리 프레임워크라고 표현하기도 한다
    - DAO 인터페이스, DaoImpl 클래스 부분을 담당하는 프레임워크