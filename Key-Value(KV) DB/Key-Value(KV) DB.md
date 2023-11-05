# 정의
### NoSQL의 DB 유형 중 하나로 가장 단순한 형태이다.
### [[연관 배열(Associative Array)|연관 배열]]의 저장, 검색, 관리를 위해 설계된 Data Storage Paradigm
- Dictionary에 객체나 튜플(레코드)의 모음(Collection)이 포함됨
- 각기 다른 수많은 필드(속성)가 포함되고 각각이 데이터를 담는 구조
### 개념도
![[Pasted image 20231015013719.png]]

---

# 구조
### Key
- 값을 가져오기 위한 식별자
- name space 내에서 고유해야 한다.
	- name space : key-value collection database
- key 값 처리를 위해 hash 함수 사용
### Value(값)
- 값의 데이터 타입에 큰 제약 없음
	- 암묵적 제약만 고려

---

# Query 형태
### 고유한 key에 하나의 value 쌍으로 데이터가 저장
### key는 value에 접근하기 위한 용도로 사용
### value는 어떤 형태의 데이터라도 저장 가능(이미지, 비디오 등)
### key 기반의 간단한 get, put, delete 등 기능 제공
- 빠른 처리 가능
- 예시) value := get(key) 형태의 API로 접근

---

# 특징
### 단순성
- 고유의 key를 통해 값을 획득하는 단순한 구조
- value에 대한 타입 제한이 없어 원하는 형태의 데이터 입력 가능
- value의 일부 검색 또는 Join 등의 복잡한 연산은 불가능
### 속도
- 빠른 처리 속도
	- 메모리 내에서 데이터를 관리하는 방식 사용(In Memory, Cache)
### 확장성
- [[분산 데이터베이스(distributed database)|분산 데이터베이스]]로 수평적 확장 용이

---

# 단점
### value의 내용을 통한 query 불가능
- key를 사용해 value를 읽어 들인 뒤 애플리케이션 레벨에서 적절히 처리해야 한다.
### 범위에 대한 질의를 지원하지 않는다.
### 간단한 조회를 위한 query 언어로 구성되어 있다.
- SQL처럼 활용도가 높은 질의 언어가 없다

---

# 주요 DB
### Amazon DynamoDB
### Redis
### Memcached
### Riak