# 1.基础语法

## 1.1 注释

单行注释

```java
//注释信息
```

多行注释

```java
/*注释信息*/
```

文档注释

```java
/** 注释信息*/
```

## 1.2 关键字

- 关键字的字母全部时小写
- 常用的代码编辑器，针对关键字由特殊的颜色标记，非常直观

## 1.3 常量

常量：在程序运行过程中，其值不可以发生改变的量。

| 常量类型   | 说明                 | 举例                    |
| ---------- | -------------------- | ----------------------- |
| 字符串常量 | 用双引号括起来的内容 | “我爱我的祖国”          |
| 整数常量   | 不带小数的数字       | 520，-1314              |
| 小数常量   | 带小数的数字         | 13.14，-5.21            |
| 字符常量   | 用单引号括起来的内容 | 'A','B','9','我'        |
| 布尔常量   | 布尔值，表示真假     | 只有两个值：true、false |
| 空常量     | 一个特殊的值,空值    | 值是：null              |

空常量是不能直接输出的

## 1.4 数据类型

**计算机存储单元**

计算机存储设备的最小信息单元叫"位(bit)",我们又称为"比特位"，通常用小写的字母"b"表示。而计算机中最小的存储单元叫"字节（byte)",通常用大写字母"B"表示，字节由连续的8个位组成。

1B(字节）=8bit（比特位）

1KB=1024B

1MB=1024KB

1GB=1024MB

1TB=1024GB

**数据类型**

Java语言是强类型语言，对于每一种数据都给出了明确的数据类型，不同的**数据类型**也会分配了不同的**存储空间**，所以表示它表示的**数据大小**也是不一样的。



## 1.5 变量

变量：在程序运行过程中，其值可以发送改变的量。从本质上讲，变量是内存中的一小块区域。

变量格式：数据类型  变量名=变量值；  eg:  int a=10;

变量的使用：取值和修改值。

注意事项：

1）同一个作用域下，变量名不能重复。

2） 未赋值不能使用。

3） long类型的变量定义的时候，为了防止整数过大，后面要加L

4） float 类型的变量定义的时候，为了防止类型不兼容，后面要加F

## 1.6 标识符

标识定义规则

- 由数字、字母、下划线和美元符号组成
- 不能以数字开头
- 不能是关键字
- 区分大小写

常见命名约定

- 小驼峰命名法：方法、变量
- 大驼峰命名法：类

## 1.7 类型转换

类型转化分类：

- 自动类型转换
- 强制类型转换

自动类型转换：把一个标识数据范围小的数值或者变量赋值给另一个表示数据范围大的变量

byte —》short—》int—》long—》float—》double

char—》int—》long—》float—》double

强制类型转换：把一个表述数据范围大的数据或者变量赋值给另一个数据范围小的变量

强制类型转换格式： 目标数据类型  变量名=（目标数据类型）值或者变量；

# 2.运算符

## 2.1 算术运算符

| 运算符 | 中文意思 | 说明 |
| ------ | -------- | ---- |
| +      | 加       |      |
| -      | 减       |      |
| *      | 乘       |      |
| /      | 除       |      |
| %      | 取余     |      |

## 2.2 赋值运算符



## 2.3 自增自减运算符



## 2.4 关系运算符



## 2.5逻辑运算符



## 2.6 三元预算符

# 3 分支语句





# 9.反射

## 9.1 类加载

当 程序使用某个类时，如果该类还未被加载到内存中，则系统会通过类的加载，类的连接，类的初始化这三个步骤对类进行初始化。如果不出现意外情况，JVM将会连续完成这三个步骤，所以有时也把这三个步骤统称为类加载或类初始化。

类的加载：

-  就是指将class文件读入内存，并为之创建一个java.lang.Class对象
- 任何类被使用时，系统都会为之建立一个java.lang.Class对象

类的连接：

- 验证阶段：用于检验被加载的类是否有正确的内部结构，并和其他类协调一致
- 准备阶段：负责为类的变了分配内存，并设置默认初始化值
- 解析阶段：将类的二进制数据中的符号引用替换为值引用

类的初始化：

- 类的初始化步骤：
  1. 假如类还未被加载和连接，则程序先加载并连接该类
  2. 假如该类的直接父类还未被初始化，则先初始化其直接父类
  3. 假如类中有初始化语句，则系统依次执行这些初始化语句
- 类初始化时机：
  1. 创建类的实例
  2. 调用类的方法
  3. 访问类或者接口的类，或者为该类变量赋值
  4. 使用反射方式来强制创建某个类或者接口对应的java.lang.Class对象
  5. 初始化某个类的子类
  6. 直接使用java.exe命令运行某个主类

## 9.2  类加载器

​	类加载器的作用

- 负责将.class文件加载到内存中，并为之生成对应额java.lang.class
- 虽然我们不用过分关心类加载机制，但是了解这个机制我们就能更好的理解程序运行

JVM的类加载机制

- 全盘负责：就是当一个类加载器负责加载某个class是，该class所依赖的和引用的其他Class也将由该类加载器负责载入，除非显示使用另外一个类加载器未载入
- 父亲委托：就是当一个类加载器负责加载某个Class时，先让父类加载器试图加载该Class，只有父亲加载器无法加载该类时，才尝试从自己的类路径中加载类
- 缓存机制：保证所有加载过的Class都会被缓存，当程序需要使用某个Class对象是，类加载器先从缓存区中搜索该Class,只有当缓存区中不存在该Class对象时，系统才会读取该类对应的二进制数据，并将其转换成Class对象，存储到缓存区。

ClassLoader:负责加载类的对象

Java运行时具有以下内置类加载器

- Bootstrap class loader:他是虚拟机的内置类加载器，通常标识为null,并没有父null
- Plantform class loader:平台类加载器可以看到所有平台类，平台类包括由平台类加载器或者其祖先定义的JavaSe平台API，其实现类和JDK特定的运行时类
- System class loader:它也被称为应用程序类加载器，与平台类加载器不同。系统类加载器通常用于定义应用程序类路径，模块路径和JDK特定工具上的类

ClassLoader中的两个方法

- static ClassLoader getSystemClassLoader();返回用于委派的系统类加载器

- ClassLoader getParent(); 返回父类加载器进行委派

## 9.3反射

### 9.3.1 反射概述

Java反射机制的核心是在程序运行时动态加载类并获取类的详细信息，从而操作类或对象的属性和方法。。本质是JVM得到class对象之后，再通过class对象进行反编译，从而获取对象的各种信息。

### 9.3.2 获取Class类的对象

我们想要通过反射去使用一个类，首先我们要获取该类的字节码文件对象，也就是类型为Class类型的对象。

这里，我们提供三种方式获取Class类对应的Class对象。

- 使用类的class属性来获取该类对应的Class对象。

```java
Class<Student> c1=Student.class;
```

- 调用对象的getClass()方法，返回该对象所属类对应的Class对象

  该方法是Object类中的方法，所有的Java对象都可以调用该方法

  ```java
  Student s=new Student();
  Class<? extends Student> c3=s.getClass();
  ```

- 使用Class 类中的静态方法forName(String className),该方法需要传入字符串参数，该字符串参数的值是某个类的全路径（完整的包路径）

```java
Class<?> c4=Class.forName("com.study.Student");
```

### 9.3.3 通过反射获取构造方法并使用

在反射机制中，把类中的成员（构造方法、成员方法、成员变量）都封装成了对应的类进行表示。

其中，构造方法使用Constructor表示。可以通过Class类中提示的方法获取构造方法：

返回一个构造方法：

- 获取public修饰，指定参数类型所对应的构造方法

```java
public Constructor<T> getConstructor(Class<?>...parameterTypes)
```

- 获取指定参数类型所对应的构造方法（包含私有方法）

```java
public Constructor<T> getDeclaredConstructor(Class<?>...parameterTypes)
```

返回多个构造方法：

- 获取所有的public修饰的构造方法

```java
public Constructor<?>[] getConstructors()
```

- 获取所有的构造方法（包含私有的）

```java
public Constructor<?>[] getDeclaredConstructor()
```

通过放射方式，获取构造方法，创建对象

步骤：

1. 获取Class对象

2. 获取指定的构造方法

3. 暴力访问，通过setAccessible(boolean flag) 方法（私有才需要）

4. 通过构造方法类Constructor中的方法，创建对象

   ```java
   public T newInstance(Object...initargs)
   ```

### 9.3.4 通过反射获取成员变量并使用

在反射机制中，类中的成员变量使用Field表示。可以通过Class类中提供的方法获取成员变量

返回一个成员变量：

- 获取指定的public修饰的变量

  ```java
  public Field getField(String name) 
  ```

- 获取指定的任意变量（含私有变量）

  ```java
  public Field getDeclaredField(String name)
  ```

返回多个成员变量：

- 获取所有的public修饰的变量

  ```java
  public Field[] getFields()
  ```

- 获取所有的变量（包含私有）

  ```
  public Field[] getDeclaredFields()
  ```

通过反射，创建对象，并获取指定成员变量，进行赋值与获取值操作

步骤：

1. 获取Class对象

2. 获取构造方法

3. 通过构造方法，创建对象

4. 获取指定的成员变量（私有成员变量，通过setAccessible(boolean flag) 方法暴力访问)

