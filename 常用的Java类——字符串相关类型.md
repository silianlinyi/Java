# 常用的Java类——字符串相关类型

### String类

String类用来表示字符串常量的，用它创建的每个对象都是字符串常量，一经建立便不能修改。调用String类的常用方法改变后的字符串
都成为一个新的字符串，原字符串不变。

### StringBuffer类

* 与String类区别：StringBuffer类对象保存可修改的Unicode编码字符序列；
* 与StringBuilder类区别：StringBuffer类是线程安全的；

在实际开发中，我们经常需要对字符串的内容进行修改，使用String类型不是不可以，但的确效率不高（因其对象一经创建内容不可改变，
就只能不断地创建新对象并销毁旧的对象），这种情况下使用java.lang.StringBuffer类就比较适合了，该类表示的是内容可以修改的
Unicode编码字符序列，其对象创建之后，所保存的字符串内容和长度均可以修改，实际上每个StringBuffer对象都拥有一个可变容量的
字符串缓冲区，该缓冲区的容量（缓冲区占有的内存空间大小，或者说可以容纳字符的数量）可以随着内容的增加自动扩充，也可以
直接设定。

### StringBuilder类

StringBuilder类是线程不安全的，即不保证其对象的同步性，在多线程环境中是不安全的。除了不保证同步性之外，StringBuilder类在
性能上要比StringBuffer好一些，因此在单线程编程或者能够确定线程安全的情况下，建议尽量用StringBuilder；反之，则应使用
StringBuffer。

### StringTokenizer类

java.util.StringTokenizer类的功能是将当前字符串按照默认或指定的分隔符（即分隔标记）分解为多个片段。
