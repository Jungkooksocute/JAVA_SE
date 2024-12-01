# 一、if判断语句作业

## 题目1

李雷想买一个价值7988元的新手机，她的旧手机在二手市场能卖1500元，而手机专卖店推出以旧换新的优惠，把她的旧手机交给店家，新手机就能够打8折优惠。为了更省钱，李雷要不要以旧换新？请在控制台输出。

### 训练提示

1. 用什么知识点能够对不同购买方式的价格做判断？

### 解题方案

1. 使用if...else语句判断

### 操作步骤

1. 计算不使用以旧换新时的花费。
2. 计算使用以旧换新时的花费。
3. 使用if..else语句判断哪种方式更省钱，并输出结果

### 参考答案

```java
public class Demo1 {
    public static void main(String[] args) {
        //1.计算不使用以旧换新的花费
        int money1 = 7988 - 1500;
        //2.计算以旧换新的花费
        double money2 = 7988 * 0.8;
        //3.判断两种方式
        if(money1 > money2){
            System.out.println("使用以旧换新更省钱");
        }else{
            System.out.println("不使用以旧换新更省钱");
        }
    }
}
```

## 题目2

让用户依次录入三个整数，求出三个数中的最小值，并打印到控制台。

### 训练提示

1. 如何完成用户录入？
2. 求最小值需要用到什么知识点？

### 解题方案

1. 使用Scanner键盘录入三个数字，使用三元运算符实现

2. 使用Scanner键盘录入三个数字，使用if..else的嵌套实现（不做要求）


### 操作步骤

1. 使用三次键盘录入的方法让用户输入三个整数
2. 使用三元运算符求出最小值
3. 打印输出最小值

### 备注：

​	本题，也可以使用if嵌套的方式书写，但是非常麻烦，建议用三元运算符。

​	可以自己试着写一下if嵌套方式，然后跟三元运算符方式进行对比一下，看看谁更简单。

### 参考答案

```java
public class Test04 {
    public static void main(String[] args){
        int a,b,c,min;
        Scanner reader=new Scanner(System.in);
        System.out.println("请输入第一个数字：");
        a=reader.nextInt();
                System.out.println("请输入第二个数字：");
        b=reader.nextInt();
                System.out.println("请输入第三个数字：");
        c=reader.nextInt();
        min=a;
        if(b<=min){
        min=b;
            if(c<=min){
            min=c;
            }
        }
        else{
            if(c<=min){
            min=c;
            }
        }
        System.out.println(a+","+b+","+c+"三个数中最小的数是："+min);
        
    }
}


/*
if( a< b && a < c){
            min = a;
        }else if( c < b && c < a){
            min = c;
        }else{
            min = b;
        }
*/





/*//三目运算符的写法
public class Test04 {
    public static void main(String[] args){
        int a,b,c,min;
        Scanner reader=new Scanner(System.in);
        System.out.println("请输入第一个数字：");
        a=reader.nextInt();
                System.out.println("请输入第二个数字：");
        b=reader.nextInt();
                System.out.println("请输入第三个数字：");
        c=reader.nextInt();
        min=a;
        min=(a>=b)?((b>=c)?c:b):((a>=c)? c:a);
        System.out.println(a+","+b+","+c+"三个数中最小的数是："+min);
        
    }
}

变量=（条件）？expression1：expression2  //条件那里打起括号不容易出错

*/
```

## 题目3（一般难度）

某银行推出了整存整取定期储蓄业务，其存期分为一年、两年、三年、五年，到期凭存单支取本息。存款年利率表如下：

​	存期		年利率（%）

​	一年		2.25

​	两年		2.7

​	三年		3.25

​	五年		3.6

请存入一定金额（1000起存），存一定年限（四选一），计算到期后得到的本息总额。

提示：

​	存入金额和存入年限均由键盘录入

​	本息计算方式：本金+本金×年利率×年限

### 训练提示

1. 使用什么方式让用户输入内容？
2. 使用哪种if语句的格式对信息作出判断？

### 解题方案

1. 使用Scanner和if..else...的嵌套操作。

### 操作步骤

1. 键盘录入金额和年份。
2. 使用多条件if...else判断年份，计算本息金额。
3. 输出结果。

### 参考答案

