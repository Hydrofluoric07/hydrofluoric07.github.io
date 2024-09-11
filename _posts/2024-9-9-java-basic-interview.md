---
title: Java基础面试知识点
date: 2024-09-09 20:05:56 +0800
categories: [interview, java]
tags: [java, note, interview]     # TAG names should always be lowercase
typora-root-url: ./..
---
## Java基础(上)

### JVM vs JDK vs JRE

JVM是运⾏ Java 字节码的虚拟机，是 Java 语言“⼀次编译，随处可以运⾏”的关键所在。

JDK( Java Development Kit)包括JRE，javac，javadoc，jdb

JRE 是 Java 运⾏时环境。它是运⾏已编译 Java 程序所需的所有内容的集合，包括 Java 虚拟机 （JVM），Java 类库，java 命令和其他的⼀些基础构件。但是，它不能⽤于创建新程序

### 什么是字节码?采用字节码的好处是什么?

JVM 可以理解的代码就叫做字节码（即扩展名为 .class 的⽂件），⼀定程度上解决了传统解释型语言执行效率低的问题，同时又保留了解释型语言可移植的特点

![java-to-source](/assets/img/2024-9-9-java-basic-interview/java-to-source.png)

### 为什么说 Java 语言“编译与解释并存“？

Java 语言被称为“编译与解释并存”的原因是它在执行过程中同时使用了编译和解释两种方式。

-   **编译**: 源代码会经过编译器（javac）将其转换成字节码文件（.class），这个过程就是编译。编译后的字节码文件可以在任何支持 Java 虚拟机（JVM）的平台上运行。     
-   **解释**: 当 Java 程序运行时，Java 虚拟机会对字节码进行解释或即时编译为机器码再执行。解释执行是逐条解释执行字节码指令，而即时编译则是将热点代码（经常执行的代码）编译成本地机器码，以提高执行效率。   

### Java 语言关键字有哪些？

虽然 true , false , 和 null 看起来像关键字但实际上他们是字面值

### 成员变量与局部变量的区别？

**语法形式** ：成员变量是属于类的，⽽局部变量是在代码块或⽅法中定义的变 量或是⽅法的参数；成员变量可以被 public , private , static 等修饰符所修饰，⽽局部变量不 能被访问控制修饰符及 static 所修饰；但是，成员变量和局部变量都能被 final 所修饰。 

**存储方式** ：如果成员变量是使⽤ static 修饰的，那么这个成员变量是属于类的，如果没有使⽤ static 修饰，这个成员变量是属于实例的。⽽对象存在于堆 内存，局部变量则存在于栈内存。 

**生存时间** ：成员变量是对象的⼀部分，它随着对象的创建⽽ 存在，⽽局部变量随着⽅法的调⽤⽽⾃动⽣成，随着⽅法的调⽤结束⽽消亡。

 **默认值** ：从变量是否有默认值来看，成员变量如果没有被赋初始值，则会⾃动以类型的默认值 ⽽赋值（⼀种情况例外:被 final 修饰的成员变量也必须显式地赋值），⽽局部变量则不会⾃动 赋值。

### 静态变量有什么作⽤？

静态变量可以被类的所有实例共享。⽆论⼀个类创建了多少个对象，它们都共享同⼀份静态变量。 通常情况下，静态变量会被 final 关键字修饰成为常量。

### 字符型常量和字符串常量的区别? 

形式 : 字符常量是单引号引起的⼀个字符，字符串常量是双引号引起的 0 个或若⼲个字符。

 字符常量相当于⼀个整型值( ASCII 值),可以参加表达式运算; 字符串常量代表⼀个地址值 (该字符串在内存中存放位置)。

 占内存⼤⼩ ： 字符常量只占 2 个字节; 字符串常量占若⼲个字节。

### 静态⽅法和实例⽅法有何不同？

1、调⽤⽅式

实例方法使用对象名.方法名来调用，静态方法还可以使用类名.方法名调用，静态⽅法不属于类的某个对象⽽是属于这个类，⼀般建议使⽤ 类名.⽅法名

2、访问类成员是否存在限制

静态⽅法在访问本类的成员时，只允许访问静态成员（即静态成员变量和静态⽅法），不允许访问实 例成员（即实例成员变量和实例⽅法），⽽实例⽅法不存在这个限制。

### 重载和重写的区别

