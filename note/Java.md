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













