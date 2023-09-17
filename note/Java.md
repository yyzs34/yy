# 每日难点

## 	2023/9/6

### 		d 排序与使用二分法查找

---

使用Array类调用方法实现查找；

```java
public static int binarySearch(double[] a,double number)
```

判断参数 number 指定的数是否在参数a指定的数组中，即 number 是否和数组 a 的某个元素的值相同，其中，数组 a 必须是事先已排序的数组。如果 number 和数组 a 的某个元素的值相同，那么int binarySearch(double[] a,double number)方法返回该元素的索引，否则返回一个负数。

事先的排序也用Array类调用方法；

```java
public static void sort(double[] a)
```

将数组 a 按照升序排序；

```java
public static void sort(double[] a,int start,int end)
```

将数组中 start 至 end-1 的元素升序排序；

示例：

```java
import java.util.*;
public class Example{
	public static void main(String args[]) {
		int []a= {12,34,9,23,45,6,45,90,123,19,34};
		Arrays.sort(a);
		System.out.println(Arrays.toString(a));
		int number= 45;
		int index= Arrays.binarySearch(a,number);
		if(index>= 0){
			System.out.println(number+"和数组中索引为"+ index+"的元素值相同");
        }
        else{
			System.out.println(number+"不与数组中的任何元素值相同");
		}
	}
}
```

待完善......

## 2023/9/7

### 枚举类型

Java中比较特殊的数据类型，类似于自定义的感觉，Java使用关键字enum声明枚举类型。

``` java
enum 枚举名{
    常量列表
}
```

例如：

```java
enum 余毅的特点{
    帅,很帅,真的帅,帅爆了
}
```

示例：

```java
import java.util.Scanner;

enum 余毅的特点{
    帅,很帅,真的帅,帅爆了
}

public class Yuyi{
    public static void main(String args[]){
        余毅的特点 yuyi=null;
        Scanner reader=new Scanner(System.in);
        int n=0;
        while(true){
            System.out.println("请输入一到四之间的整数");     
            if(reader.hasNextInt()){
               n=reader.nextInt();              
            }
            reader.nextLine();                                        
            if(n>=1&&n<=4){
                break;
            }
        }          
        if(n==1){
            yuyi=余毅的特点.帅;
        }
        else if(n==2){
            yuyi=余毅的特点.很帅;
        }
        else if(n==3){
            yuyi=余毅的特点.真的帅;
        }
        else if(n==4){
            yuyi=余毅的特点.帅爆了;
        }
        System.out.println("余毅的第"+n+"个特点是"+yuyi);
    }
}
```

​	在写示例的过程中，遇到了处理输入的相关报错，我发现我对程序输入字母等其他数据类型时，会因为数据类型不匹配而导致程序报错，所以我进行了更改，添加了hasNextInt( )方法进行判断键盘缓存区是否符合数据类型。

```java
if(reader.hasNextInt()){
               n=reader.nextInt();              
            }
```



​	但仅此还不够，我发现添加了之后会出现 while循环停止不了的情况，经过判断发现这是由于键盘缓存区出现的问题，所以我使用了Scanner类的nextLine()方法清空输入缓冲区，之后程序运行正常。

```java
reader.nextLine();
```

## 2023/9/8

### d 位运算符

#### 	按位与运算符

& 按位与，是将两边的数先转换为二进制位，然后运算最终值;

运算规则 ：如果两个二进制位上的数都是1，那么运算结果为1，其他情况运算结果均为0。

(0&0=0 1&1=1 1&0=0 0&1=0)

#### 	按位或运算符

 | 按位或和&按位与计算方式都是：先转换为二进制数，再计算;

 运算规则：两个二进制位上的数字如果都为0，那么运算结果为0，否则运算结果是1。

 (0|0=0 0|1=1 1|0=1 1|1=1)

#### 	取反运算符

按位取反运算符写法是”~”，它的运算规则是：

对每个二进制位进行取反操作，所谓取反就是原来二进制位上如果是0，那么就变成1，反之，如果原来二进制位上是1，那么就变为0。即：取反就是1为0，0为1。

