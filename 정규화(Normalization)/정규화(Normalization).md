# 용어 정리
### 정규화(Normalization)
- 함수적 종속성(FD : Functional Dependency) 등과 같은 이론에 근거해 관계형 데이터베이스 테이블의 삽입∙삭제∙갱신 이상(Anomaly) 현상발생을 최소화하기 위해 더 작은 단위의 테이블로 설계하는 과정.
- 데이터 모델을 정규형에 맞도록 고치는 과정
### 정규형(NF: Normal Form)
- 정규화 규정
- 정규화 결과에 의해 도출된 데이터 모델이 갖춰야 할 특성
### 함수적 종속성(FD : Functional Dependency)
- table의 특정 column A 값을 알면 다른 column B 값을 알 수 있을 때, column B는  column A에 함수적 종속성이 있다고 한다.
	- 예) 고객명은 고객주민등록번호에 함수적 종속성이 있다.
### 결정자(Determinant)
- 위의 함수적 종속성 설명에서 column A를 결정자라고 한다.
### 다치종속(MVD: MultiValued Dependency)
- 결정자 column A에 의해 column B의 값을 여러 개 알 수 있을 때, column B는 column A에 다치종속되었다고 한다.
	- 예) 학번을 알면 학생의 수강과목들을 알 수 있을 때, 수강과목은 학번에 다치종속관계이다.

---

# 정규화를 통한 성능 향상 전략
### 정규화 수행 : <font color="#ff0000">데이터를 결정하는 결정자</font>에 의해 <font color="#ff0000">함수적 종속을 가지는 일반속성을 의존자</font>로 하여 <font color="#ff0000">입력/수정/삭제 이상현상을 제거</font>하는 것
### 데이터의 중복[[Attribute|속성]] 제거 + 결정자에 의해 동일한 의미의 일반속성이 하나의 테이블로 집약
**<font size=5>→ 테이블의 데이터 용량 최소화 가능</font>** 
### 일반적으로 정규화된 테이블은 <font color="#ff0000">데이터처리 성능이 향상</font>되며, <font color="#ff0000">데이터 조회 트랜잭션시에는 성능이 향상될수도 있고 저하</font>될 수도 있다.
![[Pasted image 20231013134211.png]]

---

# 정규화 이론

### <font color="#00b0f0">1차 정규화</font>
- 함수종속
- <font color="#ff0000">복수의 속성값을 갖는 속성을 분리</font>
- 속성의 원자성 확보
### <font color="#00b0f0">2차 정규화</font>
- 함수종속
- <font color="#ff0000">주식별자에 완전종속적이지 않은 속성 분리</font>자
- 부분종속 속성(Partial Dependency Attribute) 분리
### <font color="#00b0f0">3차 정규화</font>
- 함수종속
- <font color="#ff0000">일반속성에 종속적인 속성 분리</font>
- 이전종속 속성(Transitive Dependency) 분리
### <font color="#00b0f0">보이스-코드(BCNF) 정규화</font>
- 함수종속
- <font color="#ff0000">결정자 안에 함수종속을 가진 주식별자를 분리</font>
### <font color="#00b0f0">4차 정규화</font>
- <font color="#ff0000">다치종속(Multi-Valued Dependency) 속성분리</font>
### <font color="#00b0f0">5차 정규화</font>
- <font color="#ff0000">결합종속(Join Dependency)일 경우, n개로 분리(2개 이상)</font>

>[!정규화 수행]
>- 1차, 2차, 3차, 보이스-코드 정규화는 <font color="#ff0000">함수종속성에 근거</font>하여 정규화 수행
>- 4차 정규화는 속성의 값이 다수 발생하는 <font color="#ff0000">다치종속 제거</font>로 정규화 수행
>- 5차 정규화는 조인에 의해 발생하는 <font color="#ff0000">이상현상 제거</font>로 정규화 수행

---

# 정규형(NF : Normal Form)
### <font color="#00b0f0">1st NF</font>
- <font color="#ff0000">모든 column은 원자 값을 가져야 한다.</font>
	- 즉, 다중 값을 가질 수 있는 column은 분리되어야 한다.
- 예시
	 ![[Pasted image 20231013142027.png]]
	- 주문상품코드, 주문상품명, 주문상품가격, 주문상품수량은 <font color="#ff0000">Business Definition에 의해 하나의 주문에 대해 다수 값을 가질 수 있으므로 분리한다.</font>
	- 정규화에 의해 분리 설계된 [[Entity]](예:주문상품)는 <font color="#ff0000">원본 Entity의 식별자를 상속하여 해당 Entity의 식별자로 정의하는 것이 일반적이다.</font>
	- 분리된 속성들 중에서 [[Identifiers|식별자]] 특성을 갖는 것은 식별자(의 일부)로 지정하고, 그렇지 않으면 대체 식별자(Surrogate identifier)를 추가로 설계한다.
### <font color="#00b0f0">2nd NF</font>
- <font color="#ff0000">1st NF를 만족하고, 모든 Non-key column은 기본 키 전체에 종속되어야 한다.</font>
	- 즉, 기본 키에 종속적이지 않거나 기본 키 일부 column(s)에만 종속적인 column은 분리되어야 한다.
- 예시
	 ![[Pasted image 20231013142248.png]]
	 - 결정자(예:주문상품코드) 및 종속된 속성(주문상품명, 주문상품가격)을 분리하여 별도 Entity(예:상품)를 설계한다.
	 - 일반적으로 결정자를 식별자로 지정한다.
### <font color="#00b0f0">3rd NF</font>
- <font color="#ff0000">2nd NF를 만족하고, Non-key column들 간에도 종속관계가 존재하지 않아야 한다.</font>
	- 즉, Non-key column들 간 종속관계가 존재하는 것들은 분리되어야 한다.
- 예시
	![[Pasted image 20231013142625.png]]
	- 
- 결정자(예:주문고객번호) 및 종속된 속성(주문고객병, 주문고객휴대폰번호)을 분리하여 별도 Entity(예:고객)를 설계한다.
- 일반적으로 결정자를 식별자로 지정한다.

---

# [[반정규화(denormalization)|반정규화]]
### 정규화된 데이터베이스의 <font color="#ff0000">성능 개선, 개발 및 운영의 편의성</font> 등을 위해 <font color="#ff0000">정규화된 데이터를 통합, 중복, 분리</font>하는 과정
### <font color="#ff0000">의도적으로 정규화 원칙을 위배하는 행위</font>










