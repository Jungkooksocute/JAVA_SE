## 第一题：

### 需求：

​	在黑马程序员中有很多员工(Employee)。

​	按照工作内容不同分教研部员工(Teacher)和行政部员工(AdminStaff)

1. 教研部根据教学的方式不同又分为讲师(Lecturer)和助教(Tutor)
2. 行政部根据负责事项不同,又分为维护专员(Maintainer),采购专员(Buyer)
3. 公司的每一个员工都编号,姓名和其负责的工作
4. 每个员工都有工作的功能，但是具体的工作内容又不一样。

```java
public class Administaff extends Employee{
    private String duty="administrate";

    public Administaff() {
    }

    public Administaff(String duty) {
        this.duty = duty;
    }

    public Administaff(String id, String name, String duty) {
        super(id, name);
        this.duty = duty;
    }
}//1
public class Buyer extends Administaff{
    public Buyer() {
    }

    public Buyer(String duty) {
        super(duty);
    }

    public Buyer(String id, String name, String duty) {
        super(id, name, duty);
    }
    public void work(){
        System.out.println("采购专员：采购");
    }
}//2
public class Employee {
    private String id;
    private String name;

    public Employee() {
    }

    public Employee(String id, String name) {
        this.id = id;
        this.name = name;
    }

    public String getId() {
        return id;
    }

    public void setId(String id) {
        this.id = id;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }
}//3
public class Lecturer extends Teacher{
    public Lecturer() {
    }

    public Lecturer(String duty) {
        super(duty);
    }

    public Lecturer(String id, String name, String duty) {
        super(id, name, duty);
    }
    public void work(){
        System.out.println("讲师：讲课");
    }
}//4
public class Maintainer extends Administaff{
    public Maintainer() {
    }

    public Maintainer(String duty) {
        super(duty);
    }

    public Maintainer(String id, String name, String duty) {
        super(id, name, duty);
    }
    public void work(){
        System.out.println("维护专员：维护");
    }
}//5
public class Teacher extends Employee{
    private String duty="teach";

    public Teacher() {
    }

    public Teacher(String duty) {
        this.duty = duty;
    }

    public Teacher(String id, String name, String duty) {
        super(id, name);
        this.duty = duty;
    }
}//6
public class Tutor extends Teacher{
    public Tutor() {
    }

    public Tutor(String duty) {
        super(duty);
    }

    public Tutor(String id, String name, String duty) {
        super(id, name, duty);
    }
    public void work(){
        System.out.println("助教：帮忙讲课");
    }
}//7


//test
public class test {
    public static void main(String[] args) {
        Lecturer a1=new Lecturer();
        Tutor a2=new Tutor();
        Maintainer a3=new Maintainer();
        Buyer a4=new Buyer();
        a1.work();
        a2.work();
        a3.work();
        a4.work();
    }
}





```





## 第二题：

### 需求：

​	 在传智教育的tlias教学资源管理系统中，存在学生、老师角色会进入系统。

### 分析：

​	学生信息和行为（名称，年龄，所在班级，查看课表，填写听课反馈fillForm）

​	老师信息和行为（名称，年龄，部门名称，查看课表，发布问题publishForm）

​	定义角色类作为父类包含属性（名称，年龄），行为（查看课表）

​	定义子类：学生类包含属性（所在班级），行为（填写听课反馈）

​	定义子类：老师类包含属性（部门名称），行为（发布问题）

```java
public class member {
    private String name;
    private int age;

    public member() {
    }

    public member(String name, int age) {
        this.name = name;
        this.age = age;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }
    public void schedule(){
        System.out.println("查看课表");
    }
}//1
public class student extends member{
    private int part;

    public student() {
    }

    public student(String name, int age, int part) {
        super(name, age);
        this.part = part;
    }

    public void fillform(){
        System.out.println("填写听课反馈");
    }
    public int getPart() {
        return part;
    }

    public void setPart(int part) {
        this.part = part;
    }
}//2
public class teacher extends member{
    private String department;

    public teacher() {
    }

    public teacher(String name, int age, String department) {
        super(name, age);
        this.department = department;
    }
    public void publishForm(){
        System.out.println("发布问题");
    }
    //

    public String getDepartment() {
        return department;
    }

    public void setDepartment(String department) {
        this.department = department;
    }
}//3
//
public class Test {
    public static void main(String[] args) {
        student a=new student();
        teacher b=new teacher();
        a.fillform();
        a.schedule();
        b.publishForm();
        b.schedule();
    }
}


```





## 第三题：

​	1.手机类Phone

​	  属性:品牌brand,价格price

### 思考:

​	假设所有的手机都有属性屏幕的尺寸(int size),而且假设所有手机的屏幕尺寸为6,应该如何实现?  

### 提示：

​	可以把size定义为静态







## 第四题：

### 需求：

​	分析以下需求，并用代码实现

​	1.定义Person类

​		属性：

​			姓名name、性别gender、年龄age、国籍nationality；

​		方法：

​			吃饭eat、睡觉sleep，工作work。

​	2.根据人类，创建一个学生类Student

​		增加属性：

​			学校school、学号stuNumber；

​		重写工作方法（学生的工作是学习）。	

​	3.根据人类，创建一个工人类Worker

​		增加属性：

​			单位unit、工龄workAge；

​		重写工作方法（工人的工作是盖房子）。

​	4.根据学生类，创建一个学生干部类 StudentLeader

​		增加属性：

​			职务job；

​		增加方法：开会meeting。

​	5.编写测试类分别对上述3类具体人物进行测试。

​	6.要求运行结果:

```java
学生需要学习!
工人的工作是盖房子!
学生干部喜欢开会!
```



## 第五题：

### 需求：

​	1.定义项目经理类 
​		属性：
​			姓名 工号 工资 奖金
​		行为：
​			工作work
​	2.定义程序员类
​		属性：
​			姓名 工号 工资
​		行为：
​			工作work

​	3.向上抽取一个父类,让这两个类都继承这个父类,共有的属性写在父类中，子类重写父类中的方法

​	4.编写测试类:完成这两个类的测试









## 第六题：

### 需求：

​	根据需求完成代码:

​	1.定义动物类

​		属性：
​			年龄，颜色
​		行为:
​			eat(String something)方法(无具体行为,不同动物吃的方式和东西不一样,something表示吃的东西)

​		生成空参有参构造，set和get方法

​	2.定义狗类继承动物类	  

​		行为:
​			eat(String something)方法,看家lookHome方法(无参数)

​	3.定义猫类继承动物类

​		行为:

​			eat(String something)方法,逮老鼠catchMouse方法(无参数)

​	4.定义Person类

​		属性：
​			姓名，年龄

​		行为：
​			keepPet(Dog dog,String something)方法

​			功能：喂养宠物狗，something表示喂养的东西

​			该方法调用后打印结果为：颜色为黑色的2岁的狗，在吃骨头

​		行为：
​			keepPet(Cat cat,String something)方法
​			功能：喂养宠物猫，something表示喂养的东西

​			该方法调用后打印结果为：颜色为白色的2岁的猫，在吃小鱼干

​	5.生成空参有参构造，set和get方法  

​	6.测试以上方法

