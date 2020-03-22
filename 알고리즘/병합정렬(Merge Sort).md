# 병합정렬(Merge Sort) 

<br>

## 정의 
퀵정렬과 마찬가지로 분할 정복(Divide and Conquer)법을 사용하여 정렬하는 알고리즘

`* 분할정복(Divice and Conquer) : 문제를 작은 2개의 문제로 분리하고 각각 해결한 다음 결과를 모아서 다시 원래의 문제를 해결하는 방법으로 대게
순환호출을 이용하여 구현한다`

분할 시 항상 **균등한** 크기로 분할한다는 점에서 퀵정렬과 차이가 있다

<br>

## 과정
1. 배열의 길이가 1이상이면 절반으로 잘라 두 부분배열로 분할한다

2. 각 부분배열의 원소들을 서로 비교하며 정렬한다

3. 두 부분배열을 다시 하나의 배열로 합병한다

4. 위 과정을 반복한다

<br>

## Python 코드(오름차순)
```python
temp = [0]*10

def sort(arr, a, mid, b):
    global temp
    x = a
    y = mid+1
    idx = a

    #대소관계를 비교하여 temp에 넣어준다
    while x <= mid and y <= b:
        if arr[x] <= arr[y]:
            temp[idx] = arr[x]
            x+=1
        else:
            temp[idx] = arr[y]
            y+=1
        idx+=1

    #한 쪽의 비교연산이 모두 완료되었을 경우 나머지를 넣어준다
    if x > mid:
        for i in range(y, b+1):
            temp[idx] = arr[i]
            idx+=1
    else:
        for i in range(x, mid+1):
            temp[idx] = arr[i]
            idx+=1

    #원래 배열에 옮겨준다
    for i in range(a,b+1):
        arr[i] = temp[i]

def merge_sort(arr, a, b):
    #원소가 1개 이상일때만
    if a < b:
        mid = (a+b)//2

        #반으로 나누고
        merge_sort(arr, a, mid)
        merge_sort(arr, mid+1, b)
        #나중에 합친다
        sort(arr, a, mid, b)

    return arr

print(merge_sort([1,10,5,8,7,6,4,3,2,9], 0, 9))
```

<br>


## GIF로 이해하기

  ![MergeSort](https://user-images.githubusercontent.com/48934537/77249467-828d4280-6c84-11ea-93dc-52436f5af6d9.gif)

<br>

## 시간복잡도
**최선, 평균, 최악 모두 O(N*log₂N)로 동일**
- 순환 호출의 횟수 : log₂N

  레코드의 개수 N이 2의 거듭제곱이라고 가정했을 때, n=2^3일 경우 2^3->2^2->2^1->2^0로 줄어들어 순환 호출깊이가 3이 된다
  
  ![merge](https://user-images.githubusercontent.com/48934537/77249489-b0728700-6c84-11ea-8bfe-066343964126.png)

- 각 순환 호출 단계에서의 비교 연산 : N

  크기가 1인 배열 2개 합병 * 4쌍 = 8
  
  크기가 2인 배열 2개 합병 * 2쌍 = 8
  
  크기가 4인 배열 2개 합병 * 1쌍 = 8

  배열이 분할되어도 평균N번 정도의 비교가 이루어진다  

<br>

## 특징
- 분할 시 배열의 크기를 균등하게 분할한다

- 배열로 구현할 경우 제자리정렬이 아니지만 연결리스트를 활용하면 제자리정렬로 구현할 수 있다

- **분할 - 정복 - 결합** 과정을 거친다

<br>

## 장점
- 최악의 경우에도 시간복잡도 N*log₂N을 유지할 수 있다

- 항상 절반으로 분할하기 때문에 퀵정렬(Quick Sort)과 달리 피벗에 따라 성능에 영향을 받지 않는다

<br>

## 단점
- 시간복잡도면에서 퀵정렬(Quick Sort)보다 우세하지만 정렬 중 임시배열을 만들어 추가적인 메모리를 할당한다는 점에서 퀵정렬이 평균적으로 더 빠른 결과를 보여준다

- 버블정렬(Bubble Sort), 삽입정렬(Insertion Sort)과 마찬가지로 중복된 원소에 대하여 순서를 유지하는 **안정 정렬(Stable Sort)** 이다
