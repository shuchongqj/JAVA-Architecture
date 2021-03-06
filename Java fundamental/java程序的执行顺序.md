
在Java中， 创建一个对象常常需要经历如下几个过程：父类的类构造器<clinit>() -> 子类的类构造器<clinit>() -> 父类的成员变量和实例代码块 -> 父类的构造
函数 -> 子类的成员变量和实例代码块 -> 子类的构造函数。
 
 如果类还没有被加载： 
 
1、先执行父类的静态代码块和静态变量初始化，并且静态代码块和静态变量的执行顺序只跟代码中出现的顺序有关。 

2、执行子类的静态代码块和静态变量初始化。 

3、执行父类的实例变量初始化 

4、执行父类的构造函数 

5、执行子类的实例变量初始化 

6、执行子类的构造函数 

如果类已经被加载： 
则静态代码块和静态变量就不用重复执行，再创建类对象时，只执行与实例相关的变量初始化和构造方法。

 
```java

public class StaticTest {
    public static void main(String[] args) {
        staticFunction();
    }

    static StaticTest st = new StaticTest();

    static {   //静态代码块
        System.out.println("1");
    }

    {       // 实例代码块
        System.out.println("2");
    }

    StaticTest() {    // 实例构造器
        System.out.println("3");
        System.out.println("a=" + a + ",b=" + b);
    }

    public static void staticFunction() {   // 静态方法
        System.out.println("4");
    }

    int a = 110;    // 实例变量
    static int b = 112;     // 静态变量
}
/* Output: 
        2
        3
        a=110,b=0
        1
        4
```
大家能得到正确答案吗？虽然笔者勉强猜出了正确答案，但总感觉怪怪的。因为在初始化阶段，当JVM对类StaticTest进行初始化时，首先会执行下面的语句：

```java

static StaticTest st = new StaticTest();

```

也就是实例化StaticTest对象，但这个时候类都没有初始化完毕啊，能直接进行实例化吗？事实上，这涉及到一个根本问题就是：实例初始化不一定要在类初始化结束之后才开始初始化。 下面我们结合类的加载过程说明这个问题。

　　我们知道，类的生命周期是：加载->验证->准备->解析->初始化->使用->卸载，并且只有在准备阶段和初始化阶段才会涉及类变量的初始化和赋值，因此我们只针对这两个阶段进行分析：

　　首先，在类的准备阶段需要做的是为类变量（static变量）分配内存并设置默认值(零值)，因此在该阶段结束后，类变量st将变为null、b变为0。特别需要注意的是，如果类变量是final的，那么编译器在编译时就会为value生成ConstantValue属性，并在准备阶段虚拟机就会根据ConstantValue的设置将变量设置为指定的值。也就是说，如果上述程度对变量b采用如下定义方式时：

```java
static final int b=112

```

那么，在准备阶段b的值就是112，而不再是0了。

　　此外，在类的初始化阶段需要做的是执行类构造器<clinit>()，需要指出的是，类构造器本质上是编译器收集所有静态语句块和类变量的赋值语句按语句在源码中的顺序合并生成类构造器<clinit>()。因此，对上述程序而言，JVM将先执行第一条静态变量的赋值语句：
```java
 st = new StaticTest ()
```
 
 此时，就碰到了笔者上面的疑惑，即“在类都没有初始化完毕之前，能直接进行实例化相应的对象吗？”。事实上，从Java角度看，我们知道一个类初始化的基本常识，那就是：在同一个类加载器下，一个类型只会被初始化一次。所以，一旦开始初始化一个类型，无论是否完成，后续都不会再重新触发该类型的初始化阶段了(只考虑在同一个类加载器下的情形)。因此，在实例化上述程序中的st变量时，实际上是把实例初始化嵌入到了静态初始化流程中，并且在上面的程序中，嵌入到了静态初始化的起始位置。这就导致了实例初始化完全发生在静态初始化之前，当然，这也是导致a为110b为0的原因。

　　因此，上述程序的StaticTest类构造器<clinit>()的实现等价于：

```java

public class StaticTest {
    <clinit>(){
        a = 110;    // 实例变量
        System.out.println("2");        // 实例代码块
        System.out.println("3");     // 实例构造器中代码的执行
        System.out.println("a=" + a + ",b=" + b);  // 实例构造器中代码的执行
        类变量st被初始化
        System.out.println("1");        //静态代码块
        类变量b被初始化为112
    }
}

```

因此，上述程序会有上面的输出结果。下面，我们对上述程序稍作改动，如下所示：

```java

public class StaticTest {
    public static void main(String[] args) {
        staticFunction();
    }

    static StaticTest st = new StaticTest();

    static {
        System.out.println("1");
    }

    {
        System.out.println("2");
    }

    StaticTest() {
        System.out.println("3");
        System.out.println("a=" + a + ",b=" + b);
    }

    public static void staticFunction() {
        System.out.println("4");
    }

    int a = 110;
    static int b = 112;
    static StaticTest st1 = new StaticTest();
}


```
在程序最后的一行，增加以下代码行：

```java

 static StaticTest st1 = new StaticTest();

```

那么，此时程序的输出又是什么呢？如果你对上述的内容理解很好的话，不难得出结论(只有执行完上述代码行后，StaticTest类才被初始化完成)，即：

```java
2
3
a=110,b=0
1
2
3
a=110,b=112
4
