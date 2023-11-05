# 정의
### 전송매체(Transmission Media)로 서로 연결해 데이터를 교환하는 시스템들의 모음
### 모뎀, LAN, 케이블 및 무선매체 등의 통신설비를 갖춘 컴퓨터를 서로 연결하는 조직이나 체계, 통신망

---

# 구성요소
### 메시지 - 통신을 하고자 하는 정보
- 텍스트, 숫자, 그림, 비디오 정보 등으로 구성
### 전송장치 - 메시지(혹은 데이터) 전송장치
### 수신장치 - 메시지를 수신하는 장치
- [[서버(Server)|서버]]가 해당 역할을 수행함
### 전송미디어 - 메시지가 전달되는 실제 전송로
### 프로토콜 - 데이터통신과 관련된 규칙들로 구성
- TCP, UDP, FTP, HTTP 등

---

# 규모에 따른 분류
### LAN(Local Area Network) - <font color="#00b0f0">근거리</font> 통신 네트워크
- 건물같이 일정지역 내의 네트워크 구성
### MAN(Metropolitan Area Network) - <font color="#00b0f0">넓은 지역</font> 연결용 네트워크
- 대도시 정도의 지역 담당
- IEEE802.16 working group에서 무선 MAN 프로토콜 승인
### WAN(Wide Area Network) - <font color="#00b0f0">광범위 지역</font> 연결용 네트워크
- 하나의 국가내에서 도시와 도시 연결, 혹은 국가와국가 연결
- 흔히 인터넷이라고 부르는 네트워크이다.
### PAN(Personal Area Network) - <font color="#00b0f0">10m</font> 이내의 단거리 네트워크
- IEEE802.15 위원회에서 표준화됨
- 무선 PAN 기술로 블루투스, 지그비 등이 있다.
### BAN(Body Area Network) - <font color="#00b0f0">옷이나 인체 부착 장치</font>로 구성된 네트워크

---

# OSI 7 계층 및 TCP/IP 3계층
### [[OSI 모형(OSI 7계층)|OSI 7계층]]

---

# 네트워크 [[시스템 아키텍처(system architecture)|아키텍처]]
### LAN to LAN 망구조의 시스템
- 같은 건물 또는 위치에서 물리적/논리적 네트워크 영역을 나누어 구현
- 일반적으로 VLAN(Virtual LAN) 기반으로 구현
	- 각 VLAN의 영역(IP대역 및 게이트웨이, 서브넷)은 다름
	- 각 다른 영역의 <font color="#00b0f0">VLAN 연결</font>을 위해 <font color="#00b0f0">OSI 3계층의 라우터 또는 스위치</font> 사용
	- <font color="#00b0f0">End-point(서버, PC 단말기 등) 연결</font>을 위해서는 <font color="#00b0f0">OSI 2계층의 스위치</font> 사용
	- L2스위치, L3스위치로 나뉘어 있는 것은 L3스위치의 포트 수 한계를 극복하기 위해서이다.(on Premise 기반)
- 예시(On Premise 기반)
	![[Pasted image 20231015025517.png]]
	- 위 예시를 [[시스템 아키텍처(system architecture)||시스템 아키텍처]] 측면에서 아래와 같이 표현 가능
		![[Pasted image 20231015025825.png]]
		- L3스위치는 VLAN1~3의 세그먼트를 나누어 생성하고 각기 다른 네트워크 영역을 할당한다.
			- 만약 VLAN1의 서버가 VLAN3의 DBMS에 접속하려면 L3스위치에서 VLAN 접속허용 필요
		- L2스위치는 L3스위치로부터 할당받은 VLAN 정보를 기반으로 각 시스템에 해당 영역으로 IP 할당

>[!Cloud]
>[[클라우드 컴퓨팅(Cloud Computing)|Cloud 시스템]]에서 VLAN의 역할을 수행하는 것이 VPC이다.
### WAN to LAN 망구조의 시스템
- WAN은 서로 다른 지역 및 국가간 연결을 위한 광대력 네트워크 시스템이다.
- 서로 다른 네트워크에 접속하기 위해 [[OSI 모형(OSI 7계층)#^d37559|OSI 3계층]]의 라우팅 기술이 필요하다.
	- 라우팅 기술 사용이 가능한 네트워크 장비 : <font color="#00b0f0">L3백본 스위치 또는 라우터</font>
- 예시(On Premise 기반)
	![[Pasted image 20231015031413.png]]
	- WAN의 인터넷을 통해 한국-미국간 네트워크 연결
		- 외부와의 보안관리를 위해 방화벽 설치 필수
	- 한국지사와 미국지사간 네트워크 연결을 위해 라우터와 L3스위치로 <font color="#00b0f0">IP라우팅 설정</font>