取反运算符是一个单目运算符，所以只需要一个操作数就可以了。

例如：5的二进制位是0000 0101，取反后为1111 1010，值为-6

#### 	异或运算符

 ^ 异或运算符顾名思义，异就是不同;

 运算规则：两个二进制位上的数字如果相同，则运算结果为0；

 如果两个二进制位上的数字不相同，则运算结果为1。

 （1^0 = 1 , 1^1 = 0 , 0^1 = 1 , 0^0 = 0）

比如说：ab与ba是等价的，虽然a和b交换了位置，但还是会运算出相同的结果。

可以利用异或运算的性质进行文字加密解密；

示例：

```java
public class Yuyi{
	public static void main(String args[]) {
        char a1 ='余',a2='毅',a3='阿',a4= '布';
        char secret='A';
        a1=(char)(a1^secret);
        a2=(char)(a2^secret);
        a3=(char)(a3^secret);
        a4=(char)(a4^secret);
        System.out.println("密文:"+a1+a2+a3+a4);
        a1=(char)(a1^secret);
        a2=(char)(a2^secret);
        a3=(char)(a3^secret);
        a4=(char)(a4^secret);
        System.out.println("原文:"+a1+a2+a3+a4);
	}
}
```

待完善......

## 2023/9/9

### Java switch开关语句


switch语句是单条件多分支的开关语句，语法格式如下：

```java
switch(表达式) {
    case 常量值1:语句1;break;
    case 常量值2:语句2;break;
    case 常量值3:语句3;break;
    ……
    case 常量值n:语句n;break;
    default:语句n+1;
}
```

​	switch语句中“表达式”的值可以是byte、short、int、char型，“常量值1”到“常量值n”也是byte、short、int、char型，而且要互不相同。

​	switch语句首先计算表达式的值，如果表达式的值和某个case后面的常量值相等，就执行该case里的语句直到碰到break语句为止。如

果某个case中没有使用break语句，一旦表达式的值和该case后面的常量值相等，程序不仅执行该case里的语句，而且继续执行后继的

case里的语句，直到碰到break语句为止。若switch语句中的表达式的值不与任何case的常量值相等，则执行default后面的语句。switch

语句中的default是可选的，如果它不存在，并且switch语句中表达式的值不与任何case的常量值相等，那么switch语句就不会进行任何

处理。

​	我们前面学习的if条件分支语句的共同特点是根据一个或多个条件选择执行一个分支操作，而不是选择执行多个分支操作。在switch语

句中，通过合理地使用break语句，可以达到根据一个条件选择执行一个分支或多个分支操作的结果。

**实例：**

```java
public class Main {
    public static void main(String args[]){
        char grade = 'B';
        switch(grade) {
            case 'A':
                System.out.println("优秀");
                break;
            case 'B':
                System.out.println("良好");
                break;
            case 'C':
                System.out.println("及格");
                break;
            default:
                System.out.println("未知");
        }
    }
}
```

运行结果如下：

```java
 良好
```

## 2023/9/10

### Java do-while循环语句

do-while循环语句的语法格式如下：

```java
do {
    //语句
}while(表达式)
```

**注意：**

do-while循环和while循环的区别是do-while的循环体至少被执行一次。



do-while循环语句的执行规则：

（1）执行循环体，再进行（2）。

（2）计算表达式的值，若该值为true，则进行（1），否则进行（3）。

（3）结束do-while语句的执行。



**实例：**

```java
public class Main {
    public static void main(String[] args){
        int a = 1;
        do{
            System.out.print(a);
            a++;
            System.out.print("\n");
        }while( a < 10 );
    }
}
```



运行结果如下：

```java
1
2
3
4
5
6
7
8
9
```

## 2023/9/11

### Java continue语句

continue语句是用关键字continue加上分号构成的语句，在循环体中可以使用continue语句。

在一个循环中，如果在某次循环中执行了continue语句，那么本次循环就结束，即不再执行本次循环中循环体中continue语句后面的语句，而转入进行下一次循环。

