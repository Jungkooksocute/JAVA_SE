# 知识点

方法

## 题目1

定义一个方法，该方法能够找出两个小数中的较小值并返回。在主方法中调用方法进行测试。

### 训练提示

1. 根据方法的功能描述，方法的参数应该是两个小数。
2. 要返回两个小数的较小值，所以返回值类型也是小数类型。

### 解题方案

### 操作步骤

1. 定义方法getMin()，方法的参数是double a ，double b。
2. 在方法中对两个数字进行判断，返回较小值。
3. 在主方法中调用getMin()方法并接受返回值。
4. 在主方法中打印结果。

### 参考代码

```java
public class Test1 {
    public static void main(String[] args) {
        System.out.println(getMin(2.1,3.7));
    }

    public static double getMin(double a, double b) {
        return (a < b ? a : b);
       
    }

}
```

## 题目2//抓住比较大小 的作用于2个对象

定义一个方法，该方法能够找出三个整数中的最大值并返回。在主方法中调用方法测试执行。

### 训练提示

1. 根据题意，方法中需要使用三个整数，所以方法参数应该是三个整数类型。
2. 方法需要有返回值，返回值的类型也是整数类型。

### 解题方案

### 操作步骤

1. 定义方法getMax()，方法的参数是三个int类型变量a,b,c，方法的返回值是int类型。
2. 在方法中使用多分支if...else...或者三元运算符判断出最大值并返回。
3. 在主方法中调用getMax()方法并接受返回值。
4. 在主方法中打印结果。

### 参考代码

```java
public class MyExercise{
    public static void main(String[] args){
      Scanner reader=new Scanner(System.in);
      int a,b,c;
      System.out.println("请输入第一个数:");
      a=reader.nextInt();
      System.out.println("请输入第二个数:");
      b=reader.nextInt();
      System.out.println("请输入第三个数:");
     c=reader.nextInt();
      System.out.println("三个数中最大的那个数为："+getMax(a,b,c)); 
      
      
      }
   
      public static int getMax(int a,int b,int c){
          return (a>=b)?((a>=c)?a:c):((b>=c)?b:c);
      }
        
        
}

/*

public class Test1 {
    public static void main(String[] args) {
        System.out.println(getMax(3,17,10));
    }

    public static int getMax(int a, int b, int c) {
       int temp = a > b ? a : b;
       int max = temp > c ? temp : c ;
       return max;
    }
}



public class Test2 {
    public static void main(String[] args) {
        System.out.println(getMax(3, 17, 10));
    }

    public static int getMax(int a, int b, int c) {
        if (a > b) {
            //a 大
            //拿着大的跟第三个数再比较
            if(a > c){
                return a;
            }else{
                return c;
            }
        }else{
            //b 大
            if(b > c){
                return b;
            }else{
                return c;
            }
        }
}}

*/
```

## ☆☆☆☆☆☆☆☆☆☆☆☆☆☆☆☆题目3

在主方法中通过键盘录入三个整数。定义一个方法，方法接收三个整数变量，在方法中从大到小依次打印三个变量。执行效果如下：

```
请输入第一个整数：10
请输入第二个整数：30
请输入第三个整数：20
从大到小的顺序是： 30 20 10 
```

### 训练提示

1. 方法需要接受三个整数，那么方法的形式参数如何定义？
2. 方法没有返回值的需求，返回值类型是什么？

### 解题方案

### 操作步骤

1. 使用键盘录入分别录入三个整数。

2. 定义method方法，方法的参数是三个int类型，方法的返回值类型是void。

   2.1. 定义整数变量max用于存储最大值，定义min变量用于存储最小值。

   2.2. 使用if..else..多分支判断语句或者三元运算符计算三个整数中的最大值并赋值给max。

   2.3. 使用if..else..多分支判断语句或者三元运算符计算三个整数中的最小值并赋值给min。

   2.4. **<u>*定义变量mid代表中间数,三个整数的和减去max,再减去min,就是中间数的值。*</u>**

   2.5. 依次打印最大值，中间值和最小值。

3. 在主方法中调用method方法，传入参数。

### 参考答案

