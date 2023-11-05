# 개요
### 데이터가 무작위로 여러 개 있을 때, 가장 작은 데이터를 선택해 맨 앞에 있는 데이터와 바꾸고, 그 다음 작은 데이터를 선택해 앞에서 두번째 데이터와 바꾸는 과정을 반복하는 방법
### 가장 원시적인 방법은 매번 가장 작은 데이터를 선택하는 것이다.
### 공간 복잡도 : O(N)
### 시간 복잡도 : O(N<sup>2</sup>)
---
# 특징
### 정렬된 값을 배열의 맨 앞부터 하나씩 채워 나가며 뒤로 갈수록 비교 범위가 하나씩 줄어든다.
index 0에서는 n-1까지 비교해야 하지만, index n-1에서는 남은 숫자가 하나밖에 없으므로 비교할 필요가 없다.
### 입력 배열의 정렬 여부와 상관없이 동일한 연산량을 가진다.
최적화 여지가 적어 다른 O(N<sup>2</sup>)에 비해 성능이 떨어지는 편이다.

---
# 복잡도 분석
### 공간 복잡도 : O(N)
별도의 추가 공간을 사용하지 않고 주어진 배열이 차지하고 있는 공간 내에서 값들의 위치만을 바꾼다.
### 시간 복잡도 : O(N<sup>2</sup>)
우선 루프문을 통해 모든 인덱스에 접근해야 하므로 기본적으로 O(N)시간을 소모한다.
하나의 루프에서는 현재 인덱스의 값과 다른 인덱스의 값들을 비교하여 최소값을 찾은 후 현재 인덱스에 있는 값과 상호 자리 교대(swap)를 해야 하므로 O(N)시간이 필요하다.

---
# 예시
### 예시 데이터
<center><font size=6>7 5 9 0 3 1 6 2 4 8</font></center>

### 정렬 과정
<font color="#ffff00">노란색</font>은 선택한 데이터와 바뀔 데이터
<font color="#7f7f7f">회색</font>은 바꾸기 위해 선택한 데이터
<font color="#00b0f0">파란색</font>은 정렬이 완료된 데이터
- 초기 단계에서는 모든 데이터가 정렬되어 있지 않으므로, 전체 중에서 가장 작은 데이터를 선택한다.
	- 따라서 '0'을 선택해 맨 앞에 있는 데이터 '7'과 바꾼다.
<center><font size=6><font color="#ffff00">7</font> 5 9 <font color="#7f7f7f">0</font> 3 1 6 2 4 8</font></center>
- 정렬되지 않은 데이터 중 가장 작은 데이터인 '1'을 선택해 처리되지 않은 데이터 중 가장 앞의 데이터인 '5'와 바꾼다.
<center><font size=6><font color="#00b0f0">0</font> <font color="#ffff00">5</font> 9 7 3 <font color="#7f7f7f">1</font> 6 2 4 8</font></center>
- 정렬되지 않은 데이터 중 가장 작은 데이터인 '2'를 선택해 처리되지 않은 데이터 중 가장 앞의 데이터인 '9'와 바꾼다.
<center><font size=6><font color="#00b0f0">0 1</font> <font color="#ffff00">9</font> 7 3 5 6 <font color="#7f7f7f">2</font> 4 8</font></center>
- 위의 과정을 반복하여 정렬을 완료한다.
<center><font size=6>...</font></center>
<center><font size=6><font color="#00b0f0">0 1 2 3 4 5 6 7 8 9</font></font></center>
<center><font size=6></font></center>
---
# 파이썬 예시
- 입력 : \[7,5,9,0,3,1,6,2,4,8]

```python
array = [7,5,9,0,3,1,6,2,4,8]

def selectionSort(data):
	for i in range(len(data)):
		min_index=i
		for j in range(i+1, len(array)):
			if data[min_index] > data[j]:
				min_index=j
		data[i], data[min_index] = data[min_index], data[i] # 스와프
selectionSort(array)
print(array)
```
- 출력 : \[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]