重载是同⼀个类中多个同名⽅法根据不同的传参来执⾏不同的逻辑处理，重写是子类继承父类方法时覆盖父类方法

发⽣在同⼀个类中（或者⽗类和⼦类之间），⽅法名必须相同，参数类型不同、个数不同、顺序不 同，⽅法返回值和访问修饰符可以不同。

⽅法的重写要遵循“两同两⼩⼀⼤”： “两同”即⽅法名相同、形参列表相同； “两⼩”指的是⼦类⽅法返回值类型应⽐⽗类⽅法返回值类型更⼩或相等，⼦类⽅法声明抛出的异 常类应⽐⽗类⽅法声明抛出的异常类更⼩或相等； “⼀⼤”指的是⼦类⽅法的访问权限应⽐⽗类⽅法的访问权限更⼤或相等。

![overload&override.png](/assets/img/2024-9-9-java-basic-interview/overload&override.png)

### 什么是可变长参数

允许在调⽤⽅法时传⼊不定⻓度的 参数，只能作为函数的最后⼀个参数

方法重载时会优先匹配固定参数的方法

### Java基本数据类型

![java-data-type](/assets/img/2024-9-9-java-basic-interview/java-data-type.png)

### 基本类型和包装类型的区别？

成员变量包装类型不赋值就是 null ，⽽基本类型有默认值且不是 null 。 

包装类型可⽤于泛型，⽽基本类型不可以。 

基本数据类型的局部变量存放在 Java 虚拟机栈中的局部变量表中，基本数据类型的成员变量 （未被 static 修饰 ）存放在 Java 虚拟机的堆中。

包装类型属于对象类型，我们知道⼏乎所有 对象实例都存在于堆中。 相⽐于对象类型， 基本数据类型占⽤的空间⾮常⼩。

![basic-type-wrapper](/assets/img/2024-9-9-java-basic-interview/basic-type-wrapper.png)

```java
Integer i1=40;
Integer i2=new Integer(40);
System.out.println(i1==i2);
```

Integer i1=40 这⼀⾏代码会发⽣装箱，也就是说这⾏代码等价于 Integer i1=Integer.valueOf(40) 。因 此， i1 直接使⽤的是缓存中的对象。⽽ Integer i2 = new Integer(40) 会直接创建新的对象，答案是false。

Float,Double没有实现缓存机制

### ⾃动装箱与拆箱了解吗？原理是什么？

装箱：将基本类型⽤它们对应的引⽤类型包装起来； 

拆箱：将包装类型转换为基本数据类型；

现装箱其实就是调⽤了 包装类的 valueOf() ⽅法，拆箱其实就是调⽤了 xxxValue() ⽅法。

### 如何解决浮点数运算的精度丢失问题？

BigDecimal 可以实现对浮点数的运算，不会造成精度丢失。通常情况下，⼤部分需要浮点数精确运 算结果的业务场景（⽐如涉及到钱的场景）都是通过 BigDecimal 来做的。

### 超过 long 整型的数据应该如何表示？

BigInteger 内部使⽤ int[] 数组来存储任意⼤⼩的整形数据。 相对于常规整数类型的运算来说， BigInteger 运算的效率会相对᫾低。

### 如果⼀个类没有声明构造⽅法，该程序能正确执⾏吗?

⼀个类没有声明构造⽅法也会有默认的不带参数的构造⽅法。如果我们⾃⼰添加了类的构造⽅法（⽆论是否有参），Java 就不会再添加默认的⽆ 参数的构造⽅法了。如果我们重载了有参的构造⽅法，建议把⽆参的 构造⽅法也写出来（⽆论是否⽤到），因为这可以帮助我们在创建对象的时候少踩坑。

### 构造⽅法有哪些特点？是否可被 override?

名字与类名相同。 没有返回值，但不能⽤ void 声明构造函数。 ⽣成类的对象时⾃动执⾏，⽆需调⽤。

 构造⽅法不能被 override（重写）,但是可以 overload（重载）,所以你可以看到⼀个类中有多个构造 函数的情况。

## Java基础(中)

### 面向对象三大特征

封装是指把⼀个对象的状态信息（也就是属性）隐藏在对象内部，不允许外部对象直接访问对象的内 部信息

