# 1、设计模式简介

设计模式（Design pattern）代表了最佳的实践，通常被有经验的面向对象的软件开发人员所采用。设计模式是软件开发人员在软件开发过程中**面临的一般问题的解决方案**。这些解决方案是众多软件开发人员经过相当长的一段时间的试验和错误总结出来的。

设计模式是一套被反复使用的、多数人知晓的、经过分类编目的、代码设计经验的总结。使用**设计模式是为了重用代码、让代码更容易被他人理解、保证代码可靠性**。 毫无疑问，设计模式于己于他人于系统都是多赢的，设计模式使代码编制真正工程化，设计模式是软件工程的基石，如同大厦的一块块砖石一样。项目中合理地运用设计模式可以完美地解决很多问题，每种模式在现实中都有相应的原理来与之对应，每种模式都描述了一个在我们周围不断重复发生的问题，以及该问题的核心解决方案，这也是设计模式能被广泛应用的原因。

# 2、设计模式的类型

根据设计模式的参考书 **Design Patterns - Elements of Reusable Object-Oriented Software（中文译名：设计模式 - 可复用的面向对象软件元素）** 中所提到的，总共有 23 种设计模式。这些模式可以分为三大类：<font style='color:red;'>**创建型模式（Creational Patterns）**</font>、<font style='color:red;'>**结构型模式（Structural Patterns）**</font>、<font style='color:red;'>**行为型模式（Behavioral Patterns）**</font>。



| 序号 | 模式 & 描述                                                  | 包括                                                         |
| :--- | :----------------------------------------------------------- | :----------------------------------------------------------- |
| 1    | **创建型模式**<br /> 这些设计模式提供了一种在创建对象的同时隐藏创建逻辑的方式，而不是使用 new 运算符直接实例化对象。<br />这使得程序在判断针对某个给定实例需要创建哪些对象时更加灵活。 | 单例模式（Singleton Pattern）<br />工厂模式（Factory Pattern）<br />抽象工厂（Abstract Factory Pattern）<br />建造者模式（Builder Pattern）<br />原型模式（Prototype Pattern） |
| 2    | **结构型模式** <br />用于描述如何将类和对象按某种布局组成更大的结构。<br />这些设计模式关注类和对象的组合。<br />继承的概念被用来组合接口和定义组合对象获得新功能的方式。 | 适配器模式（Adapter Pattern）<br />桥接模式（Bridge Pattern）<br />组合模式（Composite Pattern）<br />装饰器模式（Decorator Pattern）<br />外观模式（Facade Pattern）<br />享元模式（Flyweight Pattern）<br />代理模式（Proxy Pattern） |
| 3    | **行为型模式** <br />用于描述类和对象之间怎样相互协作共同完成单个对象无法单独完成的任务，以及怎样分配职责<br />这些设计模式特别关注对象之间的通信。 | 责任链模式（Chain of Responsibility Pattern）<br />命令模式（Command Pattern）<br />解释器模式（Interpreter Pattern）<br />迭代器模式（Iterator Pattern）<br />中介者模式（Mediator Pattern）<br />备忘录模式（Memento Pattern）<br />观察者模式（Observer Pattern）<br />状态模式（State Pattern）<br />策略模式（Strategy Pattern）<br />模板模式（Template Pattern）<br />访问者模式（Visitor Pattern） |

# 3、UML图

统一建模语言（UML)是用来设计软件的可视化建模语言，它的特点是简单、统一、图形化、能表达软件设计中的动态和静态信息。

UML从目标系统的不同角度出发，定义了用例图、类图、对象图、状态图、活动图、时序图、协作图、构建图、部署图等9中图。

## 3.1 类图概述

<font style='color:red'>**类图（Class diagram)是显示了模型的静态结构**</font>，特别是模型中存在的类，类的内部结构以及他们与其他类的关系等。类图不显示暂时性的信息。类图是面向对象建模的主要组成部分。

