# Array는 어떤 자료구조인가?

## 핵심 개념
Array는 연관된 데이터를 **메모리상에 연속적이며 순차적으로 미리 할당된 크기**만큼 저장하는 자료구조입니다.

---

## 💡면접 대비 핵심 포인트💡
**Array vs Linked List**의 비교되는 특징
1. **메모리에 저장되는 방식**
2. 1번에 따른 **operation의 연산 속도(time complexity)**<br>

---

## Array의 특징
-핵심 특징 : **고정된 저장 공간**에 **순차적인 데이터 저장**을 한다.

- Array의 장점 : **lookup**과 **append**가 빠르다.  
-> **조회를 자주 해야 하는 작업**일 때 자주 Array 자료구조를 자주 사용한다.

- Array의 단점 : **저장 공간이 고정되어 있음으로 Array의 크기를 미리 정해야** 한다.  
-> 이는 메모리 낭비나 추가적인 **overhead(작업 시간 소요)** 가 발생할 수 있다.

---

## 시간복잡도
⚠️ 핵심 특징 : **고정된 저장 공간**에 **순차적인 데이터 저장**을 기억하며 계산하자!
<img width="524" alt="image" src="https://github.com/user-attachments/assets/e2393ef3-621d-4823-ae08-ed8a6019d855">


### 접근(access) 탐색(search)
✅ 접근 혹은 탐색하려는 **인덱스 값을 알고 있으므로 `O(1)`**<br>
✅ 접근 혹은 탐색하려는 **인덱스 값을 모르면 `O(n)`**

### 추가(append)와 삽입(insertion)
추가하려는 데이터의 **위치가 맨 뒤이고 배열에 공간이 남아있다면, `O(1)`**<br>
추가하려는 데이터가 **위치가 맨 뒤가 아니면**, 추가되는 데이터 위치 이후에 있는 **모든 데이터들을 한 칸씩 미뤄야하므로 `O(n)`**<br>
추가하려는 데이터가 **공간이 남아 있지 않다면**, **크기를 늘릴 수 없어서 새로 만들어야하므로 `O(n)`**

### 삭제(deletion)
삭제하려는 데이터의 **위치가 맨 뒤이고 배열에 공간이 남아있다면, `O(1)`**<br>
삭제하려는 데이터의 **위치가 맨 뒤가 아니라면, 새로 만들어야하므로 `O(n)`**

---

## 꼬리 질문
**Q)** 예상보다 데이터를 저장하느라 Array의 size를 넘어서게되었다. 이 때, 어떻게 해결 방법은?

---
<br><br><br>

# Dynamic Array는 어떤 자료구조인가?

## 핵심 개념
Array는 **size가 고정**되었기 때문에 선언 시에 설정한 size보다 많은 개수의 data가 추가되면 저장할 수 없습니다.  
이에 반해 **Dynamic Array**는 저장공간이 가득 차게 되면 **resize**를 하여 유동적으로 size를 조절하며 데이터를 저장하는 자료구조입니다.

---

## 💡면접 대비 핵심 포인트💡 
Array의 특징 중에 **fixed-size의 한계점**을 보완하고자 고안된 자료구조인 **Dynamic Array**에 대한 공부 포인트.
1. **resize를 하는 방식**
2. **데이터 추가(append)할 때의 시간복잡도**

---

## Dynamic Arra의 개념과 특징

**개념** : Dynamic Array는 **size**를 자동적으로 **resizing**하는 Array이다.<br>
고정된 사이즈를 가진 Static Array의 한계점을 보완하고자 고안되었다.

**방식** : **Resizing**
1. 데이터를 계속 **추가(append)** 하다가 기존에 할당된 메모리를 초과한다.
2. **size를 늘린 배열을 선언**하고 그것으로 모든 데이터를 일일이 옮긴다.
   
-> 따라서 Dynamic Array는 size를 미리 고민할 필요가 없다.
(물론, resizing시마다 개발적으로 좋진 않다.)

---

## Doubling

✅ **개념** : resize의 대표적인 방법을 기존 Array **size의 2배**로 늘린다.(컴퓨터의 default 방식이다.)<br>
✅ **시간 복잡도** : **n개의 데이터를 옮겨야 하기 때문에, `O(n)`**

---

## 데이터 추가(append)할 때의 시간복잡도는?

❓ Dynamic Array에 데이터를 추가할 때마다 `O(1)`의 시간이 걸린다.<br>
하지만 **추가를 하다가 미리 선언된 size를 넘어서게 되는 순간**에 **resize**를 하게 되며, 이때는는 **모든 데이터를 옮겨야 하므로, `O(n)`의 시간**이 걸린다.<br>
그렇다면 결과적으로 **append**의 시간복잡도는 `O(1)`일까? 아니면 `O(n)`일까?
<br><br>

