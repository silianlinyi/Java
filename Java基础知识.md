# Java基础知识

第一个程序Helloworld.java

    public class Helloworld {
    	public static void main(String[] args) {
    		System.out.println("Helloworld");
    	}
    }

编译java程序（-verbose 输出有关编译器正在执行的操作的消息）
    
> javac -verbose Helloworld.java
    
    [解析开始时间 RegularFileObject[Helloworld.java]]
    [解析已完成, 用时 14 毫秒]
    [源文件的搜索路径: .]
    [类文件的搜索路径: 
    C:\Program Files\Java\jdk1.7.0_40\jre\lib\resources.jar,
    C:\Program Files\Java\jdk1.7.0_40\jre\lib\rt.jar,
    C:\Program Files\Java\jdk1.7.0_40\jre\lib\sunrsasign.jar,
    C:\Program Files\Java\jdk1.7.0_40\jre\lib\jsse.jar,
    C:\Program Files\Java\jdk1.7.0_40\jre\lib\jce.jar,
    C:\Program Files\Java\jdk1.7.0_40\jre\lib\charsets.jar,
    C:\Program Files\Java\jdk1.7.0_40\jre\lib\jfr.jar,
    C:\Program Files\Java\jdk1.7.0_40\jre\classes,
    C:\Program Files\Java\jdk1.7.0_40\jre\lib\ext\access-bridge.jar,
    C:\Program Files\Java\jdk1.7.0_40\jre\lib\ext\dnsns.jar,
    C:\Program Files\Java\jdk1.7.0_40\jre\lib\ext\jaccess.jar,
    C:\Program Files\Java\jdk1.7.0_40\jre\lib\ext\localedata.jar,
    C:\Program Files\Java\jdk1.7.0_40\jre\lib\ext\sunec.jar,
    C:\Program Files\Java\jdk1.7.0_40\jre\lib\ext\sunjce_provider.jar,
    C:\Program Files\Java\jdk1.7.0_40\jre\lib\ext\sunmscapi.jar,
    C:\Program Files\Java\jdk1.7.0_40\jre\lib\ext\sunpkcs11.jar,
    C:\Program Files\Java\jdk1.7.0_40\jre\lib\ext\zipfs.jar,.]
    [正在加载ZipFileIndexFileObject[C:\Program Files\Java\jdk1.7.0_40\lib\ct.sym(META-INF/sym/rt.jar/java/lang/Object.class)]]
    [正在加载ZipFileIndexFileObject[C:\Program Files\Java\jdk1.7.0_40\lib\ct.sym(META-INF/sym/rt.jar/java/lang/String.class)]]
    [正在检查Helloworld]
    [正在加载ZipFileIndexFileObject[C:\Program Files\Java\jdk1.7.0_40\lib\ct.sym(META-INF/sym/rt.jar/java/lang/AutoCloseable.class)]]
    [正在加载ZipFileIndexFileObject[C:\Program Files\Java\jdk1.7.0_40\lib\ct.sym(META-INF/sym/rt.jar/java/lang/System.class)]]
    [正在加载ZipFileIndexFileObject[C:\Program Files\Java\jdk1.7.0_40\lib\ct.sym(META-INF/sym/rt.jar/java/io/PrintStream.class)]]
    [正在加载ZipFileIndexFileObject[C:\Program Files\Java\jdk1.7.0_40\lib\ct.sym(META-INF/sym/rt.jar/java/io/FilterOutputStream.class)]]
    [正在加载ZipFileIndexFileObject[C:\Program Files\Java\jdk1.7.0_40\lib\ct.sym(META-INF/sym/rt.jar/java/io/OutputStream.class)]]
    [已写入RegularFileObject[Helloworld.class]]
    [共 146 毫秒]
    
最后，执行编译生成的字节码（class）文件

> java Helloworld

## Java数据类型

* 基本数据类型
    * 数值型
        * 整型类型（byte,short,int,long）
        * 浮点型（float,double）
    * 字符型
    * 布尔型（boolean）
* 引用数据类型
    * 类（class）
    * 接口（interface）
    * 数组


















    