## 3.2类图的作用

- 在软件工程中，类图是一种静态的结构图，描述了系统的类的集合，类的属性和类之间的关系，可以简化了人们对系统的理解；
- 类图是系统分析和设计阶段的重要产物，是系统编码和测试的重要模型。

## 3.3 类图表示方法

### 3.3.1 类的表示方式

在UML类图中，类使用包含<font style='color:red;'> **类名**</font>、<font style='color:red;'> **属性（field)**</font>和 <font style='color:red;'>**方法（method)** </font>,使用带有分割的矩形表示。

属性/方法名称前的符号表示这个属性/方法的可见性，UML类图中表示可见性的符号有三种：

> - **+：表示public**
> - **-：表示private**
> - **#：表示protected**
> - **还有一种表示默认，什么都不加**
>

属性的完整表示方式为： **可见性  名称：类型 [ = 缺省值]**

方法的完整表示方式为： **可见性  名称(参数列表)[ : 返回类型]**

![image-20220220090836685](.\images\设计模式\331-1.png)



> 注意：
>
> 1.中括号中的内容表示是可选的
>
> 2.也有将类型放在变量名前面的，返回值类型放在方法名前面



举个栗子：

![image-20220220090836685](.\images\设计模式\331-2.png)

上述Demo定义了两个属性，三个方法：

> - name 属性：修饰符为private,类型为String
> - age 属性：修饰符为private,类型为int
>
> - method() 方法：修饰符为public，没有参数没有返回值
> - method1() 方法：修饰为private,没有参数，返回值类型为String
> - method2() 方法：修饰符为protected,接收两个参数，第一个参数类型为int，第二个参数类型为int,返回值为int



### 3.3.2 类与类直接关系的表示方式

#### 3.3.2.1  关联关系

关联关系是对象之间的一种引用关系，用于表示一类对象与另一类对象之间的关系。关联关系是类和类之间最常见的一种关系，分为**一般关联关系**、**聚合关系**和**组合关系**。（聚合关系和组合关系也属于关类关系）。

一般关联关系可以分为：单向关联、双向关联、自关联。

1.单向关联(如：顾客（Customer）拥有地址（Address）)

在UML类图中，<font style='color:red;'>**单向关类用一个带箭头的实线表示**</font>。

2.双向关联（如：顾客（Customer）购买商品（Product），反之，卖出去的商品总是与某个顾客与之相关联）

所谓的双向关联就是<font style="color:red;">**双方各自持有对方类型的成员变量**</font>。

在UML类图中，<font style="color:red;">**双向关联用一个不带箭头的直线表示**</font>。

3、自关联

在UML类图中，自关联用指向自身的带箭头实线表示。（也就是自己包含自己）

#### 3.3.2.2 聚合关系

聚合关系式关联关系的一种，是强关联关系，是<font style='color:red;'>**整体和部分之间的关系**</font>。

聚合关系也是**通过成员对象来实现的**，其中**<font style='color:red;'>成员对象是整体对象的一部分</font>，但是<font style='color:red;'>成员对象可脱离整体对象而独立存在</font>**。

在UML类图中，聚合关系可以用<font style='color:red;'>**空心菱形的实线来表示，菱形指向整体**</font>。（如学校与老师）



![image-20220220090836685](.\images\设计模式\3322-1.png)

#### 3.3.2.3 组合关系

组合表示类之间的整体与部分关系，但它是一种**更强烈的聚合关系**。

在组合关系中，<font style='color:red;'>**整体对象可以控制部分对象的生命周期**</font>，一旦整体对象不存在，部分对象也将不存在，部分对象不能脱离整体对象而存在。

在UML类图中，<font style='color:red;'>**组合关系用带是实心菱形的实线来表示，菱形指向整体**</font>。（如头和嘴的关系）

![image-20220220090836685](.\images\设计模式\3323-1.png)

