# 웹 시스템 계층 아키텍처
### 시스템 아키텍처 패턴 중 레이어(Tier)패턴이 적용될 수 있다.
- [[웹 시스템 계층 아키텍처(1-Tier)|1-Tier]]
- [[웹 시스템 계층 아키텍처(2-Tier)|2-Tier]]
- [[웹 시스템 계층 아키텍처(3-Tier)|3-Tier]]
---
# 구성
![[Pasted image 20231022005857.png]]
### Presentation(클라이언트) 계층
- Front-end 계층이라고 한다.
- 사용자 인터페이스를 지원하는 계층이다.
- 인터넷 브라우저의 정적인 데이터를 처리한다.
- 비즈니스 로직이나 데이터 관리 코드가 포함되면 안된다.
### Application(비즈니스) 계층
- Middleware 또는 Back-end 계층이라고 한다.
- 정보처리의 규칙을 가진다.
- 동적 데이터가 처리된다.
- 프레젠테이션 코드나 데이터 코드가 포함되면 안된다.
### Data 계층
- [[DataBase(DB)|데이터베이스]]를 주로 의미한다.
- DB 또는 파일시스템의 접근통제를 관리한다.
---
# 웹 시스템 관련기술
### Front-end
- **[[Apache]]**
- **[[Nginx]]**
### Back-end
- **[[Tomcat]]**
- **[[Spring Framework]]**
- **[[Spring Boot]]**
### Back-end
- [[관계형 데이터베이스(RDBMS)|RDBMS]]
- [[NoSQL]]