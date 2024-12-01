### 

## 题目3

有如下员工信息：

~~~java
姓名：张三，工资：3000
姓名：李四，工资：3500
姓名：王五，工资：4000
姓名：赵六，工资：4500
姓名：田七，工资：5000
~~~

先需要将所有的员工信息都存入ArrayList集合中，并完成如下操作：

1、判断是否有姓名为“王五”的员工，如果有，改名为“王小五”

2、判断是否有姓名为“赵六”的员工，如果有，将其删除

3、给姓名为“田七”的员工，涨500工资

### 训练目标

ArrayList集合的修改元素和删除元素API

### 训练提示

1、需要定义员工类，将员工信息进行封装

2、创建ArrayList集合，创建员工对象，将所有员工对象存入集合

3、需要判断集合中元素的信息，那么肯定需要遍历集合获取到所有元素

4、ArrayList集合中，修改元素和删除元素的方法是什么？在遍历集合时，删除了集合中的元素，会不会对遍历产生影响呢？如果会，该怎么解决？

### 训练步骤

1、定义员工类Worker，私有属性name和salary，分别为String和int类型，表示姓名和工资，提供构造、get、set方法

2、创建ArrayList集合，泛型为Worker类型，创建员工对象，将所有员工对象存入集合

3、使用for循环遍历集合，获取到每一个元素。

​	3.1、判断元素的name属性，如果符合条件，作出相应的修改或者删除。

​	3.2、遍历时如果删除元素，后面的元素会往前走，索引再加1就会有元素遗漏，所以删除后遍历索引要相应的减1，防止有元素遍历不到。

### 参考答案

~~~java
public class test {
    public static void main(String[] args) {
        ArrayList<member> list=new ArrayList<>();
        /*member m1=new member("张三",3000);
        member m2=new member("李四",3500);
        member m3=new member("王五",4000);
        member m4=new member("赵六",4500);
        member m5=new member("田七",4000);

        list.add(m1);
        list.add(m2);
        list.add(m3);
        list.add(m4);
        list.add(m5);
*/
        list.add(new Worker("张三", 2000));
        list.add(new Worker("李四", 2500));
        list.add(new Worker("王五", 3000));
        list.add(new Worker("赵六", 3500));
        list.add(new Worker("田七", 4000));
        
        int index;
        member tem=new member();

        //操作1
        index=contains("王五",list);
        if(index>=0){
            tem=list.get(index);
            member newM=new member("王小五",tem.getSalary());
            list.set(index,newM);
            ///*为了方便起见，如果只更改一两个数据，是可以直接改的，因为引用数据类型的变量名传递的是地址*/list.get(index).setName("王小五");
        }
        else{
            System.out.println("不存在姓名为“王五”的员工");
        }

        //操作2
        index=contains("赵六",list);
        if(index>=0){
            list.remove(index);
        }
        else{
            System.out.println("不存在姓名为“王五”的员工");
        }

        //操作3
        index=contains("田七",list);
        if(index>=0){
            tem=list.get(index);
            member newM=new member(tem.getName(),tem.getSalary()+500);
            list.set(index,newM);
            ///*只改变一两个数据时可以直接改变*/ list.get(index).setSalary(list.get(index).getSalary()+500);
        }
        else{
            System.out.println("不存在姓名为“田七”的员工");
        }
/*//打印结果
        for (int i = 0; i < list.size(); i++) {
            System.out.println("姓名："+list.get(i).getName()+"\t,"+
                            "工资："+list.get(i).getSalary()+"\t");
        }
*/

    }
//
    public static int contains(String s,ArrayList<member> qw){
        for (int i = 0; i <qw.size() ; i++) {
            if(s.equals(qw.get(i).getName())){

                    return i;
            }

        }
                    return -1;
    }


}

~~~



## **<u>*//方法2  当每个条件的实现都需要进行循环遍历的时候，不如把他们都写在一个遍历下用不同的if 分开*</u>**

```
public class Worker {
    private String name;
    private int salary;

    public Worker() {
    }
    
    public Worker(String name, int salary) {
        this.name = name;
        this.salary = salary;
    }
    
    public String getName() {
        return name;
    }
    
    public void setName(String name) {
        this.name = name;
    }
    
    public int getSalary() {
        return salary;
    }
    
    public void setSalary(int salary) {
        this.salary = salary;
    }

}

import java.util.ArrayList;

public class Test03 {
    public static void main(String[] args) {
        // 创建集合对象
        ArrayList<Worker> list = new ArrayList<>();
        // 创建员工对象并添加到集合中
        list.add(new Worker("张三", 2000));
        list.add(new Worker("李四", 2500));
        list.add(new Worker("王五", 3000));
        list.add(new Worker("赵六", 3500));
        list.add(new Worker("田七", 4000));
        // 判断是否有王五，如果有，改名为王小五
        // 判断是否有赵六，如果有，删除赵六
        // 给田七加500块工资
        for (int i = 0; i < list.size(); i++) {
            Worker w = list.get(i);
            if ("王五".equals(w.getName())) {
                w.setName("王小五");//
               // list.set(i, w);可有可无这句话
            }
            if ("赵六".equals(w.getName())) {
                // 注意，一旦删除元素，后面的元素会往前走，索引再加1就会有元素遗漏，所以删除后要--
                list.remove(i--);
            }
            if ("田七".equals(w.getName())) {
                w.setSalary(w.getSalary() + 500);
               // list.set(i, w);可有可无这句话
            }
        }
        // 再次遍历查看结果
        for (int i = 0; i < list.size(); i++) {
            Worker w = list.get(i);
            System.out.println(w.getName() + "---" + w.getSalary());
        }
    }
}
```



