# 정의
### 물리적으로 다른 시스템을 논리적으로 통합하거나, 하나의 시스템을 논리적으로 분할해 자원을 사용하는 기술
---
# 유형
### 가상화되는 부분에 따른 유형
![[Pasted image 20231027003342.png]]
- 흔히 우리가 사용하는 데스크톱 가상화는 운영체제에서부터 시작된다.
- 물리적 환경인 단말기는 논리적으로 운영체제를 구동시키기 위한 시스템 중 하나로 작동된다.
### 분류에 따른 유형
- **SW 가상화**
	- OS Emulation
		- 다른 OS환경에서 구동되는 어플리케이션을 특정 OS에서 구동되게 한다.
		- 사례 : [[JVM(Java Virtual Machine, 자바 가상 머신)|JVM]]
	- 자원관리
		- 단일 OS환경에서 처리 또는 사용자들의 서버관리 사용량을 관리한다.
		- 사례 : PRM(Process Resource Management)
	- 가상운영체제
		- 하나의 서버에서 여러 가상 OS를 구축하여 중간급 이하 서버군에 대한 Consolidation을 가능하게 한다.
		- 사례 : VMWare, VirtualBox, VM
- **HW 가상화**
	- Partitioning
		- 서버자원을 물리적 또는 논리적으로 분할하여 독립적인 여러 서버로 다시 분할할 수 있게 한다.
			- 물리적인 서버들을 하나의 High-end급 서버로 Consolidation이 가능하게 한다.
		- 사례 : IBM LPAR, HP CPARs/NPARs, VMWare ESX server
- **SW+HW 가상화**
	- Distributed Workload Mgmt
		- 다중 OS환경에서 Workload Manager가 OS들의 리소스 사용량을 관리한다.
			- 다수의 OS들이 또 다른 다수의 자원들을 공유할 수 있게 해주는 기술을 의미한다.
		- 사례 : IBM bWLM, HP gWLM
### 기술 구분에 따른 유형
- **인프라 자원**
	- [[서버(Server)|서버]] 가상화
		- 가상화 기술 : Partitioning, 가상 I/O, HyperVisor
	- [[스토리지(Storage)|스토리지]] 가상화
		- 가상화 기술 : 블록 가상화, 가상 테이프라이브러리(VLTO)
	- [[네트워크(Network)|네트워크]] 가상화
		- 가상화 기술 : L2~L7활용, VPNs, VLANs
- **정보**
	- 파일 가상화
		- 가상화 기술 : 클러스터 파일, 그리드 파일 시스템
	- 데이터 가상화
		- 가상화 기술 : 데이터 연합 및 Consolidation
- **Workload**
	- 트랜잭션 가상화
		- 가상화 기술 : JVM [[Load Balancing(부하분산)|로드밸런싱]]
	- Task 가상화
		- 가상화 기술 : 컴퓨팅 그리드
	- Presentation 가상화
		- 가상화 기술 : 서비스 기반 컴퓨팅(SBC)
- **운영 환경**
	- 전사적 workload
		- 가상화 기술 : Enterprise Workload Manager
	- 전력/냉각 효율화
		- 가상화 기술 : Hibernation, Partition Mobility
	- Utility Service
		- 가상화 기술 : Metering, Provisioning
	- 백업 가상화
		- 가상화 기술 : VTL 백업, 테이프 라이브러리 기반 백업
	- 클라이언트 데스크탑 가상화
		- PC 가상화, 서버기반 컴퓨팅, VDI(Virtual Desktop Infrastructure)
---
# 효과
### 친환경 구현
- 열발생, 탄소발생을 줄여 친환경 구현에 기여
### TCO 절감
- 잔여자원(메모리, CPU, Cache)의 재사용을 통해 비용을 줄일 수 있다.
### 개인정보유출 위험 감속
- 논리적 가상화는 기밀정보의 유출을 원천적으로 차단하는 효과를 제공한다.
---
# 원리
### 공유(Sharing)
- 물리적으로 위치한 자원을 사용자에게 나누어 사용할 수 있다.
- 관련기술 : 파티셔닝, VLAN
### 단일화(Aggregation)
- 분산자원을 통합, 논리적 단순화를 통해 자원활용 향상 및 관리에 용이하다.
- 관련기술 : [[DB 클러스터(DB Cluster)|클러스터링]]
### Emulation
- 가상화로 인한 논리적 객체는 물리적인 객체와 동일한 기능을 수행한다.
- VTL, 에뮬레이터
### 절연(Insulation)
- 물리적인 자원의 교체나 변경에도 서비스를 안정적으로 유지한다.
- 관련기술 : RAID, HA, L4