#### 3.3.2.4 依赖关系

依赖关系是一种使用关系，它是对象之间耦合度最弱的一种关联方式，是<font style='color:red;'>**临时性的关联**</font>。在代码中，**某个类的方法通过局部变量、方法的参数或者对静态方法的调用来访问另外一个类**（被依赖类）中的某些方法来完成一些职责。

在UML类图中，<font style='color:red;'>**依赖关系使用带箭头的虚线表示，箭头从使用类指向被依赖的类**</font>。（如司机和汽车）

![image-20220220090836685](.\images\设计模式\3324-1.png)

#### 3.3.2.5 继承关系

继承关系是对象之间耦合度最大的一种关系，是<font style='color:red;'>**父类与子类之间的关系**</font>，是一种继承关系。

在UML类图中国，<font style='color:red;'>**泛化关系用空心三角箭头的实线来表示，箭头从子类指向父类**</font>。在代码实现时，**使用面向对象的继承机制来实现泛化关系**。（如Student类和Teacher 都是继承Person类）

![image-20220220090836685](.\images\设计模式\3325-1.png)

#### 3.3.2.6 实现关系

实现关系时接口与实现类之间的关系。在这种关系中，类实现了接口，类中的操作实现了接口中所有声明的所有抽象操作。

在UML类图中，<font style='color:red;'>**实现关系使用带空心的三角箭头的虚线来表示，箭头从实现类指向接口**</font>。（汽车和船实现了交通工具）

![image-20220220090836685](.\images\设计模式\3326-1.png)



# 4、设计模式的六大原则

**1、开闭原则（Open Close Principle）**

开闭原则的意思是：**对扩展开放，对修改关闭**。在程序需要进行拓展的时候，不能去修改原有的代码，实现一个热插拔的效果。简言之，是为了使程序的扩展性好，易于维护和升级。想要达到这样的效果，我们需要使用接口和抽象类，后面的具体设计中我们会提到这点。

**2、里氏代换原则（Liskov Substitution Principle）**

里氏代换原则是面向对象设计的基本原则之一。 里氏代换原则中说，任何基类可以出现的地方，子类一定可以出现。LSP 是继承复用的基石，只有当派生类可以替换掉基类，且软件单位的功能不受到影响时，基类才能真正被复用，而派生类也能够在基类的基础上增加新的行为。里氏代换原则是对开闭原则的补充。实现开闭原则的关键步骤就是抽象化，而基类与子类的继承关系就是抽象化的具体实现，所以里氏代换原则是对实现抽象化的具体步骤的规范。

**3、依赖倒转原则（Dependence Inversion Principle）**

这个原则是开闭原则的基础，具体内容：针对接口编程，依赖于抽象而不依赖于具体。

**4、接口隔离原则（Interface Segregation Principle）**

这个原则的意思是：使用多个隔离的接口，比使用单个接口要好。它还有另外一个意思是：降低类之间的耦合度。由此可见，其实设计模式就是从大型软件架构出发、便于升级和维护的软件设计思想，它强调降低依赖，降低耦合。

**5、迪米特法则，又称最少知道原则（Demeter Principle）**

最少知道原则是指：一个实体应当尽量少地与其他实体之间发生相互作用，使得系统功能模块相对独立。

**6、合成复用原则（Composite Reuse Principle）**

合成复用原则是指：尽量使用合成/聚合的方式，而不是使用继承。



# 5、创建者模式

## 5.1单例模式

单例模式 是Java中最简单的设计模式之一。这种类型的设计模式属于创建模式，它提供了一种创建对象的最佳方式。

这种模式涉及到一个单一的类，**该类负责创建自己的对象**。同时确保只有**单个对象被创建**，这个类**提供了一种访问其唯一对象的方式**，可以**直接访问，不需要实例化该类的对象**。

### 5.1.1 单例模式的结构

单例模式的主要有以下角色：

