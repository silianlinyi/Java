# 常用的Java类——Object

### clone()方法

在应用开发过程中，我们可能会需要拷贝（copy，复制）一个现有的对象，即得到一个新对象并希望其与现有对象封装完全相同的信息
（属性值），主要是为了此后两者互不相干，修改其中的一个对象不会影响到另一个，我们知道，简单地进行引用变量间的赋值是不能解决
问题的，因为并没有创建新对象；而自己编写代码先创建一个新对象，再将原始对象的属性值一一复制过来也比较繁琐，且存在后述的
“浅度拷贝”问题；这种情况下，利用clone()方法来实现对象拷贝不失为一种明智的选择。

clone方法原型如下：

    protected native Object clone() throws CloneNotSupportedException;

clone方法在Object类中被定义为protected的，因此只有在其子类中进行重写才能真正发挥作用，Java语言规定，所有要进行“克隆”的对象
所属的类必须实现java.lang.Cloneable接口，这是一种安全性保护。

<b>实现简单的克隆clone操作：</b>

> 源文件：Person.java

    public class Person implements Cloneable {
    	private String name;
    	private int age;
    
    	public Person(String name, int age) {
    		this.name = name;
    		this.age = age;
    	}
    
    	public void setName(String name) {
    		this.name = name;
    	}
    
    	public void setAge(int age) {
    		this.age = age;
    	}
    
    	public void display() {
    		System.out.println("Name: " + name + "\tAge: " + age);
    	}
    
    	public Object clone() {
    		Person p = null;
    		try {
    			p = (Person) super.clone();
    		} catch (CloneNotSupportedException e) {
    			e.printStackTrace();
    		}
    		return p;
    	}
    
    }

> 源文件：TestClone.java

    public class TestClone {
    	public static void main(String[] args) {
    		Person p1 = new Person("Tom", 18);
    		Person p2 = (Person) p1.clone();
    		System.out.println(p1 == p2);
    		p2.setAge(34);
    		p2.display();
    		p1.display();
    	}
    }

程序运行结果输出为：

    false
    Name: Tom	Age: 34
    Name: Tom	Age: 18

细心的读者可能会去查看java.lang.Cloneable接口的源代码，并惊奇地发现该接口中没有任何内容，其源代码如下：

    package java.lang;
    public interface Cloneable {
    }

这样的接口被称为空接口，实际上只是起到标记的作用————必须是该接口实现类的实例才能进行克隆操作，因此这样的接口也称
“标记性接口”。需要小心的是，使用上述的clone方法进行对象拷贝可能出现“浅度拷贝”的问题，我们还是先看一个直观的例子，然后
再作分析。

<b>浅度拷贝</b>

> 源文件：Person.java(同上)
> 源文件：Book.java

    import java.lang.Cloneable;
    import java.lang.String;
    
    public class Book implements Cloneable {
    	String bookName;
    	double price;
    	Person author;
    
    	public Book(String bn, double price, Person author) {
    		this.bookName = bn;
    		this.price = price;
    		this.author = author;
    	}
    
    	public Object clone() {
    		Book b = null;
    		try {
    			b = (Book) super.clone();
    		} catch (CloneNotSupportedException e) {
    			e.printStackTrace();
    		}
    		return b;
    	}
    
    	public void display() {
    		System.out.print(bookName + "\t" + price + "\t");
    		author.display();
    	}
    }

> 源文件TestLowCopy.java

    public class TestLowCopy {
    	public static void main(String[] args) {
    		Book b1 = new Book("Java编程", 30.50, new Person("张三",34));
    		Book b2 = (Book)b1.clone();
    		b2.price = 44.0;
    		b2.author.setAge(45);
    		b2.author.setName("李四");
    		b2.bookName = "Java开发";
    		b1.display();
    		b2.display();
    	}
    }

程序运行输出结果为：

    Java编程	30.5	Name: 李四	Age: 45
    Java开发	44.0	Name: 李四	Age: 45

可以看出克隆后b2对象及其属性author所引用的Person对象的改动影响到了b1，这是由clone()方法的实现机制决定的————clone方法先在
内存中开辟一块目标对象所需的存储空间（只要是同属于一个类型，则对象占有的存储空间大小也一定相同），然后直接将原始对象存储
空间中的内容（包括各属性的值）原样拷贝过来。对基本类型的属性，其属性值就是真正要用的信息，这样的操作当然没有问题，但对于
引用类型的属性，其值只是所引用的其他对象的句柄，这就导致clone后“副本”对象与原始对象的引用类型属性指向同样的对象，为更
直观，现给出上述程序运行到关键点时的内存状态，如图：












