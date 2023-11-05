# 정의
### [[데이터베이스 관리 시스템(DBMS)]] 또는 유사한 시스템에서 데이터베이스의 상태를 변화시키기 위해 수행하는 작업의 논리적 단위
### 어떤 시스템들에서는 논리적 작업 단위(LUW, Logical Units of Work)라고 불림
### transaction은 상황에 따라 여러 개가 만들어 질 수 있고, 각각의 트랜잭션들은 상황에 따라 <font color="#00b0f0">Commit(저장)</font> 되거나 <font color="#00b0f0">Rollback(철회)</font> 될 수 있다.
- ##### Commit : 모든 부분작업이 정상적으로 완료하면 이 변경사항을 한꺼번에 DB에 반영한다.
- ##### Rollback : 부분 작업이 실패하면 transaction 실행 전으로 되돌린다.

---

# 목적
### 안전성 확보

---

# 특징(ACID)

^9fdbe2

- ### <font size="5" color="#00b0f0">Atomicity(원자성)</font>
	-  <font size="4" color="#fbd5b5">정의</font> : **transaction의 연산은 모든 연산이 완벽히 수행되어야 하며, 한 연산이라도 오류가 발생하면 트랜잭션 전부가 취소되어야 한다.**
		- <font color="#ff0000">All or Nothing</font>의 개념으로 작업 단위 일부분만 실행하지는 않는 것을 의미
		- 변경 사항은 commit하여 저장하고, 오류 발생 시 rollback하여 오류 이전 상태로 되돌림
		- [[rollback segment]]에 수정되기 전 파일, 블록 ID같은 정보 및 데이터 저장
		- save point를 지정하여 rollback하는 시점을 지정할 수 있다.
			- 일반적으로 rollback을 명시하면 작업 전체(INSERT, DELETE, UPDATE 등)가 취소
			- save point로 전체가 아닌 특정 부분에서 트랜잭션 취소 가능
- ### <font size=5 color="#00b0f0">Consistency(일관성)</font>
	-  <font size="4" color="#fbd5b5">정의</font> : **transaction이 실행을 성공적으로 완료하면 언제나 일관성 있는 데이터베이스 상태로 유지한다.**
		- 고정요소는 트랜잭션 수행 전과 완료 후의 상태가 같아야 한다.
		- 일관성 보장은 이벤트와 조건이 발생 시, [[Trigger]]를 통해 보장한다.
			- 예) 한쪽 데이터베이스의 테이블에 수정이 발생하면 다른 쪽 테이블에도 함께 정보가 수정될 수 있도록 명시적으로 자동 업데이트를 하는 명령 등을 구성
- ### <font size=5 color="#00b0f0">Isolation(고립성)</font>
	-  <font size="4" color="#fbd5b5">정의</font> : **둘 이상의 transaction 수행 시 다른 transaction의 연산 작업이 끼어들 수 없다. = 수행중인 transaction이 완전히 완료될 때까지 다른 transaction에서 수행 결과를 참조할 수 없다.**
		- 고립성 보장을 위해 [[Lock&Unlock]] 기법 사용
		- 잘못하면 [[deadlock]] 상태에 빠질 수 있음
- ### <font size=5 color="#00b0f0">Durability(지속성, 내구성)</font>
	-  <font size="4" color="#fbd5b5">정의</font> : **성공적으로 수행된 트랜잭션은 영원히 반영되어야 한다. = 비위발성 메모리에 데이터 저장**
		- commit 하면 현재 상태는 영원히 보장된다는 것을 의미