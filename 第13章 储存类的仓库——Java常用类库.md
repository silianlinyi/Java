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





