通过使⽤继承，可以快速地创建新的类，可以提⾼代码的重⽤，程序的可维护性，节省⼤ 量创建新类的时间 ，提⾼开发效率。⼦类拥有⽗类对象所有的属性和⽅法（包括私有属性和私有⽅法），但是⽗类中的私有属性和⽅ 法⼦类是⽆法访问，只是拥有。 ⼦类可以拥有⾃⼰属性和⽅法，即⼦类可以对⽗类进⾏扩展。 ⼦类可以⽤⾃⼰的⽅式实现⽗类的⽅法。

多态：*同一个方法在不同的对象上执行会产生不同的结果。*三个必要条件：继承、重写、父类引用指向子类对象：Parent p=new Child();

### 接口和抽象类区别

1. 抽象类不能被实例化
2. 抽象类中不一定包含抽象方法，但是有抽象方法的类必定是抽象类。
3. 抽象类中的抽象方法只是声明，不包含方法体。
4. 构造方法，类方法（用 static 修饰的方法）不能声明为抽象方法。
5. 抽象类的子类必须给出抽象类中的抽象方法的具体实现，除非该子类也是抽象类。

共同点 ： 都**不能被实例化**。 **都可以包含抽象⽅法**。 都可以有默认实现的⽅法（Java 8 可以⽤ default 关键字在接⼝中定义默认⽅法）。

 区别 ： 接⼝主要⽤于对类的⾏为进⾏约束，你实现了某个接⼝就具有了对应的⾏为。抽象类主要⽤于代 码复⽤，强调的是所属关系。 ⼀个类只能继承⼀个类，但是可以实现多个接⼝。 接⼝中的成员变量只能是 public static final 类型的，不能被修改且必须有初始值，⽽抽象类的 成员变量默认 default，可在⼦类中被重新定义，也可被重新赋值。

### 深拷⻉和浅拷⻉区别了解吗？什么是引⽤拷⻉？

浅拷⻉会在堆上创建⼀个新的对象（区别于引⽤拷⻉的⼀点），如果原对象内部 的属性是引⽤类型的话，浅拷⻉会直接复制内部对象的引⽤地址，也就是说拷⻉对象和原对象共 ⽤同⼀个内部对象。 深拷⻉会完全复制整个对象，包括这个对象所包含的内部对象。

引⽤拷⻉就是两个不同的引⽤指向同⼀个对象

![java-clone](/assets/img/2024-9-9-java-basic-interview/java-clone.png)

### == 和 equals() 的区别

对于基本数据类型来说， == 比较的是值。 对于引⽤数据类型来说， == 比较的是对象的内存地址。因为 Java 只有值传递，所以，对于 == 来说，不管是⽐᫾基本数据类型，还是引⽤数据类型的 变量，其本质⽐᫾的都是值，只是引⽤类型变量存的值是对象的地址。

因为 Java 只有值传递，所以，对于 == 来说，不管是⽐᫾基本数据类型，还是引⽤数据类型的 变量，其本质⽐᫾的都是值，只是引⽤类型变量存的值是对象的地址。

```java
public boolean equals(Object obj){
    return (this==obj);
}
```



equals() ⽅法存在两种使⽤情况： 类没有重写 equals() ⽅法 ：通过 equals() ⽐较该类的两个对象时，等价于通过“==”⽐较这两个 对象，使⽤的默认是 Object 类 equals() ⽅法。 类重写了 equals() ⽅法 ：⼀般我们都重写 equals() ⽅法来⽐较两个对象中的属性是否相等； 若它们的属性相等，则返回 true(即，认为这两个对象相等)。String 中的 equals ⽅法是被重写过的。

当创建 String 类型的对象时，虚拟机会在常量池中查找有没有已经存在的值和要创建的值相同的对 象，如果有就把它赋给当前引⽤。如果没有就在常量池中重新创建⼀个 String 对象。

### hashCode() 有什么用？

hashCode() 的作⽤是获取哈希码（ int 整数），这个哈希码的作⽤是确定该对象在 哈希表中的索引位置。 Object 的 hashCode() ⽅法是native⽅法，也就是⽤ C 语⾔或 C++ 实现 的，该⽅法通常⽤来将对象的内存地址转换为整数之后返回。

### 为什么要有 hashCode？

把对象加入HashSet时首先会根据对象的hashCode值来确定对象加入的位置，若发现有hashCode相同的对象再调用equals来检查对象是否真的相同，减少了equals的次数提高了执行速度

