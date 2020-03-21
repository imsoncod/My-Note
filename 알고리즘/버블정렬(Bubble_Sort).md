# 버블정렬(Bubble Sort) 

<br>

## 정의 
서로 **인접**한 두 원소의 대소를 비교하여 조건에 맞지 않다면 자리를 교환(Swap)하며 정렬하는 알고리즘

ex) 오름차순 정렬일경우, 바로 옆에 있는 값과 비교해서 더 작은 값을 앞으로 보내기

<br>

## 과정(오름차순)
1. 인접한 두 원소의 대소관계를 비교하여 큰값을 뒤로 보낸다

2. 한 번 회전이 끝날때마다 탐색대상 집합기준 마지막 원소를 제외하고 위 과정을 반복한다

<br>

## Python 코드(오름차순)
```python
def bubble_sort(array):
    n = len(array)
    for i in range(n):
        for j in range(n-i-1):
            if array[j] > array[j+1]:
                temp = array[j]
                array[j] = array[j+1]
                array[j+1] = temp
    return array

print(bubble_sort([1,10,5,8,7,6,4,3,2,9]))
```

<br>

## GIF로 이해하기
![Bubble_Sort](https://user-images.githubusercontent.com/48934537/77142476-8e7dd680-6ac3-11ea-81ef-5588fb80efcc.gif)

<br>

## 시간복잡도
데이터의 개수가 N개일 경우 : (N-1) + (N-2) + (N-3) + ... 2 + 1 = N(N-1)/2

최선, 평균, 최악 모두 **O(N^2)** 로 동일

<br>

## 특징
- 탐색 대상 집합의 크기가 하나씩 감소한다

- 정렬된 값을 맨 뒤부터 채워나감 - 회전을 할때마다 비교연산 횟수가 하나씩 감소한다

- N-1인덱스에는 앞이 정렬이 다 된 상황임으로 사실상 비교 할 필요가 없다

<br>

## 장점
- 알고리즘 방식이 매우 단순하다

- 선택정렬(Selection Sort)과 비교하면 교환(Swap)의 횟수가 많아 시간복잡도는 동일해도 실수행시간이 더 길다

- 선택정렬(Selection Sort)과 마찬가지로 정렬하고자 하는 배열내에서 모든 작업이 이루어진다

  -> **제자리 정렬(In-Place_Sorting)**
  
- 중복된 원소에 대하여 순서를 유지하는 **안정 정렬(stable Sort)** 이다

<br>

## 단점
- N의 값이 조금만 커져도 많은 연산을 수행해야 한다 - **비효율적인 알고리즘**

- 정렬이 되어있던 안되어있던 인접한 2개의 원소를 비교한다
