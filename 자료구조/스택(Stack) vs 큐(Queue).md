# 스택(Stack) vs 큐(Queue)

<br>

## 정의

* 스택 : 나중에 들어온 데이터가 먼저 나가는 **후입선출(LIFO : Last In First Out)** 형 자료구조

  * 관련 용어 : Push, Pop, Top, Overflow, Underflow

  * ex) 문서작업중 Ctrl+Z, 브라우저 뒤로가기, 택배 상하차

* 큐 : 먼저 들어온 데이터가 먼저 나가는 **선입선출(FIFO : First In First Out)** 형 자료구조

  * 관련 용어 : Enqueue, Dequeue, Rear, Front, Peek

  * ex) 은행 번호표, 인쇄 대기열

<br>

## 구조

|스택|큐|
|:-----:|:-----:|
|![image](https://user-images.githubusercontent.com/48934537/78421828-c1b09000-7695-11ea-89b9-ef861f9d9db4.png)|![image](https://user-images.githubusercontent.com/48934537/78421841-e573d600-7695-11ea-817a-0f29884206a6.png)|
|후입선출(LIFO)|선입선출(FIFO)|

<br>

## 코드

```python
# 스택
stack = []
stack.append(1)
stack.append(2)
stack.append(3)
stack.append(4)
stack.append(5)
#stack = [1, 2, 3, 4, 5]
print(stack.pop()) # 5

# 큐
queue = []
queue.append(1)
queue.append(2)
queue.append(3)
queue.append(4)
queue.append(5)
#stack = [1, 2, 3, 4, 5]
print(queue.pop(0)) # 1
```
