# 정의
### 인메모리 컴퓨팅 기반 데이터 분산처리 시스템
- 디스크 I/O 효율화
- 데이터 분석작업에 용이

---

# 특징
### HDFS 사용 - [[하둡2.0(Hadoop2.0)|하둡]]의 파일시스템 기반 동작
### 직관적 이해 - 스칼라기반 최소화코드로 작성
### RDD(Resilient Distribute Dataset) - RDD 단위로 데이터 연산 수행

---

# 구성도 및 구성요소
![[Pasted image 20231015033535.png]]
- ### 구성요소
	- Spark Core - [[하둡2.0(Hadoop2.0)|하둡]]과 같은 일괄처리를 담당하며 다른 프레임워크의 기반으로 되어 있음
	- SQL - [[Data Warehouse|DataWare House]]처럼 SQL에서 인터랙티브 분석가능
	- Streaming - IoT센서 데이터나 SNS 데이터 등 실시간으로 스트리밍 처리
	- 자원스케줄링 - 자원 스케줄링 기능(YARN) 사용
		- 스케줄링을 위해 메소드 계층배치
- ### 요소기술
	- RDD - 데이터 내 장애성 보유구조
		- 데이터 집합의 추상적 객체 개념
	- RDD 연산자 - RDD에 대한 병렬 데이터 처리 연산지원 및 연산자 제공
	- 인터랙션 - 함수형 프로그래밍이 가능하도록 Scala를 사용하여 쉘 사용가능
	- 작업스케줄링 - RDD가 변화하는 과정을 그래프로 표현하고 스케줄링

---

# 동작방식

![[Pasted image 20231015034027.png]]
- ### 구성
	- Spark Application : Driver와 Executor의 프로세스로 실행되는 프로그램
	- Driver Program : Spark Application을 실행하는 프로세스
	- SparkContext : Cluster Manager와 연결되는 객체
	- Cluster Manager : Spark Application의 리소스들을 효율적으로 배분
	- Executor : Work node의 Task 실행을 담당하는 프로세스
- ### 동작순서
	1. Client는 Application을 제출
	2. Driver는 main 함수를 실행하고 SparkContext 생성, SparkContext는 Cluster Manager와 연결
		- 이때 클러스터 내부의 Work node에서 Executor 사용을 준비함
	3. Driver는 Cluster Manager로부터 Executor 실행을 위한 리소스 요청
	4. SparkContext는 작업할 내용을 Task 단위로 분할하여 Executor로 전달
	5. Work node의 각 Executor는 작업을 진행하고 결과를 지정하고 Driver에게 알려줌