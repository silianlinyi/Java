# 第13章 储存类的仓库——Java常用类库

## 13.4 System类与Runtime类

### 13.4.1 System类

getProperties()方法是获得当前虚拟机的环境属性。每一个属性都是变量与值以成对的形式出现的。

> 打印当前虚拟机的所有环境属性

    import java.util.Enumeration;
    import java.util.Properties;
    
    public class SystemInfo {
    	public static void main(String[] args) {
    		Properties properties = System.getProperties();
    		Enumeration<?> e = properties.propertyNames();
    		while(e.hasMoreElements()) {
    			String key = (String)e.nextElement();
    			System.out.println(key + " = " + properties.getProperty(key));
    		}
    	}
    }

### 13.4.2 Runtime类

Runtime.getRuntime()获得正在运行的Runtime对象的引用。

> Java进程与子进程交互RuntimeDemo.java

    public class RuntimeDemo {
    	public static void main(String[] args) {
    		Runtime run = Runtime.getRuntime();
    		try {
    			run.exec("notepad.exe");
    		} catch (Exception e) {
    			e.printStackTrace();
    		}
    	}
    }

## 14.4 打包工具——Jar命令的使用

jar文件就是Java Archive File，而它的应用是与Java息息相关的。jar文件就是一种压缩文件，与常见的ZIP压缩文件格式兼容，习惯
上称之为jar包。如果开发者开发了许多类，当需要把这些类提供给用户使用时，通常会将这些类压缩到一个jar文件中，以jar包的方式
提供给用户使用。

















