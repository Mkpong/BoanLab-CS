
# 정렬 (Sorting)

## 기본 정렬 알고리즘
**정렬 알고리즘:**  데이터 집합을 특정 순서(예: 오름차순 또는 내림차순)로 재배열하는 방법 
- **버블 정렬 (Bubble Sort)**
- **선택 정렬 (Selection Sort)**
- **삽입 정렬 (Insertion Sort)**

### 버블 정렬 (Bubble Sort)

**정의:**
- 인접한 두 요소를 비교하여 정렬을 수행
- 정렬이 완료될 때까지 반복하여 수행

**특징:**
- 비교 기반 정렬 알고리즘으로, 인접한 요소를 반복적으로 비교
- 최악의 경우 모든 요소를 n-1번 반복하여 비교해야 함
- 시간복잡도: O(n^2)
- 공간복잡도: O(1) (In-place 알고리즘)
- 안정 정렬

**동작 방식:**
1. 첫 번째와 두 번째 요소를 비교하여 교환
2. 두 번째와 세 번째 요소를 비교하여 교환
3. 마지막 요소까지 반복 수행
4. 한 번의 반복이 끝나면 마지막 요소는 정렬 완료된 상태로 간주

**장점:**
- 구현이 매우 간단함
**단점:**
- 데이터 개수가 많을수록 성능 저하

**활용:**
- 소규모 데이터의 간단한 정렬에 사용

![bubble](./image/1.png)
>위 그림은 버블 정렬 방법의 실행 과정을 보여줌

**실습 코드**
<details>
<summary>Bubble sort - python</summary>

```python
def bubble_sort(arr):
    n = len(arr)
    for i in range(n):  # 배열 전체를 반복
        swapped = False  # 교환 여부를 확인
        for j in range(0, n - i - 1):  # 아직 정렬되지 않은 부분
            if arr[j] > arr[j + 1]:  # 인접한 두 값을 비교
                arr[j], arr[j + 1] = arr[j + 1], arr[j]  # 교환
                swapped = True
        if not swapped:  # 교환이 없으면 정렬 완료
            break
    return arr

# 테스트
data = [64, 34, 25, 12, 22, 11, 90]
print("Unsorted Array:", data)

sorted_data = bubble_sort(data)
print("Sorted Array:", sorted_data)

```
</details>

---

### 선택 정렬 (Selection Sort)

**정의:**
- 리스트에서 가장 작은 요소를 선택하여 정렬 수행
- 첫 번째부터 마지막까지 반복적으로 수행

**특징:**
- 비교 기반 정렬 알고리즘으로, 선택된 최소값을 정렬된 영역으로 이동
- 데이터 교환 횟수는 적지만, 비교 횟수가 많음
- 시간복잡도: O(n^2)
- 공간복잡도: O(1)
- 불안정 정렬

**동작 방식:**
1. 리스트에서 최소값을 찾음
2. 최소값을 현재 위치로 이동
3. 정렬된 부분을 제외하고 나머지 리스트에 대해 반복

**장점:**
- 교환 횟수가 적음
**단점:**
- 시간복잡도가 높아 비효율적임

**활용:**
- 데이터 이동이 적은 경우 적합

![select](./image/2.png)
>위 그림은 선택정렬 방식의 실행 과정을 보여줌

**실습 코드**
<details>
<summary>Selection sort - python</summary>

```python
def selection_sort(arr):
    n = len(arr)
    for i in range(n):
        # 현재 반복에서 가장 작은 값의 인덱스를 찾음
        min_idx = i
        for j in range(i + 1, n):
            if arr[j] < arr[min_idx]:
                min_idx = j
        # 가장 작은 값과 현재 위치 값을 교환
        arr[i], arr[min_idx] = arr[min_idx], arr[i]
    return arr

# 테스트
data = [64, 25, 12, 22, 11]
print("Unsorted Array:", data)

sorted_data = selection_sort(data)
print("Sorted Array:", sorted_data)

```
</details>

---

### 삽입 정렬 (Insertion Sort)

**정의:**
- 각 요소를 적절한 위치에 삽입하여 정렬 수행
- 초기 정렬된 부분과 정렬되지 않은 부분으로 나뉨

**특징:**
- 비교 기반 정렬 알고리즘으로, 작은 배열에서 매우 효율적임
- 이미 정렬된 데이터에서 최적의 성능 발휘
- 시간복잡도: O(n^2) (최악), O(n) (최선, 이미 정렬된 경우)
- 공간복잡도: O(1)
- 안정 정렬

**동작 방식:**
1. 첫 번째 요소를 기준으로 정렬된 부분 생성
2. 다음 요소를 정렬된 부분과 비교하며 적절한 위치에 삽입
3. 정렬된 부분을 확장하며 모든 요소를 삽입

**장점:**
- 이미 정렬된 데이터에서 매우 효율적임
**단점:**
- 데이터가 많을 경우 성능 저하

**활용:**
- 데이터가 거의 정렬된 경우 적합

![insert](./image/3.png)
>위 그림은 기본정렬 방식의 실행 과정을 보여줌 

**실습 코드**
<details>
<summary>Insertion sort - python</summary>

```python
def insertion_sort(arr):
    # 첫 번째 요소는 이미 정렬된 것으로 간주하므로 두 번째 요소부터 시작
    for i in range(1, len(arr)):
        key = arr[i]
        j = i - 1

        # key 값이 정렬된 부분의 값보다 작으면 위치를 이동
        while j >= 0 and key < arr[j]:
            arr[j + 1] = arr[j]
            j -= 1

        # key 값을 올바른 위치에 삽입
        arr[j + 1] = key

    return arr

# 테스트
data = [12, 11, 13, 5, 6]
print("Unsorted array:", data)

sorted_data = insertion_sort(data)
print("Sorted array:", sorted_data)
```
</details>

---
## 고급 정렬 알고리즘

### 병합 정렬 (Merge Sort)

**정의:**
- 분할 정복(divide and conquer) 방식의 정렬 알고리즘
- 데이터를 반으로 나눈 후 병합하여 정렬 수행

**특징:**
- 비교 기반 정렬 알고리즘으로, 안정성을 보장
- 추가 메모리 공간이 필요함
- 시간복잡도: O(n log n)
- 공간복잡도: O(n)
- 안정 정렬

**동작 방식:**
1. 배열을 절반으로 분할
2. 각 부분을 재귀적으로 병합 정렬 수행
3. 정렬된 두 부분을 병합하여 최종 배열 생성

**장점:**
- 데이터 크기에 비례한 성능 유지
**단점:**
- 추가 메모리 공간이 필요함

**활용:**
- 대규모 데이터 정렬에 적합

![merge](./image/4.png)
>위 그림은 배열을 분리해서 정렬 후 다시 병합하는 과정을 보여줌 

**실습 코드**
<details>
<summary>Merge sort - python</summary>

```python
def merge_sort(arr):
    if len(arr) <= 1:  # 배열 길이가 1 이하이면 이미 정렬된 상태
        return arr

    # 배열을 두 부분으로 분할
    mid = len(arr) // 2
    left_half = merge_sort(arr[:mid])
    right_half = merge_sort(arr[mid:])

    # 분할된 부분 병합
    return merge(left_half, right_half)

def merge(left, right):
    sorted_array = []
    i = j = 0

    # 두 배열을 비교하며 작은 값을 결과에 추가
    while i < len(left) and j < len(right):
        if left[i] < right[j]:
            sorted_array.append(left[i])
            i += 1
        else:
            sorted_array.append(right[j])
            j += 1

    # 남은 요소 추가
    sorted_array.extend(left[i:])
    sorted_array.extend(right[j:])

    return sorted_array

# 테스트
data = [38, 27, 43, 3, 9, 82, 10]
print("Unsorted Array:", data)

sorted_data = merge_sort(data)
print("Sorted Array:", sorted_data)

```
</details>

---

### 퀵 정렬 (Quick Sort)

**정의:**
- 분할 정복 방식의 효율적인 정렬 알고리즘
- 기준(pivot)을 중심으로 정렬 수행

**특징:**
- 비교 기반 정렬 알고리즘으로, 평균적으로 빠른 성능 발휘
- pivot 선택에 따라 최악의 성능이 나타날 수 있음
- 시간복잡도: O(n log n) (평균), O(n^2) (최악)
- 공간복잡도: O(log n)
- 불안정 정렬

**동작 방식:**
1. pivot을 선택
2. pivot보다 작은 요소는 왼쪽, 큰 요소는 오른쪽으로 분할
3. 각 부분에 대해 재귀적으로 정렬 수행

**장점:**
- 평균적으로 매우 빠른 성능
**단점:**
- 최악의 경우 성능 저하

**활용:**
- 데이터 크기가 큰 경우 적합

![quick](./image/5.png)
>위 그림은 Pivot을 이용하여 정렬하는 실행 과정을 보여줌 

**실습 코드**
<details>
<summary>Quick sort - python</summary>

```python
def quick_sort(arr):
    if len(arr) <= 1:  # 배열 길이가 1 이하이면 이미 정렬된 상태
        return arr

    # 피벗 선택 (여기서는 첫 번째 요소 사용)
    pivot = arr[0]

    # 피벗을 기준으로 왼쪽(작은 값)과 오른쪽(큰 값)으로 분할
    less = [x for x in arr[1:] if x <= pivot]
    greater = [x for x in arr[1:] if x > pivot]

    # 재귀적으로 왼쪽과 오른쪽 배열 정렬 후 병합
    return quick_sort(less) + [pivot] + quick_sort(greater)

# 테스트
data = [10, 7, 8, 9, 1, 5]
print("Unsorted Array:", data)

sorted_data = quick_sort(data)
print("Sorted Array:", sorted_data)

```
</details>

---

### 힙 정렬 (Heap Sort)

**정의:**
- 힙 자료구조를 이용한 정렬 알고리즘
- 최대/최소 힙을 생성하여 정렬 수행

**특징:**
- 비교 기반 정렬 알고리즘으로, 메모리 사용이 적음
- 정렬 과정에서 힙의 성질을 유지하며 루트를 정렬된 영역으로 이동
- 시간복잡도: O(n log n)
- 공간복잡도: O(1)
- 불안정 정렬

**동작 방식:**
1. 입력 배열을 힙으로 변환
2. 힙의 루트를 제거하고 마지막 요소와 교환
3. 힙을 재구성하여 정렬 완료될 때까지 반복

**장점:**
- 추가 메모리 사용이 적음
**단점:**
- 구현이 복잡함

**활용:**
- 메모리 사용이 제한적인 경우 적합

![heap](./image/6.png)
>위 그림은 배열을 힙으로 정렬하는 과정을 보여줌 