5. 通过方法，给指定对象的指定成员变量赋值获取值

   在指定的对象obj中，将Field对象表示的成员变量设置为指定的新值

   ```java
   public void set(Object obj,Object value)
   ```

   在指定对象obj中，获取Field 对象表示的成员变量的值

   ```java
   public Object get(Object obj)
   ```

### 9.3.5 通过反射获取方法并使用

在反射机制中，类中的方法使用Method表示。可通过Class类中提供的方法获取成员方法：

返回获取一个方法：

- 获取public 修饰的方法（name 要查找的方法名称；paramterTypes 该方法的参数类型）

  ```java
  public Method getMethod(String name,Class<?>...paramterTypes)
  ```

- 获取任意的方法，包含私有

  ```java
  public Method getDeclaredMethod(String name,Class<?>...paramterTypes)
  ```

返回获取多个方法：

- 获取本类与父类中所有public修饰的方法

  ```java
  public Method[] getMethods()
  ```

- 获取本类中所有的方法（包含私有方法）

  ```java
  public Method[] getDeclaredMethod()
  ```

通过反射，创建对象，调用指定的方法

步骤：

1.  获取Class对象

2. 获取构造方法

3. 通过构造方法，创建对象

4. 获取指定的方法

5. 开启暴力访问setAccessible(true)

6. 执行找到的方法

   ```java
   public Object invoke(Object obj,Object...args)
   ```

   执行指定对象obj中，当前Method对象所代表的方法，方法入参通过args指定。

