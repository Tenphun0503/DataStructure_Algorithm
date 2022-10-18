# Queue 队列

Similar to a stack, queue is also a special liner data structure. What different is that queue only allows adding entities at one end of the sequence, and removing entities from the other end.  
与栈类似，也是一种特殊的线性表。不同的是，队列只允许在表的一端进行插入操作，而在另一端进行删除操作。  

First in, first out (FIFO)  
遵循先进先出，后进后出的顺序

adding data from `rear` of the sequence and deleting data from `front` of the sequence.  
数据从队头 `rear` 出队，从队尾 `front`入队

***
## 顺序队列
理论上，队列没有长度限制，也不存在假溢出问题。  
实际使用会设长度，所以会有假溢出。

### Structure 结构
```
queue:
  maxSize : int
  front   : int
  rear    : int
  item[]
```
### Operations 操作
#### Initalize 初始化
```
Init(que : queue, size):
  maxSize = size
  item[maxSize]
  front = rear = 0
```
#### Add 入队
#### Delete 出队
#### IfEmpty 是否为空
#### GetLength 获取队长
#### GetHead 获取头元素
#### Clear 清空队列
