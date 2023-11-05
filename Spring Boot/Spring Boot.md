![[Pasted image 20231022023848.png]]
# 개요
### [[Spring Framework]]의 단점을 보완한 프레임워크
- 수많은 필요설정부분들을 간략하게 처리해준다.
---
# 특징
### 간결한 설정
- Spring과 다르게 번거로운 XML 설정이 필요 없다.
- 기본적인 설정을 자동으로 처리하여 개발자가 따로 많은 설정을 할 필요 없다.
### 내장된 서버
- 별도의 내장된 서버([[Tomcat]], Jetty, Undertow)를 제공한다.
	- 별도의 WAS를 설치할 필요 없다.
- 의존성 라이브러리가 포함된 JAR 파일을 외부 서버 없이 싫행시킬 수 있다.
### 의존성관리 간소화
- Starter라는 의존성 통합모듈을 제공
	- 3rd party 의존성 관리를 용이하게 해준다.
	- Maven/Gradle 설정 시 버전관리가 쉬워진다.
### 운영의 편의성
- 어플리케이션의 Status monitoring, logging, Security 등 운영에 필요한 기능들을 제공한다.
---
# 활용범위
### 웹 어플리케이셔 개발
- RESTful API, MSA 등 다양한 웹 어플리케이션을 개발할 수 있다.
### 배치처리
- 대용량 데이터 처리, 일관처리 및 정기적인 스케줄링 작업을 효율적으로 처리할 수 있다.
### 보안 및 인증
- Spring security와 통합하여 사용자 인증, 권한부여, 세션관리 등 다양한 보안인증을 처리한다.
### 클라우드 Native app
- MSA, 컨테이너, 스케일링, logging, monitoring 등 개발과 배포를 용이하게 한다.
### [[DataBase(DB)|DB]] Access
- JDBC, JPA, Spring Data JPA 등 다양한 DB 연동지원을 통해 쉽게 DB에 접근할 수 있다.
---
# 기본 동작원리
### 사용자로부터 요청을 받을 수 있는 Servlet 컨테이너부터 다시 피드백을 주기 위한 응답까지 유기적으로 연결되어 Back-end 단에서 작동한다.
### 동작 단계
1. **Servelt 컨테이너**
	- 사용자로부터 http 요청을 받아 웹페이지를 동적으로 생성한다.
	- 기본적으로 Servlet 컨테이너인 Tomcat이 기본적으로 내장되어 있다.
	- URL 방식이 아닌 URI 방식을 사용한다.
2. **web.xml**
	- web.xml : Spring Boot의 상세한 설정(보안기능을 포함한 여러 기능 수행)
		- 권한과 인증을 위해 ServletContext 초기 파리미터 설정
		- Servlet과 JSP 파일을 체크하여 이에 대한 정의 및 Mapping 설정
		- 보안을 위해 Session 유효값 설정
		- Mime Type Mapping : Spring에 접근하는 데이터타입을 확인하여 목적지 타입으로 변경
		- Welcome File List 설정 : 필터링 영역에 없는 데이터 접근 시 공통영역에 보내기 위한 설정
		- Error Page 처리설정 : 필터링 할 수 없는 데이터 접근 시 Error Page를 보여주기 위한 설정
		- Listener, 필터설정, 보안 등
3. **DispatcherServlet**
	- FrontController : web.xml의 일을 나누어 하도록 하는 패턴
	- RequestDispatcher : FrontController로부터 요청 및 응답을 그대로 유지시켜줌
4. **Spring 컨테이너**
	- ApplicationContext : DispatcherServlet에 의해 생성되는 객체
		- IoC컨테이너라고도 한다.
		- 종류
			- servlet-applicationContext
			- root-applicationContext
	- Bean factory : 객체를 등록하는 곳
		- @Bean -> 객체 로 로딩한다.
5. **Controller 요청**
	- 요청된 목적지에 따라 적절하게 Controller의 함수를 찾아 실행한다.
6. **Response**
	- 사용자에게 다시 응답하는 방식
		- 파일을 return 하는 방식으로 ViewResolver가 작동되는 방식
		- 데이터 return 방식
	- 응답을 위해 MessageConverter(@ResponseBody)가 작동된다.
### 동작단계 예시
![[Pasted image 20231022025733.png]]
![[Pasted image 20231022025809.png]]
1. 웹브라우저에서 http://localhost:8080/hello-value로 요청
2. 요청을 Tomcat 서버가 받는다.
	- DispatcherServlet이 web.xml에 있는 데이터를 읽고 해당 Spring 컨테이너를 생성한다.
3. 진행됨에 따라 필요한 객체들을 bean factory에 등록한다.
4. Spring 컨테이너에서 Tomcat 서버를 통해 들어온 요청에 맞는 Controller를 찾아 처리한다.
5. viewResolver가 최종 처리에 맞는 html 파일을 찾아 다시 웹브라우저를 통해 사용자에게 응답해준다.





