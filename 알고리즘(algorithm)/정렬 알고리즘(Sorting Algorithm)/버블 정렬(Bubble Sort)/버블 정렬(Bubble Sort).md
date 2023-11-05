# 개요
### 현재 자신과 그 다음을 비교하여 다음 숫자가 더 작으면 서로의 위치를 바꾸는 작업 반복한다.
### 공간 복잡도 : O(1)
### 시간 복잡도 : O(N<sup>2</sup>)
---
# 특징
### 점점 큰 값들을 뒤에서부터 앞으로 하나씩 쌓아 나가기 때문에 후반으로 갈수록 정렬 범위가 하나씩 줄어든다.
### 선택 정렬과 정반대의 정렬 방향을 가진다.
### 다른 정렬 알고리즘에 비해 자료 교대(swap)가 빈번하게 일어나는 경향이 있다. 
---
# 복잡도 분석
### 공간 복잡도 : O(1)
별도의 추가 공간을 사용하지 않고 주어진 배열이 차지하고 있는 공간 내에서 값들의 위치만 바꾼다.
### 시간 복잡도 : O(N<sup>2</sup>)
우선 루프문을 통해 맨 뒤부터 맨 앞까지 모든 인덱스를 접근해야 하기 때문에 기본적으로 O(N) 시간을 소모한다.
하나의 루프에서 인접한 값들의 대소 비교 및 자리 교대를 위해 O(N)시간을 필요로 한다.
**따라서 총 O(N<sup>2</sup>)의 시간 복잡도를 가진다.**
### 부분적으로 정렬된 배열에 대해서는 최적화를 통해 성능을 대폭 개선할 수 있다.
완전히 정렬되어 있는 배열이 들어올 경우, O(N)까지 시간 복잡도를 향상시킬 수 있다.

---
# 예시
### 예시 데이터
<center><font size=6>7 5 9 0 3</font></center>

### 정렬 과정
<font color="#7f7f7f">회색 부분</font>은 비교해서 순서를 바꾸어야 하는 부분을 표시
<font color="#4f81bd">파란색 부분</font>은 정렬이 완료된 부분을 표시

<center>
<font size=6><font color="#7f7f7f">7 5</font> 9 0 3</font>
</center>
<center>
<font size=6>5 7<font color="#7f7f7f"> 9 0</font> 3</font>
</center>
<center>
<font size=6>5 7 0 <font color="#7f7f7f">9 3</font></font>
</center>
<center>
<font size=6>5 <font color="#7f7f7f">7 0</font> 3 <font color="#4f81bd">9</font></font>
</center>
<center>
<font size=6>5 0 <font color="#7f7f7f">7 3</font> <font color="#4f81bd">9</font></font>
</center>
<center>
<font size=6><font color="#7f7f7f">5 0</font> 3 <font color="#4f81bd"><font color="#4f81bd">7 9</font></font></font>
</center>
<center>
<font size=6><font color="#4f81bd">0</font> <font color="#7f7f7f">5 3</font> <font color="#4f81bd">7 9</font></font>
</center>
<center>
<font size=6><font color="#4f81bd">0 3 5 7 9</font></font>
</center>

---
# 파이썬 예시
- 입력 : \[7,5,9,0,3,1,6,2,4,8]

```python
array = [7,5,9,0,3,1,6,2,4,8]

def bubbleSort(data):
	for i in range(len(data)=1, 0, -1):
		for j in range(i):
			if dataa[i] > data[j+1]:
				data[j], data[j+1] = data[j+1], data[j] #스와프

bubbleSort(array)
print(array)
```
- 출력 : \[0,1,2,3,4,5,6,7,8,9]