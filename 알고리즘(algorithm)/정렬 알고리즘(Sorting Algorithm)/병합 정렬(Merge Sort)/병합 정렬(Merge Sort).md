# 개요
### 분할 정복(Devide and Conquer) 기법과 재귀 알고리즘을 이요한 정렬 알고리즘
즉, 주어진 배열을 원소가 하나밖에 남지 않을 때까지 둘로 쪼갠 후 다시 크기 순으로 재배열 하면서 원래 크기의 배열로 합친다.
### 공간 복잡도 : O(N)
### 시간 복잡도 : O(N<sub>log</sub>N)
---
# 특징
### 알고리즘을 크게 분할(split) 단계와 병합(merge) 단계로 나눌 수 있다.
단순히 중간 인덱스를 찾아야 하는 분할 비용보다 모든 값들을 비교해야 하는 병학 비용이 더 크다.
### 다른 정렬 알고리즘과 달리 인접한 값들간의 상호 자리 교대(swap)가 일어나지 않는다.
---
# 복잡도 분석
### 공간 복잡도 : O(N)
두개의 배열을 병합할 때 병합 결과를 담아 놓을 배열이 추가로 필요하다.
### 시간 복잡도 : O(N<sub>log</sub>N)
전반적인 반복의 수는 절반씩 줄어들어 O(<sub>log</sub>N) 시간이 필요하다.
각 단계에서 병합할 때 모든 값들을 비교해야 하므로 O(N)시간이 소모된다.
총 시간 복잡도는 O(N<sub>log</sub>N) 이다.

---
# 예시
### 예시 데이터
<center><font size=6>6 5 3 1 8 7 2 4</font></center>

### 분할(split) 단계
<center><font size=6>{ 6 5 3 1 8 7 2 4 }</font></center>
<center><font size=6>{ 6 5 3 1 } { 8 7 2 4 }</font></center>
<center><font size=6>{ 6 5 } { 3 1 } { 8 7 } { 2 4 }</font></center>
<center><font size=6>{6} {5} {3} {1} {8} {7} {2} {4}</font></center>

### 병합(merge) 단계
작은 숫자가 앞에 위치하고 큰 숫자를 뒤에 위치한다.
<center><font size=6>{ 5 6 } { 1 3 } { 7 8 } { 2 4 }</font></center>
<center><font size=6>{ 1 3 5 6 } { 2 4 7 8 }</font></center>
<center><font size=6>{ 1 2 3 4 5 6 7 8 }</font></center>

---
# 파이썬 예제
- 입력 : \[6, 5 3, 1, 8, 7, 2, 4]

```python
array = [6,5,3,1,8,7,2,4]

def merge(left, right):
	result = []
	while len(left) > 0 and len(right) > 0: # 왼쪽 & 오른쪽 배열이 모두 존재한다면,
		if left[0] <= right[0]:             # 왼쪽이 더 작으면 왼쪽을 추가,
			result.append(left[0])
			left=left[1:]
		else:                               # 아니라면 오른쪽 추가
		result.append(right[0])
		right=right[1:]
	if len(left) > 0:
		result += left
	if len(right) > 0:
		result +=right
	# result.extend([*left, *right])
	return result

def mergeSort(data):
	if len(data) <= 1:                 # 배열의 길이가 1보다 작거나 같으면(=원소의 개수가 1이면),
		return data
	mid = len(data)//2                 # 배열을 1/2로 나누기 위해 배열의 중간 인덱스를 구한다.
	left = mergeSort(data[:mid])       # 왼쪽 배열을 병합하기 위해 호출
	right = mergeSort(data[mid:])      # 오른쪽 배열을 병합하기 위해 호출
	result = merge(left, right)       # 왼쪽 배열과 오른쪽 배열을 합칠 임시 배열 result를 선언한다.
	return result

print(mergeSort(array))
```
- 출력 : \[1,2,3,4,5,6,7,8]
