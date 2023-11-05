![[Pasted image 20231022020756.png]]
# 개요
### [[웹 시스템 계층 아키텍처(3-Tier)|WAS]] 프레임워크이다.
- 웹 컨테이너 또는 Servlet 컨테이너라고 불린다.
### [[JDK(Java Developement Kit)#^a69cd3|JAVA EE]] 기반으로 개발되었다.
- JSP/Servlet을 구동하기 위한 역할을 수행한다.
### 동적인 기능들을 담당한다.
- [[DataBase(DB)|DB]]연결, 다른 응용 프로그램과의 상호작용 등 
### 동작 프로세스
1. HTTP 요청을 Coyote가 받아서 Catalina로 전달
2. Catalina에서 전달받은 HTTP 요청을 처리할 웹 어플리케이션의 Context를 찾고, WEB-INF/web.xml 파일 내용을 참조하여 요청을 전달한다.
3. 요청된 Servlet을 통해 생성된 JSP 파일들이 호출될 때, Jasper가 검증 및 컴파일리 체크를 한다.
---
# 구성
### Coyote(Http Component) : Tomcat에 TCP를 통한 프로토콜 지원
### Catalina(Servlet Container) : Java Servlet을 호스팅하는 환경
### Jasper(JSP Engine) : JSP 페이지의 요청을 처리하는 Servlet
---
# 동작원리
![[Pasted image 20231022022323.png]]
1. HTTP를 통한 요청을 Servlet 컨테이너로 전달한다.
2. Servlet 컨테이너는 HttpServletRequest, HttpServletResponse 두 객체를 생성한다.
3. Client가 요청한 URL을 분석하여 어느 Servlet에 대한 요청인치 체크한다.
4. 만약 해당 Servlet이 한번도 실행되지 않았거나 메모리에 생성된 인스턴스가 없다면 새로 생성한다.
	- init()메소드를 실행하여 초기화 한 후 스레드를 하나 생성한다.
	- 이미 인스턴스가 존재할 경웅는 스레드만 하나 생성한다.
5. Servlet 컨테이너는 service() 메소드를 호출하고 POST/GET 방식에 따라 doGet() 또는 doPost()를 호출한다.
6. 실행된 service 메소드는 동적인 페이지를 생성하고 HttpServletResponse 객체에 응답한다.
7. 응답이 Client에 완료되면 HttpServletRequest, HttpServletResponse 두 객체를 소멸시킨다.