1）单例类。只创建一个实例的类

2）访问类。使用单例类

### 5.1.2 单例模式的实现

> 单例涉及模式分类两种：
>
> 饿汉模式：类加载会导致该单实例对象被创建
>
> 懒汉模式：类加载不会导致该单实例对象被创建，而是首次使用该对象的才会创建

1、饿汉式 ——方式1 （静态变量方式）

```java
/**
 * 饿汉式：静态成员变量的方式
 */
public class Singleton {
    //1. 私有构造方法
    private Singleton() {}

    //2.再本类中创建本类的对象
    private static Singleton instance = new Singleton();

    //提供一个公共的访问方式，让外界获取该对象
    public static Singleton getInstance() {
        return instance;
    }
}
```

```java
public class SingletonTest {
    @Test
    public void getSingleton(){
        Singleton instance1 = Singleton.getInstance();
        System.out.println(instance1);
        Singleton instance2 = Singleton.getInstance();
        System.out.println(instance2);

    }
}
```

测试输出结果

```java
com.design.pattern.singleton.demo1.Singleton@3b764bce
com.design.pattern.singleton.demo1.Singleton@3b764bce
```

2、饿汉式——方式2  （静态代码块方式）

```java
/**
 * 静态代码块
 */
public class Singleton {
    //私有构造方法
    private Singleton() {}
    
    //申明Singleton类型的变量
    private static Singleton instance;//null

    //在静态代码块中进行赋值
    //静态代码块在类加载时调用，并且只调用一次。
    static {
        instance = new Singleton();
    }

    //对外提供获取该类对象的方法
    public static Singleton getInstance() {
        return instance;
    }
}
```

```java
public class SingletonTest {
    @Test
    public void getSingletonTest(){
        Singleton instance1 = Singleton.getInstance();
        Singleton instance2 = Singleton.getInstance();
        System.out.println(instance1);
        System.out.println(instance2);
    }
}
```

```java
com.design.pattern.singleton.demo2.Singleton@3b764bce
com.design.pattern.singleton.demo2.Singleton@3b764bce
```

3、懒汉式——方式1（线程不安全）

```java
/**
 * 懒汉式
 * 线程不安全
 */
public class Singleton {
    //私有构造方法
    private Singleton() {
    }

    //申明Singleton 类型的变量 instance

    private static Singleton instance;

    //对外提供访问方式
    public static Singleton getInstance() {
        //判断 instance 是否已经存在，如果为null,说明还没有创建Singleton 类的对象
        if (instance == null) {
            //线程1等待，线程2 获取到cpu的执行权，也会进入到该判断的里
            instance = new Singleton();
        }
        return instance;
    }
}
```



4、懒汉式——方式2（线程安全）

说明：该方式实现了懒汉加载效果，同时又解决了线程安区，但是getInstance()方法添加了synchronized关键字，导致该方法的执行效果特别低。从上面的代码我们可以看出，其实就是初始化instance的时候才会出现线程安全，一旦初始化完成就不能在。

```java
/**
 * 懒汉式
 * 线程不安全
 */
public class Singleton {
    //私有构造方法
    private Singleton() {
    }

    //申明Singleton 类型的变量 instance

    private static Singleton instance;

    //对外提供访问方式(加锁保证线程安全)
    public static synchronized Singleton getInstance() {
        //判断 instance 是否已经存在，如果为null,说明还没有创建Singleton 类的对象
        if (instance == null) {
            instance = new Singleton();
        }
        return instance;
    }
}
```

5、懒汉式——方式3 （双重检查锁）

```java
/**
 * 懒汉式 双重检查锁方式
 */
public class Singleton {
    //私有构造方法
    private Singleton() {
    }

    //申明Singleton 类型的变量
    private static Singleton instance;

    //对外提供公用的访问方式
    public static Singleton getInstance() {
        //第一次判断，如果instance 的值不为null，不需要抢占锁，直接返回对象
        if (instance == null) {
            synchronized (Singleton.class) {
                //第二次判断
                if (instance == null) {
                    instance = new Singleton();
                }
            }
        }
        return instance;
    }
}
```

