## scala 笔记


### scala 数据类型

两大类：AnyVal（值类型）和 AnyRef（引用类型），且它们都是对象。
比较特殊的是 None，是 Option 的两个子类之一，另一个是 Some，用于安全的函数返回值。



### 数组

- 定义数组
    - `new Array[Int](3)`
    创建一个空数组
    
    - 直接 Array
```scala
// val 数组名 = new Array[数据类型](长度)
val arr = new Array[Int](3)

// val 数组名 = Array[数据类型](内容)
val arr2 = Array[Int](1,2,3,4,5)
```
- 遍历数组
    - for 遍历
    - foreach 遍历
```scala
for(x <- arr)println(x)
arr.foreach(x =>{println(x)})
// 也可以简写成
arr.foreach(println)
```
- 二维数组
    - 先创建再传值
    - 直接传值创建
```scala
val 二维数组名 = new Array[Array[数据类型]](长度)
val arr = new Array[Array[Int]](3)
```