```java
package myexercise;
import java.util.*;

public class MyExercise {
    
    public static void main(String[] args) {
        Scanner reader=new Scanner(System.in);
        double account,balance;
        int year;
        do{
        System.out.println("请输入本金:");
        account=reader.nextDouble();
        System.out.println("请输入存入年限:");
        year=reader.nextInt();
        }while(account<1000  ||  year>5  ||  year<1);
      switch(year){
            case 1:
                balance=account+account*year*2.25*0.01;break;
            case 2:
                balance=account+account*year*2.7*0.01;break;
            case 3:
                balance=account+account*year*3.25*0.01;break;
            default:
                 balance=account+account*year*2.25*0.01;break;
          /*  case 5:
                balance=account+account*year*3.6*0.01;break;*/
              //在这里用defalut更好,用case 5的话，系统无会考虑case可能为6的情况，然后系统提示错误“balance可能未被初始化”
               
        }
        System.out.println("本息为："+balance+'元');
    }
    
}

```

## 题目4（较难）

某商场购物可以打折，具体规则如下：

​	普通顾客购不满100元不打折，满100元打9折；

​	会员购物不满200元打8折，满200元打7.5折；

​	不同打折规则不累加计算。

请根据此优惠计划进行购物结算，键盘录入顾客的类别（0表示普通顾客，1表示会员）和购物的折前金额（整数即可），输出应付金额（小数类型）。

### 训练提示

1. 使用什么方式让用户输入内容？
2. 使用哪种if语句的格式对信息作出判断？

### 解题方案

1. 使用Scanner键盘录入和if..else判断语句的嵌套使用来完成。

### 操作步骤

1. 键盘录入会员类别和购物金额。
2. 先使用if-else判断顾客类别。
3. 在不同的顾客类别中再使用if-else语句判断购物金额。
4. 输出结果。

### 参考答案

```java
package myexercise;
import java.util.Scanner;

public class MyExercise{
    public static void main(String[] args){
    Scanner reader=new Scanner(System.in);
    int custom;
    double account;
    System.out.println("请输入顾客类别（普通顾客：0；会员：1；）：");
    custom=reader.nextInt();
    System.out.println("请输入购买的总金额：");
    account=reader.nextDouble();
    if(custom==0){
        if(account>0 && account<100){
            System.out.println("此次购物优惠后的总价格为："+account+'元');
        }
        else if(account>=100){
            System.out.println("此次购物优惠后的总价格为："+account*0.9+'元');
        }
        else{
            System.out.println("您输入的金额有误");
        }
    }
    else if(custom==1){
        if(account>0 && account<200){
            System.out.println("此次购物优惠后的总价格为："+account*0.8+'元');
        }
        else if(account>=200){
            System.out.println("此次购物优惠后的总价格为："+account*0.75+'元');
        }
        else{
            System.out.println("您输入的金额有误");
        }
    
    }
    else{
     System.out.println("您输入的顾客类别有误");   
    }
 }
}

```

## 题目5（很难）

2019年1月1日起，国家推出新的个人所得税政策，起征点上调值5000元。也就是说税前工资扣除三险一金（三险一金数额假设是税前工资的10%）后如果不足5000元，则不交税。如果大于5000元，那么大于5000元的部分按梯度交税，具体梯度比例如下：

​	0 ~ 3000元的部分，交税3%			

​	3000 ~ 12000元的部分，交税10%

​	12000 ~ 25000的部分 ， 交税20%		

​	25000 ~ 35000的部分，交税25%

​	35000 ~ 55000的部分，交税30%		

​	55000 ~ 80000的部分，交税35%

​	超过80000的部分，交税45%

比如：黑马某学员入职一家企业后，税前工资是15000，则他每月该交个税的部分是15000-1500-5000=8500元，个税缴纳数额是3000×3%+5500×10%=640元。税后工资12860元。

请完成一个个税计算程序，在用户输入税前工资后，计算出他对应的纳税数额，以及税后工资为多少？

### 训练提示

1. 工资的哪些部分是属于要纳税部分，如何计算？
2. 纳税比例有很多区间，用什么知识点能够对应多个区间？
3. 每个区间的纳税数额是多少，计算的规律是什么？

### 解题方案

1. 使用多条件的if...else对应各个纳税梯度，分别计算每一个梯度的纳税数额。

### 操作步骤