#### hashCode() 和 equals() 都是⽤于⽐较两个对象是否相等。 那为什么 JDK 还要同时提供这两个⽅法呢？

在一些容器中有了hashCode()后判断元素是否在对应的容器中效率会更高

#### 那为什么两个对象有相同的 hashCode 值，它们也不⼀定是相等的？

这是因为两个对象的 hashCode 值相等并不代表两个对象就相等。hashCode()使用的算法可能使多个不同对象传回相同的哈希值，发生哈希碰撞

- hashCode值相等，两个对象由于哈希碰撞不一定相等
- hashCode值相等且equals()返回值为true两个对象才相等
- hashCode值不相等则两个对象不相等

equals ⽅法判断两个对象是相等的，那这两个对象的 hashCode 值也要相等

### String

#### String、StringBuffer、StringBuilder 的区别？

可变性：String 是不可变的，StringBuilder 与 StringBuffer 都继承自AbstractStringBuilder 类，在 AbstractStringBuilder 中也是 使⽤字符数组保存字符串，不过没有使⽤ final 和 private 关键字修饰

线程安全性：String 中的对象是不可变的，也就可以理解为常量，线程安全。

StringBuffer 对⽅法加了同步锁或者 对调⽤的⽅法加了同步锁，所以是线程安全的。 StringBuilder 并没有对⽅法进⾏加同步锁，所以是 ⾮线程安全的。

性能: 每次对 String 类型进⾏改变的时候，都会⽣成⼀个新的 String 对象，然后将指针指向新的 String 对象。 StringBuffer 每次都会对 StringBuffer 对象本身进⾏操作，⽽不是⽣成新的对象并改 变对象引⽤,相同情况下使⽤ StringBuilder性能更高

操作少量数据使用String，单线程大量使用StringBuilder，多线程大量使用StringBuffer

#### String 为什么是不可变的?

String 类中使⽤ final 关键字修饰字符数组来保存字符串

String 真正不可变有下⾯⼏点原因：

1. 保存字符串的数组被 final 修饰且为私有的，并且 String 类没有提供/暴露修改这个字符 串的⽅法。 2. String 类被 final 修饰导致其不能被继承，进⽽避免了⼦类破坏 String 不可变。
2. java9后String，StringBuffer，StringBuilder改用byte数组存储字符串，节省一半存储空间

#### 字符串拼接用“+” 还是 StringBuilder?

java不支持运算符重载，“+”和“+=”是专⻔为 String 类重载过的运算符，仅有的重载过的两个运算符，在循环内使⽤“+”进⾏字符串的拼接的实际上是通过 StringBuilder 调⽤ append() ⽅法 实现的，拼接完成之后调⽤ toString() 得到⼀个 String 对象 ，编译器不会创建单个 StringBuilder 以复⽤，会导致创建过多的 StringBuilder 对象，应使用StringBuilder进行拼接

#### String的equals() 和 Object的equals() 有何区别？

 String 中的 equals ⽅法是被重写过的，⽐较的是 String 字符串的值是否相等。 Object 的 equals ⽅法是⽐较的对象的内存地址。

#### 字符串常量池的作⽤了解吗？

字符串常量池 是 JVM 为了提升性能和减少内存消耗针对字符串（String 类）专⻔开辟的⼀块区域， 主要⽬的是为了避免字符串的重复创建

#### String s1 = new String("abc");这段代码创建了⼏个字符串对象？

如果字符串常量池中不存在字符串对象“abc”的引⽤，那么会在堆中创建 2 个字符串对象“abc，如果存在只会创建1个

#### intern ⽅法有什么作⽤?

String.intern() 是⼀个 native⽅法，其作⽤是将指定的字符串对象的引⽤保存在字符串常量 池中

如果字符串常量池中保存了对应的字符串对象的引⽤，就直接返回该引⽤。 如果字符串常量池中没有保存了对应的字符串对象的引⽤，那就在常量池中创建⼀个指向该字符 串对象的引⽤并返回。

```java
// 在堆中创建字符串对象”Java“
// 将字符串对象”Java“的引⽤保存在字符串常量池中
String s1 = "Java";
// 直接返回字符串常量池中字符串对象”Java“对应的引⽤
String s2 = s1.intern();
// 会在堆中在单独创建⼀个字符串对象
String s3 = new String("Java");
// 直接返回字符串常量池中字符串对象”Java“对应的引⽤
String s4 = s3.intern();
// s1 和 s2 指向的是堆中的同⼀个对象
System.out.println(s1 == s2); // true
// s3 和 s4 指向的是堆中不同的对象
System.out.println(s3 == s4); // false
// s1 和 s4 指向的是堆中的同⼀个对象
System.out.println(s1 == s4); //true
```

