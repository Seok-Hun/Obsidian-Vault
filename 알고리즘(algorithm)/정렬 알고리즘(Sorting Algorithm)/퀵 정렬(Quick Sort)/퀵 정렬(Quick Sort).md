# 개요
### 기준 데이터를 설정하고 그 기준보다 큰 데이터와 작은 데이터의 위치를 바꾸는 방법이다.
### 일반적인 상황에서 가장 많이 사용되는 정렬 알고리즘 중 하나
### [[병합 정렬(Merge Sort)|병합 정렬]]과 마찬가지로 분할 정복(Devide and Conquer) 기법과 재귀 알고리즘을 이용한 정렬 알고리즘이다.
### 병합 정렬과 더불어 대부분의 프로그래밍 언어의 정렬 라이브러리의 근간이 되는 알고리즘이다.
### Pivot : 퀵 정렬에서 큰 숫자와 작은 숫자를 교환하기 위해 사용되는 기준
### 공간 복잡도
### 시간 복잡도
---
# 특징
### 파이썬의 list.sort() 함수나 [[자바(Java)|자바]]의 Arrays.sort() 처럼 프로그래밍 언어 차원에서 기본적으로 지원되는 내장 정렬 함수는 대부분 퀵 정렬을 기본으로 한다.
### 일반적으로 원소의 개수가 적어질수록 나쁜 중간 값이 선택될 확률이 높아지기 때문에, 원소의 개수에 따라 퀵 정렬을 다른 정렬과 혼합하여 사용하는 경우가 많다.
### 병합 정렬과 퀵 정렬은 유사해 보이지만 내부적으로 정렬하는 방식에는 큰 차이가 있다.
- 병합 정렬 : 정 중앙을 기준으로 단순 분할 후 병합 시점에서 값의 비교 연산 발생
- 퀵 정렬 : 분할 시점부터 비교 연산이 발생하기 때문에 이후 병합에 들어가는 비용이 매우 적다
	- 구현 방법에 따라 아예 병합을 하지 않을 수도 있다.
---
# 복잡도 분석

### 시간 복잡도(이상적) : O(N<sub>log</sub>N)
- 이상적인 경우 : pivot 값을 기준으로 동일한 개수의 작은 값들과 큰 값들로 분할
- 퀵 정렬의 성능은 pivot 값을 어떻게 설정하느냐에 따라 달라질 수 있다.
### 시간 복잡도(최악) : O(N<sup>2</sup>)
- 최악인 경우 : pivot 값을 기준으로 한 편으로 모든 값들이 값들이 치우치게 분할
- 이러한 이유로 사용 코드에서는 중앙값(median)에 가까운 pivot 값을 선택할 수 있는 섬세한 전략이 요구된다.
	- pivot 값으로 배열의 첫 값, 중앙값, 마지막 값 중 크기가 중간이 값을 사용하는 방법이 많이 사용된다.
### 공간 복잡도 : O(N<sub>log</sub>N)
- 구현 방법에 따라 달라질 수 있다.
- 입력 배열이 차지하는 메모리만을 사용하는 in-place sorting 방식으로 구현할 경우 O(N<sub>log</sub>N)의 공간 복잡도를 가진 코드 구현이 가능하다.
---
# 수행 과정
1. 리스트에서 첫번째 데이터를 pivot으로 정한다.
2. 왼쪽에서부터 pivot보다 큰 데이터를 찾고, 오른쪽에서부터 pivot보다 작은 데이터를 찾는다.
3. 큰 데이터와 작은 데이터의 위치를 서로 교환한다.
4. 위의 과정을 반복하면 pivot에 대해 정렬이 수행된다.
---
# 예시 
### 예시 데이터
<center><font size=6>5 7 9 0 3 1 6 2 4 8</font></center>

### 분할 단계
<font color="#00b0f0">파란색</font>은 pivot
<font color="#7f7f7f">회색</font>은 선택된 데이터
- pivot 값을 설정한다. 여기선 첫번째 데이터인 '5'를 pivot으로 설정하였다.
- 왼족에서부터 pivot보다 큰 데이터를 선택하므로 '7'이 선택되고, 오른쪽에서부터 pivot보다 작은 데이터를 선택하므로 '4'가 선택되었다.
- 선택된 두 데이터의 위치를 교환한다.
<center><font size=6><font color="#00b0f0">5</font> <font color="#7f7f7f">7</font> 9 0 3 1 6 2 <font color="#7f7f7f">4</font> 8</font></center>

