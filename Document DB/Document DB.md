# 정의
### [[NoSQL]]의 유형 중 하나로 Value - Key 모델의 진화 형태
### 집합 구조를 문서 형태로 확인 가능하다
### column이 없음(스키마 없음)
### JSON, XML 같은 Collection 데이터 모델 구조 채택
### 개념도
![[Pasted image 20231015013821.png]]

--- 
# 구조
### 데이터는 key와 document(문서)의 형태로 저장
- **document 내의 필드를 정의함(key-value)
### key-value 모델과의 차이점
- value가 계층적인 형태인 document 형태로 저장됨
- 객체 지향에서의 객체와 유사하며 하나의 단위로 취급되어 저장된다.
- 하나의 객체를 여러 테이블에 나누어 저장할 필요가 없다
- document 내의 item을 이용한 query 가능
	- Xquery나 다른 document 질의 언어가 필요하다.

---

# 특징
### 객체를 document의 형태로 바로 저장 가능하기 때문에 객체-관계 매핑이 불필요함
- 조인 기능 불필요
### 검색 최적화
- key-value 모델의 특징과 동일하다
- 여러 table을 하나의 document에 모아둘 수 있다.
- 한 번의 조회로 필요한 데이터 획득이 가능하다
	- 이를 통해 조인 기능을 대체한다.
### document 모델의 질의 결과 - JSON이나 XML 형태로 출력

---

# 단점
### 사용이 번거롭고 query가 SQL과 달라 익숙해지는데 시간이 필요하다.

---

# 주요 DB
### MongoDB
### Couchbase
### [[AWS(Amazon Web Service)#^61e1f6|Amazone DynamoDB]]