```java
public class MyExercise{
    public static void main(String[] args){
      Scanner reader=new Scanner(System.in);
      int a,b,c;
      System.out.println("请输入第一个数:");
      a=reader.nextInt();
      System.out.println("请输入第二个数:");
      b=reader.nextInt();
      System.out.println("请输入第三个数:");
      c=reader.nextInt();
      prtInt(a,b,c);
      
      }
   
      public static void prtInt(int a,int b,int c){
          int[] temp=new int[3];
          temp[0]=a;
          temp[1]=b;
          temp[2]=c;
          int max,mid,min,index=0;
          max=(a>=b)?((a>=c)?a:c):((b>=c)?b:c);
          min=(a<=b)?((a<=c)?a:c):((b<=c)?b:c);
          
          
          //找mid 
          if((a-b)*(a-c)*(b-c)==0){//min , max , mid 至少有2者相等
                  if(max==min) {mid=max;}//3者相等
                  else{
                      int count=0;
                      for(int e=0;e<3;e++){
                          if(max==temp[e]) count++;
                      }
                      if(count==1) mid=min;//min mid相等
                      else mid=max;//
                  }
              }
          while(index<3 &&  (a-b)*(a-c)*(b-c)!=0){//min mid max互不相等
              if(temp[index]<max  &&  temp[index]>min) { mid=temp[index];
                    break;
              }
              index++;
          }
          System.out.println("三个数从大到小排序依次为："+max+'\t'+mid+'\t'+min);
          }
      }


/*

public class Test5 {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        System.out.println("请输入第一个数");
        int num1 = sc.nextInt();
        System.out.println("请输入第二个数");
        int num2 = sc.nextInt();
        System.out.println("请输入第三个数");
        int num3 = sc.nextInt();
		
        //获取最大值
        int max = getMax(num1, num2, num3);
        //获取最小值
        int min = getMin(num1, num2, num3);
        //获取中间值
        int mid = (num1 + num2 + num3) - max - min;

        System.out.println(max + " " + mid + " " + min);
    }

    public static int getMax(int a, int b, int c) {
        int temp = a > b ? a : b;
        int max = temp > c ? temp : c;
        return max;
    }

    public static int getMin(int a, int b, int c) {
        int temp = a < b ? a : b;
        int min = temp < c ? temp : c;
        return min;
    }
}

*/
```

## 题目4

数字是有绝对值的，负数的绝对值是它本身取反，非负数的绝对值是它本身。请定义一个方法，方法能够得到小数类型数字的绝对值并返回。请定义方法并测试。

### 训练提示

1. 方法的功能是得到一个小数的绝对值，参数应该是一个小数类型。
2. 绝对值需要被返回，返回值类型应该也是小数类型。

### 解题方案

### 操作步骤

1. 定义一个小数变量num。

2. 定义获取绝对值的方法，方法的参数是一个double类型，返回值类型是double。

3. 在方法内部使用if..else..判断。

   3.1. 如果是负数则对负数取反并返回。

   3.2. 如果不是负数则直接返回数字本身。

4. 在主方法中调用绝对值方法，传入参数num,并接受返回值。
5. 打印返回的结果。

### 参考答案

```java
import java.util.Scanner;

public class JavaExe{
    public static double DoubleAb(double value){
        if(value<0) value=-1*value;
        return value;
    }
    public static void main(String[] args){
     Scanner reader=new Scanner(System.in);
     double value;
     System.out.println("请输入一个小数:");
     value=reader.nextDouble();
     System.out.println("这个小数的绝对值是："+DoubleAb(value));
    }

```

## 题目5

键盘录入一个正整数

定义一个方法,该方法的功能是计算该数字是几位数字,并将位数返回

在main方法中打印该数字是几位数

演示格式如下:
(1)演示一:
	请输入一个整数:1234
	控制台输出:1234是4位数字
(2)演示二:
	请输入一个整数:34567
	控制台输出:34567是5位数字

### 训练提示

1. 方法的功能是求有多少位，所以参数是一个，就是要计算的数据。
2. 题目说要返回，所以方法必须有返回值。

### 解题方案

### 操作步骤

1. 键盘录入一个正整数

2. 定义获取位数的方法，方法的参数是一个int类型，返回值类型是int。

3. 在方法内部使用循环获取有多少位

   可以不断的除以10，当结果为0时，循环结束。
   除以10的次数，就是数字的位数。

   举例：

   ​	123 除以第一次10之后为：12

   ​	除以第二次10之后为：1

   ​	除以第三次10之后为：0

   ​	表示123是三位数

4. 在主方法中调用方法，传入参数,并接受返回值。

5. 打印返回的结果。

### 参考答案

```java
import java.util.Scanner;

public class JavaExe{
    public static int NumCount(int a){
        int count=0;
        if(a<=0) return 0;
        while(a!=0){
           a/=10;
           count++;
        }
        return count;
        
    }
    
    public static void main(String[] args){
        int num,result;
        Scanner reader=new Scanner(System.in);
        System.out.println("请输入一个正整数");
        num=reader.nextInt();
        result=NumCount(num);
        if(result==0) System.out.println("输入不是正整数");
        else{
            System.out.println(num+"是"+result+"位数字");
        }
    }

    
}

```

## 题目6

需求：

​	定义一个方法equals(int[] arr1,int[] arr2).

功能：

​	比较两个数组是否相等（长度和内容均相等则认为两个数组是相同的）