**실습 코드**
<details>
<summary>Heap sort - python</summary>

```python
def heapify(arr, n, i):
    largest = i  # 루트를 가장 큰 값으로 초기화
    left = 2 * i + 1  # 왼쪽 자식 노드
    right = 2 * i + 2  # 오른쪽 자식 노드

    # 왼쪽 자식이 루트보다 크면 largest 업데이트
    if left < n and arr[left] > arr[largest]:
        largest = left

    # 오른쪽 자식이 largest보다 크면 largest 업데이트
    if right < n and arr[right] > arr[largest]:
        largest = right

    # largest가 루트가 아니라면 스왑 후 재귀적으로 힙 구조 재정렬
    if largest != i:
        arr[i], arr[largest] = arr[largest], arr[i]
        heapify(arr, n, largest)

def heap_sort(arr):
    n = len(arr)

    # 배열을 최대 힙으로 변환
    for i in range(n // 2 - 1, -1, -1):
        heapify(arr, n, i)

    # 하나씩 힙에서 요소를 추출하여 정렬
    for i in range(n - 1, 0, -1):
        arr[i], arr[0] = arr[0], arr[i]  # 현재 루트(최대값)과 끝 요소를 교환
        heapify(arr, i, 0)  # 남은 힙에 대해 재정렬

    return arr

# 테스트
data = [12, 11, 13, 5, 6, 7]
print("Unsorted array:", data)

sorted_data = heap_sort(data)
print("Sorted array:", sorted_data)
```
</details>

---

### 기수 정렬 (Radix Sort)

**정의:**
- 자리수를 기준으로 정렬하는 비비교 기반 정렬 알고리즘

**특징:**
- 비비교 기반 정렬 알고리즘으로, 데이터의 특성에 따라 빠른 성능 발휘
- 시간복잡도: O(nk) (n: 요소 수, k: 자릿수)
- 공간복잡도: O(n + k)
- 안정 정렬

**동작 방식:**
1. 가장 낮은 자리수를 기준으로 데이터를 정렬
2. 다음 자리수를 기준으로 정렬을 반복
3. 모든 자리수에 대해 정렬이 완료될 때까지 진행

**장점:**
- 데이터 크기와 관계없이 일정 성능 유지
**단점:**
- 자릿수에 따라 성능이 달라짐

**활용:**
- 정수형 데이터에 적합
  
---

### 계수 정렬 (Counting Sort)

**정의:**
- 요소의 개수를 세어 정렬하는 비비교 기반 정렬 알고리즘

**특징:**
- 비비교 기반 정렬 알고리즘으로, 특정 범위 내의 데이터에 적합
- 시간복잡도: O(n + k) (n: 요소 수, k: 최대값)
- 공간복잡도: O(n + k)
- 안정 정렬

**동작 방식:**
1. 각 요소의 개수를 배열에 저장
2. 누적 빈도를 계산하여 위치를 파악
3. 각 요소를 정렬된 배열에 배치

**장점:**
- 간단하고 빠름
**단점:**
- 메모리 사용량이 많음

**활용:**
- 데이터 값이 제한적인 경우 적합

![image](./image/14.png)
>위 그림은 num값의 누적계수를 기반으로 인덱스를 일치시켜 정렬하는 방식을 보여줌
---

### 셸 정렬 (Shell Sort)

**정의:**
- 삽입 정렬의 일반화된 버전
- 특정 간격(gap)을 이용하여 정렬 수행

**특징:**
- 비교 기반 정렬 알고리즘으로, 간격을 줄여가며 부분 정렬 수행
- 간격이 줄어들수록 전체 배열이 정렬됨
- 시간복잡도: O(n^(3/2)) (일반적으로)
- 공간복잡도: O(1)
- 불안정 정렬

**동작 방식:**
1. 초기 간격을 설정
2. 간격만큼 떨어진 요소를 삽입 정렬 수행
3. 간격을 점차 줄이며 반복

**장점:**
- 단순 삽입 정렬보다 효율적임
**단점:**
- 최적의 간격 설정이 어려움

**활용:**
- 중간 규모의 데이터 정렬에 적합

## 비교 기반 정렬과 비비교 기반 정렬의 차이

**비교 기반 정렬:**
- 요소 간의 비교를 통해 정렬 수행
- 예: 버블 정렬, 선택 정렬, 병합 정렬, 퀵 정렬

**비비교 기반 정렬:**
- 요소의 비교 없이 정렬 수행
- 예: 계수 정렬, 기수 정렬, 버킷 정렬

**특징:**
- 비교 기반 정렬의 시간복잡도 하한: O(n log n)
- 비비교 기반 정렬은 데이터 특성에 따라 더 빠를 수 있음
---
## (추가 학습) 안정 정렬과 불안정 정렬

### 안정 정렬 (Stable Sort)

- **정의**: 정렬 후 동일한 값의 요소들이 **정렬 이전의 순서를 유지**하는 정렬 알고리즘
- **예시**: 값이 동일한 데이터 A와 B가 있을 때, 정렬 전 A가 B보다 앞에 있었다면 정렬 후에도 A는 B보다 앞에 위치
- **장점**: 데이터의 순서가 중요한 경우(예: 학생 점수와 이름 같이 여러 기준으로 정렬해야 할 때) 적합
- **예**: 병합 정렬, 버블 정렬, 삽입 정렬 등

---

### 불안정 정렬 (Unstable Sort)

- **정의**: 정렬 후 동일한 값의 요소들이 **정렬 이전의 순서를 유지하지 않을 수 있는** 정렬 알고리즘
- **예시**: 값이 동일한 데이터 A와 B가 있을 때, 정렬 후 A가 B보다 뒤로 바뀔 수 있음
- **장점**: 일반적으로 추가 메모리 사용이 적거나 구현이 간단한 경우가 많음
- **예**: 퀵 정렬, 힙 정렬, 선택 정렬 등

---
# 탐색 (Search)

## 기본 탐색 알고리즘

### 선형 탐색 (Linear Search)

- **정의**: 데이터를 처음부터 끝까지 순차적으로 탐색하여 원하는 값을 찾는 알고리즘
- **특징**:
  - 단순하고 구현이 쉬움
  - 정렬 여부와 상관없이 동작
  - 시간복잡도: O(n)
  - 공간복잡도: O(1)
- **동작 방식**:
  1. 첫 번째 데이터부터 탐색 시작
  2. 각 요소를 순차적으로 확인
  3. 원하는 값을 찾으면 탐색 종료
  4. 끝까지 찾지 못하면 실패 반환
- **장점**:
  - 정렬되지 않은 데이터에서도 사용 가능
- **단점**:
  - 데이터가 많을수록 성능 저하
- **활용**:
  - 소규모 데이터나 정렬되지 않은 데이터에서 사용

![linear](./image/7.png)
> 위 그림은 순차적 탐색을 통해 29를 찾는 과정을 보여줌 

**실습 코드**
<details>
<summary>Linear search - python</summary>

```python
def linear_search(arr, target):
    # 배열의 각 요소를 순차적으로 확인
    for i in range(len(arr)):
        if arr[i] == target:  # 대상 값을 찾으면 인덱스 반환
            return i
    return -1  # 대상 값이 없으면 -1 반환

# 테스트
data = [10, 20, 30, 40, 50]
target = 30

result = linear_search(data, target)
if result != -1:
    print(f"Element found at index {result}")
else:
    print("Element not found")
```
</details>

---

### 이진 탐색 (Binary Search)

- **정의**: 정렬된 데이터에서 중간 값을 기준으로 탐색 범위를 절반씩 줄이며 값을 찾는 알고리즘
- **특징**:
  - 입력 데이터가 정렬되어 있어야 동작
  - 탐색 범위를 줄이기 때문에 효율적
  - 시간복잡도: O(log n)
  - 공간복잡도: O(1) (반복적 구현 시)
- **동작 방식**:
  1. 배열의 중간 요소를 선택
  2. 중간 값이 찾는 값보다 크면 왼쪽 절반 탐색
  3. 작으면 오른쪽 절반 탐색
  4. 값을 찾거나 범위를 줄일 수 없을 때까지 반복
- **장점**:
  - 대규모 데이터에서 빠른 탐색 가능
- **단점**:
  - 데이터가 정렬되어 있지 않다면 사용 불가
- **활용**:
  - 정렬된 데이터에서 효율적으로 탐색할 때 사용

![binary](./image/8.png)
>위 그림은 데이터의 중간값을 기준으로 정렬하는 과정을 보여줌 

**실습 코드**
<details>
<summary>Binary Search</summary>

```python
def binary_search_recursive(arr, target, low, high):
    if low > high:
        return -1  # 대상 값이 없으면 -1 반환

    mid = (low + high) // 2  # 중간 인덱스 계산

    if arr[mid] == target:
        return mid  # 대상 값 찾음
    elif arr[mid] > target:
        return binary_search_recursive(arr, target, low, mid - 1)  # 왼쪽 절반 탐색
    else:
        return binary_search_recursive(arr, target, mid + 1, high)  # 오른쪽 절반 탐색

def binary_search_iterative(arr, target):
    low, high = 0, len(arr) - 1

    while low <= high:
        mid = (low + high) // 2  # 중간 인덱스 계산

        if arr[mid] == target:
            return mid  # 대상 값 찾음
        elif arr[mid] > target:
            high = mid - 1  # 왼쪽 절반으로 범위 줄이기
        else:
            low = mid + 1  # 오른쪽 절반으로 범위 줄이기

    return -1  # 대상 값이 없으면 -1 반환

# 테스트
data = [10, 20, 30, 40, 50, 60]
target = 30

result = binary_search_recursive(data, target, 0, len(data) - 1)
if result != -1:
    print(f"Element found at index {result}")
else:
    print("Element not found")
```
</details>

---

### 이진 탐색 변형 (lower/upper bound 등)

- **정의**: 이진 탐색의 변형으로, 특정 값 이상의 가장 작은 인덱스(lower bound)나 특정 값 이하의 가장 큰 인덱스(upper bound)를 찾는 알고리즘
- **특징**:
  - 정렬된 데이터에서 동작
  - 탐색의 목적에 따라 기준을 다르게 설정
  - 시간복잡도: O(log n)
  - 공간복잡도: O(1)
- **동작 방식**:
  1. 이진 탐색으로 값의 범위를 찾음
  2. lower bound는 값 이상인 첫 위치, upper bound는 값 초과 첫 위치 반환
- **장점**:
  - 정렬된 데이터에서 특정 범위를 빠르게 탐색 가능
- **단점**:
  - 데이터 정렬이 필수적
- **활용**:
  - 정렬된 데이터의 범위를 계산하거나 이진 탐색과 결합하여 사용


## 고급 탐색 알고리즘

