# 삽입정렬(Insertion Sort) 

<br>

## 정의 
자료 배열의 모든 요소를 앞에서부터 차례대로 이미 정렬된 배열부분과 비교하여, 자신의 위치를 찾아 삽입함으로써 정렬하는 알고리즘

매 순서마다 해당 원소를 삽입할 수 있는 적절한 위치를 찾아 삽입

ex) 각 숫자를 적절한 위치에 삽입하기

<br>

## 과정
1. 정렬할 원소를 기존에 정렬된 원소들 사이의 올바른 자리를 찾아 삽입한다 
2. 정렬이 안 된 원소들 중 한 원소를 대상으로 위 과정을 반복한다

<br>

## Python 코드(오름차순)
```python
def insertion_sort(array):
    n = len(array)
    for i in range(1,n-1):
        j = i
        while array[j] > array[j+1]:
            temp = array[j]
            array[j] = array[j+1]
            array[j+1] = temp
            j-=1

    return array

print(insertion_sort([0,1,10,5,8,7,6,4,3,2,9]))
```

<br>

## GIF로 이해하기
![Insertion Sort](https://user-images.githubusercontent.com/48934537/77147590-f4248f80-6ad0-11ea-8759-a252727ab6e4.gif)

<br>

## 시간복잡도
최선(데이터가 거의 정렬 된 상태) : **O(N)**

평균 : **O(N^2)**

최악 : **O(N^2)**

<br>

## 특징
- 처음 Key값이 두번째 자료부터 시작한다
- 필요할때만 정렬을 수행한다 <--> 선택,버블과 

<br>

## 장점
- 알고리즘 방식이 단순하다
- 데이터가 거의 정렬된 상태일경우 어떠한 알고리즘보다 효율적이다
- 선택정렬(Selection Sort), 버블정렬(Bubble Sort)과 비교했을 때 상대적으로 빠르다
- 선택정렬(Selection Sort), 버블정렬(Bubble Sort)과 마찬가지로 정렬하고자 하는 배열내에서 모든 작업이 이루어진다

  -> **제자리 정렬(In-Place_Sorting)**
- 버블정렬(Bubble Sort)과 마찬가지로 중복된 원소에 대하여 순서를 유지하는 **안정 정렬(stable Sort)** 이다

<br>

## 단점
- N의 값이 조금만 커져도 많은 연산을 수행해야 한다 - **비효율적인 알고리즘**
