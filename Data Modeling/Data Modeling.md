# Modeling
### <font color="#e36c09">정의</font>

![[Pasted image 20231012201758.png]]
##### 가설적 또는 일정 양식에 맞춘 표현
##### 사건에 대한 양상(Aspect)이나 관점(Perspective)을 연관된 사람이나 그룹을 위해 명확하게 하는 것
##### <font color="#00b0f0">Model</font> : <font color="#ff0000">현실 세계의 추상화</font>된 반영

### <font color="#e36c09">특징</font>

- ##### 추상화(모형화, 가설적) : 현실세계를 <font size=4 color="#ff0000">일정한 형식에 맞추어 표현</font>
- ##### 단순화 : 복잡한 현실세계를 약속된 규약에 의해 제한된 표기법이나 언어로 표현하여 <font size=4 color="#ff0000">쉽게 이해할 수 있도록 하는 개념</font>
- ##### 명확화 : 누구나 이해하기 쉽게 하기 위해 대상에 대한 <font size=4 color="#ff0000">애매모호함을 제거</font>하고 <font size=4 color="#ff0000">정확하게 현상을 기술</font>

### <font color="#e36c09">관점</font>

![[Pasted image 20231012203011.png]]

- ##### 데이터 관점 : 업무가 어떤 데이터와 관련이 있는지 또는 데이터간의 관계는 무엇인지에 대해 모델링하는 방법
	- <font color="#00b0f0">What, Data</font>
- ##### 프로세스 관점 : 업무가 실제하고 있는 일은 무엇인지 또는 무엇을 해야 하는지를 모델링하는 방법
	- <font color="#00b0f0">How, Process</font>
- ##### 데이터와 프로세스의 상관관점 : 업무가 처리하는 일의 방법에 따라 데이터는 어떻게 영향을 받고 있는지 모델링하는 방법
	- <font color="#00b0f0">Interaction</font>

---

# 정의
### 정보시스템 구축을 위해, 해당 업무에 어떤 데이터가 존재하는지 또는 업무가 필요로 하는 정보는 무엇인지 분석하는 방법
### 현실세계의 데이터(What)에 대해 약속된 표기법에 의해 표현하는 과정
### [[DataBase(DB)|데이터베이스]]를 구축하기 위한 분석/설계의 과정

---

# 특징
### 시스템을 현재 또는 원하는 모습으로 <font color="#ff0000">가시화</font>하도록 도와줌
### 시스템의 구조와 행동을 <font color="#ff0000">명세화 </font>할 수 있게 함
### 시스템을 구축하는 <font color="#ff0000">구조화된 틀을 제공</font>
### 시스템을 구축하는 과정에서 결정한 것을 <font color="#ff0000">문서화</font>
### <font color="#ff0000">추상화</font> : 다양한 영역에 집중하기 위해 다른 영역의 세부 사항은 숨김
### 특정 목표에 따라 구체화된 상세 수준의 <font color="#ff0000">표현방법 제공</font>

---

# 중요성

|<center>중요성</center>|<center>설명</center>|
|----|----|
|파급효과(Leverage)|<font color="#ff0000">프로젝트 초기에 하는 Task 중 가장 중요한 작업</font>.<br/>프로젝트 후반부에 데이터모델 변경 시 변경으로 인한 비용손실 및 납기지연가능성 커짐|
|복잡한 정보 요구사항의 간결한 표현(Conciseness)|정보 요구사항과 한계를 가장 명확하고 간결하게 표현할 수 있는 도구. 건축물에 비교하면 설계도면에 해당.|
|데이터 품질(Data Quality)|데이터모델은 데이터 품질의 값, 구조, 프로세스 중 구조에 대한 품질에 핵심적인 영향도를 가짐.<br/>중복(Duplication), 비유연성(Inflexibility), 비일관성(Inconsistency) 문제 해결에 가장 중요한 도구|

---
# 데이터 모델의 구성요소
### [[Entity|Entity(개체)]]
### [[Attribute|Attribute(속성)]]
### [[Relationship|Relationship(관계)]]
### [[Identifiers|Identifiers(식별자)]]

---

# 데이터 모델링의 3단계

![[Pasted image 20231012205542.png]]
### project life cycle에서 data modeling
- **계획 또는 분석 단계**에서 <font color="#00b0f0">개념적 데이터 모델링</font>
	- 단, 현실 프로젝트에서는 개념적 데이터 모델이 생략된 개념/논리 데이터 모델링이 분석단계에서 수행
- **분석단계**에서 <font color="#00b0f0">논리적 데이터 모델링</font>
- **설계단계**에서 <font color="#00b0f0">물리적 데이터 모델링</font>