## 题目4（综合）

利用面向对象的思想设计一个图书管理系统。图书的属性有：编号，书名，作者，价格。要求提供如下功能：

1、提供操作菜单，可以选择要进行的操作。

2、可以添加图书，添加图书时，编号需要唯一，添加成功，返回到菜单。

3、可以查询图书，显示所有图书信息，然后返回到菜单。

4、可以根据书名，查询单本图书信息，显示信息后，返回到菜单。

5、可以删除图书，通过编号删除，删除成功后，返回到菜单。

6、可以修改图书的信息，但编号不可以修改，修改成功后，返回到菜单。

7、可以退出系统，结束程序运行。

提示：

1、所有图书信息由键盘录入

2、图书的价格可以定义为字符串类型，因为在键盘录入时，不可以先使用nextInt()方法获取整数然后再使用next()方法获取字符串，这样会导致next()方法获取不到数据。



### 训练目标

ArrayList集合API的综合运用、编程逻辑的锻炼

### 训练提示

1、首先需要创建一个图书类，封装图书信息。

2、提供操作菜单，可以通过键盘录入不同的数字来表示不同的操作，选择结构语句可以实现该需求。

3、管理图书，需要将图书存放起来，首先需要创建集合容器。

4、添加图书，即将图书存入集合中，但存入之前需要判定编号的唯一性，如果编号存在，需要重新录入。

5、查询所有图书，即为遍历集合显示信息。

6、查询单本图书，需要录入图书名称，遍历集合进行查询。

7、修改图书信息，需要根据编号先找到该图书，修改其除了编号之外的信息，存入集合覆盖原来的信息。

8、删除图书信息，需要根据编号先找到该图书，根据索引直接删除即可。

9、退出系统功能，借助结束程序的API实现即可。

### 训练步骤

1、创建Book类，属性String类型的id，name，author，price。提供构造方法、get和set方法。

2、创建测试类Test04，在main方法中，创建键盘录入对象，创建ArrayList集合对象用于存储图书。

3、使用输出语句定义一个操作菜单，包含添加、查看全部、查看单个、修改、查询、退出功能，使用switch语句对键盘录入的菜单项进行判断。

4、定义方法实现判断id是否已经存在。方法返回值boolean类型，参数列表为集合ArrayList和要查找的id字符串。遍历集合，判断id是否与集合中的Book对象的id相同，如果有相同，返回true，否则返回false

5、定义方法实现添加功能。方法返回值void，参数列表为集合ArrayList。在方法中，先使用键盘录入获取用户录入的id信息，调用方法判断id是否存在，如果存在，重新录入，如果不存在，再依次获取图书的其他信息，创建图书对象，并将图书对象存入集合中，输出添加成功的提示。

6、定义方法实现查看所有图书。方法返回值void，参数列表为集合ArrayList。如果集合长度为0，给出提示，结束方法，否则遍历集合，获取每个图书对象，再调用对象的get方法，获取所有信息展示即可。

7、定义方式实现根据名称查看一本图书。方法返回值void，参数列表为集合ArrayList。键盘录入图书的名称，遍历集合，获取每个图书的名称信息进行比较，如果相同，输出该图书信息，结束方法。否则输出不存在该图书。

8、定义方法实现根据编号修改图书信息。方法返回值void，参数列表为集合ArrayList。键盘录入图书编号，查询该编号是否存在，如果存在，再依次录入图书的修改后信息，创建新的图书对象，存入集合，将原对象覆盖，给出成功的提示，否则提示该编号图书不存在。

9、定义方法实现根据编号删除图书信息。方法返回值void，参数列表为集合ArrayList。键盘录入图书编号，查询该编号是否存在，如果存在，根据索引删除该对象，返回成功的提示，否则提示该编号的图书不存在。

10、退出系统的功能直接调用System的exit方法实现即可。

### 参考答案

~~~java
public class book {
    private String ISBN;
    private String name;
    private String author;
    private String price;

    public book() {
    }

    public book(String ISBN, String name, String author, String price) {
        this.ISBN = ISBN;
        this.name = name;
        this.author = author;
        this.price = price;
    }

    public String getISBN() {
        return ISBN;
    }

