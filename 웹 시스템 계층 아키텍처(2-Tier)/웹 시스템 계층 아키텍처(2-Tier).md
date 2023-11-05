# [[웹 시스템 아키텍처(Web System Architecture)|웹 시스템 아키텍처]] 유형 중 하나이다.
---
# 개요
![[Pasted image 20231022012935.png]]
### Client 티어와 Data 티어로 구성
- Client와 Data 티어를 위해 2개의 논리적/물리적 서버로 구분될 수 있다.
### Client와 Server로 분리하여 Application과 [[DataBase(DB)|DB]]가 분리된다.
- DB 변경이 편리해질 수 있다.
### 해당 아키텍처는 단순한 Application 개발 시 사용되는 패턴 구조이다.
---
# 예시
### 보안적 요소를 추가하지 않은 초기 2-Tier 구성도
![[Pasted image 20231022013226.png]]
### SSL 연결 등 보안요소가 추가된 구성도
![[Pasted image 20231022013302.png]]
### 둘 다 공통적으로 2개의 서버가 존재한다.
- 각 서버에서 웹/웹어플리케이션, 데이터베이스 기능 또는 웹, 웹어플레케이션/데이터베이스로 작동한다.