双重检查锁模式是一种非常好的单例实现模式，解决了单例、性能、线程安全问题。在多线程的情况下，可能会出现空指针问题。出现问题的原因是JVM在实例化对象的时候会进行优化和指令重排序操作。要解决双重检查锁模式代理的指针异常的问题，值需要使用volatile关键字，volatile关键字可以保证可见性和有效性。

```java
/**
 * 懒汉式 双重检查锁方式
 */
public class Singleton {
    //私有构造方法
    private Singleton() {
    }

    //申明Singleton 类型的变量(volatile关键字可以保证可见性和有效性)
    private static volatile Singleton instance;

    //对外提供公用的访问方式
    public static Singleton getInstance() {
        //第一次判断，如果instance 的值不为null，不需要抢占锁，直接返回对象
        if (instance == null) {
            synchronized (Singleton.class) {
                //第二次判断
                if (instance == null) {
                    instance = new Singleton();
                }
            }
        }
        return instance;
    }
}
```

6、懒汉式——方式4 （静态内部类方式）

静态内部类单例模式中实例由内部类创建，由于JVM在加载外部类的过程中，是不会加载内部类的，只有内部类的属性/方法被调用才会被调用时才会被加载，并初始化其静态属性。静态属性被static修饰，保证只被实例化一次，并且严格保证实例化顺序。

```java
/**
 * 懒汉模式：静态内部类
 */
public class Singleton {
    //私有构造方法
    private Singleton() {
    }

    private static class SingletonHolder {
        //在内部类中申明并初始化外部类的对象
        private static final Singleton INSTANCE = new Singleton();
    }

    //提供公共的访问对象
    public static Singleton getInstance() {
        return SingletonHolder.INSTANCE;
    }

}
```

<font style="color:red;">说明：</font>第一次加载Singleton 类时不会去初始化INSTANCE,只有第一次调用getInstance，虚拟机加载SingletonHolder并初始化INSTANCE,这样不仅能确保线程安全，也能保证Singleton类的唯一性。

<font style="color:red;">小结：</font>静态内部类单例模式是一种优秀的单例模式，在开源项目中比较常见的一种单例模式，在没有加任何锁的情况下，保证了多线程下的安全，并且没有任何性能影响和空间浪费。

7、枚举类型

枚举类实现单例模式是极力推荐的单例实现模式，因为枚举类型是线程安全的，并且只会装载一次，设计者充分利用了枚举的这个特性来实现单例模式，枚举的写法非常简单，而且枚举类型是所有单例实现中唯一不会破坏单例实现模式。

说明：枚举类型属于饿汉式方式。在不考虑浪费内存空间的情况下，首选枚举类型。

```java
/**
 * 枚举实现方式
 */
public enum Singleton {
    INSTANCE;
}
```

### 5.1.3 存在问题

破坏单例模式

使上面定义的单例类（Singleton)可以创建多个对象，枚举方式除外。有两种方式：序列化和反射。

#### 5.1.3.1 问题演示

- 序列化反序列

Singleton

```java
public class SingletonTest {
    //向文件中写数据
    @Test
    public void writObject2File() throws IOException {
        //获取Singleton对象
        Singleton instance = Singleton.getInstance();
        //创建对象输出流对象
        ObjectOutputStream oos = new ObjectOutputStream(new FileOutputStream("c:\\a.txt"));
        //写对象
        oos.writeObject(instance);
        //释放资源
        oos.close();
    }

    public  void readObjectFromFile() throws Exception {
        //1.创建对象输入流对象
        ObjectInputStream ois = new ObjectInputStream(new FileInputStream("c:\\a.txt"));
        //2.读取对象
        Singleton instance = (Singleton) ois.readObject();
        System.out.println(instance);
        ois.close();
    }
    @Test
    public void test() throws Exception {
        this.readObjectFromFile();
        this.readObjectFromFile();
    }
}
```