### 이진 검색 트리 (Binary Search Tree) 기반 탐색

- **정의**: 이진 검색 트리를 이용하여 데이터를 탐색하는 알고리즘
- **특징**:
  - 각 노드의 왼쪽 서브트리는 해당 노드보다 작은 값, 오른쪽 서브트리는 큰 값을 가짐
  - 평균 시간복잡도: O(log n)
  - 최악의 경우 시간복잡도: O(n) (불균형 트리)
  - 공간복잡도: O(h) (h: 트리 높이)
- **동작 방식**:
  1. 루트에서 탐색 시작
  2. 찾는 값이 현재 노드보다 작으면 왼쪽 서브트리로 이동
  3. 크면 오른쪽 서브트리로 이동
  4. 값을 찾거나 탐색할 노드가 없을 때까지 반복
- **장점**:
  - 데이터의 삽입, 삭제, 탐색이 모두 효율적 (균형 유지 시)
- **단점**:
  - 트리가 불균형할 경우 성능 저하
- **활용**:
  - 동적 데이터 탐색 및 관리

**실습 코드**
<details>
<summary>Binary search tree - python</summary>

```python
class Node:
    def __init__(self, key):
        self.key = key
        self.left = None
        self.right = None

class BinarySearchTree:
    def __init__(self):
        self.root = None

    # 삽입 함수
    def insert(self, key):
        if self.root is None:
            self.root = Node(key)
        else:
            self._insert(self.root, key)

    def _insert(self, current, key):
        if key < current.key:  # 왼쪽에 삽입
            if current.left is None:
                current.left = Node(key)
            else:
                self._insert(current.left, key)
        elif key > current.key:  # 오른쪽에 삽입
            if current.right is None:
                current.right = Node(key)
            else:
                self._insert(current.right, key)

    # 탐색 함수
    def search(self, key):
        return self._search(self.root, key)

    def _search(self, current, key):
        if current is None:
            return False  # 키를 찾을 수 없음
        if key == current.key:
            return True  # 키를 찾음
        elif key < current.key:
            return self._search(current.left, key)  # 왼쪽 서브트리 탐색
        else:
            return self._search(current.right, key)  # 오른쪽 서브트리 탐색

    # 중위 순회 (Inorder Traversal)
    def inorder(self):
        result = []
        self._inorder(self.root, result)
        return result

    def _inorder(self, current, result):
        if current:
            self._inorder(current.left, result)  # 왼쪽 서브트리
            result.append(current.key)          # 현재 노드
            self._inorder(current.right, result)  # 오른쪽 서브트리

# 이진 검색 트리 생성
bst = BinarySearchTree()

# 노드 삽입
bst.insert(50)
bst.insert(30)
bst.insert(70)
bst.insert(20)
bst.insert(40)
bst.insert(60)
bst.insert(80)

# 탐색 테스트
print("Search 40:", bst.search(40))  # True
print("Search 25:", bst.search(25))  # False

# 중위 순회 결과 출력 (오름차순 정렬된 결과)
print("Inorder Traversal:", bst.inorder())  # [20, 30, 40, 50, 60, 70, 80]
```
</details>

---

### 해시 기반 탐색 (Hash-based Search)

- **정의**: 데이터를 해시 함수로 변환하여 빠르게 탐색하는 알고리즘
- **특징**:
  - 탐색, 삽입, 삭제의 평균 시간복잡도: O(1)
  - 최악의 경우 시간복잡도: O(n) (충돌 발생 시)
  - 공간복잡도: O(n)
- **동작 방식**:
  1. 키를 해시 함수에 입력하여 인덱스 계산
  2. 계산된 인덱스 위치에서 값을 탐색
  3. 충돌이 발생한 경우 연결된 데이터를 순차적으로 탐색
- **장점**:
  - 탐색 속도가 매우 빠름
- **단점**:
  - 충돌 관리가 필요하며, 해시 함수 설계에 따라 성능이 좌우됨
- **활용**:
  - 키-값 쌍 기반 데이터 검색 (예: 해시 테이블)

**실습 코드**
<details>
<summary>Hash-based search - python</summary>

```python
class HashTable:
    def __init__(self, size):
        self.size = size
        self.table = [None] * size

    # 해시 함수: 키를 배열의 인덱스로 변환
    def _hash(self, key):
        return hash(key) % self.size

    # 삽입 함수
    def insert(self, key, value):
        index = self._hash(key)
        if self.table[index] is None:
            self.table[index] = []
        # 동일 키 존재 시 업데이트, 없으면 추가
        for pair in self.table[index]:
            if pair[0] == key:
                pair[1] = value
                return
        self.table[index].append([key, value])

    # 탐색 함수
    def search(self, key):
        index = self._hash(key)
        if self.table[index] is not None:
            for pair in self.table[index]:
                if pair[0] == key:
                    return pair[1]
        return None  # 키를 찾을 수 없는 경우

    # 삭제 함수
    def delete(self, key):
        index = self._hash(key)
        if self.table[index] is not None:
            for i, pair in enumerate(self.table[index]):
                if pair[0] == key:
                    self.table[index].pop(i)
                    return True
        return False  # 키를 찾을 수 없는 경우

# 해시 테이블 생성
hash_table = HashTable(10)

# 데이터 삽입
hash_table.insert("apple", 5)
hash_table.insert("banana", 10)
hash_table.insert("orange", 15)

# 데이터 탐색
print("Search 'apple':", hash_table.search("apple"))  # 5
print("Search 'grape':", hash_table.search("grape"))  # None

# 데이터 삭제
hash_table.delete("banana")
print("Search 'banana':", hash_table.search("banana"))  # None
```
</details>

---

### 트라이 (Trie) 기반 검색

- **정의**: 문자열 데이터를 효율적으로 저장하고 검색하기 위해 사용되는 트리 기반 자료구조
- **특징**:
  - 각 노드는 문자열의 한 문자에 해당
  - 데이터 길이에 따라 시간복잡도 결정: O(m) (m: 문자열 길이)
  - 공간복잡도: O(n * m) (n: 단어 수, m: 평균 단어 길이)
- **동작 방식**:
  1. 문자열의 각 문자를 노드로 추가
  2. 검색 시 루트에서 시작하여 문자에 따라 트리를 따라감
  3. 문자열의 끝까지 도달하면 검색 성공
- **장점**:
  - 문자열 검색이 빠르고, 공통 접두사를 효율적으로 관리 가능
- **단점**:
  - 메모리 사용량이 많음
- **활용**:
  - 자동완성, 사전 구현, 접두사 검색

## 탐색 알고리즘의 시간 복잡도 분석

| 알고리즘         | 시간복잡도 (평균) | 시간복잡도 (최악) | 공간복잡도 |
|------------------|------------------|------------------|------------|
| 선형 탐색       | O(n)            | O(n)            | O(1)       |
| 이진 탐색       | O(log n)        | O(log n)        | O(1)       |
| 이진 검색 트리  | O(log n)        | O(n)            | O(h)       |
| 해시 기반 탐색  | O(1)            | O(n)            | O(n)       |
| 트라이 기반 탐색 | O(m)            | O(m)            | O(n * m)   |
# 재귀 및 분할 정복 (Recursion and Divide and Conquer)

## 재귀 (Recursion)

### 기본 재귀 및 기저 조건

**정의:**
- 함수가 자기 자신을 호출하여 문제를 해결하는 방식
- 반드시 종료 조건(기저 조건, Base Case)이 필요

**특징:**
- 문제를 작은 하위 문제로 나누어 해결
- 기저 조건이 없으면 무한 루프 발생
- 시간복잡도와 공간복잡도는 호출 횟수에 비례

**동작 방식:**
1. 문제를 해결 가능한 가장 작은 단위로 분해
2. 기저 조건에 도달하면 함수 호출 종료
3. 반환된 결과를 이용해 상위 문제를 해결

**장점:**
- 코드가 간결하고 직관적
- 문제를 단계적으로 나누어 해결 가능

**단점:**
- 호출 스택 사용으로 메모리 낭비 가능
- 기저 조건을 잘못 설정하면 무한 루프 발생

**활용:**
- 팩토리얼 계산, 피보나치 수열, 하노이 탑 문제 등

---

### 꼬리 재귀 (Tail Recursion)

**정의:**
- 함수의 마지막 작업이 자기 자신을 호출하는 재귀 방식

**특징:**
- 호출 스택을 유지하지 않으므로 메모리 사용 효율적
- 일부 프로그래밍 언어에서 꼬리 호출 최적화(Tail Call Optimization) 지원

**동작 방식:**
1. 함수의 마지막 작업이 자기 자신 호출
2. 재귀 호출 후 별도의 추가 작업 수행하지 않음

**장점:**
- 메모리 사용 최소화 가능
- 스택 오버플로우 방지 가능

**단점:**
- 꼬리 호출 최적화를 지원하지 않는 언어에서는 효과가 제한적
- 특정 문제에만 적용 가능

**활용:**
- 피보나치 수열 계산, 최대공약수(GCD) 계산 등

---

### 재귀와 반복 비교

| 항목         | 재귀                               | 반복                           |
|--------------|------------------------------------|--------------------------------|
| **장점**     | 코드가 간결하고 직관적             | 메모리 사용이 적음            |
| **단점**     | 호출 스택 사용으로 메모리 낭비 가능 | 구현이 복잡할 수 있음          |
| **사용 사례** | 문제를 작은 하위 문제로 나눌 때 적합 | 반복적으로 처리 가능한 작업에 적합 |

---

## 분할 정복 (Divide and Conquer)

**정의:**
- 문제를 작은 하위 문제로 나누고, 하위 문제를 해결한 뒤 합쳐서 전체 문제를 해결하는 방식

**특징:**
- 재귀적으로 문제를 해결
- 문제를 계속 나누다가 더 이상 나눌 수 없는 크기가 되면 해결 후 병합

**동작 방식:**
1. 문제를 여러 하위 문제로 나눔
2. 각 하위 문제를 재귀적으로 해결
3. 해결된 결과를 결합하여 최종 결과 생성

**장점:**
- 대규모 데이터 처리에 효율적
- 병렬 처리에 적합

**단점:**
- 재귀 호출로 인해 스택 오버플로우 발생 가능
- 추가 메모리 사용

**활용:**
- 병합 정렬, 퀵 정렬, 이진 탐색 등

---

### 병합 정렬 (Merge Sort)

**정의:**
- 배열을 반으로 나누어 각각 정렬한 뒤 병합하여 정렬하는 알고리즘

**특징:**
- 안정 정렬
- 시간복잡도: O(n log n)
- 공간복잡도: O(n)

**동작 방식:**
1. 배열을 절반으로 나눔
2. 각 부분을 재귀적으로 정렬
3. 정렬된 부분을 병합