#### String 类型的变量和常量做“+”运算时发⽣了什么？

```java
String str1 = "str";
String str2 = "ing";
String str3 = "str" + "ing";
String str4 = str1 + str2;
String str5 = "string";
System.out.println(str3 == str4);//false
System.out.println(str3 == str5);//true
System.out.println(str4 == str5);//false
```

对于编译期可以确定值的字符串，也就是常量字符串 ，jvm 会将其存⼊字符串常量池,字符 串常量拼接得到的字符串常量在编译阶段就已经被存放字符串常量池,于 String str3 = "str" + "ing"; 编译器会优化成 String str3 = "string"

，引⽤的值在程序编译期是⽆法确定的，编译器⽆法对其进⾏优化，对象引⽤和“+”的字符串拼接⽅式，实际上是通过 StringBuilder 调⽤ append() ⽅法实现的，拼接完 成之后调⽤ toString() 得到⼀个 String 对象，写代码时要尽量避免多个字符串对象拼接

字符串使⽤ final 关键字声明之后，可以让编译器当做常量来处理，编译器在程序编译期就可以确定 它的值，其效果就相当于访问常量。 如果 编译器在运⾏时才能知道其确切值的话，就⽆法对其优化

## Java基础(下)

### Exception 和 Error 有什么区别？

Exception :程序本身可以处理的异常，可以通过 catch 来进⾏捕获。 Exception ⼜可以分为 Checked Exception (受检查异常，必须处理) 和 Unchecked Exception (不受检查异常，可以不 处理)。

 Error ： Error 属于程序⽆法处理的错误 ，我们没办法通过 catch 来进⾏捕获不建议通过 catch 捕获 。例如 Java 虚拟机运⾏错误（ Virtual MachineError ）、虚拟机内存不够错误 ( OutOfMemoryError )、类定义错误（ NoClassDefFoundError ）等 。这些异常发⽣时，Java 虚拟 机（JVM）⼀般会选择线程终⽌。

Exception和Error都是Throwable的子类

### Checked Exception 和 Unchecked Exception 有什么区别？

![java-exception](/assets/img/2024-9-9-java-basic-interview/java-exception.png)

Checked Exception 即 受检查异常 ，Java 代码在编译过程中，如果受检查异常没有被 catch 或 者 throws 关键字处理的话，就没办法通过编译:IO相关异常、ClassNotFoundException、SQLException

Unchecked Exception 即 不受检查异常 ，Java 代码在编译过程中 ，我们即使不处理不受检查异常 也可以正常通过编译

RuntimeException 及其⼦类都统称为⾮受检查异常，常⻅的有： NullPointerException、IllegalArgumentException 、NumberFormatException 、ArrayIndexOutOfBoundsException 、ClassCastException、ArithmeticException、SecurityException、 UnsupportedOperationException 

![unchecked&checked-exception](/assets/img/2024-9-9-java-basic-interview/unchecked&checked-exception.png)

### Throwable 类常⽤⽅法有哪些？

- String getMessage() : 返回异常发⽣时的简要描述 

- String toString() : 返回异常发⽣时的详细信息

- String getLocalizedMessage() : 返回异常对象的本地化信息。使⽤ Throwable 的⼦类覆盖这个⽅ 法，可以⽣成本地化信息。如果⼦类没有覆盖该⽅法，则该⽅法返回的信息与 getMessage() 返 回的结果相同 

- void printStackTrace() : 在控制台上打印 Throwable 对象封装的异常信息

### try-catch-finally 如何使⽤？

try 块 ： ⽤于捕获异常。其后可接零个或多个 catch 块，如果没有 catch 块，则必须跟⼀个 finally 块。

 catch 块 ： ⽤于处理 try 捕获到的异常。

 finally 块 ： ⽆论是否捕获或处理异常， finally 块⾥的语句都会被执⾏。当在 try 块或 catch 块中遇到 return 语句时， finally 语句块将在⽅法返回之前被执⾏。