### [[개념적 데이터 모델링]]
### [[논리적 데이터 모델링]]
### [[물리적 데이터 모델링]]
---
# 절차

### 1. 요구사항 수집 및 분석
- 구축해야 할 정보시스템에 대한 요구사항 중 지속적으로 관리할 필요가 있는 데이터에 대한 요구사항을 수집하고 분석
- 현행(As-ls) 정보시스템의 데이터 구조를 분석하여 문제점 및 개선방향 도출 실시
### 2. 데이터 주제영역(Subject Area) 정의
- 데이터 모델링의 대상이 되는 전체 데이터 영역에 대해 데이터의 주제영역을 식별하여 정의
- <font color="#00b0f0">High Cohesion & Loose Coupling(고응집도&저결합도)</font> 관점에서 주제영역 세분화
### 3. <font color="#ff0000">개념 데이터 모델링</font>
- 각 데이터 주제영역별로 핵심 Entity 및 Identifier를 도출
- 핵심 Entity 간 주요 Relationship 도출
### 4. <font color="#ff0000">논리 데이터 모델링</font>
- 주제영역별 핵심 Entity의 모든 업무적 Attribute들 및 Relationship 도출
- 주제영역별 세부적인 데이터 모델 완성
### 5. <font color="#ff0000">물리 데이터 모델링</font>
- 논리 데이터 모델링 결과를 구현할 데이터베이스 종류(관계형, 객체지향형, 객체관계형 등)에 맞게 변환
	- 예) 구현할 데이터베이스가 관계형일 경우 Entity를 Table로, Attribute 및 Relationship을 Column으로 변환
### 6. 물리 설계
- 물리 데이터 모델링 결과를 구현할 데이터베이스 제품(Oracle, SQL-Server, Sybase 등)에 맞게 변환
- 성능적 측면, 개발생산성 측면 등을 종합 검토해 실시

---

# 표기법

##### IE 시스템 위주로 살펴봄

##### 데이터 모델링 표기법
![[Pasted image 20231012224144.png]]

##### Entity 표기법
- Entity
![[Pasted image 20231012224323.png]]
- Supertype/Subtype
![[Pasted image 20231012224424.png]]

---
# ERD(Entity Relationship Diagram)

### 정의
##### <font color="#ff0000">각 업무분석에서 도출된 Entity와 Entity간의 관계를 이해하기 쉽게 도식화된 다이어그램으로 표시하는 방법</font>
### 작업순서

![[Pasted image 20231012225530.png]]
##### [[ERD 작업순서]]

---

# 데이터 모델 평가 요소

|<center>중요성</center>|<center>설명</center>|
|----|----|
|완전성(Completeness)|업무에서 필요로 하는 모든 데이터가 데이터 모델에 정의됨|
|중복배제(Non-Redundancy)|하나의 데이터베이스 내에 동일한 사실은 반드시 한 번만 기록|
|업무규칙(Business Rules)|업무규칙(Business Rules)을 데이터 모델에 표현하고 이를 해당 데이터 모델을 활용하는 모든 사용자가 공유|
|데이터 재사용(Data Reusability)|데이터의 통합성과 독립성에 대해 충분히 고려|
|의사소통(Communication)|정보 시스템을 운용, 관리하는 관계자들이 설계자가 정의한 업무 규칙들을 동일한 의미로 받아들이고 정보시스템을 활용할 수 있게 하는 역할|
|통합성(Integration)|데이터가 조직의 전체에서 한번만 정의되고 이를 여러 다른 영역에서 참조, 활용|

---

# 성능 데이터 모델링
### 정의
##### <font color="#ff0000">데이터베이스 성능향상을 목적</font>으로 설계단계부터 성능과 관련된 사항이 데이터 모델링에 반영될 수 있도록 하는 것
### 데이터 모델의 좋은 성능을 위해서는 데이터 모델링부터 <font color="#00b0f0">정규화, 반정규화, 테이블통합/분할, 조인구조, PK순서 등</font> 여러 성능과 관련된 사항을 고려해야 함
### 수행시점
- 성능 데이터 모델링은 <font color="#ff0000">사전에 할수록 비용이 적게 든다.</font>
- 분석/설계 단계에서의 성능 데이터 모델링은 성능저하에 다른 재업무(Rework) 비용 최소화 기회를 가짐
### 고려사항
- [[정규화(Normalization)|정규화]]를 정확하게 수행
- 데이터베이스 용량산정 수행
- 데이터베이스에 발생되는 [[Database Transaction|트랜잭션]]의 유형 파악
- 용량과 트랜잭션의 유형에 따라 반정규화 수행
- 이력모델의 조정, PK/FK조정, 쓔퍼타입/서브타입 조정 등 수행
- 성능관점에서 데이터 모델 검증