- 왼쪽에서부터 pivot보다 큰 데이터인 '9'가 선택되고, 오른쪽에서부터 pivot보다 작은 데이터인 '2'가 선택되었다.
- 선택한 두 데이터의 위치를 교환한다.
<center><font size=6><font color="#00b0f0">5</font> 4 <font color="#7f7f7f">9</font> 0 3 1 6 <font color="#7f7f7f">2</font> 7 8</font></center>

- 왼쪽에서부터 pivot보다 큰 데이터인 '6'이 선택되고, 오른쪽에서부터 pivot보다 작은 데이터인 '1'이 선택되었다.
- 단, <font color="#ff0000">이처럼 위치가 엇갈리는 경우에는 pivot과 작은 데이터의 위치를 서로 교환한다.</font>
<center><font size=6><font color="#00b0f0">5</font> 7 9 0 3 <font color="#7f7f7f">1 6</font> 2 4 8</font></center>

### 분할 완료
- 이제 pivot의 왼쪽에 있는 데이터는 모두 pivot보다 작고, 오른쪽에 있는 데이터는 모두 pivot보다 크다.
- 이렇게 pivot을 기준으로 데이터 묶음을 나누는 작업을 <font color="#ff0000">분할(Divide)</font>라고 한다.
<center><font size=6>1 4 2 0 3 <font color="#00b0f0">5</font> 6 9 7 8</font></center>

- 이제 기존의 pivot을 기준으로 왼쪽의 데이터 묶음과 오른쪽의 데이터 묶음을 각각 정렬한다.
### 왼쪽 데이터 묶음 정렬
- 새로운 pivot 값을 설정하여 정렬을 수행한다. 여기서는 첫번째 데이터인 '1'을 pivot으로 설정하였다.
<center><font size=6><font color="#00b0f0">1</font> 4 2 0 3 _ _ _ _ _</font></center>

### 오른쪽 데이터 묶음 정렬
- 새로운 pivot 값을 설정하여 정렬을 수행한다. 여기서는 첫번째 데이터인 '6'을 pivot으로 설정하였다.
<center><font size=6>_ _ _ _ _ _ <font color="#00b0f0">6</font> 9 7 8</font></center>

### 각각의 데이터 묶음에 남는 데이터가 pivot밖에 없을 때까지 반복한다.
---
# 파이썬 예제
### 예제 1

```python
array = [5,7,9,0,3,1,6,2,4,8]

def quickSort(data, start, end)
	if start >=end:    # 원소가 1개인 경우 종료
		return
	pivot = start      # pivot은 첫번째 원소
	left = start+1
	reight = end

	while left <= right:
		while left <= end and data[left] <= data[pivot]:    # pivot보다 큰 데이터를 찾을 때까지 반복
			left += 1
		while right > start and data[right] >= data[pivot]: # pivot보다 작은 데이터를 찾을 때까지 반복
			right -= 1

		if left > right:                                    # 엇갈렸다면 작은 데이터와 pivot 교체
			data[right],data[pivot] = data[pivot],data[right]
		else:                                               # 엇갈리지 않았다면 작은 데이터와 큰 데이터 교체
			data[left],data[right] = data[right], data[left]

	quickSort(data, start, right-1)                         # 분할 이후 왼쪽 부분과 오른쪽 부분에서 각각 정렬 수행
	quickSort(data, right+1, end)

quickSort(array, 0, len(array)-1)
print(array)
```

### 예제 2 - 재귀 알고리즘 활용

```python
array = [5,7,9,0,3,1,6,2,4,8]

def quickSort(data):
	if len(data) <= 1:     # 리스트가 하나 이하의 원소만을 가지고 있다면 종료
		return data
	pivot = data[0]        # pivot은 첫번째 원소
	tail = data[1:]        # pivot을 제외한 리스트

	left_side = [x for x in tail if x <= pivot]  # 분할된 왼쪽 부분
	right_side = [x for x in tail if x > pivot]  # 분할된 오른쪽 부분

	return quickSort(left_side) + [pivot] + quickSort(right_side)
	# 분할 이후 왼쪽 부분과 오른쪽 부분에서 각각 정렬을 수행하고, 전체 리스트를 반환
print(quickSort(array))
```

### 예제 3 - 리스트의 가운제 원소를 pivot으로 설정

```python
array = [5,7,9,0,3,1,6,2,4,8]

def quickSort(data, start, end):
	pivot = data[(start+end)//2] # pivot은 가운데 원소
	left,right = start,end

	while True:
		while data[left] < pivot:
			left += 1
		while data[right] > pivot:
			right -= 1

		if left >= right: break
		data[left],data[right] = data[right], data[left]

	if start < right: quickSort(data,start,right)
	if left < end: quickSort(data, right+1, end)

quickSort(array, 0, len(array)-1)
print(array)

```