不要在 finally 语句块中使⽤ return, 当 try 语句和 finally 语句中都有 return 语句时，try 语句 块中的 return 语句会被忽略,这是因为是因为 try 语句中的 return 返回值会先被暂存在⼀个本地变量中， 当执⾏到 finally 语句中的 return 之后，这个本地变量的值就变为了 finally 语句中的 return 返回值。

### finally 中的代码⼀定会执⾏吗？

不一定，

- finally 之前虚拟机被终⽌运⾏

- 程序所在的线程死亡。
- 关闭 CPU。

### 如何使⽤ try-with-resources 代替 try-catch-finally ？

1. 适⽤范围（资源的定义）： 任何实现 java.lang.AutoCloseable 或者 java.io.Closeable 的对象
2.  关闭资源和 finally 块的执⾏顺序： 在 try-with-resources 语句中，任何 catch 或 finally 块在声 明的资源关闭后运⾏

```java
//读取⽂本⽂件的内容
Scanner scanner = null;
try {
	scanner = new Scanner(new File("D://read.txt"));
	while (scanner.hasNext()) {
	System.out.println(scanner.nextLine());
 	}
} catch (FileNotFoundException e) {
	e.printStackTrace();
} finally {
	if (scanner != null) {
	scanner.close();
 }
}
```

```java
try (Scanner scanner = new Scanner(new File("test.txt"))) {
	while (scanner.hasNext()) {
	System.out.println(scanner.nextLine());
 }
} catch (FileNotFoundException fnfe) {
	fnfe.printStackTrace();
}
```

### 异常使⽤有哪些需要注意的地⽅？

- 不要把异常定义为静态变量，因为这样会导致异常栈信息错乱。每次⼿动抛出异常，我们都需要 ⼿动 new ⼀个异常对象抛出。

- 抛出的异常信息要有意义,具体的异常⽐如字符串转换为数字格式错误的时候应该抛出 NumberFormatException ⽽不是其⽗类 IllegalArgumentException 。 
- 使⽤⽇志打印异常之后就不要再抛出异常了

### 反射的优缺点？

反射可以让我们的代码更加灵活、为各种框架提供开箱即⽤的功能提供了便利。安全问题，⽐如可以⽆视泛型参 数的安全检查（泛型参数的安全检查发⽣在编译时）,性能也要稍差点

### 反射的应⽤场景？

框架中使用了大量动态代理，动态代理实现依赖反射，注解的实现用到反射

### 什么是序列化?什么是反序列化?

序列化： 将数据结构或对象转换成⼆进制字节流的过程 

反序列化：将在序列化过程中所⽣成的⼆进制字节流转换成数据结构或者对象的过程

对于不想进⾏序列化的变量，使⽤ transient 关键字修饰。transient 关键字的作⽤是：阻⽌实例中那些⽤此关键字修饰的的变量序列化；当对象被反序列化 时，被 transient 修饰的变量值不会被持久化和恢复。

transient 只能修饰变量，不能修饰类和⽅法。 transient 修饰的变量，在反序列化后变量值将会被置成类型的默认值。例如，如果是修饰 int 类型，那么反序列后结果就是 0 。 static 变量因为不属于任何对象(Object)，所以⽆论有没有 transient 关键字修饰，均不会被序 列化。

### Java IO 流

Java IO 流的 40 多个类都是从如下 4 个抽象类基类中派⽣出来的。 InputStream / Reader : 所有的输⼊流的基类，前者是字节输⼊流，后者是字符输⼊流。

OutputStream / Writer : 所有输出流的基类，前者是字节输出流，后者是字符输出流。

### I/O 流为什么要分为字节流和字符流呢?

不管是⽂件读写还是⽹络发送接收，信息的最⼩存储单元都是字节，那为什么 I/O 流 操作要分为字节流操作和字符流操作呢？

字符流是由 Java 虚拟机将字节转换得到的，这个过程较耗时；

 如果我们不知道编码类型的话，使⽤字节流的过程中很容易出现乱码问题。

## Java集合

![collection-map](/assets/img/2024-9-9-java-basic-interview/collection-map.png)

### 说说 List, Set, Queue, Map 四者的区别？

List : 存储的元素是有序的、可重复的。

 Set: 存储的元素是⽆序的、不可重复的。

 Queue : 按特定的排队规则来确定先后顺序，存储的元素是有序的、可 重复的。 

Map: 使⽤键值对（key-value）存储,key 是⽆序的、不可重复的，value 是⽆序的、可重复的，每个键最 多映射到⼀个值。

