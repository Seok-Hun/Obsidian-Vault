# 정의
### 리스트 안에 있는 특정한 데이터를 찾기 위해<font color="#ff0000"> 앞에서부터 데이터를 하나씩 확인</font>하는 방법
- <font color="#ff0000">보통 정렬되지 않은 리스트</font>에서 데이터를 찾아야 할 때 사용
	- 정렬된 리스트는 [[이진 탐색 알고리즘(Binary Search Algorithm)|이진 탐색 알고리즘]]을 통해 더 빠른 탐색 가능
### 정렬 여부와 상관없이 가장 앞에 있는 원소부터 하나씩 확인
### 최악 시간 복잡도 : O(N)
- 데이터 개수가 N개일 때 최대 N번의 비교 연산 필요

---

# 단계
리스트에서 Banana 문자열을 찾는 과정을 예시로 단계 설명
### 0. 초기 단계
![[Pasted image 20231017145844.png]]
### 1-1.  순서대로 데이터 확인(첫번째 데이터 Apple 확인)
![[Pasted image 20231017145909.png]]
- Apple은 찾고자 하는 문자열과 다르므로 다음 데이터로 이동
### 1-2. 순서대로 데이터 확인(두번째 데이터 Orange 확인)
![[Pasted image 20231017150059.png]]
- Orange는 찾고자 하는 문자열과 다르므로 다음 데이터로 이동
### 2. 데이터 탐색 완료(세번째 데이터 Banana 확인)
![[Pasted image 20231017150453.png]]
- Banana는 찾고자 하는 문자열이므로 탐색 종료