即提前结束此次循环。

**实例：**

```java
public class Main {
    public static void main(String[] args) {
        for(int a = 1; a < 10; a = a+1) {
            if( a%2 == 0 ) {
                continue;
            }
            System.out.print(a);
            System.out.print("\n");
        }
    }
}
```

运行结果如下：

```java
1
3
5
7
9
```

## 2023/9/12

### Java break语句


break语句是用关键字break加上分号构成的语句，在循环体中可以使用break语句。


在一个循环中，如果在某次循环中执行了break语句，那么整个循环语句就结束。


**实例：**

```java
public class Main {
    public static void main(String[] args) {
        for(int a = 1; a < 10; a = a+1) {
            if( a%2 == 0 ) {
                break;
            }
            System.out.print(a);
            System.out.print("\n");
        }
    }
}
```



运行结果如下：

```java
1
```

## 2023/9/13

### Java中Enum类下的values()方法

枚举类中的元素是无法通过下标值来访问的，如果你想指定访问枚举类中的某个值，你只能直接写出它们的值，除此之外，别无他法。但

是枚举类有一个values()方法，这个方法可以将枚举类转换成一个枚举类型的数组，转换成数组之后我们就可以通过下标来访问我们的枚

举类中的值。比如下面的代码：

```java
enum Direction {
 
    LEFT, RIGHT, UP, DOWN
 
}
```


​    这里面有四个值，如果我们想通过下标来访问的话，就必须进行如下的操作：

```java
Direction dirs[] = Direction.values();
 
for (int i = 0; i < dirs.length; i++) {
 
     System.out.println(dirs[i]);
 
}
```


这个操作有什么用呢?主要用途就是从这个枚举类中选取一个随机值，具体的代码如下：

```java
 Random r = new Random();
 
int ri = r.netInt(dirs.length);
 
Direction dir = dirs[ri];
```



## 2023/9/14

### Java枚举的valueOf方法

1. 前言
在Java中，枚举是一种特殊的数据类型，它由一组常量值组成。枚举类型可以方便地定义一系列相关的常量，并对这些常量进行分类和操作。在Java中，我们可以使用枚举的valueOf方法来将一个字符串转换成相应的枚举常量。本文将详细介绍Java枚举的valueOf方法，包含代码示例和详细解释。

2. 枚举的valueOf方法概述
在Java中，枚举的valueOf方法是一个静态方法，用于将一个字符串转换成相应的枚举常量。它的定义如下：

``` java
public static <T extends Enum<T>> T valueOf(Class<T> enumType, String name)
```

其中，enumType表示枚举类型的Class对象，name表示要转换的字符串。该方法将返回一个枚举常量，如果没有找到相应的常量，则抛出IllegalArgumentException异常。

3. 代码示例
下面通过一个简单的示例来演示如何使用枚举的valueOf方法。

3.1 定义枚举类型
首先，我们定义一个枚举类型Season，表示四季。代码如下：

``` java
public enum Season {
    SPRING, SUMMER, AUTUMN, WINTER
}
```

3.2 使用valueOf方法
然后，我们使用valueOf方法将字符串转换成枚举常量。代码如下：

```java
String seasonName = "SPRING";
Season season = Season.valueOf(Season.class, seasonName);
System.out.println(season);
```

运行以上代码，输出结果为：

```java
SPRING
```

以上代码中，我们首先定义了一个字符串seasonName，然后通过valueOf方法将字符串"SPRING"转换成了枚举常量Season.SPRING，并将其赋值给了变量season。最后，我们通过System.out.println方法打印出了变量season的值。

4. valueOf方法的实现原理
在Java中，枚举的valueOf方法是由编译器自动生成的。它的实现原理如下：

4.1 获取枚举类型的所有常量
首先，valueOf方法通过传入的enumType参数获取到枚举类型的Class对象，然后通过Class对象的getEnumConstants方法获取到该枚举类型的所有常量。代码如下：

```java
T[] enumConstants = enumType.getEnumConstants();
```