**장점:**
- 데이터 크기에 비례한 일정한 성능
- 안정성을 보장

**단점:**
- 추가 메모리 공간 필요

**활용:**
- 대규모 데이터 정렬

---

### 퀵 정렬 (Quick Sort)

**정의:**
- 피벗을 기준으로 배열을 분할하고, 분할된 부분을 재귀적으로 정렬하는 알고리즘

**특징:**
- 불안정 정렬
- 시간복잡도: O(n log n) (평균), O(n^2) (최악)
- 공간복잡도: O(log n)

**동작 방식:**
1. 피벗을 선택
2. 피벗보다 작은 요소는 왼쪽, 큰 요소는 오른쪽으로 분할
3. 분할된 부분을 재귀적으로 정렬

**장점:**
- 평균적으로 매우 빠름
- 추가 메모리 사용 적음

**단점:**
- 최악의 경우 성능 저하
- 데이터가 정렬된 경우 비효율적

**활용:**
- 대규모 데이터 정렬

---

### 이진 탐색 (Binary Search)

**정의:**
- 정렬된 배열에서 중간 값을 기준으로 탐색 범위를 반씩 줄여가며 값을 찾는 알고리즘

**특징:**
- 시간복잡도: O(log n)
- 공간복잡도: O(1)

**동작 방식:**
1. 배열의 중간 값을 선택
2. 찾는 값이 중간 값보다 크면 오른쪽, 작으면 왼쪽 범위를 탐색
3. 값을 찾거나 범위를 줄일 수 없을 때까지 반복

**장점:**
- 매우 효율적
- 탐색 범위를 빠르게 줄일 수 있음

**단점:**
- 데이터가 정렬되어 있어야만 사용 가능

**활용:**
- 정렬된 데이터에서의 탐색

---

## 백트래킹 (Backtracking)

**정의:**
- 가능한 모든 경우를 탐색하되, 유망하지 않은 경로는 더 이상 탐색하지 않는 방식

**특징:**
- 상태 공간 트리를 기반으로 탐색
- 가지치기(pruning)를 통해 탐색 효율성을 높임

**동작 방식:**
1. 현재 경로에서 가능한 선택을 시도
2. 선택이 유망하지 않으면 되돌아감
3. 모든 경로를 탐색하거나 해답을 찾을 때까지 반복

**장점:**
- 모든 경우의 수를 탐색 가능
- 유망하지 않은 경로를 배제하여 효율성 향상

**단점:**
- 경우의 수가 많으면 탐색 시간이 매우 길어질 수 있음
- 메모리 사용량이 많아질 수 있음

**활용:**
- N-Queens 문제, Sudoku Solver, 순열 및 조합 생성 등

---

### 대표 문제

#### N-Queens

**정의:**
- N x N 체스판에 N개의 퀸을 서로 공격하지 않도록 배치하는 문제

**동작 방식:**
1. 첫 번째 행부터 한 행씩 퀸을 배치
2. 이미 배치된 퀸과 충돌하지 않는 열에 배치 시도
3. 충돌이 발생하면 백트래킹하여 이전 행으로 돌아감

**장점:**
- 상태 공간 트리를 효율적으로 탐색

**단점:**
- N 값이 클수록 탐색 시간이 증가

**실습 코드**
<details>
<summary>N-Queen - python</summary>

```python
def solve_n_queens(n):
    def is_safe(board, row, col):
        # 같은 열에 퀸이 있는지 확인
        for i in range(row):
            if board[i] == col:
                return False

        # 왼쪽 위 대각선에 퀸이 있는지 확인
        for i, j in zip(range(row - 1, -1, -1), range(col - 1, -1, -1)):
            if board[i] == j:
                return False

        # 오른쪽 위 대각선에 퀸이 있는지 확인
        for i, j in zip(range(row - 1, -1, -1), range(col + 1, n)):
            if board[i] == j:
                return False

        return True

    def backtrack(row):
        # 모든 퀸을 배치한 경우
        if row == n:
            result.append(board[:])
            return

        for col in range(n):
            if is_safe(board, row, col):
                board[row] = col  # 퀸 배치
                backtrack(row + 1)  # 다음 행으로 이동
                board[row] = -1  # 백트래킹 (원상 복구)

    result = []
    board = [-1] * n  # 각 행에서 퀸이 배치된 열을 저장
    backtrack(0)
    return result

def print_solutions(solutions, n):
    for solution in solutions:
        for i in range(n):
            row = ["."] * n
            row[solution[i]] = "Q"
            print(" ".join(row))
        print("\n")

# 테스트
n = 8
solutions = solve_n_queens(n)
print(f"Number of solutions for {n}-Queens: {len(solutions)}\n")
print_solutions(solutions[:3], n)  # 첫 3개의 솔루션만 출력
```
</details>

#### Sudoku Solver

**정의:**
- 주어진 스도쿠 퍼즐을 채우는 문제로, 각 행, 열, 그리고 3x3 박스에 1부터 9까지의 숫자가 겹치지 않도록 채움

**동작 방식:**
1. 빈 칸을 순차적으로 채움
2. 현재 위치에 유효한 숫자를 시도
3. 숫자가 유효하지 않으면 백트래킹하여 이전 단계로 돌아감

**장점:**
- 효율적인 가지치기를 통해 해를 찾음

**단점:**
- 퍼즐이 복잡할수록 탐색 시간이 증가

**실습 코드**
<details>
<summary>Sudoku solver - python</summary>

```python
def solve_sudoku(board):
    empty_cell = find_empty_cell(board)
    if not empty_cell:  # 빈 칸이 없으면 퍼즐 해결 완료
        return True

    row, col = empty_cell

    for num in range(1, 10):  # 1부터 9까지 숫자 시도
        if is_valid(board, row, col, num):
            board[row][col] = num  # 숫자를 배치
            if solve_sudoku(board):  # 재귀 호출로 다음 빈 칸 시도
                return True
            board[row][col] = 0  # 실패 시 원상 복구

    return False  # 모든 숫자가 실패하면 False 반환


def find_empty_cell(board):
    for row in range(9):
        for col in range(9):
            if board[row][col] == 0:  # 빈 칸은 0으로 표시됨
                return (row, col)
    return None


def is_valid(board, row, col, num):
    # 행 확인
    if num in board[row]:
        return False

    # 열 확인
    if num in [board[i][col] for i in range(9)]:
        return False

    # 3x3 박스 확인
    box_row = row // 3 * 3
    box_col = col // 3 * 3
    for i in range(3):
        for j in range(3):
            if board[box_row + i][box_col + j] == num:
                return False

    return True


def print_board(board):
    for row in board:
        print(" ".join(str(num) if num != 0 else "." for num in row))


# 테스트용 스도쿠 퍼즐 (0은 빈 칸을 의미)
sudoku_board = [
    [5, 3, 0, 0, 7, 0, 0, 0, 0],
    [6, 0, 0, 1, 9, 5, 0, 0, 0],
    [0, 9, 8, 0, 0, 0, 0, 6, 0],
    [8, 0, 0, 0, 6, 0, 0, 0, 3],
    [4, 0, 0, 8, 0, 3, 0, 0, 1],
    [7, 0, 0, 0, 2, 0, 0, 0, 6],
    [0, 6, 0, 0, 0, 0, 2, 8, 0],
    [0, 0, 0, 4, 1, 9, 0, 0, 5],
    [0, 0, 0, 0, 8, 0, 0, 7, 9],
]

print("Original Sudoku Board:")
print_board(sudoku_board)

if solve_sudoku(sudoku_board):
    print("\nSolved Sudoku Board:")
    print_board(sudoku_board)
else:
    print("\nNo solution exists!")

```
</details>

# 그리디 알고리즘 (Greedy Algorithm)

## 개념 및 특징

**정의:**
- 현재 단계에서 가장 최적의 선택(최선의 해)을 하여 전체 문제를 해결하는 알고리즘 설계 기법

**특징:**
- 문제를 단계별로 해결하며, 각 단계에서 최적의 선택을 함
- 선택이 현재뿐만 아니라 전체 문제에 대해서도 최적의 해를 보장해야 함
- 일반적으로 지역 최적해(Local Optimal Solution)를 통해 전역 최적해(Global Optimal Solution)를 도출

**장점:**
- 구현이 간단하고 빠름
- 특정 조건을 만족하는 문제에서 매우 효율적

**단점:**
- 문제에 따라 최적해를 보장하지 못할 수 있음
- 선택이 전역 최적해를 보장하는지 확인 필요

**활용:**
- 네트워크 설계, 자원 할당 문제, 경로 탐색 등

---

## 대표 문제

### 동전 거슬러 주기 (Coin Change Problem)

**정의:**
- 거스름돈을 최소 개수의 동전으로 반환하는 문제

**동작 방식:**
1. 가장 큰 가치의 동전부터 선택
2. 남은 금액에 대해 반복적으로 수행
3. 금액이 0이 될 때까지 반복

**특징:**
- 사용되는 동전의 종류에 따라 최적해를 보장하지 못할 수 있음

**장점:**
- 간단하고 직관적

**단점:**
- 특정 동전 조합에서는 최적해가 되지 않을 수 있음

**실습 코드**
<details>
<summary>Coin Change Problem - python</summary>

```python
def coin_change_greedy(amount, coins):
    # 큰 단위의 동전부터 사용하기 위해 내림차순 정렬
    coins.sort(reverse=True)

    result = {}
    for coin in coins:
        if amount >= coin:
            count = amount // coin  # 해당 동전으로 거슬러 줄 수 있는 개수
            result[coin] = count
            amount %= coin  # 남은 금액 계산

    # 남은 금액이 0이 아니면 거슬러 줄 수 없는 경우
    if amount != 0:
        return "Cannot give exact change"

    return result

# 테스트
coins = [500, 100, 50, 10]  # 동전 단위
amount = 2190  # 거슬러 줄 금액

result = coin_change_greedy(amount, coins)
print("Change for", amount, ":", result)
```
</details>

---

### 활동 선택 문제 (Activity Selection Problem)

**정의:**
- 주어진 활동들 중에서 서로 겹치지 않으면서 최대한 많은 활동을 선택하는 문제

**동작 방식:**
1. 활동들을 종료 시간이 빠른 순서로 정렬
2. 가장 먼저 끝나는 활동을 선택
3. 선택한 활동과 겹치지 않는 다음 활동을 반복적으로 선택

**특징:**
- 그리디 선택 조건을 만족하므로 최적해 보장

**장점:**
- 효율적으로 최대 활동 개수를 선택 가능

**단점:**
- 정렬 과정이 필요하여 초기 오버헤드 발생 가능

