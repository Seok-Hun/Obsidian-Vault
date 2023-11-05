# 정의
### 서비스형 소프트웨어라고도 하는 [[클라우드 컴퓨팅(Cloud Computing)#^8d4cbe|클라우드 서비스 유형]]
### 클라우드 애플리케이션과 이를 실행하는 플랫폼을 제공한다.
### 예시
- **Google** - Calendar, Docs, Maps
- **Saleforce** - Salesforce.com
- **Microsoft** - Office365
---
# 현실에서의 예시
### 기존기업에서는 필요한 만큼의 소프트웨어 라이선스를 구매 및 취득 후 모든 PC에 직접 설치하여 사용했었다.
### 현재에는 [[클라우드 컴퓨팅(Cloud Computing)|클라우드]] 기반의 소프트웨어의 라이선스를 [[네트워크(Network)|네트워크]]를 통해 인증하고 소프트웨어 엔진은 클라우드상에서 작동한다.
### 소프트웨어 아키텍처 예시 - Office365(Mocrosoft)
![[Pasted image 20231021212120.png]]
- 사용자들은 자신의 네트워크 및 인터넷을 통해 라이선스 인증을 요청
- 인증 및 사용요청에 관련된 트래픽은 중간의 Egress & Security Stack을 통해 보호받는다.
- 사용자들의 네트워크는 Network POP(Point of Presence)로 라우팅 되어 MS 글로벌 네트워크의 Office365 데이터 센터에 접속하기 위해 Security Front Door까지 라우팅된다.
---
# 특징
- ### 비용절감과 빠른 서비스 도입, 운영 생상선 향상 등에 유리
- ### [[다중 사용자 환경(Multi-Tenant)]]을 기반으로 하여 여러 사용자들에게 안정적인 서비스 공유를 위해 플랫폼 기술 확보가 중요
- ### Application 실행 환경, [[DataBase(DB)|데이터베이스]] 관리, 보안기술제공 필수
---