    public void setISBN(String ISBN) {
        this.ISBN = ISBN;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public String getAuthor() {
        return author;
    }

    public void setAuthor(String author) {
        this.author = author;
    }

    public String getPrice() {
        return price;
    }

    public void setPrice(String price) {
        this.price = price;
    }
}//book标准类的创建









import java.util.ArrayList;
import java.util.Scanner;
public class test {
    public static void main(String[] args) {
        ArrayList<book> inventory=new ArrayList<>();   // 创建集合用于存储图书信息
        Scanner reader=new Scanner(System.in); // 键盘录入
        int choose;
        while (true) {
            System.out.println("-----欢迎来到图书管理系统-----");
            System.out.println("添加图书。请输入1；");
            System.out.println("查询所有图书信息。请输入2；");
            System.out.println("查询单本图书信息。请输入3；");
            System.out.println("删除图书。请输入4；");
            System.out.println("修改图书信息。请输入5；");
            System.out.println("退出系统。请输入6；");
            System.out.println("请根据需要输入所需执行的操作：");
            choose=reader.nextInt();//输入操作
            switch(choose){
                case 1:{//添加图书
                    addBook(inventory);
                    break;
                }
                case 2: {//查询所有图书信息
                    showAll(inventory);
                    break;
                }
                case 3: {//查询单本图书信息
                    enqBook(inventory);
                    break;
                }
                case 4:{//删除图书
                    deleBook(inventory);
                    break;
                }
                case 5:{//修改图书信息
                    setBook(inventory);
                    break;
                }
                case 6:
                    System.exit(0);//退出
                default:
                    System.out.println("输入错误");
                    break;//错误输入

            }//




        }
        //main里的其他操作

    }
    //class的其他类方法
    public static int countainIndex(ArrayList<book> ju,String id){
        for (int i = 0; i <ju.size() ; i++) {
            if(ju.get(i).getISBN().equals(id)){
                return i;
            }
        }
        return -1;
    }//查询编号
    public static boolean countains(ArrayList<book> ju,String id){
        if(countainIndex(ju,id)>=0){
            return true;
        }
        else{
            return false;
        }
    }//存在 true ;不存在 false

    public static void addBook(ArrayList<book> ju) {
        Scanner reader = new Scanner(System.in);
        String id;
        while (true) {
            System.out.println("请输入要添加图书的ISDN：");
            id = reader.next();
            if (countains(ju, id)) {
                System.out.println("该图书已存在，添加失败");

            }
            else {
                System.out.println("请输入要添加图书的书名：");
                String name=reader.next();
                System.out.println("请输入要添加图书的作者：");
                String author=reader.next();
                System.out.println("请输入要添加图书的价格：");
                String price=reader.next();
                book newB=new book(id,name,author,price);
                ju.add(newB);
                System.out.println("添加成功");
                break;
            }
        }
    }//

    public static void showAll(ArrayList<book> ju){
        System.out.println("ISDN:\t\t书名\t\t作者\t\t价格\t");
        for (int i = 0; i <ju.size() ; i++) {
            System.out.println(ju.get(i).getISBN()+"\t\t"+
                    ju.get(i).getName()+"\t\t"+ju.get(i).getAuthor()
            +"\t\t"+ju.get(i).getPrice()+"\t");
        }
    }//查看所有图书信息

    public static void enqBook(ArrayList<book> ju){
        System.out.println("请输入图书的名字：");
        Scanner reader=new Scanner(System.in);
        String name=reader.next();
        for (int i = 0; i <ju.size() ; i++) {
            if(ju.get(i).getName().equals(name)){
                System.out.println("ISBN:"+ju.get(i).getISBN()+"\t书名："+
                        ju.get(i).getName()+"\t作者："+ju.get(i).getAuthor()+
                        "\t价格："+ju.get(i).getPrice());
                return;
            }

        }
        System.out.println("该书不存在");
        return;
    }//查询单本图书信息

    public static void deleBook(ArrayList<book> ju){
        System.out.println("请输入书的ISBN：");
        Scanner reader=new Scanner(System.in);
        String id=reader.next();
        int index=countainIndex(ju,id);
        if(index>=0){
            ju.remove(index);
            System.out.println("删除成功");
        }
        else{
            System.out.println("不存在这本书，删除失败");
        }
        return;
    }//删除图书

    public static void setBook(ArrayList<book> ju){
        Scanner reader=new Scanner(System.in);
        System.out.println("请输入要修改图书的ISBN：");
        String id=reader.next();
        int index=countainIndex(ju,id);
        if(index>=0){
            System.out.println("请输入修改后书名：");
            String name=reader.next();
            System.out.println("请输入修改后作者：");
            String author=reader.next();
            System.out.println("请输入修改后价格：");
            String price=reader.next();
            book newB=new book(id,name,author,price);
            ju.set(index,newB);
            System.out.println("修改完成");
        }
        else{
            System.out.println("不存在该图书，修改失败");
        }

        return;

    }//修改图书

}








~~~



### 