# 개요
### 처리되지 않은 데이터를 하나씩 골라 적절한 위치에 삽입한다.
### 특정한 데이터가 적절한 위치에 들어가기 이전에, 그 앞까지의 데이터는 이미 정렬되어 있다고 가정한다.
### 정렬되어 있는 데이터 리스트에서 적절한 위치를 찾아 그 위치에 삽입한다.
### 공간 복잡도 : O(N)
### 시간 복잡도 : O(N<sup>2</sup>)
---
# 특징
### [[선택 정렬(Selection Sort)|선택 정렬]]에 비해 구현 난이도 높은 편이지만, 일반적으로 더 효율적으로 동작한다.
### 선택/[[버블 정렬(Bubble Sort)|버블 정렬]]이 단계를 거듭할수록 탐색 범위가 줄어드는 반면, 삽입 정렬은 정렬 범위가 점점 넓어진다.
### 바깥 루프는 순방향, 안쪽 루프는 역방향으로 진행된다.
---
# 복잡도 분석
### 공간 복잡도 : O(N)
별도의 추가 공간을 사용하지 않고 주어진 배열이 차지하는 공간 내에서 값들의 위치만 바꾼다.
### 시간 복잡도 : O(N<sup>2</sup>)
루프문을 통해 정렬 범위를 2개로 시작해서 전체로 확장해야 하기 때문에 기본적으로 O(N) 시간을 소모한다.
각 단계에서 정렬 범위에 새롭게 추가된 값과 기존 값들의 비교 및 자리 교체를 위해 O(N) 시간이 필요하다.
총 O(N<sup>2</sup>)의 시간 복잡도를 가진다.
### 최적화를 통해 부분적으로 정렬된 배열에 대해서 성능을 대폭 개선할 수 있다.
완전히 정렬되어 있는 배열이 들어올 경우 O(N)까지 시간 복잡도를 향상시킬 수 있다.

---
# 예시
### 예시 데이터
<center><font size=6>7 5 9 0 3 1 6 2 4 8</font></center>

### 정렬 과정
**오름차순 정렬**
<font color="#ffff00">노란색</font>은 선택한 데이터가 삽입될 위치, 삽입될 수 있는 위치는 v로 표시하였다.
<font color="#7f7f7f">회색</font>은 바꾸기 위해 선택한 데이터
<font color="#00b0f0">파란색</font>은 정렬이 완료된 데이터
- 첫 번째 데이터 '7'을 그 자체로 정렬되어 있다고 판단하고, 다음 데이터인 '5'가 어떤 위치로 들어갈지 판단한다.
- 오름차순 정렬이므로 7의 왼쪽에 삽입한다.
<center><font size=6><font color="#ffff00">v</font><font color="#00b0f0">7</font>v<font color="#7f7f7f">5</font> 9 0 3 1 6 2 4 8</font></center>
- '9'가 어느 위치로 삽입될지 판단한다. '9'는 '5'와 '7'보다 크므로 원래 자리에 둔다.
<center><font size=6>v<font color="#00b0f0">5</font>v<font color="#00b0f0">7</font><font color="#ffff00">v</font><font color="#7f7f7f">9</font> 0 3 1 6 2 4 8</font></center>
- '0'이 어느 위치로 삽입될지 판단한다. '0'은 '5','7','9'와 비교했을 때 가장 작으므로 첫 번째 위치에 삽입한다.
<center><font size=6><font color="#ffff00">v</font><font color="#00b0f0">5</font>v<font color="#00b0f0">7</font>v<font color="#00b0f0">9</font>v<font color="#7f7f7f">0</font> 3 1 6 2 4 8</font></center>
- 위의 과정을 정렬이 완료될 때까지 반복한다.
<center><font size=6>...</font></center>
<center><font size=6><font color="#00b0f0">1 2 3 4 5 6 7 8 9</font></font></center>

---
# 파이썬 예제
- 입력 : \[7,5,9,0,3,1,6,2,4,8]

```python
array = [7,5,9,0,3,1,6,2,4,8]

def insertionSort(data):
	for i in range(1, len(data)):
		for j in range(i, 0, -1):
			if data[j] < data[j-1]: # 한칸씩 왼쪽으로 이동
				data[j], data[j-1] = data[j-1], data[j]
			else: # 자기보다 작은 데이터를 만나면 해당 위치에서 멈춘다.
				break
insertionSort(array)
print(array)
```
- 출력 : \[1,2,3,4,5,6,7,8,9]