**실습 코드**
<details>
<summary>Activity Selection Probelm - python</summary>

```python
def activity_selection(activities):
    # 종료 시간을 기준으로 활동 정렬
    activities.sort(key=lambda x: x[1])

    selected_activities = []  # 선택된 활동 저장
    last_end_time = 0  # 마지막으로 선택된 활동의 종료 시간

    for activity in activities:
        start, end = activity
        # 현재 활동이 마지막으로 선택된 활동과 겹치지 않는 경우 선택
        if start >= last_end_time:
            selected_activities.append(activity)
            last_end_time = end

    return selected_activities

# 테스트
activities = [
    (1, 4),  # 활동 1: 시작 시간 1, 종료 시간 4
    (3, 5),  # 활동 2
    (0, 6),  # 활동 3
    (5, 7),  # 활동 4
    (3, 8),  # 활동 5
    (5, 9),  # 활동 6
    (6, 10), # 활동 7
    (8, 11), # 활동 8
    (8, 12), # 활동 9
    (2, 13), # 활동 10
    (12, 14) # 활동 11
]

result = activity_selection(activities)
print("Selected activities:", result)
```
</details>

---

### 최소 신장 트리 (MST: Minimum Spanning Tree)

**정의:**
- 그래프에서 모든 정점을 연결하면서 간선 가중치의 합이 최소가 되는 트리를 찾는 문제
![mst](./image/9.png)
>위 그림은 간선의 가중치의 합이 최소가 되도록 찾는 과정을 보여줌 

#### 크루스칼 알고리즘 (Kruskal's Algorithm)

**동작 방식:**
1. 모든 간선을 가중치의 오름차순으로 정렬
2. 최소 가중치 간선부터 선택하며 사이클이 발생하지 않도록 추가
3. 트리의 간선 수가 (정점 수 - 1)이 될 때까지 반복

**특징:**
- 간선 중심 접근 방식
- 시간복잡도: O(E log E) (E: 간선 수)

**장점:**
- 간선이 적은 그래프에 유리

**단점:**
- 간선 정렬 과정이 필요

![krus](./image/10.png)
>위 그림은 기존 트리에서 가중치가 작은 것부터 선택하여 트리를 완성하는 과정을 보여줌 

#### 프림 알고리즘 (Prim's Algorithm)

**동작 방식:**
1. 임의의 정점을 시작 정점으로 선택
2. 선택한 정점에 연결된 간선 중 최소 가중치 간선을 선택하여 트리에 추가
3. 모든 정점을 포함할 때까지 반복

**특징:**
- 정점 중심 접근 방식
- 시간복잡도: O(E + V log V) (V: 정점 수)

**장점:**
- 정점이 많은 밀집 그래프에 유리

**단점:**
- 우선순위 큐를 사용해야 효율적임

![prim](./image/11.png)
>위 그림은 정점하나를 기준으로 트리를 만들어나가는 과정을 보여줌 

---

### 허프만 코딩 (Huffman Coding)

**정의:**
- 데이터 압축을 위해 사용되는 알고리즘으로, 문자 빈도수를 기준으로 최적의 이진 트리를 생성하여 각 문자에 고유한 접두사 코드(prefix code)를 할당

**동작 방식:**
1. 각 문자의 빈도를 우선순위 큐에 삽입
2. 빈도가 가장 낮은 두 노드를 합쳐 새로운 노드를 생성
3. 새 노드를 큐에 삽입하고 반복하여 트리를 생성
4. 트리의 각 리프 노드에 고유한 이진 코드를 할당

**특징:**
- 손실 없는 데이터 압축 방식
- 접두사 코드로 디코딩 과정이 간단함

**장점:**
- 압축 효율이 높음
- 구현이 비교적 간단함

**단점:**
- 빈도가 균일한 데이터에서는 큰 효과를 보지 못함

**활용:**
- 파일 압축, 데이터 전송 최적화
---
# 동적 계획법 (Dynamic Programming)

## 기본 개념

**정의:**
- 복잡한 문제를 작은 하위 문제로 나누어 해결하며, 동일한 하위 문제를 반복적으로 계산하지 않도록 결과를 저장하여 효율적으로 해결하는 알고리즘 기법

**특징:**
- 최적 부분 구조(Optimal Substructure): 문제의 최적해가 하위 문제의 최적해로 구성됨
- 중복되는 하위 문제(Overlapping Subproblems): 동일한 하위 문제가 여러 번 계산됨
- 메모리 사용 증가와 실행 시간 감소의 트레이드오프

**장점:**
- 계산량을 줄여 효율적
- 중복 계산 방지로 실행 시간 감소

**단점:**
- 메모리 사용량 증가
- 문제에 따라 최적 부분 구조가 성립하지 않을 수 있음

**활용:**
- 최단 경로 계산, 문자열 비교, 수열 문제 해결 등

---

### 메모이제이션 (Memoization)

**정의:**
- 재귀를 활용하며, 계산 결과를 캐시에 저장하여 동일한 계산을 반복하지 않도록 하는 방식

**동작 방식:**
1. 함수 호출 시 캐시에 값이 저장되어 있는지 확인
2. 값이 없으면 계산하여 캐시에 저장
3. 값이 있으면 저장된 값 반환

**특징:**
- Top-Down 방식
- 재귀를 활용하므로 함수 호출 오버헤드가 발생

**장점:**
- 코드가 간결하고 직관적

**단점:**
- 호출 스택 사용으로 메모리 낭비 가능

**활용:**
- 피보나치 수열, 최장 공통 부분 수열 등

---

### 타뷸레이션 (Tabulation)

**정의:**
- 반복문을 사용하여 하위 문제의 결과를 테이블에 저장하며 점진적으로 전체 문제를 해결하는 방식

**동작 방식:**
1. 가장 작은 하위 문제부터 해결
2. 결과를 테이블에 저장
3. 저장된 값을 사용하여 더 큰 문제 해결

**특징:**
- Bottom-Up 방식
- 재귀 호출 없이 반복문으로 구현

**장점:**
- 호출 스택 오버헤드 제거
- 메모리 사용 효율적

**단점:**
- 테이블 초기화 및 관리가 필요

**활용:**
- 피보나치 수열, 배낭 문제 등

---

## 대표 문제

### 피보나치 수열

**정의:**
- 피보나치 수열은 첫 번째와 두 번째 수가 1이며, 이후의 수는 바로 앞 두 수의 합으로 정의됨

**동작 방식:**
1. 첫 번째와 두 번째 값을 초기화
2. 이전 두 값의 합을 계산하여 결과 테이블에 저장
3. 원하는 항까지 반복

**특징:**
- 메모이제이션 또는 타뷸레이션을 사용하여 계산 효율화

**장점:**
- 중복 계산 제거로 빠른 수행 시간

**단점:**
- 추가적인 메모리 사용

**활용:**
- 재귀와 반복 구현 비교, 수학적 문제 해결

**실습 코드**
<details>
<summary>Fibonacci - python</summary>

```python
def fibonacci_memo(n, memo={}):
    if n in memo:  # 이미 계산된 결과가 있으면 반환
        return memo[n]
    if n <= 1:  # 기본 케이스
        return n
    # 재귀적으로 계산하고 결과를 메모에 저장
    memo[n] = fibonacci_memo(n - 1, memo) + fibonacci_memo(n - 2, memo)
    return memo[n]

def fibonacci_bottom_up(n):
    if n <= 1:
        return n
    # DP 배열 생성
    dp = [0] * (n + 1)
    dp[1] = 1
    for i in range(2, n + 1):
        dp[i] = dp[i - 1] + dp[i - 2]  # 이전 두 값의 합
    return dp[n]

# 테스트
n = 10
print(f"Fibonacci({n}) =", fibonacci_bottom_up(n))
print(f"Fibonacci({n}) =", fibonacci_memo(n))
```
</details>

---

### 배낭 문제 (Knapsack Problem)

**정의:**
- 주어진 무게와 가치의 물품들 중에서, 배낭의 최대 무게를 초과하지 않으면서 최대 가치를 얻도록 선택하는 문제

**동작 방식:**
1. 물품의 무게와 가치를 테이블로 정리
2. 각 물품을 포함하거나 포함하지 않는 경우를 계산
3. 최대 가치를 찾도록 테이블 갱신

**특징:**
- 0/1 배낭 문제는 동적 계획법으로 해결 가능
- 시간복잡도: O(nW) (n: 물품 수, W: 배낭 용량)

**장점:**
- 최적해 보장

**단점:**
- 메모리와 시간 자원 소모 큼

**활용:**
- 자원 최적화, 비용 최소화 문제

**실습 코드**
<details>
<summary>Kanpsack - python</summary>

```python
def knapsack(values, weights, capacity):
    n = len(values)  # 물건 개수
    # DP 테이블 초기화 (크기: (n+1) x (capacity+1))
    dp = [[0] * (capacity + 1) for _ in range(n + 1)]

    # DP 계산
    for i in range(1, n + 1):
        for w in range(1, capacity + 1):
            if weights[i - 1] <= w:  # 현재 물건을 배낭에 넣을 수 있는 경우
                dp[i][w] = max(
                    dp[i - 1][w],  # 물건을 넣지 않는 경우
                    dp[i - 1][w - weights[i - 1]] + values[i - 1]  # 물건을 넣는 경우
                )
            else:
                dp[i][w] = dp[i - 1][w]  # 물건을 넣을 수 없는 경우

    return dp[n][capacity]

# 테스트
values = [60, 100, 120]  # 물건 가치
weights = [10, 20, 30]  # 물건 무게
capacity = 50  # 배낭 용량

result = knapsack(values, weights, capacity)
print("Maximum value:", result)
```
</details>

---

### 최장 공통 부분 수열 (LCS: Longest Common Subsequence)

**정의:**
- 두 문자열에서 순서를 유지하며 공통으로 나타나는 가장 긴 부분 수열을 찾는 문제

**동작 방식:**
1. 두 문자열의 길이를 기준으로 2차원 테이블 생성
2. 각 문자 비교하며 테이블 갱신
3. 테이블의 마지막 값이 최장 공통 부분 수열의 길이

**특징:**
- 시간복잡도: O(nm) (n, m: 문자열 길이)
- 공간복잡도: O(nm)

**장점:**
- 최적해 보장

**단점:**
- 테이블 크기에 따른 메모리 사용량 증가

**활용:**
- DNA 서열 분석, 텍스트 편집기 구현

**실습 코드**
<details>
<summary>LSC - python</summary>

