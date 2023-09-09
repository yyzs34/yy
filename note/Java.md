# 每日难点

## 	2023/9/6

### 		排序与使用二分法查找

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





## 2023/9/9

















