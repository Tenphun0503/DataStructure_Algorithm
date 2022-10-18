# Stack 栈

Stack is a special liner data structure. It can only add or delete data at the top of the stack.  
栈是一种特殊的线性表，它只能在一个表的一个固定端进行数据节点的插入和删除操作

Last in, first out  
遵循先进后出，后进先出的顺序

***
### Structure 结构
```
stack:  
  maxSize : int     //有时候定义栈的大小  
  top     : int     //栈顶位置, 同时也代表数据数量(top+1)
  item[]            //栈本身  
```

### Operations 操作

#### Initialize 初始化
``` 
Init(stk : stack, size):
  maxSize = size    
  item[maxSize]     //给定大小的空表
  top = -1              //top初始一个无效值
```

#### Push 插入
```
push(stk : stack, data):
  if top = maxSize:
    overflow error 
  else:
     item[++top] = data     //top值涨1，data赋给最新空位
```

#### Pop 删除
```
pop(stk : stack):
  if top = 0:
    underflow error 
  else:
     return item[top--]     //弹出top处的值，top值降1
```

另外还有`peek() : 查看top处的值`以及`ifEmpty() : 是否为空` `ifFull() : 是否为满`之类的基本操作
```
peek() --> item[top]
```
```
ifEmpty() --> if top == -1
```
```
ifFull() --> if top == maxSize
```

参考: [菜鸟](https://www.runoob.com/java/data-stack.html) | [Wiki](https://en.wikipedia.org/wiki/Stack_(abstract_data_type))
