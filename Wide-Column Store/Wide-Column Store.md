# 정의
### NoSQL 데이터베이스의 유형 중 하나이다.
### table, row, column을 사용하지만 RDB와 달리 column의 이름과 포맷은 동일한 table의 row마다 다를 수 있다.
- Column-Family는 RDB의 table과 같은 의미이다.
### 2차원 [[Key-Value(KV) DB|Key-Value Store]]로 해석 가능하다.
### 개념도
![[Pasted image 20231014232011.png]]

---

# 구조
### Row Key
- Row 식별자
	- 검색 시 사용되는 기본 키
- Row Key 순으로 자동 정렬된다.
### Column
- key-value 쌍이다.
- 하나의 row에 수백만~수억 개의 column이 허용된다.
- 항상 timestamp 값이 함께 저장된다.
- Column Family : Column의 값이 다시 여러 Column의 Map으로 구성된 것

---

# 특징
- Google의 BigTable Paper에서 유래되었다.
- Key-Value에서 발전된 형태의 Column Family 데이터 모델 사용
- table join을 사용하지 않음
	- 포함된 방대한 양의 데이터 확장 및 성능 향상
- 일반적인 데이터베이스의 형태이다.(=수십억의 행과 수백의 열로 구성된 데이터베이스)

---

# 주요 DB
### HBase
### Cassandra
### ScyllaDB