```
public static boolean equals(int[] arr1,int[] arr2){
        if(arr1.length!=arr2.length) return false;
        int maxlen=arr1.length;
        while(maxlen!=0){
        if(arr1[maxlen-1]!=arr2[maxlen-1]) return false;
        }
        return true;
    }
```



## 题目7：

需求：

​	定义一个方法fill(int[] arr,int value)

功能：

​	将数组arr中的所有元素的值改为value

```
public static void fill(int[] arr,int value){
        for(int i=0;i<arr.length;i++){
        arr[i]=value;
        }
    }
```



## 题目8：（较难）

需求：

​	定义一个方法fill(int[] arr,int fromIndex,int toIndex,int value)

功能：

​	将数组arr中的元素从索引fromIndex开始到toIndex（不包含toIndex）对应的值改为value

```
public static boolean fill(int[] arr,int fromIndex,int toIndex,int value){
        if(fromIndex<0 || toIndex<0 || fromIndex>arr.length || toIndex>arr.length ||
                fromIndex>=toIndex) return false;
        for(int i=fromIndex;i<toIndex-1;i++){ 
        arr[i]=value;
        }
        return true;
    }
```



## 题目9：（较难）

需求：

​	定义一个方法copyOf(int[] arr, int newLength)

功能：

​	将数组arr中的newLength个元素拷贝到新数组中，并将新数组返回，从索引为0开始

public class equals{
    public static final int MaxSize=100;
    public static int[] copyOf(int[]arr,int newLength){
    if(newLength>MaxSize || newLength>arr.length) return null;
    int[] newarr=new int[MaxSize];
    for(int i=0;i<newLength;i++){
        newarr[i]=arr[i];
        }
    return newarr;
    }



## 题目10：（较难）

需求：

​	定义一个方法copyOfRange(int[] arr,int from, int to)

功能：

​	将数组arr中从索引from（包含from）开始，到索引to结束（不包含to）的元素复制到新数组中，

​	并将新数组返回。

```
public class equals{
    public static int[] copyOfRange(int[]arr,int from,int to){
   /* if(from>=MaxSize-1 || from<0|| to<=0 || to>=MaxSize|| from>=to) return null;*/
    int[] newarr=new int[to-from];
    int index=0;//伪造索引思想
    for(int i=from;i<=to-1;i++){
        newarr[index++]=arr[i];
        }
    return newarr;
    }

## 题
```

## 目11（很难）

一个大V直播抽奖，奖品是现金红包，分别有{2,588,888,1000,10000}五个奖金。请使用代码模拟抽奖，打印出每个奖项，奖项的出现顺序要随机且不重复。打印效果如下：（随机顺序，不一定是下面的顺序）

```
888元的奖金被抽出
588元的奖金被抽出
10000元的奖金被抽出
1000元的奖金被抽出
2元的奖金被抽出
```

### 训练提示

1. 奖项要随机出现，但奖金不是连续的数字，不能被随机产生。能随机产生的只有数组的索引了，可以使用随机索引来代表随机元素。因为索引和元素是一一对应的，
2. 哪些奖被抽过了，哪些奖没有被抽过，要定义一个数组来存放已经被抽过的奖项。
3. 每个奖项只能被抽出一次，要写一个方法来控制奖项不重复。

### 解题方案

​	使用数组存放多个奖金，再使用另一个数组存放已经被抽过的奖金，使用方法来判断某个奖金是否已经被抽取过。

### 操作步骤

1. 定义奖金的数组arr。
2. 定义数组brr准备存放已经被抽过的奖金，两个数组长度相同。
3. 定义一个变量index,用户代表数组brr的索引。
4. 定义方法，判断数组中是否存在某数字，存在返回true,不存在返回false。
5. 写一个while循环，如果index<arr.length则说明奖项没有被抽完继续抽取。
6. 在循环中使用随机数产生一个随机索引i。
7. 使用步骤4的方法判断brr数组中是否包含arr[i]奖金。
8. 如果不包含，则打印arr[i]奖金，并且把它放入brr数组中代表已经被抽取过，同时index加一。

### 参考答案

```java
public static void getAward(){
        int[] award={2,588,888,1000,10000};
        int[] rannum=new int[5];
        int temindex;
        boolean sign1,sign2;//标记变量
        Random r=new Random();
        for(int i=0;i<5;i++){
            temindex=i;
            sign1=true;
            while(sign1){
            rannum[i]=r.nextInt(5);
            sign2=true;
            for(int a=0;a<temindex;a++){
                if(rannum[a]==rannum[i]){
                    sign2=false;
                    break;
                }
            }
            if(sign2){
                sign1=false;
            }
            
            }
        }
            
        for(int y=0;y<5;y++){
            System.out.println(award[rannum[y]]+"元的奖金被抽出");
        }   
    }
```