```java
com.design.pattern.singleton.demo7.Singleton@484b61fc
com.design.pattern.singleton.demo7.Singleton@45fe3ee3
```

- 反射破坏单例模式

```java
public class SingletonTest {
    @Test
    public void getSingleton() throws NoSuchMethodException, IllegalAccessException, InvocationTargetException, InstantiationException {
        //1.获取Singleton的字节码对象
        Class clazz = Singleton.class;
        //2 获取无参构造方法对象
        Constructor cons = clazz.getDeclaredConstructor();
        //3 取消访问检查
        cons.setAccessible(true);
        Singleton instance = (Singleton) cons.newInstance();
        Singleton instance1 = (Singleton) cons.newInstance();
        System.out.println(instance);
        System.out.println(instance1);
    }
}
```

```java
com.design.pattern.singleton.demo8.Singleton@3b764bce
com.design.pattern.singleton.demo8.Singleton@759ebb3d
```

#### 5.1.3.2 问题解决

- 序列化、反序列方式破坏单例模式的解决办法

在Singleton类中添加readResolve()的方法，在反序列化时被反射调用，如果定义了这个方法，就返回这个方法的值，如果没有定义，则返回新new出来的对象。

```java
public class Singleton implements Serializable {
    //私有构造方法
    private Singleton() {
    }

    private static class SingletonHolder {
        //在内部类中申明并初始化外部类的对象
        private static final Singleton INSTANCE = new Singleton();
    }

    //提供公共的访问对象
    public static Singleton getInstance() {
        return SingletonHolder.INSTANCE;
    }

    //当进行反序列化时，会自动调用该方法，将该方法的返回值直接返回
    public Object readResolve(){
        return SingletonHolder.INSTANCE;
    }

}
```

```java
com.design.pattern.singleton.demo7.Singleton@484b61fc
com.design.pattern.singleton.demo7.Singleton@484b61fc
```

- 反射方式破解单例的解决办法

```java
public class Singleton {
    private static boolean flag = false;
    //私有构造方法
    private Singleton() {
        synchronized (Singleton.class) {
            //判断flag的值是否时true,如果是true，说明非第一次访问，直接抛一个异常，如果是false的话，说明第一次访问
            if (flag) {
                throw new RuntimeException("不能创建多个对象");
            }
            //将flag 设置为true
            flag = true;
        }
    }
    private static class SingletonHolder {
        //在内部类中申明并初始化外部类的对象
        private static final Singleton INSTANCE = new Singleton();
    }
    //提供公共的访问对象
    public static Singleton getInstance() {
        return SingletonHolder.INSTANCE;
    }
}
```

```java
@Test
public void getSingleton() throws NoSuchMethodException, IllegalAccessException, InvocationTargetException, InstantiationException {
    //1.获取Singleton的字节码对象
    Class clazz = Singleton.class;
    //2 获取无参构造方法对象
    Constructor cons = clazz.getDeclaredConstructor();
    //3 取消访问检查
    cons.setAccessible(true);
    Singleton instance = (Singleton) cons.newInstance();
    Singleton instance1 = (Singleton) cons.newInstance();
    System.out.println(instance);
    System.out.println(instance1);
}
```

