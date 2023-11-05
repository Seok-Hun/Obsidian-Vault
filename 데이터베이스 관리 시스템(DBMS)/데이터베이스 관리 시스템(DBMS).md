# 정의
### DBMS([[DataBase(DB)|DataBase]] Management System) : 조직에 필요한 데이터를 데이터베이스에 통합하여 저장하고 관리하는 시스템
### 여러 사용자 및 시스템이 동시에 공유 및 접근이 가능해야 한다.

---
# 주요 기능

- ### 정의 기능 : 데이터베이스 구조를 정의하거나 수정을 할 수 있다.
- ### 조작 기능 : 데이터를 삽입∙삭제∙수정∙검색하는 연산을 할 수 있다.
- ### 제어 기능 : 데이터를 항상 정확하고 안전하게 유지할 수 있다.

---

# 장단점

- ### 장점
	- ### 데이터 중복 통제 가능
		- 데이터베이스에 데이터를 통합해 관리하므로 <font color="#00b0f0">데이터 중복 문제 해결</font>
	- ### 데이터 독립성 확보
		- 응용 프로그램 대신 데이터베이스에 접근하고 관리하는 모든 책임 담당
			→ 응용 프로그램과 데이터베이스 사이에 <font color="#00b0f0">독립성 확보</font>
	 - ### 데이터 <font size=5 color="#ff0000">동시 공유</font>
		- 동일한 데이터를 여러 응용 프로그램이 공유하여 동시에 접근할 수 있게 지원
			→ <font color="#00b0f0">동시 접근 제어</font> 기술 보유
	- ### 데이터 보안 향상
		- 중앙 집중식으로 데이터 관리 → <font color="#00b0f0">효율적인 접근 제어 가능</font> 
	- ### <font size=5 color="#ff0000">데이터 무결성</font> 유지
		- 데이터 삽입/수정 등의 연산이 수행될 때마다 유효성 검사로 <font color="#00b0f0">데이터 무결성(정확성) 유지</font>
	- ### 표준화 가능
		- DBMS가 정한 <font color="#00b0f0">표준화된 방식</font>을 통해 데이터베이스에 접근
	- ### 장애 발생 시 <font size=5 color="#ff0000">회복</font> 가능
		- 데이터 일관성과 무결성을 유지하며 장애 이전 상태로 <font color="#00b0f0">데이터를 복구하는 회복 기능 지원</font>
	- ### 응용 프로그램 개발 비용 절감
		- 파일 시스템보다 <font color="#00b0f0">데이터 관리 부담이 줄어듬</font>
- ### 단점
	- ### 비용이 많이듬
		- 별도 <font color="#00b0f0">구매 비용</font>, 동시 사용을 허용하는 <font color="#00b0f0">사용자 수에 따라 가격 증가</font>
	- ### 백업, 회복 방법 복잡
		- 장애 발생 원인과 상태 파악이 어렵고 회복 방법도 <font color="#00b0f0">복잡함</font>
	- ### 중앙 집중 관리로 취약점 존재
		- 장애 발생 시 <font color="#00b0f0">전체 시스템의 업무 처리가 중단됨</font>

---
# [[Database Transaction]]으로 작업 수행

---

# Database Block

### 정의
- DB 데이터 검색과 저장의 <font color="#ff0000">가장 기본 단위 </font>(2K, 4K, 8K, 16K, 32K, 64K)
- 물리적 디스크 공간 크기에 따라 Block 크기가 결정된다.
### 모든 DB I/O는 <font color="#ff0000">DB Block</font> 단위로 수행
### 보통 Block 당 평균 수십 개의 레코드가 들어갈 수 있는 크기로 구성
- 단, <font color="#ff0000">하나의 레코드만 읽을 경우라도 최소 1 Block을 Access 해야함</font>
### <font color="#00b0f0">Clustering Factor</font> - Index key column을 기준으로 데이터들이 얼마나 잘 정렬되어 있는지를 나타내는 수치
- 즉, <font color="#ff0000">비슷한 값들이 얼마나 서로 모여 있는지</font>를 나타내는 수치이다.
- 해당 값이 클수록 데이터 처리를 위해 Access할 Block의 건수가 적어져 I/O 횟수를 줄일 수 있다.
	- 아래 예시처럼 클러스터링 팩터가 높은 케이스1에선 데이터를 찾기 위해 2개의 Block만 Access 한다.
		![[Pasted image 20231014154655.png]]
	- 단, <font color="#00b0f0">검색 조건이 달라질 경우 오히려 성능 저하가 발생할 수 있다.</font>
		- <font color="#ff0000">다양한 조건 검색을 염두에 두고 데이터 저장 구조를 설계해야 한다.</font>
- <font color="#ff0000">동일한 table이더라도 검색 조건에 따라 Clustering Factor가 달라질 수 있다.</font>
	- 아래 예시에선 같은 테이블에서 다른 조건으로 검색할 경우의 클러스터링 팩터 차이를 알 수 있다.
	![[Pasted image 20231014155315.png]]

---

# I/O Access 유형
### Sequential Access(순차 Scan) - 정해진 순서대로 데이터를 <font color="#ff0000">순차적으로 검색</font>
- 데이터를 읽는 양은 Random Access보다 많을 수 있지만 대용량 데이터를 읽을 때는 더 효과적이다.
	![[Pasted image 20231014160510.png]]

### Random Access(임의 Access) - 순차적으로 레코드를 읽지 않고고 <font color="#ff0000">원하는 레코드만을 직접 Access</font>
- <font color="#ff0000">데이터를 빨리 검색할 수 있는 Access 방식</font>
- 검색할 레코드들과 관련된 <font color="#ff0000">key</font> 필요
	- DBMS에서는 <font color="#00b0f0">Index를 경유한 Table</font> 활용
		![[Pasted image 20231014160424.png]]

---

# [[NoSQL]]
### 기존의 [[관계형 데이터베이스(RDBMS)|RDBMS]]의 특성 뿐만 아니라 다른 특성들을 부가적으로 지원
- 여러 유형의 데이터베이스 사용
### NoSQL = No RDBMS 가 아니다
- KV(Key-Value)-store : BerkleyDB, SQL 부분집합 수준의 호환 레이어 제공
### 표준 query가 없다.
- 예시로 [[MongoDB]] 쿼리 언어와 [[CouchDB]] 쿼리 언어가 다르다.
>[!Query]
>- 데이터베이스에 정보를 요청하는 것을 뜻한다.
>- 웹 서버에 특정한 정보를 웹 클라이언트 요청에 의해 처리하는 것이다.
>- 겁색된 결과를 자유로이 조회할 수 있는 기능을 지원하는 것이 특징이다.