1. 提示用户输入税前工资，使用键盘录入让用户输入一个整数。
2. 计算工资中应交税部分。也就是去除三险一金和起征点数额。
3. 使用多条件if..else..对每个区间分别判断，用每个梯度的计算公式求出对应的纳税数额。
4. 根据求出的纳税数额求出税后工资。

### 参考答案

```java
package myexercise;
import java.util.Scanner;

public class MyExercise{
    public static void main(String[] args){
    System.out.println("请输入税前工资：");
    Scanner reader=new Scanner(System.in);
    double preTax,starPoint,aftTax,tax=0;
    preTax=reader.nextDouble();
    starPoint=preTax*0.9-5000;
    if(preTax*0.9<5000){
    System.out.println("不用缴税");
    }
    else{
        if(starPoint>=0  && starPoint<3000){
        tax=starPoint*3*0.01;    
        }
        else if(starPoint>=3000  && starPoint<12000){
        tax=3000*3*0.01+(starPoint-3000)*10*0.01;
        }
        else if(starPoint>=12000 && starPoint<25000){
        tax=3000*3*0.01+(12000-3000)*10*0.01+(starPoint-12000)*20*0.01;
        }
        else if(starPoint>=25000 && starPoint<35000){ 
        tax=3000*3*0.01+(12000-3000)*10*0.01+(25000-12000)*20*0.01+(starPoint-25000)*25*0.01;
        }
        else if(starPoint>=35000 && starPoint<55000){
        tax=3000*3*0.01+(12000-3000)*10*0.01+(25000-12000)*20*0.01+(35000-25000)*25*0.01+(starPoint-35000)*30*0.01;
        }
        else if(starPoint>=55000 && starPoint<80000){
        tax=3000*3*0.01+(12000-3000)*10*0.01+(25000-12000)*20*0.01+(35000-25000)*25*0.01+(55000-35000)*30*0.01+(starPoint-55000)*35*0.01;
        }
        else{
        tax=3000*3*0.01+(12000-3000)*10*0.01+(25000-12000)*20*0.01+(35000-25000)*25*0.01+(55000-35000)*30*0.01+(80000-55000)*35*0.01+(starPoint-80000)*45*0.01;
        }
        
    }
    System.out.println("个人缴纳的税为："+tax+'元');
    System.out.println("个人的税后工资为："+(preTax*0.9-tax)+'元');
 }
}

```

# 二、switch选择语句作业

## 题目1

模拟计算器功能，对键盘录入的两个int类型的数据进行加、减、乘、除的运算，并打印运算结果。

要求：

​	键盘录入三个整数,其中前两个整数代表参加运算的数据，第三个整数为要进行的运算(1:表示加法运算,2:表示减法运算,3:表示乘法运算,4:表示除法运算)，演示效果如下:

​		请输入第一个整数: 30

​		请输入第二个整数: 40

​		请输入您要进行的运算(1:表示加法,2:表示减法,3:表示乘法,4:表示除法): 1

​		控制台输出:30+40=70

### 训练提示

1. 用户录入了数据之后，用什么知识点去判断加减乘除四种不同的操作？ 

### 解题方案

1. 使用switch判断语句完成。

### 操作步骤

1. 使用键盘录入三个变量。
2. 使用switch判断语句对第三个变量进行判断，匹配要执行的操作。
3. 在每一个case中分别对第一个变量和第二个变量进行不同的操作。

### 参考答案

```java
package myexercise;
import java.util.Scanner;

public class MyExercise{
    public static void main(String[] args){
    Scanner reader=new Scanner(System.in);
    int pre,nex,type;
    System.out.println("请输入第一个数字：");
    pre=reader.nextInt();
    System.out.println("请输入第二个数字：");
    nex=reader.nextInt();
    System.out.println("请输入要进行运算的方式（1:表示加法,2:表示减法,3:表示乘法,4:表示除法)");
    type=reader.nextInt();
    switch(type){
        case 1:
            System.out.println(pre+"+"+nex+"="+（pre+nex）);
            /*System.out.println(pre+'+'+nex+'='+（pre+nex）);这样是错误的
            char,byte,short在进行运算的时候会自动类型转换为Int型
            用双引号的话电脑则会认为是字符串的拼接
            */
            break;
        case 2:
            System.out.println(pre+"-"+nex+"="+（pre-nex）);
            break;
        case 3:
            System.out.println(pre+"*"+nex+"="+（pre*nex）);
            break;
        case 4:
            System.out.println(pre+"/"+nex+"="+（pre*1.0/nex））);
            //☆☆☆☆☆☆☆☆☆☆☆☆☆☆☆☆☆直接打印出来除法（pre*1.0/nex）
            break;
        default:
            System.out.println("您输入的运算类别有误");
            break;

    }
    
 }
}
```

