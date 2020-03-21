# 선택정렬(Selection Sort) 

<br>

## 정의 
해당 순서에 원소를 넣을 위치는 이미 정해져 있고, 어떤 원소를 넣을지 **선택** 하는 알고리즘

ex) 오름차순 정렬일경우, 가장 작은 것을 **선택** 하여 제일 앞으로 보내기

<br>

## 과정(오름차순)
1. 주어진 배열중에서 최솟값을 찾는다

2. 찾은 최솟값을 정렬되지 않은 배열 중 맨 앞의 값과 교체(Swap)한다

3. 위 과정을 반복한다

<br>

## Python 코드(오름차순)
```python
import math

def selection_sort(array):
    n = len(array)
    idx = 0
    
    for i in range(n-1):
        min = math.inf
        for j in range(i, n):
            if array[j] < min:
                min = array[j]
                idx = j
                
        temp = array[i]
        array[i] = array[idx]
        array[idx] = temp
        
    return array

print(selection_sort([1,10,5,8,7,6,4,3,2,9]))
```

<br>

## GIF로 이해하기
![Selection_Sort](https://user-images.githubusercontent.com/48934537/77140569-612e2a00-6abd-11ea-9a83-450425f9eab2.gif)

<br>

## 시간복잡도
데이터의 개수가 N개일 경우 : (N-1) + (N-2) + (N-3) + ... 2 + 1 = N(N-1)/2

최선, 평균, 최악 모두 **O(N^2)** 로 동일

<br>

## 특징
- 탐색 대상 집합의 크기가 하나씩 감소한다

- 정렬된 값을 맨 앞부터 채워나감 - 뒤에 있는 index로 갈수록 비교연산 횟수가 하나씩 감소한다

- N-1인덱스에는 앞이 정렬이 다 된 상황임으로 사실상 비교 할 필요가 없다

<br>

## 장점
- 알고리즘 방식이 단순하다

- 버블정렬(Bubble Sort)와 비교하면 교환(Swap)의 횟수가 적어 실수행시간은 적다

- 버블정렬(Bubble Sort)와 마찬가지로 정렬하고자 하는 배열내에서 모든 작업이 이루어진다

  -> **제자리 정렬(In-Place_Sorting)**

<br>

## 단점
- N의 값이 조금만 커져도 많은 연산을 수행해야 한다 - **비효율적인 알고리즘**

- 중복된 원소에 대하여 순서를 유지하지 않는 **불안정 정렬(Unstable Sort)** 이다