其中，T表示枚举类型的泛型。

4.2 遍历比较常量名称
然后，valueOf方法遍历比较每个常量的名称，直到找到与传入的name参数相等的常量名称。代码如下：

```java
for (T constant : enumConstants) {
    if (constant.name().equals(name)) {
        return constant;
    }
}
```

其中，constant.name()方法用于获取常量的名称。

4.3 抛出异常
如果没有找到相应的常量，valueOf方法将抛出IllegalArgumentException异常。代码如下：

```java
throw new IllegalArgumentException(name);
```



5. 注意事项
在使用枚举的valueOf方法时，需要注意以下几点：

5.1 字符串的大小写
枚举的valueOf方法默认是区分大小写的，即字符串的大小写必须与枚举常量的大小写完全一致，否则将抛出IllegalArgumentException异常。如果需要忽略大小写，可以在valueOf方法之前调用String类的toLowerCase或toUpperCase方法，将字符串转换成统一的大小写。

5.2 枚举常量的顺序

枚举常量的顺序与其在枚举类型中定义的顺序一致。在使用valueOf方法时，传入的字符串必须与定义的枚举常量的名称完全一致，否则将抛出IllegalArgumentException异常。因此，在使用valueOf方法之前，需要确保传入的字符串的准确性。

## 2023/9/15

### Java枚举的ordinal() 方法
通过调用枚举类型实例的 ordinal() 方法可以获取一个成员在枚举中的索引位置。下面的示例创建一个包含 3 个成员的枚举类型 Signal，然后调用 ordinal() 方法输出成员及对应索引位置。

```java
public class TestEnum1
{
    enum Signal
    {
        //定义一个枚举类型
        GREEN,YELLOW,RED;
    }
    public static void main(String[] args)
    {
        for(int i=0;i<Signal.values().length;i++)
        {
            System.out.println("索引"+Signal.values()[i].ordinal()+"，值："+Signal.values()[i]);
        }
    }
}
```

结果

``` java
//索引0，值：GREEN
//索引1，值：YELLOW
//索引2，值：RED
```



## 2023/9/16

### Java instanceof运算符实例讲解

**instanceof运算符**左面的操作数是一个**对象**，右面的操作数是一个**类**，当左面的对象是右面的类或子类创建的对象时，该运算符运算的

结果是true，否则是false。

**实例：**

```java
public class Application {
    public static void main(String[] args){
        Object o = new Student();
        System.out.println(o instanceof Person);
    }
}
```



运行结果如下：

```java
true
```

## 2023/9/17

### d java forEach使用
foreach 是 Java 中的一种语法糖，目的是方便程序员开发和提高性能。其实就是编译期间以特定的字节码或特定的方式来对这些语法进行处理。

1.普通数组for用法
对于数组，foreach 循环实际上还是用的普通的 for 循环，怎么说foreach 循环就是for 循环

```java
int[] arr= {1,2,3,4,5}

//普通for循环
for(int i=0;i<arr.length;i++) 
	System.out.println("数组元素:"+arr[i]);

//for in写法
for(int i:arr)
	System.out.println("数组元素:"+i);

```

2.集合类forEach用法

对于集合，foreach 循环实际上是用的 iterator 迭代器迭代，写法也一样。

``` java
ArrayList<Integer> arrlist = new ArrayList<Integer>();
arrlist.add(1);
arrlist.add(2);
arrlist.add(3);
//for in用法
for(Integer a:arrlist)
	System.out.println("集合数据："+a);
	
//迭代器循环
for(Iterator<Integer> it = arrlist.iterator();it.hasNext();)
	System.out.println("集合数据："+it.next());

//forEach 循环
arrlist.forEach(item->{
    System.out.println("元素"+item);
});

//如果是map,传入的是kv对
HashMap<String, String> map = new HashMap<>();
map.forEach((k,v)->{
     System.out.println(k);
     System.out.println(v);
});

//forEach 循环(包含语法糖)
arrlist.forEach(System.out::println);
```

待完善......