# 三、循环语句作业

## 题目1

​	键盘录入两个数字number1和number2表示一个范围，求这个范围之内的数字和。

### 训练提示

1. number1和number2不知道谁大谁小，需要先判断大小关系
2. 确定大小之后，可以循环得到范围里面的每一个数
3. 把每一个数字进行累加即可

### 参考答案

```java
import java.util.Scanner;

public class MyExercise{
    public static void main(String[] ags){
    int fir,nex,maxn,minn,count=0;  
    Scanner reader=new Scanner(System.in);
    System.out.println("请输入第一个数字：");
    fir=reader.nextInt();
    System.out.println("请输入第二个数字：");
    nex=reader.nextInt();
    maxn=fir>nex?fir:nex;
    minn=fir<nex?fir:nex;
    for(int i=minn;i<=maxn;i++){
      count+=i;
    } 
    System.out.println(minn+"到"+maxn+"这个范围内数字之和为："+count);
    }
}
```

## 题目2

需求：键盘录入两个数字，表示一个范围。

​           统计这个范围中。

​	    既能被3整除，又能被5整除数字有多少个？

### 训练提示

1. 需要先判断键盘录入两个数字的大小关系
2. 确定大小之后，可以循环得到范围里面的每一个数
3. 找到一个符合条件的数字，统计变量就自增一次

### 操作步骤

1. 确定键盘录入的两个数字大小关系
2. 定义for循环，找到范围之内的每一个数字
3. 对每一个数字进行判断
4. 符合条件统计变量自增一次

### 参考答案

```java

import java.util.Scanner;

public class MyExercise{
    public static void main(String[] ags){
    int fir,nex,maxn,minn,count=0;  
    Scanner reader=new Scanner(System.in);
    System.out.println("请输入第一个数字：");
    fir=reader.nextInt();
    System.out.println("请输入第二个数字：");
    nex=reader.nextInt();
    maxn=（fir>nex）?fir:nex;
    minn=（fir<nex）?fir:nex;
    for(int i=minn;i<=maxn;i++){
        if(i%15==0){
      count+=1;
        }
    } 
    System.out.println(minn+"到"+maxn+"这个范围内能被3和5整除的数的个数为："+count);
    }
}

```

## <u>*☆☆☆☆☆☆☆☆☆☆☆☆☆☆☆☆☆☆☆☆☆题目3*</u>

需求：世界最高山峰是珠穆朗玛峰(8844.43米=8844430毫米)，

​	假如我有一张足够大的纸，它的厚度是0.1毫米。

​	请问，我折叠多少次，可以折成珠穆朗玛峰的高度?

### 参考答案

```java
import java.util.Scanner;

public class MyExercise{
    public static void main(String[] ags){
        int count=0;
        double height=0.1;
        while(height<8844430){
        height*=2;
        count++;
        
        }
        System.out.println("为了达到珠穆朗玛峰的高度，所需要折叠的次数为："+count+"次");
    }
}
```

## <u>*☆☆☆☆☆☆☆☆☆☆☆☆☆☆☆☆☆☆☆☆☆题目4*</u>

***<u>需求：给你一个整数 x 。</u>***

​           ***<u>如果 x 是一个回文整数，打印 true ，否则，返回 false 。</u>***

***<u>解释：回文数是指正序（从左向右）和倒序（从右向左）读都是一样的整数。</u>***

***<u>例如，121 是回文，而 123 不是。</u>***

### 参考答案

```java
import java.util.Scanner;

public class MyExercise{
    public static void main(String[] ags){
      System.out.println("请输入一个整数：");
      Scanner reader=new Scanner(System.in);
      int num,get,result=0,tem;
      num=reader.nextInt();
      tem=num;
      while(num!=0){
          get=num%10;//<u>*☆☆☆☆☆☆☆☆☆☆☆☆☆☆get 就是从原来的那个数里面取最右边的那个数字
          result=result*10+get;//<u>*☆☆☆☆☆☆☆☆☆☆☆☆☆☆要把新取的个位数加进来，之前的数字必须向前移动一位
          num/=10;
      }
      System.out.println(result==tem?true:false);
    }
}
```