```python
def lcs(s1, s2):
    m, n = len(s1), len(s2)
    # DP 테이블 생성 (크기: (m+1) x (n+1))
    dp = [[0] * (n + 1) for _ in range(m + 1)]

    # DP 테이블 채우기
    for i in range(1, m + 1):
        for j in range(1, n + 1):
            if s1[i - 1] == s2[j - 1]:  # 문자가 같으면
                dp[i][j] = dp[i - 1][j - 1] + 1
            else:  # 문자가 다르면
                dp[i][j] = max(dp[i - 1][j], dp[i][j - 1])

    # LCS 길이 반환
    return dp[m][n], dp

def reconstruct_lcs(s1, s2, dp):
    i, j = len(s1), len(s2)
    lcs_str = []

    # DP 테이블을 역추적하여 LCS 문자열 복원
    while i > 0 and j > 0:
        if s1[i - 1] == s2[j - 1]:  # 문자가 같으면 LCS에 포함
            lcs_str.append(s1[i - 1])
            i -= 1
            j -= 1
        elif dp[i - 1][j] > dp[i][j - 1]:  # 위쪽 값이 더 크면 위로 이동
            i -= 1
        else:  # 왼쪽 값이 더 크면 왼쪽으로 이동
            j -= 1

    return ''.join(reversed(lcs_str))

# 테스트
s1 = "AGGTAB"
s2 = "GXTXAYB"

lcs_length, dp_table = lcs(s1, s2)
lcs_string = reconstruct_lcs(s1, s2, dp_table)

print("Length of LCS:", lcs_length)
print("LCS:", lcs_string)
```
</details>

---

### 최장 증가 부분 수열 (LIS: Longest Increasing Subsequence)

**정의:**
- 주어진 수열에서 증가하는 부분 수열 중 가장 긴 수열을 찾는 문제

**동작 방식:**
1. 각 요소를 기준으로 이전 요소들과 비교
2. 증가하는 관계를 만족하면 현재까지의 최대 길이 갱신
3. 전체 수열 탐색 후 최댓값 반환

**특징:**
- 시간복잡도: O(n^2) 또는 O(n log n) (이진 탐색 활용 시)

**장점:**
- 증가하는 수열의 최적해 계산 가능

**단점:**
- O(n^2) 알고리즘은 큰 입력 데이터에 비효율적

**활용:**
- 데이터 분석, 패턴 인식

**실습 코드**
<details>
<summary></summary>

```python
def lis(arr):
    n = len(arr)
    dp = [1] * n  # 각 요소에서의 LIS 길이를 저장

    # LIS 계산
    for i in range(1, n):
        for j in range(i):
            if arr[i] > arr[j]:  # 증가하는 관계일 경우
                dp[i] = max(dp[i], dp[j] + 1)

    return max(dp)  # LIS의 최대 길이 반환

# 테스트
data = [10, 22, 9, 33, 21, 50, 41, 60, 80]
print("Array:", data)
print("Length of LIS:", lis(data))
```
</details>

---

### 최단 경로 알고리즘 (예: Floyd-Warshall)

**정의:**
- 그래프에서 모든 정점 간 최단 경로를 찾는 알고리즘

**동작 방식:**
1. 정점 간 거리를 행렬 형태로 초기화
2. 모든 정점을 중간 경로로 고려하며 최단 경로 갱신
3. 모든 정점 쌍에 대해 반복 수행

**특징:**
- 시간복잡도: O(n^3) (n: 정점 수)
- 음수 가중치를 처리 가능

**장점:**
- 모든 정점 간 최단 경로 계산 가능

**단점:**
- 큰 그래프에서는 실행 시간이 오래 걸릴 수 있음

**활용:**
- 네트워크 경로 최적화, 지도 데이터 처리
---
# 그래프 알고리즘 (Graph Algorithms)

## 탐색

### 깊이 우선 탐색 (DFS: Depth-First Search)

**정의:**
- 그래프에서 한 경로를 가능한 깊이까지 탐색한 후, 다른 경로를 탐색하는 방식

**특징:**
- 스택 또는 재귀를 사용
- 시간복잡도: O(V + E) (V: 정점 수, E: 간선 수)

**동작 방식:**
1. 시작 정점에서 탐색 시작
2. 방문한 정점을 스택에 추가
3. 인접한 정점 중 방문하지 않은 정점으로 이동
4. 더 이상 이동할 정점이 없으면 스택에서 꺼내 이전 정점으로 돌아감

**장점:**
- 경로 탐색 및 연결 요소 검출에 유리

**단점:**
- 최단 경로를 보장하지 않음

**활용:**
- 미로 찾기, 사이클 검출, 강연결 요소 탐색

![dfs](./image/12.png)
>위 그림은 가장 상단 트리에서 부터 가장 하단 트리까지 도달하는 과정을 보여줌 

---

### 너비 우선 탐색 (BFS: Breadth-First Search)

**정의:**
- 시작 정점에서 가까운 정점부터 탐색을 진행하는 방식

**특징:**
- 큐를 사용
- 시간복잡도: O(V + E)

**동작 방식:**
1. 시작 정점을 큐에 추가하고 방문 표시
2. 큐에서 정점을 꺼내 인접한 정점을 모두 큐에 추가
3. 모든 정점을 방문할 때까지 반복

**장점:**
- 최단 경로 보장

**단점:**
- 메모리 사용량이 많을 수 있음

**활용:**
- 최단 경로 탐색, 레벨별 탐색

![bfs](./image/13.png)
>위 그림은 가장 왼쪽 트리부터 가장 오른쪽 트리까지 도달하는 과정을 보여줌 

---

## 최단 경로

### 다익스트라 알고리즘 (Dijkstra's Algorithm)

**정의:**
- 가중치가 양수인 그래프에서 특정 시작 정점으로부터 모든 정점까지의 최단 경로를 찾는 알고리즘

**특징:**
- 우선순위 큐 사용
- 시간복잡도: O(V log V + E)

**동작 방식:**
1. 시작 정점을 초기화하고, 나머지 정점의 거리를 무한대로 설정
2. 우선순위 큐에서 최소 거리를 가진 정점을 선택
3. 선택된 정점의 인접 정점을 탐색하며 거리 갱신
4. 모든 정점을 처리할 때까지 반복

**장점:**
- 효율적으로 최단 경로 계산

**단점:**
- 음수 가중치 처리 불가

**활용:**
- 네트워크 경로 최적화, 지도 데이터 처리

---

### 벨만-포드 알고리즘 (Bellman-Ford Algorithm)

**정의:**
- 음수 가중치를 포함한 그래프에서도 최단 경로를 찾는 알고리즘

**특징:**
- 간선 중심으로 동작
- 시간복잡도: O(VE)

**동작 방식:**
1. 모든 간선을 반복적으로 확인하며 거리 갱신
2. 음수 사이클이 존재하면 이를 감지

**장점:**
- 음수 가중치 처리 가능

**단점:**
- 다익스트라 알고리즘보다 느림

**활용:**
- 금융 네트워크 분석, 음수 비용 경로 탐색

---

### 플로이드-워셜 알고리즘 (Floyd-Warshall Algorithm)

**정의:**
- 그래프에서 모든 정점 쌍 간 최단 경로를 찾는 알고리즘

**특징:**
- 동적 계획법 기반
- 시간복잡도: O(V^3)

**동작 방식:**
1. 정점 간 초기 거리를 행렬로 설정
2. 모든 정점을 중간 경로로 사용하며 최단 거리 갱신

**장점:**
- 모든 정점 간 최단 경로 계산 가능

**단점:**
- 큰 그래프에서 비효율적

**활용:**
- 네트워크 경로 최적화, 물류 경로 분석

---

## 최소 신장 트리 (Minimum Spanning Tree)

### 크루스칼 알고리즘 (Kruskal's Algorithm)

**정의:**
- 간선을 정렬하여 최소 가중치 간선을 추가하며 MST를 생성하는 알고리즘

**특징:**
- 간선 중심 접근 방식
- 시간복잡도: O(E log E)

**동작 방식:**
1. 모든 간선을 가중치 오름차순으로 정렬
2. 최소 가중치 간선부터 선택하며 사이클이 발생하지 않도록 추가
3. MST가 완성될 때까지 반복

**장점:**
- 간선이 적은 그래프에 유리

**단점:**
- 간선 정렬이 필요

**활용:**
- 네트워크 설계, 클러스터링

**실습 코드**
<details>
<summary>Kruskal problem - python</summary>

```python
class DisjointSet:
    def __init__(self, vertices):
        self.parent = {v: v for v in vertices}
        self.rank = {v: 0 for v in vertices}

    def find(self, vertex):
        if self.parent[vertex] != vertex:
            self.parent[vertex] = self.find(self.parent[vertex])  # 경로 압축
        return self.parent[vertex]

    def union(self, u, v):
        root_u = self.find(u)
        root_v = self.find(v)

        if root_u != root_v:
            if self.rank[root_u] > self.rank[root_v]:
                self.parent[root_v] = root_u
            elif self.rank[root_u] < self.rank[root_v]:
                self.parent[root_u] = root_v
            else:
                self.parent[root_v] = root_u
                self.rank[root_u] += 1

def kruskal(graph, vertices):
    edges = []
    for u in graph:
        for v, weight in graph[u]:
            edges.append((weight, u, v))

    # 간선을 가중치 기준으로 정렬
    edges.sort()

    ds = DisjointSet(vertices)
    mst = []

    for weight, u, v in edges:
        if ds.find(u) != ds.find(v):
            ds.union(u, v)
            mst.append((u, v, weight))

    return mst

# 테스트
graph = {
    0: [(1, 4), (7, 8)],
    1: [(0, 4), (2, 8), (7, 11)],
    2: [(1, 8), (3, 7), (8, 2), (5, 4)],
    3: [(2, 7), (4, 9), (5, 14)],
    4: [(3, 9), (5, 10)],
    5: [(4, 10), (3, 14), (2, 4), (6, 2)],
    6: [(5, 2), (8, 6), (7, 1)],
    7: [(0, 8), (1, 11), (6, 1), (8, 7)],
    8: [(2, 2), (6, 6), (7, 7)],
}
vertices = list(graph.keys())

mst = kruskal(graph, vertices)
print("Kruskal's MST:", mst)
```
</details>

---

### 프림 알고리즘 (Prim's Algorithm)

**정의:**
- 정점을 확장하며 MST를 생성하는 알고리즘

**특징:**
- 정점 중심 접근 방식
- 시간복잡도: O(E + V log V)

**동작 방식:**
1. 임의의 시작 정점을 선택
2. 선택된 정점과 연결된 간선 중 최소 가중치를 가진 간선을 선택
3. 모든 정점이 포함될 때까지 반복

**장점:**
- 정점이 많은 밀집 그래프에 유리

**단점:**
- 우선순위 큐 필요

**활용:**
- 통신 네트워크 설계, 전력망 설계

**실습 코드**
<details>
<summary>Prim problem - python</summary>

