# :pushpin: JOIN

### :bulb: 조인, JOIN
- **두 개 이상의 테이블을 한번에 SELECT(조회)하는 방법**
- 조인되는 테이블들의 모든 조합을 조회한다
    - 모든 행들의 조합 + 모든 컬럼의 조합
    - 조인되는 **행들의 곱**만큼, 조인되는 **컬럼들의 합**만큼 결과가 생긴다
	```sql
    ex)	emp TB : 12rows 8cols 
		dept TB : 4rows 3cols
		emp x dept : 48rows(12*4) 11cols(8+3)
    ```
- 의미있는 데이터를 추출하기 위해 조인 조건을 설정한다
    - **Primary Key**와 **Foreign Key**를 이용하여 조건절을 구성한다
    - 조인 조건 : 조인되는 테이블들의 관계를 설정하는 조건문(WHERE절 이용)

### :bulb: Primary Key, PK, 기본키, 주키
- 테이블의 각 행(데이터)들을 구분하기 위한 **식별데이터**로 쓰이는 컬럼
- **기본키 무결성 원칙**
    - 해당 컬럼은 테이블에서 **고유한 값**을 가져야 한다 - UNIQUE
    - 해당 컬럼은 **NULL값을 가질 수 없다** - NOT NULL
    > ex)   emp.empno   
	        dept.deptno

### :bulb: Foreign Key, FK, 외래키, 참조키
- 다른 테이블의 컬럼을 참조하고 있는 컬럼
- **다른 테이블의 Primary Key를 참조한다**
- **참조 무결성 원칙**
    - 참조 테이블의 **기본키**의 값으로 존재하는 데이터만 가질 수 있다
	> ex)   emp.deptno

### :bulb: 조인 문법 종류
- 오라클 전용 문법: 오라클 SQL만의 특수한 조인 문법
- ANSI 표준 문법 : ANSI기구가 표준으로 지정한 조인 문법
> **ANSI ( American Nation Standards Institude )**   
미 국립 표준 협회   
ISO 기구에 속해있는 협회

> **ISO ( International Standard Organization )**   
국제 표준화 기구

> **IEEE ( Institude of Electric and Electronics Engineers )**   
전기, 전자 기술자 학회   
IEEE 802.3 - 이더넷 (유선 통신)   
IEEE 802.11 - 와이파이

#### :bulb: EQUI JOIN, 등가 조인
- 오라클 전용 구문
- FROM절에 조인 대상 테이블들을 , 로 나열한다
- **테이블들의 공통데이터를 가지는 컬럼**으로 조인한다(equal비교, 등가 비교, =)
- **WHERE절을 이용하여 조인 조건을 적용한다**
- 가장 많이 사용되는 조인 구문이다
#### :bulb: INNER JOIN, 내부 조인
- ANSI 표준 문법
- EQUI JOIN과 같은 결과를 얻을 수 있다
- 구문 형식
    ```sql
    FROM 조인대상테이블
	INNER JOIN 조인테이블
	ON 조인조건
    ```
#### :bulb: NON-EQUI JOIN, 비등가 조인
- EQUI-JOIN과 문법은 같으나 조인조건의 비교 연산자 =(equal)이 아닌 경우
#### :bulb: SELF JOIN, 자체 조인
- 하나의 테이블이 **자기 자신 테이블과 조인**하는 것
#### :bulb: CROSS JOIN, 상호 조인
- 카테시안 곱을 얻을 때 사용하는 구문
> **카테시안 곱, Cartesian Product**   
테이블의 조인 결과로 조회가능한 **모든 경우의 수를 출력**하는 것   
모든 컬럼, 모든 행의 조합을 생성한다
#### :bulb: NATURAL JOIN, 자연 조인
- 조인 조건을 설정하지 않고 EQUI JOIN(등가 조인)을 자동으로 수행한다
- 조인 조건이 되는 컬럼을 알아서 자동으로 판단한다
	- 조인 조건을 개발자가 마음대로 제어하는 데 어려움이 있다
#### :bulb: OUTER JOIN, 외부 조인
- **조인 조건에 사용한 컬럼의 값을 한 쪽 테이블이 가지고 있지 않을 때** 사용하는 조인
- NULL값이 포함된 컬럼을 조인 결과로 추가할 때 사용할 수 있다
- **서로 일치하지 않는 각각의 데이터를 조인 결과에 추가해준다**
- 오라클 전용구문에서는 조인 조건에 **(+)연산자**를 추가해서 사용한다
	- (+) : 외부(OUTER) 조인 연산자
- EQUI JOIN구문에서 조인 조건의 비교컬럼에 연산자를 붙인다
	- 연산자가 적용된 컬럼의 테이블쪽에 null값을 채워준다
- 조인조건의 왼쪽 컬럼쪽 테이블 데이터가 부족하면 왼쪽컬럼에 (+) 사용한다
- 조인조건의 오른쪽 컬럼쪽 테이블 데이터가 부족하면 오른쪽컬럼에 (+) 사용한다
- **테이블 데이터가 부족한 쪽에 (+) 사용한다**
#### :bulb: 오라클 구문 -> ANSI 구문 변환 방법
- **FROM절의 테이블 순서와 조인조건의 컬럼 순서를 같은 순서로 둬야 한다**
- 조인조건의 왼쪽 컬럼에 (+)연산자가 붙어있으면 RIGHT OUTER JOIN으로 변환
- 조인조건의 오른쪽 컬럼에 (+)연산자가 붙어있으면 LEFT OUTER JOIN으로 변환
#### :bulb: FULL OUTER JOIN
- ANSI 표준 구문으로만 제공된다
- **조인되는 테이블 양쪽에 모두 NULL데이터를 추가**할 때 사용한다

### :bulb: TCL(Transaction Control Language)
- 트랜잭션 제어(관리) SQL 구문
> COMMIT - 트랜잭션 영구 반영(물리적으로 저장된다)   
ROLLBACK - 원상 복구(작업 내역을 되돌린다)

### :bulb: 트랜잭션, Transaction
- 클라이언트별로 **작업 내역을 임시로 보관**하는 것이다
- 데이터베이스의 작업 단위
- **DML의 INSERT, UDPATE, DELETE 내역만 보관한다**
- **SELECT는 보관하지 않는다**