## 题目5

需求：

​       给定两个整数，被除数dividend和除数divisor（都是正数，且不超过int的范围） 。

​      将两数相除，要求不使用乘法、除法和 % 运算符。

​      得到商和余数。

### 参考答案

```java

import java.util.Scanner;
import static java.lang.Math.*;

public class MyExercise{
    public static void main(String[] ags){
        Scanner reader=new Scanner(System.in);
        int dividened,divisior;
        do{
        System.out.println("请输入被除数:");
        dividened=reader.nextInt();
        }while(dividened<0 || dividened >Math.pow(2,31)-1);
        
        do{
        System.out.println("请输入除数:");
        divisior=reader.nextInt();
        }while(divisior<0 || divisior>Math.pow(2,31)-1);
        int count=0,sum=0,remainder=0;
        while(sum<dividened){
            if(sum+divisior>dividened){
              remainder=dividened-sum;
              break;
            }
        sum+=divisior;
        count++;
        }
        System.out.println("商为："+count+"    余数为："+remainder);
        
    }
}

/*
//更优算法：


import java.util.Scanner;
import static java.lang.Math.*;

public class MyExercise{
    public static void main(String[] ags){
        Scanner reader=new Scanner(System.in);
        int dividened,divisior;
        do{
        System.out.println("请输入被除数:");
        dividened=reader.nextInt();
        }while(dividened<0 || dividened >Math.pow(2,31)-1);
        
        do{
        System.out.println("请输入除数:");
        divisior=reader.nextInt();
        }while(divisior<0 || divisior>Math.pow(2,31)-1);
        int count=0;
        while(dividened>=divisior){
               dividened-=divisior;
               count++;
        }//dividened 直接可以作为存储余数的变量
        System.out.println("商为："+count+"    余数为："+dividened);
        
    }
}






*/
```

## 题目6（较难）

已知2019年是猪年，请在控制台输出从1949年到2019年中所有是猪年的年份。

### 训练提示

1. 1949到2019有很多年？逐个判断这么多年份肯定要用循环。
2. 用什么条件来判断是否是猪年？

### 解题方案

1. 使用for循环逐年判断，根据2019是猪年这个条件，使用if来判断其他是猪年的年份。

### 操作步骤

1. 定义for循环，1949到2019的年份是循环次数。
2. 对每个年份逐个判断，如果年份和2019的差值是12的倍数，说明这年是猪年
3. 打印符合条件的年份

### 参考答案

```java
public class MyExercise{
    public static void main(String[] ags){
        System.out.println("1949到2019的猪年有：");
    for(int year=2019;year>=1949;year-=12){
    System.out.print(year+"\t");
    }
    }
}


/*
public class Demo1 {
    public static void main(String[] args) {
        //1.循环开始是1949 结束是2019
        for (int i = 1949; i < 2019; i++) {
            //2.如果年份和2019年的差值是12的倍数 则说明是猪年
            if( (2019 - i) % 12 == 0 ){
                //3.打印符合条件的年份
                System.out.println(i);
            }
        }
    }
}
*/
```

## 题目7（较难）

中国有闰年的说法。闰年的规则是：**<u>*四年一闰，百年不闰，四百年再闰*</u>**。（年份能够被4整除但不能被100整除算是闰年，年份能被400整除也是闰年）。请打印出1988年到2019年的所有闰年年份。

### 训练提示

1. 从1988年到2019年有很多年，每年都需要判断，用什么知识点对每年进行判断？

### 解题方案

1. 使用while循环完成

2. 使用for循环完成

   以下以方案2为准

### 操作步骤

1. 定义for循环，循环开始是1988，结束是2019
2. 在循环中对年份进行判断  
3. 如果符合闰年的判断条件，则打印该年份

### 参考答案

```java

public class MyExercise{
    public static void main(String[] ags){
        System.out.println("1989到2019的闰年有：");
    for(int year=1989;year<=2019;year++){
        if(（year%4==0 && year%100!=0） ||  year%400 ==0){
                System.out.print(year+"\t");
        }
    }
    }
}
```



