```python
import heapq

def prim(graph, start):
    mst = []  # 최소 신장 트리의 간선
    visited = set()  # 방문한 노드
    min_heap = [(0, start, None)]  # (가중치, 현재 노드, 이전 노드)

    while min_heap:
        weight, current, previous = heapq.heappop(min_heap)
        if current in visited:
            continue

        visited.add(current)
        if previous is not None:
            mst.append((previous, current, weight))

        # 현재 노드에 연결된 모든 간선을 확인
        for neighbor, edge_weight in graph[current]:
            if neighbor not in visited:
                heapq.heappush(min_heap, (edge_weight, neighbor, current))

    return mst

# 테스트
graph = {
    0: [(1, 4), (7, 8)],
    1: [(0, 4), (2, 8), (7, 11)],
    2: [(1, 8), (3, 7), (8, 2), (5, 4)],
    3: [(2, 7), (4, 9), (5, 14)],
    4: [(3, 9), (5, 10)],
    5: [(4, 10), (3, 14), (2, 4), (6, 2)],
    6: [(5, 2), (8, 6), (7, 1)],
    7: [(0, 8), (1, 11), (6, 1), (8, 7)],
    8: [(2, 2), (6, 6), (7, 7)],
}

mst = prim(graph, 0)
print("Prim's MST:", mst)
```
</details>

---

## 네트워크 플로우 (Network Flow)

### 에드몬드-카프 알고리즘 (Edmonds-Karp Algorithm)

**정의:**
- 최대 유량 문제를 해결하는 알고리즘으로, BFS를 사용하여 증가 경로를 찾음

**특징:**
- 시간복잡도: O(VE^2)

**동작 방식:**
1. 초기 유량을 0으로 설정
2. BFS를 사용해 증가 경로를 찾음
3. 경로의 최소 잔여 용량만큼 유량을 추가
4. 더 이상 경로가 없을 때 종료

**장점:**
- 구현이 비교적 간단

**단점:**
- 큰 그래프에서 비효율적

**활용:**
- 물류 네트워크, 전송 네트워크 설계

---

### 푸시-재명칭 알고리즘 (Push-relabel Algorithm)

**정의:**
- 정점 기반의 최대 유량 계산 알고리즘

**특징:**
- 시간복잡도: O(V^2E)

**동작 방식:**
1. 초기 유량 설정
2. 정점에 잔여 용량이 있으면 푸시 또는 재명칭 수행
3. 잔여 용량이 더 이상 없을 때 종료

**장점:**
- 높은 유량 계산 효율성

**단점:**
- 구현 복잡

**활용:**
- 물류 최적화, 통신 네트워크

---

## 위상 정렬 (Topological Sorting)

**정의:**
- 방향 그래프에서 정점들을 선형 순서로 정렬하는 알고리즘으로, 각 간선이 u -> v일 때 u가 v보다 앞에 위치

**특징:**
- 사이클이 없는 방향 그래프(DAG)에서만 적용 가능
- 시간복잡도: O(V + E)

**동작 방식:**
1. 진입 차수가 0인 정점을 큐에 추가
2. 큐에서 정점을 꺼내 연결된 간선을 제거
3. 진입 차수가 0이 된 정점을 큐에 추가
4. 모든 정점이 처리될 때까지 반복

**장점:**
- 간단하고 효율적

**단점:**
- 사이클이 있는 그래프에서는 적용 불가

**활용:**
- 작업 스케줄링, 종속성 분석

---

# 문자열 알고리즘 (String Algorithms)

## 문자열 검색

### KMP 알고리즘 (Knuth-Morris-Pratt Algorithm)

**정의:**
- 부분 문자열 검색 문제를 효율적으로 해결하기 위한 알고리즘으로, 접두사와 접미사를 활용해 불필요한 비교를 줄임

**특징:**
- 시간복잡도: O(n + m) (n: 본문 문자열 길이, m: 패턴 문자열 길이)
- 접두사와 접미사를 이용한 테이블(Prefix Table)을 활용

**동작 방식:**
1. 패턴 문자열의 접두사와 접미사가 일치하는 길이를 기록한 Prefix Table 생성
2. 본문 문자열에서 패턴 문자열을 탐색하며, 불일치 시 Prefix Table을 참고하여 이동
3. 일치하는 패턴을 찾으면 종료

**장점:**
- 반복적인 비교를 줄여 효율적

**단점:**
- Prefix Table 생성 단계에서 추가적인 메모리 사용

**활용:**
- 텍스트 에디터 검색 기능, 문자열 매칭 문제

---

### 라빈-카프 알고리즘 (Rabin-Karp Algorithm)

**정의:**
- 해시 함수를 이용하여 부분 문자열 검색을 수행하는 알고리즘

**특징:**
- 시간복잡도: O(n + m) (평균), O(nm) (최악, 해시 충돌 발생 시)
- 문자열의 해시값을 비교하여 빠르게 검색

**동작 방식:**
1. 패턴 문자열과 본문 문자열의 초기 해시값 계산
2. 본문 문자열에서 슬라이딩 윈도우 방식으로 해시값 비교
3. 해시값이 일치하면 실제 문자열 비교

**장점:**
- 해시 충돌이 적은 경우 효율적

**단점:**
- 해시 충돌 발생 시 성능 저하

**활용:**
- 문자열 검색, DNA 서열 분석

---

## 접미사 배열 및 트라이

### 접미사 배열 (Suffix Array)

**정의:**
- 문자열의 모든 접미사를 사전순으로 정렬한 배열

**특징:**
- 시간복잡도: O(n log n) (구현에 따라 상이함)
- 문자열의 정렬된 접미사에 대한 인덱스를 저장

**동작 방식:**
1. 문자열의 모든 접미사 생성
2. 접미사를 사전순으로 정렬
3. 정렬된 접미사의 시작 위치를 저장

**장점:**
- 공간 효율적

**단점:**
- 정렬 과정에서 추가적인 계산 필요

**활용:**
- 문자열 검색, 문자열 유사도 계산

---

### 접미사 트리 (Suffix Tree)

**정의:**
- 문자열의 모든 접미사를 트리 구조로 표현한 자료구조

**특징:**
- 시간복잡도: O(n)
- 중복된 접미사를 효율적으로 표현

**동작 방식:**
1. 문자열의 각 접미사를 트리에 삽입
2. 공통 접두사는 노드로 병합

**장점:**
- 서브 문자열 검색이 매우 빠름

**단점:**
- 메모리 사용량이 많음

**활용:**
- 서브 문자열 검색, 반복 패턴 탐지

---

## 롤링 해시 및 Z-알고리즘

### 롤링 해시 (Rolling Hash)

**정의:**
- 슬라이딩 윈도우 방식으로 문자열의 해시값을 계산하며 검색을 최적화하는 방법

**특징:**
- 시간복잡도: O(n + m)
- 이전 윈도우의 해시값을 활용하여 새 해시값 계산

**동작 방식:**
1. 초기 윈도우의 해시값 계산
2. 윈도우를 한 칸 이동하며 새로운 해시값 갱신
3. 패턴과 해시값이 일치하면 실제 문자열 비교

**장점:**
- 해시 재계산이 빠름

**단점:**
- 충돌이 발생할 수 있음

**활용:**
- 문자열 검색, Rabin-Karp 알고리즘과 결합

---

### Z-알고리즘 (Z-Algorithm)

**정의:**
- 문자열의 접두사가 해당 문자열의 다른 위치에서 얼마나 일치하는지 계산하는 알고리즘

**특징:**
- 시간복잡도: O(n)
- Z 배열을 이용하여 접두사 매칭 정보를 저장

**동작 방식:**
1. Z 배열을 생성하여 각 위치에서 접두사 매칭 길이 계산
2. Z 배열을 활용하여 패턴 검색 수행

**장점:**
- 문자열 검색을 빠르게 수행

**단점:**
- 구현이 다소 복잡

**활용:**
- 문자열 패턴 검색, 텍스트 유사도 분석

---

# 수학 및 수치 알고리즘 (Mathematical and Numerical Algorithms)

## 기초 수학 알고리즘

### 유클리드 호제법 (Greatest Common Divisor, GCD)

**정의:**
- 두 정수의 최대공약수를 구하는 알고리즘으로, 나눗셈을 반복하여 계산

**특징:**
- 시간복잡도: O(log(min(a, b)))
- 반복적인 나머지 계산을 통해 최대공약수 도출

**동작 방식:**
1. 두 정수 a와 b 중 b가 0이 될 때까지 나머지를 반복 계산
2. b가 0이 되면, a가 최대공약수

**장점:**
- 간단하고 효율적

**단점:**
- 큰 정수 계산에서는 나머지 계산 비용이 증가

**활용:**
- 분수의 기약분수 변환, 정수론 문제 해결

---

### 소수 판별 (Primality Testing)

**정의:**
- 주어진 수가 소수인지 확인하는 알고리즘

**특징:**
- 시간복잡도: O(√n) (단순 구현)
- 소수는 1과 자기 자신만을 약수로 가짐

**동작 방식:**
1. 2부터 √n까지의 모든 수로 나누어 떨어지는지 확인
2. 나누어 떨어지지 않으면 소수

**장점:**
- 간단한 구현 가능

**단점:**
- 큰 수에 대해 비효율적

**활용:**
- 암호학, 소수 생성

---

### 에라토스테네스의 체 (Sieve of Eratosthenes)

**정의:**
- 특정 범위 내 모든 소수를 효율적으로 찾는 알고리즘

**특징:**
- 시간복잡도: O(n log log n)
- 체를 사용하여 소수가 아닌 수를 제거

**동작 방식:**
1. 2부터 시작하여 해당 수의 배수를 제거
2. √n 이하의 모든 수에 대해 반복
3. 남은 수가 소수

**장점:**
- 대량의 소수를 효율적으로 계산 가능

**단점:**
- 추가 메모리 사용

**활용:**
- 소수 집합 생성, 암호학

---

## 모듈러 연산

### 빠른 거듭제곱 (Fast Exponentiation)

**정의:**
- 거듭제곱 연산을 분할 정복 방식으로 빠르게 계산하는 알고리즘

**특징:**
- 시간복잡도: O(log n)
- 모듈러 연산을 병행하여 오버플로우 방지 가능

**동작 방식:**
1. 지수를 절반으로 나누어 재귀적으로 계산
2. 지수가 짝수이면 결과를 제곱
3. 지수가 홀수이면 추가 곱셈 수행

**장점:**
- 큰 수의 계산 효율적

**단점:**
- 재귀 호출로 인한 스택 사용 증가 가능

**활용:**
- 암호학, 모듈러 계산

---

### 중국인의 나머지 정리 (Chinese Remainder Theorem)

