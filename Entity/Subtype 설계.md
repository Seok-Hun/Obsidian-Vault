# Entity 설계 : Subtype - Supertype
### 기본적으로 Subtype과 Supertype는 일반 Entity와 동일하다.
### Subtype
- Entity를 상세화(Specialization)하면 생기는 Supertype 과 쌍을 이루는 Entity
- 각각의 Subtype에는 해당 Subtype에서만 사용되는 고유 속성 존재
### Supertype
- Entity를 일반화(Generalization)하면 생기는 모든 사브타입으로 상속되는 공통 Entity
### 예시
![[Pasted image 20231012221948.png|500]]
- Supertype : 고객 Entity
- Subtype : 개인고객 Entity, 법인고객 Entity