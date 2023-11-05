# 정의
### [[네트워크(Network)|네트워크]] 상에서 한곳에 가중되고 있는 부하를 전체적으로 분산시키는 기술
- 저장장치와 같은 컴퓨터 자원들에게 작업을 나누게 함
- 크게 [[인프라 확장(Scale-Out,Scale-Up)|Scale-Up, Scale-Out]]이 있음
### 로드 밸런싱은 OSI 계층 중 [[OSI 모형(OSI 7계층)#^8e9b22|4계층]]과 [[OSI 모형(OSI 7계층)#^319ffe|7계층]]에 속한다.
- 즉, TCP/UDP 프로토콜 또는 HTTP, HTTPS 등의 Application 단의 프로토콜을 기반으로 부하분산
### 로드 밸런싱을 위한 네트워크 장비 : L4 스위치 및 L7 스위치

>[!Cloud]
>[[클라우드 컴퓨팅(Cloud Computing)|Cloud 시스템]]에서는 대표적으로 [[AWS(Amazon Web Service)|AWS]]의 ELB(Elastic Load balancer)와 HAProxy를 사용한다.

---

# 알고리즘
### <font color="#d83931">라운드로빈(RR, Round-Robin)</font>
- 일반적으로 가장 많이 사용함(2023.10 기준)
- **[[서버(Server)|서버]]에 들어온 요청을 순서대로 배정하는 방식
- Client의 요청을 순서대로 배분
	- 따라서, 여러대의 서버가 동일한 스팩을 가지고 있다.
- 서버와의 연결이 오래 지속되지 않는 경우에 적합하다.
### <font color="#d83931">가중 라운드로빈(Weighted Round Robin)</font>
- **각각 서버마다 가중치를 주고 가중치가 높은 것부터 우선적으로 배분하는 방식
- 서버들의 트래픽 처리 능력이 상이한 경우 사용되는 부하 방식이다.
### <font color="#d83931">IP 해시 방식(IP Hash)</font>
- **Client의 IP주소를 특정서버로 매핑하여 요청을 처리하는 방식
- IP를 hashing하고 로드를 분산
	- 사용자가 항상 동일한 서버로 연결되는 것이 보장된다.
### <font color="#d83931">최소 연결 방식(Least Connection)</font>
- **Client로부터 요청이 들어온 시점에 가장 적은 연결상태를 보이는 서버에 우선적으로 트래픽을 분산하는 방식
- 연결 세션이 길어지거나 분배된 트래픽이 일정하지 않은 경우에 적합하다.
### <font color="#d83931">최소 응답시간 방식(Least Response Time)</font>
- **가장 적은 연결상태와 짧은 응답시간을 보이는 서버에 우선적으로 로드를 배분하는 방식
- 서버의 현재 연결 상태와 응답시간을 모두 고려하여 트래픽을 분산한다.

---

# 예시
### public cloud상에서는 기본적으로 로드밸런싱 서비스를 제공한다.
### On Premise상에서는 별도의 L4 및 L7의 하드웨어 스위치를 설치한다. 혹은, 소프트웨어적으로 HAProxy 및 Nginx를 이용할 수도 있다.