**정의:**
- 여러 모듈러 방정식의 해를 구하는 알고리즘

**특징:**
- 각 방정식의 모듈러 값이 서로소일 때 적용 가능

**동작 방식:**
1. 각 방정식의 해를 독립적으로 계산
2. 결과를 병합하여 하나의 해로 표현

**장점:**
- 모듈러 연산을 병렬로 처리 가능

**단점:**
- 조건(서로소 모듈러)이 만족되지 않으면 적용 불가

**활용:**
- 암호학, 주기 계산

---

## 행렬 연산 (Matrix Operations)

### 기본 행렬 연산

**정의:**
- 행렬의 덧셈, 곱셈, 전치, 역행렬 등을 포함하는 연산

**특징:**
- 행렬 곱셈의 일반적 시간복잡도: O(n^3)
- Strassen 알고리즘 등의 고급 방법으로 개선 가능

**동작 방식:**
1. 행렬 곱셈: 각 행과 열의 원소를 곱한 후 합산
2. 전치 행렬: 행과 열을 교환
3. 역행렬: 가우스-조던 소거법 등으로 계산

**장점:**
- 다양한 수치 계산 문제 해결 가능

**단점:**
- 고차원 행렬에서 계산 비용 증가

**활용:**
- 그래픽스, 선형대수, 데이터 분석

---

# 조합 및 확률 (Combinatorics and Probability)

## 조합론

### 순열 (Permutation) 및 조합 (Combination)

**정의:**
- 순열: 주어진 원소를 순서에 따라 배열하는 경우의 수
- 조합: 주어진 원소를 순서에 상관없이 선택하는 경우의 수

**특징:**
- 순열의 경우의 수: n! / (n - r)!
- 조합의 경우의 수: n! / (r! * (n - r)!)

**동작 방식:**
1. 순열: 순서가 중요한 경우로 각 위치에 올 수 있는 원소를 차례로 배치
2. 조합: 순서가 중요하지 않은 경우로 중복 없이 선택

**장점:**
- 다양한 문제에서 경우의 수 계산 가능

**단점:**
- 큰 입력에서 계산 비용 증가

**활용:**
- 통계, 확률 문제, 최적화 문제

---

### 비트마스크를 활용한 부분집합 생성

**정의:**
- 이진수를 사용하여 집합의 각 원소의 포함 여부를 표현

**특징:**
- 시간복잡도: O(2^n) (n: 집합의 크기)
- 모든 부분집합을 효율적으로 생성 가능

**동작 방식:**
1. 집합의 크기 n에 대해 0부터 2^n - 1까지의 이진수를 생성
2. 각 이진수의 비트가 1인 경우 해당 원소를 포함

**장점:**
- 부분집합 생성 과정이 간단

**단점:**
- 입력 크기가 클 경우 비효율적

**활용:**
- 부분집합 합 문제, 조합 생성

---

## 확률 기반 알고리즘

### 몬테카를로 시뮬레이션 (Monte Carlo Simulation)

**정의:**
- 난수를 활용하여 문제를 반복적으로 시뮬레이션하여 결과를 추정하는 알고리즘

**특징:**
- 정확한 결과가 아닌 근사치를 계산
- 반복 횟수에 따라 정확도 향상

**동작 방식:**
1. 문제를 확률적 모델로 변환
2. 난수를 생성하여 모델에 입력
3. 결과를 관찰하고 평균값을 계산

**장점:**
- 복잡한 문제를 근사적으로 해결 가능

**단점:**
- 반복 횟수에 따라 계산 비용 증가

**활용:**
- 금융 리스크 분석, 과학적 계산, 게임 이론

---

### 랜덤화 알고리즘 (Randomized Algorithms)

**정의:**
- 알고리즘 내에 난수를 도입하여 평균적 성능을 향상시키는 알고리즘

**특징:**
- 시간복잡도와 정확도는 난수의 품질에 의존
- 확률적으로 최적해를 도출

**동작 방식:**
1. 문제 해결에 난수를 포함한 임의의 선택 수행
2. 선택 결과에 따라 문제 해결
3. 결과를 반복적으로 계산하여 평균값 도출

**장점:**
- 복잡한 문제를 간단히 해결 가능

**단점:**
- 정확도를 보장하지 못할 수 있음

**활용:**
- 정렬 알고리즘 최적화, 그래프 탐색, 샘플링 문제

---

# 기타 알고리즘 (Miscellaneous Algorithms)

## 슬라이딩 윈도우 (Sliding Window)

**정의:**
- 배열이나 리스트에서 일정한 크기의 부분을 반복적으로 이동하며 처리하는 알고리즘 기법

**특징:**
- 시간복잡도: O(n) (일반적으로)
- 부분 합, 최대값/최소값 등을 효율적으로 계산

**동작 방식:**
1. 초기 윈도우를 설정
2. 윈도우를 오른쪽으로 한 칸씩 이동하며 결과 갱신
3. 전체 배열을 처리할 때까지 반복

**장점:**
- 중복 계산을 줄여 효율적

**단점:**
- 윈도우 크기를 적절히 설정해야 함

**활용:**
- 문자열 검색, 배열 내 최대/최소 합 계산

---

## 분할-정복적 접근법 (Divide and Conquer)

**정의:**
- 문제를 작은 하위 문제로 분할하여 해결한 뒤 합쳐서 전체 문제를 해결하는 알고리즘 설계 기법

**특징:**
- 시간복잡도는 문제에 따라 달라짐 (예: 병합 정렬: O(n log n))
- 재귀적 구조로 구현

**동작 방식:**
1. 문제를 해결 가능한 최소 단위로 분할
2. 각 부분을 재귀적으로 해결
3. 결과를 병합하여 전체 문제 해결

**장점:**
- 복잡한 문제를 단계적으로 해결 가능

**단점:**
- 추가적인 메모리 사용 가능

**활용:**
- 병합 정렬, 퀵 정렬, 이진 탐색

---

## 유니온-파인드 (Union-Find, Disjoint Set)

**정의:**
- 여러 개의 집합을 효율적으로 관리하며, 집합 간의 합치기(Union)와 같은 집합에 속하는지 확인(Find)하는 연산을 수행하는 자료구조

**특징:**
- 시간복잡도: O(α(n)) (α는 아커만 함수의 역함수로 매우 느리게 증가)
- 경로 압축(Path Compression)과 랭크 기반 합치기(Union by Rank)를 통해 효율성 향상

**동작 방식:**
1. 초기화: 각 원소를 독립된 집합으로 설정
2. Find 연산: 특정 원소가 속한 집합의 대표자 반환
3. Union 연산: 두 집합을 하나로 합침

**장점:**
- 집합 관련 연산을 매우 빠르게 처리 가능

**단점:**
- 구현이 다소 복잡

**활용:**
- 최소 신장 트리(MST), 네트워크 연결성 문제

---

## 두 포인터 기법 (Two-pointer Technique)

**정의:**
- 배열이나 리스트에서 두 개의 포인터를 사용하여 문제를 해결하는 알고리즘 기법

**특징:**
- 시간복잡도: O(n) (일반적으로)
- 정렬된 배열에서 자주 사용

**동작 방식:**
1. 두 포인터를 배열의 양쪽 끝이나 특정 위치에 초기화
2. 조건에 따라 한쪽 또는 양쪽 포인터를 이동
3. 모든 경우를 처리할 때까지 반복

**장점:**
- 특정 조건을 만족하는 부분 배열이나 쌍을 효율적으로 찾을 수 있음

**단점:**
- 정렬되지 않은 배열에는 추가적인 정렬 과정 필요

**활용:**
- 부분 배열 합 문제, 두 수의 합 문제

---

## 스위핑 기법 (Sweep Line Algorithm)

**정의:**
- 선분이나 영역을 따라가며 이벤트를 처리하는 알고리즘 기법

**특징:**
- 시간복잡도: O(n log n) (정렬 포함)
- 이벤트를 효율적으로 관리하기 위해 우선순위 큐 또는 정렬된 배열 사용

**동작 방식:**
1. 처리해야 할 이벤트를 정렬
2. 선을 이동하며 이벤트를 처리
3. 각 이벤트에 따라 상태를 갱신

**장점:**
- 기하학적 문제에서 효율적

**단점:**
- 이벤트 정의 및 구현이 복잡할 수 있음

**활용:**
- 선분 교차 여부, 최소 직사각형 영역 계산

---

# 알고리즘 분석 (Algorithm Analysis)

## 시간 복잡도 (Time Complexity)

### Big-O, Omega, Theta Notations

**정의:**
- 알고리즘의 수행 시간이 입력 크기에 따라 어떻게 증가하는지를 표현하는 방법

**특징:**
- Big-O (O): 최악의 경우 수행 시간 상한
- Omega (Ω): 최선의 경우 수행 시간 하한
- Theta (Θ): 평균적인 수행 시간, 상한과 하한이 동일한 경우

**활용:**
- 알고리즘의 효율성을 비교하고 성능을 예측하는 데 사용

---

### 시간 복잡도 분석 기법

**정의:**
- 알고리즘의 수행 시간을 수학적으로 분석하여 시간 복잡도를 도출하는 방법

**기법:**
1. **연산 개수 계산:** 반복문과 재귀 호출 횟수를 직접 계산
2. **재귀 관계식 분석:** 마스터 정리를 활용하여 재귀 호출의 시간 복잡도 분석
3. **주요 연산 식별:** 가장 자주 실행되는 연산에 집중하여 시간 복잡도 도출

**활용:**
- 알고리즘 성능 분석 및 최적화

---

## 공간 복잡도 (Space Complexity)

**정의:**
- 알고리즘이 실행되는 동안 필요한 메모리 공간의 양을 나타냄

**특징:**
- 고정 공간: 입력 크기와 상관없이 필요한 공간
- 가변 공간: 입력 크기에 따라 변동되는 공간

**동작 방식:**
1. 입력 크기에 비례하는 공간 계산
2. 임시 데이터 구조나 재귀 호출 스택 등의 추가 공간 고려

**활용:**
- 메모리 제한이 있는 환경에서의 알고리즘 설계

---

## 최선, 평균, 최악의 경우 분석

**정의:**
- 알고리즘의 성능을 다양한 입력 조건에 따라 분석하는 방법

**특징:**
- 최선의 경우: 가장 빠르게 종료되는 입력 조건
- 평균적인 경우: 모든 가능한 입력의 평균 성능
- 최악의 경우: 가장 오래 걸리는 입력 조건

**활용:**
- 알고리즘이 다양한 상황에서 어떻게 동작하는지 평가

**예시:**
- 정렬 알고리즘에서 최선, 평균, 최악의 경우 시간 복잡도 비교
