# DB SQL

### DBMS, DataBase Management System
- 데이터베이스 관리 시스템
- Oracle DB, MS-SQL, MySql, MongoDB, SQLite, CUBRID 등등

### 데이터베이스, Database, DB
- 데이터 저장소
- 체계적인 데이터를 저장하는 시스템
- 여러 종류의 클라이언트들이 공유하면서 사용할 목적으로 관리되는 데이터의 통합 정보 관리 시스템
- 데이터베이스 내부에 테이블(Table)들을 만들어서 데이터를 관리한다

### 내가 사용하는 오라클 DB 상황
- 버전: Oracle Database 11g Release 2
- 제품군: Express Edition (Standard Edition, Enterprise Edition, Standard One Edition도 존재)
- Express Edition(XE)에는 데이터베이스가 한 개만 존재한다
- SID(DB이름) : xe
- Standard Edition에도 DB가 한 개
- SID : orcl
- Enterprise Edition에는 DB가 여러 개

### 테이블, Table, TB
- DB 내에서 실제 데이터를 저장하고 관리하는 단위
- 표 형식으로 데이터를 관리한다
- 테이블은 소유자(Owner)를 가지고 있다
    > 소유자(Owner) - 해당 객체를 생성한 사용자 계정 (ex. scott)
    > ex) scott.dept -> scott계정으로 생성한 dept 테이블
- 소유자는 자식이 생성한 테이블에 대한 모든 권한(privilege)을 가지고 있다
- DBA계정(시스템 계정, 관리자 계정)은 권한에 상관없이 소유권에 상관없이 모든 객체를 관리할 수 있다 -> 최대한 사용하지 않도록 한다
- 오라클DB의 기본 DBA계정 : SYS, SYSTEM (DBA, DataBase Administrator)

### SQL, Structured Query Language
- 구조적 질의 언어
- 자료의 검색(조회), 관리, DB객체 생성, 수정, 관리, 삭제 등을 수행하는 언어
- 주로 CRUD작업을 수행하는 명령어들이다 (Create, Read, Update, Delete)
- 스크립트 언어이다
	- 코드를 읽어서 곧바로 실행된다
	- 인터프리트 언어

### SQL의 용도에 따른 분류
#### 1. DML, Data Manipulation Langauge
- 데이터 조작어
- 테이블의 데이터를 조작(CRUD, 조회, 삽입, 변경, 삭제)하는 명령어
- 데이터를 처리할 때 사용하는 SQL
- **SELECT, INSERT, UPDATE, DELETE**

#### 2. DDL, Data Definition Language
- 데이터 정의어
- 데이터베이스의 구조를 정의, 조작하는 SQL
- **CREATE, ALTER, DROP**
- 조회(Read)에 해당하는 구문이 없다 -> 데이터사전을 SELECT하여 확인해야 한다
    > **데이터 사전, Data Dictionary, 자료 사전**
    데이터베이스의 모든 정보를 기록해둔 특수한 테이블이다
    SYS 계정이 소유자이다
	DDL을 수행할 때마다 DBMS가 알아서 알맞는 정보를 데이터사전에 반영한다
	데이터베이스에 설정된 모든 정보들을 확인할 수 있다

#### 3. DCL, Data Control Language
- 데이터 제어어
- 데이터베이스에 제한사항을 적용하거나 해제할 때 사용하는 SQL
- 보안성, 데이터의 무결성, 병행 작업, 수행 제어, 권한 등을 정의하는 SQL
- DBA가 데이터베이스를 관리하는 목적으로 사용된다
- 권한 관련 명령어 - **GRANT, REVOKE**
- 트랜잭션 관련 명령어 - **COMMIT, ROLLBACK**
- TCL, Transaction Control Language










