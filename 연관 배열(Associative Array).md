# 정의
### Key 하나와 Value 하나가 연관되어 있는 자료구조 중 하나
- Key를 통해 연관되는 값을 얻을 수 있음
### 연상 배열, 결합형 배열, Map 사전이라고도 부른다.

---

# 지원 명령
### key와 value가 주어졌을 때 - 연관 배열에 그 두 값을 저장하는 명령
### key가 주어졌을 대 - 연관되는 value를 얻는 명령
### key와 새로운 value가 주어졌을 때 - 원래 key에 연관된 value를 새로운 value로 교체하는 명령
### key가 주어졌을 때 - 해당 key에 연관된 value를 제거하는 명령

---

# 예시
### 파이썬 예시(JSON도 해당)

```Python
{
    "Pride and Prejudice": "Alice",
    "Wuthering Heights": "Alice",
    "Great Expectations": "John"
}
```
- key인 "Great Expectations"에 대해 검색 작업을 수행 → "John" 반환

___

# 지원하는 언어
### 펄
### 파이썬
### PHP
### Java Script
### Ruby
### 등등