## 분할상환 시간복잡도 (Amortized Time Complexity)

✅ 쉽게 말하자면, 가끔 발생하는 `O(n)`의 시간을 자주 발생하는 `O(1)`의 작업들에 **분산**해서 전체적으로 **평균 `O(1)`의 시간이 걸린다고 생각**한다.<br>
이를 조금 더 정확히 표현하면 **Amortized O(1)** 이라고 부른다.

Append의 전체 과정은 다음과 같다.
1. 마지막 인덱스에 추가하는 `O(1)` 작업을 반복한다.  
2. size를 넘어서게 되는 상황에서는 데이터를 옮기는 작업(`resize O(n)`)이 발생한다.<br>
   -> 발생 빈도가 1 >>>>>> 2 이므로, 전체적으로 `append`의 **평균적인 시간복잡도는 `O(1)`** 이다.

---

## 꼬리 질문
**Q)** Dynamic Array vs Linked List 장단점을 비교하라

---
<br><br><br>

# Linked List는 어떤 자료구조인가?

## 핵심 개념
Linked List는 **noed라는 구조체**로 이루어져 있으며, **node에 데이터 값과 다음 node의 address를 저장**하는 자료구조 입니다. <br>
**메모리 상으로는 비연속적**이지만 next noded의 address를 가짐으로써 **논리적인 연속성**을 가집니다.<br>


---

## 💡면접 대비 핵심 포인트💡
1. **tree, graph**등 다른 자료구조를 구현할 떄 자주 쓰이는 자료구조이다.
2. **메모리 상으로는 불연속적**으로 데이터가 저장 되지만, next node의 address를 가짐으로써 **논리적인 연속성을 보장**한다.
3. 데이터가 **추가되는 시점에서 메모리를 할당**하기 떄문에 **메모리를 효율적으로 사용**할 수 있다.

---

<img width="702" alt="image" src="https://github.com/user-attachments/assets/644d8a23-bbef-4108-b377-d820f5384936">

## Linked List의 특징
-핵심 특징 : **메모리 상으로는 비연속적**이지만 next noded의 address를 가짐으로써 **논리적인 연속성**을 가진다.

- Linked List의 장점 : **append**와 **deletion**이 빠르다.  
-> **데이터의 삽입과 삭제**가 빈번한 작업일 때 자주 Linked List 자료구조를 자주 사용한다.

- Linked List의 단점 :
   - **access**와 **search**가 느리다.
   - Array보다 하나 당 차지하는 메모리가 더 크다.(next node address저장) 

---

## 시간복잡도
⚠️ 핵심 특징 : **유동적 저장 공간**에 **node가 next node의 adderess를 가짐으로써 연결됨**을 기억하며 계산하자!

<img width="761" alt="image" src="https://github.com/user-attachments/assets/20edd1c5-f8ef-4dbc-803d-7f5927ff6cbc">


### 접근(access) 탐색(search)
✅ **이전 node를 거쳐야만 순차적으로 다음 node**로 갈 수 있기 때문에 **`O(n)`**<br>

### 추가(append)와 삽입(insertion)
**데이터가 추가되는 시점에 메모리를 할당**하고, **next address가 가리키는 값만 변경하면 되기 때문에 `O(1)`**<br>
+) 현실적으로 데이터의 추가와 삭제 과정에서는 탐색이 필요하다. 그러므로 최악의 경우 O(n)의 시간 복잡도를 가진다.

### 삭제(deletion)
**next address가 가리키는 값만 변경하면 되기 때문에 `O(1)`**<br>
+) 현실적으로 데이터의 추가와 삭제 과정에서는 탐색이 필요하다. 그러므로 최악의 경우 O(n)의 시간 복잡도를 가진다.

---
<br>
<br>
<br>

# Array vs Linked List 비교

## 핵심 개념
|          | **Array** | **Linked List** | 비고 |
|------------|-----------|----------|--------|
|메모리 저장 방법| **연속적**으로 데이터를 저장 | **비연속적**으로 데이터를 저장 | |
|access 방법 | 각 데이터에의 **index** | 각 노드에 저장된 **next node address** | |
|조회/탐색 | **`O(1)`** | **`O(n)`** | 위치에 따라 다름 주의 |
|삽입/삭제 | **`O(n)`** | **`O(1)`** | 위치에 따라 다음 주의 |

## 결론
- **Array**
   - 데이터 크기가 크고 **조회가 빈번**할 경우 적합.
   - 단, **메모리가 남아 있을 때 맨 끝 append가 빠르다.**  
   - 고정된 사이즈로 인해서 데이터가 저장되어 있지 않더라도 메모리를 차지하기 때문에 **메모리 낭비가 발생**
   
- **Linked List**
   - **삽입/삭제가 빈번**한 경우 적합.
   - runtime중에도 사이즈 변경 가능하므로, 메모리 낭비가 없음.