### 为什么要使⽤集合？

数组的缺点是⼀旦声明之后，⻓度就不可变了；同时，声明数组时的数据类型也决定了该数组存储的 数据的类型；⽽且，数组存储的数据是有序的、可重复的，特点单⼀。 但是集合提⾼了数据存储的灵活性，Java 集合不仅可以⽤来存储不同类型不同数量的对象，还可以 保存具有映射关系的数据。

### ArrayList 和 Vector 的区别?

ArrayList 是 List 的主要实现类，底层使⽤ Object[ ] 存储，适⽤于频繁的查找⼯作，线程不 安全 ； Vector 是 List 的古⽼实现类，底层使⽤ Object[ ] 存储，线程安全的。

### ArrayList 与 LinkedList 区别?

是否保证**线程安全**： ArrayList 和 LinkedList 都是不同步的，也就是不保证线程安全；

**底层数据结构**： ArrayList 底层使⽤的是 Object 数组； LinkedList 底层使⽤的是 双向链表 数据结构

**插⼊和删除是否受元素位置的影响**：ArrayList 采⽤数组存储，所以插⼊和删除元素的时间复杂度受元素位置的影响，LinkedList 采⽤链表存储，所以，如果是在头尾插⼊或者删除元素不受元素位置的影响

**是否⽀持快速随机访问**：⽽ ArrayList ⽀持，LinkedList 不⽀持

**内存空间占⽤**：ArrayList在 list 列表的结尾会预留⼀定的容量空间， ⽽ LinkedList 的空间要 存放直接后继和直接前驱以及数据

###  ArrayList 的扩容机制

![ArrayList 类图](/assets/img/2024-9-9-java-basic-interview/arraylist.png)

略，太长

### comparable 和 Comparator 的区别

comparable 接⼝⾃ java.lang 包 ，有⼀个 compareTo(Object obj) ⽅法⽤来排序， comparator 接⼝出⾃ java.util 包，它有⼀个 compare(Object obj1, Object obj2) ⽅法⽤来排 序

### ⽆序性和不可重复性的含义是什么

⽆序性是指存储的数据在底层数组中并⾮按照数组索引的顺序添加 ，⽽ 是根据数据的哈希值决定的。 不可重复性是指添加的元素按照 equals() 判断时 ，返回 false，需要同时重写 equals() ⽅法和 hashCode() ⽅法

### ⽐较 HashSet、LinkedHashSet 和 TreeSet 三者的异同

HashSet 、 LinkedHashSet 和 TreeSet 都是 Set 接⼝的实现类，都能保证元素唯⼀，并且都 不是线程安全的。

 HashSet 、 LinkedHashSet 和 TreeSet 的主要区别在于底层数据结构不同。 HashSet 的底层数 据结构是哈希表（基于 HashMap 实现）。 LinkedHashSet 的底层数据结构是链表和哈希表， 元素的插⼊和取出顺序满⾜ FIFO。 TreeSet 底层数据结构是红⿊树，元素是有序的，排序的⽅ 式有⾃然排序和定制排序，底层数据结构不同⼜导致这三者的应⽤场景不同。 HashSet ⽤于不需要保证元素插⼊和取出顺 序的场景， LinkedHashSet ⽤于保证元素的插⼊和取出顺序满⾜ FIFO 的场景， TreeSet ⽤于 ⽀持对元素⾃定义排序规则的场景。

### Queue 与 Deque 的区别

Queue 是单端队列，只能从⼀端插⼊元素，另⼀端删除元素，实现上⼀般遵循 先进先出（FIFO） 规则

Deque 是双端队列，在队列的两端均可以插⼊或删除元素。

### PriorityQueue

与 Queue 的区别在于元素出队顺序是与优先级相关的， 即总是优先级最⾼的元素先出队，二叉堆实现的，非线程安全，默认是小顶堆，可以接收一个Comparator自定义优先级

### HashMap 和 HashSet 区别

HashSet 底层就是基于 HashMap 实现的

### HashMap 的底层实现

JDK1.8 之后当链表⻓度⼤于阈值（默认为 8）（将链表转换成红⿊树前会判断，如果当前数组的⻓度⼩于 64，那么会选择先进⾏数组扩容，⽽ 不是转换为红⿊树）时，将链表转化为红⿊树，以减少搜索时间
