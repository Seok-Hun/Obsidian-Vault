![[Pasted image 20231022154820.png]]

---
# 개요
### 2006년에 공식 서비스를 시작한 아마존닷컴의 [[클라우드 컴퓨팅(Cloud Computing)|클라우드 컴퓨팅]] 사업부이다.
### 다른 웹사이트나 클라이언트측 응용 프로그램에 대해 온라인 서비스를 제공한다.
- 서비스 상당수는 최종 사용자에 직접 공개되는것이 아니고, 다른 사용자가 사용 가능한 기능을 제공하는 플랫폼을 제공하는 [[PasS(Platform as a Service)|PaaS]]이다.
### 각종 서비스는 REST Protocol 및 SOAP Procotol을 통해 접근, 이용, 관리가 가능하다.
### 비용은 실제 사용량에 따라 결정된다.
- 일부 서비스의 경우 미리 고정된 금액을 지불하는 형태도 있다.
---
# 기술 서비스 분류
![[Pasted image 20231022155405.png]]
### EC2(Elastic Compute Cloud)
- AWS의 대표적인 컴퓨팅 서비스로 탄력있는 인스턴스 기술을 제공한다.
	- [[인프라 확장(Scale-Out,Scale-Up)|Scale-Up, Scale-Down, Scale-In, Scale-Out]]이 자유롭다.
- 전형적인 [[IaaS(Infrastructure as a Service)|IaaS]] 타입이다.
	- On-Premise와 비교해서 서버와 같은 기능 수행
- **특징**
	- 한개~수천개의 인스턴스로 확장이 가능하다.
		- 즉, 가상서버를 원하는대로 생성할 수 있다.
	- 공개된 AWS region에서 사용이 가능하다.
	- 필요에 따라 인스턴스의 생성/시작/수정/중단/삭제 기능을 제공한다.
	- Linux/Winodws OS에서 사용 가능하며 모든 소프트웨어를 설치할 수 있다.
	- 사용한 사용량에 대해서만 시간 단위 비용을 부과한다.(On-Demand 방식)
		- 다양한 비용모델(On-Demand, Spot, 예약)을 선택 가능하다.