```java
java.lang.reflect.InvocationTargetException
	at sun.reflect.NativeConstructorAccessorImpl.newInstance0(Native Method)
	at sun.reflect.NativeConstructorAccessorImpl.newInstance(NativeConstructorAccessorImpl.java:62)
	at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(DelegatingConstructorAccessorImpl.java:45)
	at java.lang.reflect.Constructor.newInstance(Constructor.java:422)
	at com.design.pattern.singleton.demo9.SingletonTest.getSingleton(SingletonTest.java:19)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:62)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:497)
	at org.junit.runners.model.FrameworkMethod$1.runReflectiveCall(FrameworkMethod.java:59)
	at org.junit.internal.runners.model.ReflectiveCallable.run(ReflectiveCallable.java:12)
	at org.junit.runners.model.FrameworkMethod.invokeExplosively(FrameworkMethod.java:56)
	at org.junit.internal.runners.statements.InvokeMethod.evaluate(InvokeMethod.java:17)
	at org.junit.runners.ParentRunner$3.evaluate(ParentRunner.java:306)
	at org.junit.runners.BlockJUnit4ClassRunner$1.evaluate(BlockJUnit4ClassRunner.java:100)
	at org.junit.runners.ParentRunner.runLeaf(ParentRunner.java:366)
	at org.junit.runners.BlockJUnit4ClassRunner.runChild(BlockJUnit4ClassRunner.java:103)
	at org.junit.runners.BlockJUnit4ClassRunner.runChild(BlockJUnit4ClassRunner.java:63)
	at org.junit.runners.ParentRunner$4.run(ParentRunner.java:331)
	at org.junit.runners.ParentRunner$1.schedule(ParentRunner.java:79)
	at org.junit.runners.ParentRunner.runChildren(ParentRunner.java:329)
	at org.junit.runners.ParentRunner.access$100(ParentRunner.java:66)
	at org.junit.runners.ParentRunner$2.evaluate(ParentRunner.java:293)
	at org.junit.runners.ParentRunner$3.evaluate(ParentRunner.java:306)
	at org.junit.runners.ParentRunner.run(ParentRunner.java:413)
	at org.junit.runner.JUnitCore.run(JUnitCore.java:137)
	at com.intellij.junit4.JUnit4IdeaTestRunner.startRunnerWithArgs(JUnit4IdeaTestRunner.java:68)
	at com.intellij.rt.junit.IdeaTestRunner$Repeater.startRunnerWithArgs(IdeaTestRunner.java:33)
	at com.intellij.rt.junit.JUnitStarter.prepareStreamsAndStart(JUnitStarter.java:230)
	at com.intellij.rt.junit.JUnitStarter.main(JUnitStarter.java:58)
Caused by: java.lang.RuntimeException: 不能创建多个对象
	at com.design.pattern.singleton.demo9.Singleton.<init>(Singleton.java:15)
	... 30 more
```

### 5.1.4 JDK 源码解析:Runtime 类

Runtime 类就是使用单例设计模式

1.通过源代码查看使用的哪中单例设计模式（查找类快捷键：ctrl+alt+shift+N)

```java
public class Runtime {
    private static Runtime currentRuntime = new Runtime();

    /**
     * Returns the runtime object associated with the current Java application.
     * Most of the methods of class <code>Runtime</code> are instance
     * methods and must be invoked with respect to the current runtime object.
     *
     * @return  the <code>Runtime</code> object associated with the current
     *          Java application.
     */
    public static Runtime getRuntime() {
        return currentRuntime;
    }

    /** Don't let anyone else instantiate this class */
    private Runtime() {}
    ......(还很多，在此省略)
}
```

通过上面源代码可以看出Runtime类使用的是饿汉式（静态变量）方式来实现单例模式

```java
@Test
public void test() throws IOException {
    Runtime runtime = Runtime.getRuntime();
    //调用
    Process exec = runtime.exec("ipconfig");
    //调用process对象获取输入的方法
    InputStream inputStream = exec.getInputStream();
    byte[] arr = new byte[1024 * 1024 * 100];
    //读取数据
    int len = inputStream.read(arr);
    //将字节数组转换为字符串输出到控制台
    System.out.println(new String(arr, 0, len, "GBK"));

}
```

