# Random

java.util.Random 伪随机数类

该类的实例用于生成**伪随机数**的流。 该类使用48位种子，其使用线性同余公式进行修改。

如果使用相同的种子创建两个Random ，并且对每个实例进行相同的方法调用序列，则它们将生成并返回相同的数字序列。 

## 构造方法

### Random()

创建一个新的随机数生成器。

### Random(long seed)

使用单个 long 种子创建一个新的随机数生成器。

## 常用方法

### int nextInt()

返回下一个伪随机数，它是此随机数生成器的序列中均匀分布的 `int` 值。

### int nextInt(int n)

返回一个伪随机数，它是取自此随机数生成器序列的、在 0（包括）和指定值（不包括）之间均匀分布的 `int` 值。

### double nextDouble()

返回下一个伪随机数，它是取自此随机数生成器序列的、在 `0.0` 和 `1.0` 之间均匀分布的 
`double` 值。

### float nextFloat()

返回下一个伪随机数，它是取自此随机数生成器序列的、在 `0.0` 和 `1.0` 之间均匀分布的 
`float` 值。

### long nextLong()

返回下一个伪随机数，它是取自此随机数生成器序列的均匀分布的 `long` 值。

### boolean nextBoolean()

返回下一个伪随机数，它是取自此随机数生成器序列的均匀分布的 `boolean` 值。



## Code

```java
//生成0-9之间的随机数
random.nextInt(10);
//生成1-10之间的随机数
random.nextInt(10)+1;
```

### 相同的种子生成的随机数是相同的

```java
for (int i = 0; i < 5; i++) {
    Random random = new Random();
    for (int j = 0; j < 10; j++) {
        System.out.print(random.nextInt(10)+" ");
    }
    System.out.println();
}
/*
4 2 8 7 5 5 7 6 4 8 
7 0 0 9 3 7 2 3 8 4 
0 5 1 2 0 3 2 0 2 5 
2 3 7 0 5 4 7 2 0 7 
5 9 5 9 1 4 7 4 4 6 
*/
```

```java
for (int i = 0; i < 5; i++) {
    Random random1 = new Random(10);
    for (int j = 0; j < 10; j++) {
        System.out.print(random1.nextInt(10)+" ");
    }
    System.out.println();
}
/*
3 0 3 0 6 6 7 8 1 4 
3 0 3 0 6 6 7 8 1 4 
3 0 3 0 6 6 7 8 1 4 
3 0 3 0 6 6 7 8 1 4 
3 0 3 0 6 6 7 8 1 4 
*/
```