- 설치절차
	![[Pasted image 20231022155936.png]]
	- On-Premise 서버는 설치에 한달 이상이 걸리지만 [[클라우드 컴퓨팅(Cloud Computing)#^da495e|VM]]은 최소 1시간이면 가능하다.
	- AWS의 [[클라우드 컴퓨팅(Cloud Computing)#^9f135e|콘솔시스템]]에서 진행이 가능하다.
	- 예시
		![[Pasted image 20231022160211.png]]
		- AWS에 로그인하면 콘솔 홈으로 접속
		- EC2메뉴를 선택하면 유형(스팩 및 OS 종류 등)을 선택하는 부분이 나온다.
			- EC2 설정 전에는 반드시 VPC 네트워크를 먼저 생성해야 한다.
		- EC2 VM 인스턴스 생성완료시 ID생서오가 함께 실행 중임을 콘솔창에서 확인 가능하다.
### LightSail
- AWS의 컴퓨팅 서비스 중 하나
- VPC를 가장 간편하게 시작하고 관리할 수 있는 방법을 제공한다.
	- 프로젝트 진행에 필요한 VM, SSD, DNS관리, 고정 IP 및 데이터 정송 등 모든 기능들이 이미 포함되어 있다.
- EC2 서비스보다 저렵한 요금으로 사용 가능하다.
	- 경량화된 EC2 서비스라고도 한다.
- 예시 - 콘솔화면과 아키텍처
	- AWS Lightsail 전용 페이지 - 기본적인 Lightsail 기반의 어플리케이션 목록을 볼 수 있다.
	![[Pasted image 20231022160713.png]]
	- Lightsail의 확장성과 고가용성을 나타낸 아키텍처
	![[Pasted image 20231022160733.png]]
### Auto Scaling
- 어플리케이션의 로드를 처리할 수 있는 정확한 수의 EC2 인스턴스를 유지를 가능하게 하는 기능이다.
	- EC2 인스턴스 모음 생성
	- 각 auto scaling의 최소 인스턴스 수를 지정할 수 있다.
		- EC2 auto scaling에서는 그룹의 크기가 해당 값 이하로 내려가지 않는다.
- 수요변화가 많지 않은 어플리케이션과 사용량이 시/일/주 단위로 변하는 어플리케이션 모두에게 적절하다.
- 특징
	- 어플리케이션의 가용성을 간편하게 관리할 수 있다.
	- 사용자가 정의한 조건에 따라 EC2 용량이 자동으로 확장/축소된다.
		- 용량 : CPU, 메모리 등
		- <font color="#ff0000">Scale In : 수요 측 접속자 수가 증가할 경우 인스턴스 수를 자동으로 증가시킨다.</font>
		- <font color="#ff0000">Scale Out : 수요가 적어질 경우 자동으로 용량을 감소시켜 비용낭비를 최소화한다.</font>
- Auto Scaling Group : 인스턴스 조정 및 관리를 위해 구성된 논리적 그룹
	- Auto Scaling을 수행하는 인스턴스의 모음
	![[Pasted image 20231022163337.png]]
### Lambda
![[Pasted image 20231022164119.png]]
- <font color="#ff0000">Serverless</font>
	- 서버가 없다는 개념보다는 <font color="#00b0f0">서버를 관리할 필요가 없는 자동화 기능을 가진 시스템</font>에 더 가깝다.
	- 개발자 및 시스템 엔지니어가 개발이나 우선순위가 높은 작업에 집중할 수 있도록 한다.
- 특징
	- 완전관리형 서비스이다. → 서비스 기능을 담당할 코드만 작성하면 된다.
		- 인프라를 구성하는 네트워크 및 서버의 설정 등의 관리를 신경쓸 필요가 없다.
		- 설치해야하는 소프트웨어나 런타임이 없다.
	- 유연한 확장성
		- 다른 서비스를 호출 및 연결하여 자신이 원하는 서비스로 실행시킬 수 있다.
	- [[고가용성(High Availability)|고가용성]]
		- 여러곳의 가용영역에 Lambda를 설치하고 서비스에 문제가 발생하지 않도록 쉽게 운영 가능
	- MSA와 호환성이 좋다.
		- 마이크로 서비스 특성상 호환성 등의 제약이 없어 쉽게 독립적인 다른 서비스에 연결 및 기능을 전달할 수 있다.
	- 추가적인 비용없이 항시대기가 가능하다.
		- 요청이 올 때만 provisioning(자원할당) 되므로 비용절감에 매우 효과적이다.
- 예시 - 타겟언어로 자동으로 변환해주는 솔루션 아키텍처
	- 서버관리 등을 신경 쓸 필요없이 자동으로 변환해주는 서비스
	![[Pasted image 20231022164308.png]]
	1. Amazon Translate를 이용해 소스언어를 타겟언어로 변환하기 위해 Lambda 함수 생성
	2. S3콘솔에서 S3 Object Lambda Access Point 생성
	3. 1번 과정에서 생성된 Lambda 함수 선택
	4. Original 객체로 S3 Object Lambda Access를 전달하기 위해 S3 Access Point 지원을 제공한다.
	5. S3 GetObject API를 활용하여 S3 Storage에서 파일을 회수한다.
	6. 실질적인 S3 Bucket 이름을 대신해 Object Lambda Access Point ARN(Amazon Resource Name)을 통과시킨다.
### VPN & VPC
- VPN(Virtual Private Network) : 여러 곳에 분산되어 있는 시스템들을 연결하는 보안성이 높은 사설망
- VPC(Virtual Private Cloud) : AWS에서 논리적으로 격리된 네트워크 공간
	- 가상 네트워크에서 AWS 리소스를 이용 가능하다.
- AWS는 VPC와 VPC Gateway를 통해 On-Premise의 VPN과 AWS VPN을 연결하여 [[Hybrid Cloud]]를 구현하거나 시스템 이전(Migration)을 할 수 있다.
	- 기존 데이터센터에서 작동하는 정보시스템들을 Cloud로 이전(Migration)하는 것은 매우 힘든 일이다.
	- 이를 쉽게 하는 것이 Migration Tool을 이용하는 것과 On-Premise와 클라우드간의 네트워크를 연결하느느 것이다.
- 예시 - 회사 네트워크 및 시스템 클라우드를 VPN으로 연결하는 Hybrid Cloud
	- 기업의 사용자들은 클라우드에 새롭게 구축되거나 이전된 시스템들을 원격사이트로부터 VPN 및 VPC를 통해 접속할 수 있다.
	![[Pasted image 20231022165247.png]]
### CloudFront & Route 53
- CloudFront : 웹 사이트, 동영상, API 등 정적 웹 데이터의 전송을 가속화하는 글로벌 컨텐츠 전송 네트워크 서비스이다.
	- 보안측면에서 데이터들이 전세계에 위치해 있는 데이터센터의 네트워크(Edge Network)로 전송되기 때문에 DDos 방어에도 유용하게 사용됨
	- 컨텐츠가 전송을 위해 지연 시간이 낮은 Edge Location에 위치할 경우 CloudFront가 컨텐츠를 즉시 제공한다.
		- 컨텐츠가 Edge Location에 없을 경우, CloudFront는 최신화 소스가 있는 오리진 서버(S3 Bucket, http웹서버, 미디어패킷채널 등)에서 컨텐츠 검색
- Route 53 : AWS 클라우드에서 도메인 등록, 관리 및 DNS 기능 담당, 기업의 서버 다운 및 장애를 감지하고 백업서버로 Redirection하는 기능도 있다.
- 예시 - 그림과 동영상을 CloudFront, Route53을 이용해 사용자에게 제공
	![[Pasted image 20231022171400.png]]
	- Route53은 도메인 이름으로 목적지까지 접속 가능하게 한다.
	- CloudFront는 EC2서버를 default 오리진 서버로 설정한다. 그리고 추가로 2개의 S3 Bucket(Picture, Movie)를 설정한다.
		- CloudFront의 Behavior를 적절하게 설정해주어야 한다.
		- 사용자가 .png 컨텐츠를 요청하면 ClodFront가 두번째 S3버킷으로 컨텐츠를 요청한다.
		- 사용자가 .mpeg 컨텐츠를 요청하면 CloudFront가 세번째 S3버킷으로 컨텐츠를 요청한다.
		- 그 외 요청들은 ELB 로드밸런싱을 거쳐 웹서버(Nginx)에 요청한다.
### ELB(Elastic Load Balancing)
- 일반적으로 AWS Cloud 상에서 동작하는 EC2 인스턴스의 부하를 분사닛켜 주는 역할을 하는 서비스이다.
	- AWS Direct Connect라는 네트워크 서비스와 함게, 전세계에서 분산된 AWS 네트워크 접속 지연시간을 줄일 수 있는 서비스이다.
- 크게 ALB(Application Load Balancing)과 NLB(Network Load Balancing)으로 나뉜다.
- 예시1 - 2개의 EC2 인스턴스를 ELB가 [[Load Balancing(부하분산)|부하분산]]하는 구조
	![[Pasted image 20231022172100.png]]
	- 웹서버의 HTTP Protocol 기준으로 부하분산을 하므로 ALB로 구현했다.
- 예시2 - 예시1을 3티어구조로 아키텍처 구현
	- ELB 추가 및 외부/내부의 네트워크 영역으로 나누어 진행할 수 있다.
	![[Pasted image 20231022172216.png]]
	- 빨간색 영역을 보면 내부망에 설치된 Web 어플리케이션 서버들의 부하분한을 하는 내부 ELB가 있다.
### S3(Simple Storage Service) & Glacier
- S3 : 무한대로 저장이 가능하고, 사용한 만큼 요금을 지불하는 인터넷 기반 [[스토리지(Storage)|Storage]] 서비스이다.
	- Bucket이라는 Region 내에서 유일한 영역을 생성하고 Key-Value의 형식으로 데이터  객체를 저장한다.
	- Storage 기술을 근간으로 하여 파일단위로만 접근이 가능하다.
	- 특징
		- 2006년 출시된 최초의 AWS 서비스
		- URL을 통해 쉽게 파일 공유 가능
		- 객체파일 기반의 무제한 저장 Storage
		- 기본적으로 정적 웹사이트 구축을 위한 웹서버 기능을 제공한다.
		- 높은 내구성을 가진다.
	- 활용분야
		- 기업의 데이터를 저장 및 백업하는데 사용
			- 복구, 뛰어난 내구성 및 확장성을 제공
		- 데이터 아카이빙, 금융 및 의료의 규제수준에 준수하고 빠르게 아카이브된 데이터에 접속
		- 빅데이터 분석을 위한 [[Data Lake]] 기능제공
		- 제약, 재무, 멀티미디어 데이터 등 어떤 파일이라도 빅데이터 분석에 활용 가능하게 해줌
- Glacier : 데이터 아키이빙 및 장기 백업을 위해 안전하고 안정적인 서비스를 제공하는 클라우드 Storage
	- 아카이빙, 장기간 백업 및 오래된 로그데이터 관리에 용이하다.
	- 특징
		- 비용이 S3에 비해 매우 저렴하다.
		- S3의 Bucket과 유사한 Vault라는 개별 Storage 영역을 생성해 데이터를 보관한다.
		- Console로 업로드가 가능하다.
		- 별도의 API를 이용하여 데이터 저장기능을 제공한다.
- 예시 - 보통 데이터 백업 및 분석에 사용되므로 AWS S3와 Glacier를 같이 사용한다.
	- 기업에서 파일공유서버의 데이터를 클라우드로 확장할 때 많이 사용하는 아키텍처 구조이다.
	![[Pasted image 20231022173223.png]]
	- 데이터 백업을 위해 일반적으로 S3에 저장되어 있던 데이터를 Lifecycle 옵션을 이용하여 일정시간이 지나면 관련 데이터를 자동으로 Glacier로 이동시키는 기능옵션이 있다.
	- 관리콘솔을 통해 직접적으로 파일들을 업로드 시킬 수 있다.
### EFS(Elastic File System)
- 간단하고 확장 가능한 공유파일 Storage 솔루션이다.
	- 흔히 말하는 파일공유서버라고 생각하면 된다.
- 기업에서 On-Premise의 파일서버를 AWS 클라우드로 이전(Migration)할 때, 리눅스기반의 NFS 접근으로 제공하려고 할 때 가능한 서비스이다.
	- 한 곳에서 네트워크를 통해 수백개의 인스턴스에 접속 가능
	- 단, 네트워크 대역폭 및 트래픽 상황에 따라 느려질 수도 있다.
- 예시 - AWS의 Region영역에 2개의 EFS 서비스 존재
	- 리눅스의 전형적인 Storage 마운팅 구조이다.
	- EC2는 접근권한이 있으면 마운팅을 이용하여 해당 EFS에 데이터를 저장할 수 있다.
	![[Pasted image 20231022174648.png]]
### Storage Gateway
- Storage 측면에서 On-Premise의 데이터를 AWS Cloud로 연결하는 용도로 사용하는 서비스이다.
	- 즉, 다른 유형의 Storage 환경을 연결해준다.
- On-Premise의 Storage 환경과 AWS Cloud의 Storage 환경 사이의 구애를 벗어나 Hybrid Storage 환경을 구현할 수 있다.
- 예시 - 왼쪽은 기업의 로컬 데이터 센터, 오른쪽은 AWS 클라우드 Storage 환경이다.
	- 기업의 로켈 데이터 센터는 파일공유서버, 볼륨단위의 Storage, 외부 백업을 위해 Tape 유형의 LTO 시스템이 동작한다.
	![[Pasted image 20231022175032.png]]
	- Storage 유형에 상관없이 네트워크로 연결될 수 있는 환경이라면 On-Premise 상의 파일공유서버에서 S3를 마운팅하여 가져올 수 있다.
	- AWS의 데이터 백업을 위해 다른 사이트에 저장하려면 AWS EBS Snapshot 파일을 On-Premise 사이트의 Volume Storage에 저장할 수 있다.
### RDS(Relational Database Services) & DynamoDB
- RDS : 클라우드에서 [[관계형 데이터베이스(RDBMS)|관계형 데이터베이스]]를 더욱 간편하게 설정, 운영, 확장할 수 있도록 하는 서비스이다.
	- 하드웨어 프로비저닝, 데이터베이스 설정, 패치 및 백업같은 소모적인 관리 작업을 자동화한다.
	- auto scaling을 지원하지 않는다.
- DynamoDB : AWS의 NoSQL 서비스 ^61e1f6
	- Lambda와 함께 Serverless 서비스 중 하나이다.
		- 둘이 같이 이용하는 경우가 많다.
	- auto scaling이 가능
		- 데이터처리에 대한 유연성이 좋다.
- 특징
	- 인프라의 프로비저닝/DB설치 및 유지관리가 불필요함에 따라 관리가 용이하다.
	- 서비스 중단없이 서버 및 스토리지의 확장성을 보장
	- AWS의 멀치 가용영역 제공
		- 안정성 있는 인프라 제공 → 가용성 보장
	- SSD 지원 Storage 옵션 및 고성능 OLTP에 최적화된 옵션과 비용측면에서 효율적으로 선택 가능
	- DB와 네트워크에 대한 쉬운 접근 컨트롤이 가능해 보안관리에 유용
- 예시 - DynamoDB 활용
	![[Pasted image 20231022180824.png]]
	- Lambda 함수를 통해 API를 처리하고 이것을 쉰받아 AppSync가 DynamoDB에 저장하는 형식
		- 즉, Serverless 형태로 자동적으로 처리되는 구조
	- 일반적으로 AWS Cloud 기반으로 Native mobile app 개발 시 Amplify 서비스를 이용하여 쉽고 빠른 모바일 웹앱 구축이 가능하다.
		- Amplify : 프론트앤드 개발자들이 클라우드상에서 앱의 백앤드 환경을 생성하는데 유용한 서비스
			- Lambda, NoSQL, Storage, 백앤드의 인증, 저장, API 등의 서비스들과 연결해 처리 가능
	- AppSync : 실시간 데이터 동기화 및 오프라인 프로그래밍 기능이 포함된 엔터프라이즈급의 완전관리형 GraphQL 서비스
		- GraphQL API 생성이 가능하며 React App에 연결 가능하다.
		- 스키마를 쉽게 생성하여 DynamoDB의 workTable 데이터 저장 가능
### IAM(Identity & Access Management)
- AWS 리소스에 대한 접근을 안전하게 관리해주는 서비스이다.
- 아래으 유형으로 자격증명 관리 기능을 제공한다.
	- **암호** : AWS 관리콘솔, 보안페이지에 로그인하는데 사용된다.
	- **액세스 키** : AWS API, CLI, SDK, Windows PowerShell 등
	- **CloudFront 키 페어** : CloudFront가 서명된 URL을 생성하는데 사용된다.
	- **SSH Public Key** : AWS CodeCommit Repository를 인증하는 데 사용한다.
	- **X.509 인증서** : AWS 서비스에 안전한 SOAP Protocol 요청을 수행하는데 사용한다.
- 특징
	- 사용자의 AWS 서비스와 리소스에 대한 접근을 안전하게 통제하는 것이 가능하다.
	- AWS 사용자 및 그룹을 만들고 관리하며, 리소스에 대한 액세스 허용 및 거부가 가능하다.
	- AWS를 안전하게 사용학 위한 인증/허가 시스템이다.
	- AWS 사용자 인증 및 접근 정책관리를 한다.
	- AWS 관리를 위한 그룹, 사용자 및 Role 생성을 담당한다.
	- 그룹별 제한된 권한의 부여, 사용자별 인증 및 권한부여가 가능하다.
- IAM으로 제어할 수 있는 대상
	- AWS 리소스를 관리하기 위한 콘솔 접속권한
	- AWS 내부 리소스 접속권한
	- WAS 내 데이터에 대해 API로 접속하는데 필요한 권한
- IAM을 통해 EC2 및 S3의 접근통제
	- Root(시스템관리자)는 모든 권한을 가지고 있어 접근권한을 사용자 및 그룹에 부여할 수 있다.
	![[Pasted image 20231022181225.png]]
- 예시 - IAM 동작방식
	- AWS내의 리소스 및 자원관리를 위한 사용자와 그룹의 생성 및 관리기능을 통해 고유한 보안 자격증명을 생성할 수 있다.
	![[Pasted image 20231022181700.png]]
	- 관리자는 모든 권한을 가지므로 모든 리소스(오른쪽 부분) 통제가 가능하다.
	- 개발자는 EC2인스턴스에만 권한을 가지고 S3는 권한이 없다.
	- 사용자는 읽기만 가능하다.
### KMS(Key Management System)
- AWS 내 리소스 및 자원관리를 위한 사용자와 그룹의 생성 및 관리 기능을 토앻 고유한 보안자격증명을 생성할 수 있다.
	- 고객 마스터 키(CMK, Customer Master Key)를 쉽게 생성 및 제어가 가능한 관리형 서비스이다.
- S3에 저장되어 있는 데이터를 암호화하하는데 유용한 서비스이다.
- 키 관리 방식
	- AWS managed key
		- AWS 서비스들이 KMS를 통해 Key를 서비스 받는다.
		- 자동으로 발생되므로 사용자가 직접 통제할 수 없다.
	- Customer managed key
		- 사용자가 직접 Key를 생성하고 관리한다.
		- CMK는 Region에 기반하므로 다른 Region에서 사용하려면 복제를 허용해 주어야 한다.
		- 최대 4KB 데이터를 함호화 가능
			- 더 큰 데이터는 별도의 Data Key를 사용해야 한다.
			- KMS는 Data Key를 생성할 수 있지만 관리는 불가능하다.
	- Custom stores
		- 하드웨어 기반 암호솔루션
		- CloudHSM을 활용한 Key관리 형태
- KMS 기반의 Key를 이용해 데이터를 암호화하는 과정
	- CMK로부터 Plaintext기반의 데이터 키를 이요하여 암호화
	- S3등의 Storage 데이터를 암호화 후 인증 암호화키를 이용해 다시 복호화
	- 보안성 유지에 매우 유용한 서비스이다.
![[Pasted image 20231022182722.png]]
- 예시 - AWS 및 Azure Cloud를 이용한 도메인 기반 인프라 시스템 통합
	- AWS에서는 Directory Service 사용, Azure Cloud에서는 Azure Domain Directory Service 사용
	![[Pasted image 20231022182946.png]]
	- 서로 다른 클라우드의 네트워크에 연결하기 위해 전용 터널링 VPN 구축
		- AWS 도메인은 Gachon.com의 도메인 이름으로 Azure domain controller에 Trust되어 연결됨
		- 도메인이 Trust되어 연결된 것은 계정, 서버들의 리소스들을 서로 접속 및 공유할 수 있다는 의미
			- 서버뿐만 아니라 사용자 PC도 같은 Gachon.com이라는 도메인으로 Boundary된 상태이므로 Azure domain controller에서 중앙관리가 가능하다.
			- Azure 사이트의 Azure domain controller에서 사용자 PC에 AWS EC2 접근권한을 주면 문제없이 접근이 가능하다.