> Windows IP 配置
>
>
> 以太网适配器 以太网 3:
>
>    媒体状态  . . . . . . . . . . . . : 媒体已断开连接
>    连接特定的 DNS 后缀 . . . . . . . : 
>
> ......
>
> 无线局域网适配器 WLAN:
>
>    连接特定的 DNS 后缀 . . . . . . . : 
>    本地链接 IPv6 地址. . . . . . . . : fe80::859:773a:622b:5eec%6
>    IPv4 地址 . . . . . . . . . . . . : 192.168.0.103
>    子网掩码  . . . . . . . . . . . . : 255.255.255.0
>    默认网关. . . . . . . . . . . . . : 192.168.0.1



## 5.2 工厂模式

在java 中，万物皆对象，这些对象需要创建，如果创建的时候直接new该对象，就会对该对象耦合严重，假如我们要更好对象，所有new对象的地方都需要修改一边，者显然违背了软件设计原则的开闭原则。如果我们使用工厂来生产对象，我们就只和工厂打交道就可以了，彻底和对象解耦，如果要更换对象，直接在工厂里更换该对象即可，可达到对象解耦的目的。所以说，工厂模式的有点就是：解耦。

### 5.2.1 简单工厂模式

简单工厂模式不是一种设计模式，反而是一种编程习惯。

#### 5.2.1.1 结构

简单工厂包含如下角色：

- 抽象产品：定义产品的规范，描述产品的主要特性和功能。
- 具体产品：实现或继承抽象产品的子类。
- 具体工厂：提供了创建产品的方法，调用者通过该方法来获取产品。

#### 5.2.1.2 实现方式

![image-20220220090836685](.\images\设计模式\5212-1.png)



#### 5.2.1.3 优缺点

优点：

封装了创建对象的过程，可以通过参数直接获取对象。把对象的创建和业务逻辑层分开，这样以后避免了修改客户代码，如果要实现新产品直接修改工厂类，而不需要在原代码中修改，这样就降低了客户代码修改的可能性，更容易扩展。

缺点：

增加产品时，还需要修改工厂类的代码，违背了“开闭原则”。

#### 5.2.1.4 静态工厂

在开发中也有一部分人将工厂类中的<font style="color:red">**创建对象工厂定义为静态的**</font>，这就是静态工厂模式，它也不是23中设计模式中的。

### 5.2.2 工厂方法模式

一个用于创建对象的接口，让子类决定实例化哪个产品类对象。工厂方法使一个产品类的实例化延迟到其工厂子类。

#### 5.2.2.1 结构

工厂方法模式的主要角色：

- 抽象工厂：主要提供了创建产品的接口，调用者通过访问具体工厂的方法来创建产品。
- 具体工厂：主要时实现抽象工厂中的抽象方法，完成具体产品的创建。
- 抽象产品：定义了产品的规范，描述了产品的主要特性和功能。
- 具体产品：实现了抽象产品角色所定义的接口，由具体工厂来创建，它同具体工厂直接一一对应。

#### 5.2.2.2 实现

类图：

![image-20220220090836685](.\images\设计模式\5222-1.png)

#### 5.2.2.3 优缺点

优点：

- 用户只需要知道具体工厂的名称就可得到所要的产品，无须知道产品的具体创建过程；
- 在系统增加新的产品时只需要添加具体产品类和对应的具体工厂类，无须对原工厂进行任何修改，满足开闭原则；

**缺点：**

- 每增加一个产品就要增加一个具体产品类和一个对应的具体工厂类，这增加了系统的复杂度。

### 5.2.3 抽象工厂模式

一种访问类提供一个创建一组相关或相互依赖对象的接口，且访问类无须制定所要产品的具体类就能得到同族的不同等级的产品的模式结构。

抽象工厂模式时工厂模式的升级版本，工厂方法模式只生产一个等级的产品，而抽象工厂模式可生产多个等级的产品。

### 5.2.4 模式扩展

### 5.2.5 JDK源码解析:Collection.iterator方法

