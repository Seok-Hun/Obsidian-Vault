# 정의
### 사전적 의미 : <font color="#ff0000">사물의 성질, 특징 또는 본질적인 성질</font>
### 업무에서 필요로 하여 인스턴스로 관리하고자 하는 의미상 더 이상 분리되지 않는 최소의 데이터 단위

### table에서 행(Column)에 해당한다.

---

# 특징
### Entity와 마찬가지로 해당 업무에서 필요하고 <font color="#ff0000">관리하고자 하는 정보</font>이다.
### 정규화 이론에 근간하여 정해진 주식별자에 <font color="#ff0000">함수적 종속성</font>을 가져야 한다.
### <font color="#ff0000">하나의 속성에는 한 개의 값</font>만을 가진다.
- 하나의 속성에 여러 값이 있는 다중값일 경우 별도의 Entity를 이용해 분리

---

# 분류
### 특성에 따른 분류
- ### <font size=5 color="#ff0000">기본속성(Basic Attribute)</font> : 업무분석을 통해 바로 정의한 속성
- ### <font size=5 color="#ff0000">설계속성(Designed Attribute)</font> : 업무상 존재하지 않지만 설계하며 도출해내는 속성
- ### <font size=5 color="#ff0000">파생속성(Derived Attribute)</font> : 다른 속성으로부터 계산이나 변형이 되어 생성되는 속성
### Entity 구성방식에 따른 분류
- ### <font size=5 color="#ff0000">PK(Primary Key) 속성</font> : Entity 식별 가능한 속성
- ### <font size=5 color="#ff0000">FK(Foreign Key) 속성</font> : 다른 Entity와의 관계에서 포함된 속성
- ### <font size=5 color="#ff0000">일반속성</font> : Entity에 포함되고 PK, FK에 포함되지 않은 속성