## 其他方法

- `System.currentTimeMillis(): long` : 获取1970年1月1日0时(北京时间1970年1月1日上午8时)距当前时间的时间戳，单位是毫秒
- `System.arraycopy(src: Object, srcPos: int, dest: Object, destPos: int, length: int): void` : src为源数组，srcPos是源数组起始位置，dest是目标数组，destPos是目标数组的下标，length是复制的数组长度

## 一、Math类( java.lang.Math )

1.  **常量constant**
    - `Math.PI` ：圆周率
    - `Math.E` ：自然对数的底
2.  **三角函数方法**
    - `sin(radians)` ：返回以弧度为单位的角度的三角正弦函数值
    - `cos(radians`
    - `tan(radians)`
    - `toRadians(degrees)` ：将以度为单位的角度值转换为以弧度表示
    - `toDegrees(radians)`
    - `asin(a)` ：返回以弧度为单位的角度的反三角正弦函数值
    - `acos(a)`
    - `atan(a)`
3.  **指数函数方法**
    - `exp(x)`
    - `log(x)`
    - `log10(x)`
    - `pow(a,b)`
    - `sqrt(x)`
4.  **取整方法**
    - `ceil(x)` : x向上取整，返回一个double类型
    - `floor(x)` ：x向下取整，返回一个double类型
    - `rint(x)` ：向偶数四舍五入取整，返回一个double类型
    - `round(x)` ：四舍五入取整，如果x是float类型，则返回int类型，如果x是double，则返回long类型
5.  **其他方法**
    - `min(num1,num2)` : 返回两个数的最小值
    - `max(num1,num2)` ：返回两个数的最大值
    - `abs(x)` ：返回x的绝对值
    - `random()` ：生成一个大于等于0.0且小于1.0的double类型随机数(0.0<=Math.random<1.0),可以使用a+Math.random*b生成一个a~a+b的随机数(不包括a+b)

## 二、Character类（ java.lang.Character )

|Method|Usage|
|-|-|
| isDigit(ch:char):boolean: | 判断是否是数字|
| isLetter(ch:char):boolean | 判断是否是字母|
| isLetterOrDigit(ch:char):boolean | 判断是否是数字或者字母|
| isLowerCase(ch:char):boolean | 判断是否是小写字母|
| isUpperCase(ch:char):boolean | 判断是否是大写字母|
| toLowerCase(ch:char):char| 返回指定字符的小写形式|
| toUpperCase(ch:char):char| 返回指定字符的大写形式|

## 三、String类（ java.lang.String ）

1.  **基本方法**
    - `length(): int` ： 返回字符串的字符数
    - `charAt(index: int): char` ： 返回字符串指定位置的字符
    - `concat(str: String): String` ： 将两个字符串连接起来，并返回新字符串
    - `toUpperCase(): String` ： 返回一个新字符串，其中所有字符都是大写
    - `toLowerCase(): String` ： 返回一个新字符串，其中所有字符都是小写
    - `trim(): String` ： 返回一个新字符串，去掉了两边的空白字符
2.  **比较方法**
    - `equals(str: String): boolean` ： 如果该字符串等于字符串str，返回true
    - `equalsIgnoreCase(str: String): boolean` ： 忽略大小写判读字符串是否是相等
    - `compareTo(str: String): int` ： 返回一个大于0、等于0、小于0的数，分别表示该字符串是否大于、等于、小于str
    - `compareIgnoreCase(str: String): int` ： 忽略大小写比较字符串
    - `startsWith(prefix: String): boolean` ： 判断字符串是否是以prefix为前缀
    - `endsWith(suffix: String): boolean` ： 判断字符串是否是以suffix为后缀
    - `contains(str: String): boolean` ： 如果str是该字符串的子字符串，返回true
3.  **获取子串**
    - `substring(beginIndex: int): String` : 返回该字符串的子串，从指定位置beginIndex的字符开始到字符串的结尾
    - `substring(beginIndex: int, endIndex: int): String` ： 返回该字符串的子串，从指定位置beginIndex的字符到endIndex-1的字符,不包含endIndex的字符
4.  **获取子串或者字符的下标**
    - `indexOf(ch: char): int` ： 返回字符串中出现的第一个ch下标，如果没匹配到则返回-1
    - `indexOf(cha: char, fromIndex: int): in` ： 返回字符串中从fromIndex之后出现的第一个ch下标，如果没匹配成功则返回-1
    - `indexOf(s: String): int` ： 返回字符串中出现的第一个字符串s的下标，如果没匹配成功，返回-1
    - `indexOf(s: String, fromIndex: int): int` ： 返回字符串中从fromIndex之后出现的第一个字符串s的下标，如果没匹配成功则返回-1
    - `lastIndexOf(ch: char): int` : 返回字符串中最后一个出现ch的下标，如果没匹配成功则返回-1
    - `lastIndexOf(s: String): int` ： 返回字符串中最后一个出现字符串s的下标，如果没匹配成功则返回-1
    - `lastIndexOf(ch: char, fromIndex: int): int` ： 返回字符串中从fromIndex之后出现的最后一个ch的下标，如果没有匹配成功则返回-1
    - `lastIndexOf(s: String, fromIndex: int): int` ： 返回字符串中从fromIndex之后出现的最后一个字符串s的下标，如果没匹配成功则返回-1
5.  **字符串和数字之间的转换**
    - `Integer.parseInt(intString: String): int` ： 将数值字符串转换为int类型的值
    - `Double.parseDouble(doubleString: String): double` ： 将数值字符串转换为double类型的值
6.  **替换和拆分字符串**
    - `replace(oldChar: char ,newChar: char): String` ： 将旧字符全部替换成新字符
    - `replaceFirst(oldString: String, newString: String): String` ： 替换匹配到的第一个字符串
    - `replaceAll(oldString: String, newString: String): String` ： 将全部字符串替换为新字符串
    - `split(delimiter: String): String[]` ： 返回一个字符串数组。其中包含被分隔符拆分的子字符串集
7.  **字符串与数组的转换**
    - `toCharArray(): char[]` ： 将字符串转为一个字符数组并且返回
    - `(static)getChars(srcBegin: int, srcEnd: int, dst: char[], dstBegin: int): void` ： 将字符串中从srcBegin到srcEnd-1的子字符串复制到字符数组从dstBegin开始的位置
    - `new String(dst: char[]): String` ： 从字符数组创建字符串，把字符数组转换为字符串
8.  **将字符或数值转换为字符串、格式化字符串**
    - `(static)valueOf(data: type): String` : data的类型type包括char, char\[\], int, double, long, boolean，将指定基本类型数据转为对应的字符串
    - `String.format(format,item1,item2,...)` ： 格式化字符串，用法和System.out.printf()相同

## 四、Arrays( java.util.Arrays )

- `sort(list): void` : 给数组排序，升序，对于对象，内部排序是用compareTo()比较的，也可以在后面再加一个比较器对象参数，之后就会用compare()方法比较来排序
- `sort(list, beginIndex, endIndex): void` ： 对数组的索引从beginIndex到endIndex-1的元素进行排序
- `parallelSort(list): void`  ： 多处理器排序
- `paeallelSort(list, beginIndex, endIndex): void` 
- `binarySearch(list, target): int` : 在数组list中进行二分查找target,返回target的下标，如果没查找到就返回-(insertionIndex+1)
- `equals(list1, list2): boolean` : 判断两个数组是否是严格相等
- `fill(list, element): void` : 使element填充数组
- `fill(list, beginIndex, endIndex, element): void` : 填充指定位置
- `toString(list): String` : 返回数组中所有元素
- `(static)asList(list: E[]): List<E>` : 数组转换成列表,该列表不支持add,remove

## 五、Date类( java.util.Date )

- `+Date()`
- `+Date(elapseTime: long)`
- `+toString(): String`
- `+getTime(): long`
- `+setTime(elapseTime: long): void`

## 六、Random类（ java.util.Random )

- `Random()`
- `Random(seed: long)`
- `nextInt(): int`
- `nextInt(n: int): int`
- `nextLong(): long`
- `nextDouble(): double`
- `nextFloat(): float`
- `nextBoolean(): boolean`

## 七、包装类( java.lang.* )

-  **Integer**
    
    -  `-value: int`
    -  `+(static)MAX_VALUE: int` ： 对应的基本数据的最大值
    -  `+(static)MIN_VALUE: int` ： 对应的基本数据的最小值
    -  `+Integer(value: int)` ： 从一个int类型的数字创建一个Integer对象
    -  `+Integer(s: String)` ： 从一个数值字符串创建一个Integer对象
    -  `+byteValue(): byte` ： 返回包装对象对应的byte值
    -  `+shortValue(): short`
    -  `+intValue(): int`
    -  `+longValue(): long`
    -  `+doubleValue(): double`
    -  `+floatvalue(): float`
    -  `+compareTo(o: Integer): int` ： 比较两个Integer对象大小
    -  `+toString(): String`
    -  `+(static)valueOf(s: String): Integer` ： 创建一个新对象，并将其初始化指定字符串表示的值
    -  `+(static)valueOf(s: String, radix: int): Integer`
    -  `+(static)parseInt(s: String): int` ： 将一个数值字符串转换为int值
    -  `+(static)parseInt(s: String, radix: int): int` ： 将数值字符串转换为正确的以10（十进制）或指定值为基数的数值
-  **Double**
    
    -  `-value: double`
    -  `+(static)MAX_VALUE: double`
    -  `+(static)MIN_VALUE: double`
    -  `+Double(value: double)`
    -  `+Double(s: String)`
    -  `+byteValue(): byte`
    -  `+shortValue(): short`
    -  `+intValue(): int`
    -  `+longValue(): long`
    -  `+doubleValue(): double`
    -  `+floatvalue(): float`
    -  `+compareTo(o: Double): int`
    -  `+toString(): String`
    -  `+(static)valueOf(s :String); Double`
    -  `+(static)valueOf(s: String, radix: int): Double`
    -  `+(static)parseDouble(s: String): double`
    -  `+(static)parseDouble(s: String, radix: int): douoble`
-  **Character**
    
-  **Boolean**
    
-  **Short**
    
-  **Long**
    
-  **Byte**
    
-  **Float**
    

## 八、BigInteger和BigDecimal类(java.lang.*)
- `BigInteger(str: String)` : 从数值字符串中从创建实例
- `BigDecimal(str: String)` : 从数值字符串中创建实例
- `BigInteger.ONE`：常量1
- `add(num)` ： 加法运算
- `subtract(num)` ： 减法运算
- `multiple(num)` ： 乘法运算
- `divide(num)` ： 除法运算
- `divide(BigDecimal num, int scale, int roundingMode)` : scale小数点后的位数，roundingMode舍入方式
- `remainder(num)` ： 取余运算
- `compareTo(num)` ： 比较大小

## 九、StringBuilder和StringBuffer类（ java.lang.* )

**StringBuilder**

1.  **构造方法**
    - `+StringBuilder()`
    - `+StringBuilder(capacity: int)`
    - `+StringBuilder(s: String)`
2.  **修改StringBuilder中的字符串**

- **添加**
    - `+append(data: char[]): StringBuilder`
    - `+append(data: char[], offset: int, len: int): StringBuilder`
    - `+append(v: aPrimitiveType): StringBuilder`
    - `+append(s: String): StringBuilder`
- **删除**
    - `+delete(startIndex: int, endIndex: int): StringBuilder`
    - `+deleteCharAt(index: int): StringBuilder`
- **插入**
    - `+insert(index: int, data: char[], offset: int, len: int): StringBuilder`
    - `+insert(offset: int, data char[]): StringBuilder`
    - `+insert(offset: int, b: aprimitiveType): StringBuilder`
    - `+insert(offset: int, s: String): StringBuilder`
- **其他**
    - `+replace(startIndex int, endIndex: int, s: String): StringBuilder`
    - `+reverse(): StringBuilder`
    - `+setCharAt(index: int, ch: char): void`

3.  **toString、capacity、length、setLength和charAt方法**
    - `+toString(): String`
    - `+capacity(): int`
    - `+charAt(index: int): char`
    - `+length(): int`
    - `setLength(newLength: int): void`
    - `+substring(startIndex: int): String`
    - `+substring(startIndex: int, endIndex: int): String`
    - `+trimToSize(): void`

## 十、泛型类：ArrayList数组线性表( java.util.ArrayList&lt;E&gt; )

- `+ArrayList()` ： 创建一个空的列表
- `+add(e: E): void` ： 添加一个新元素进列表的末尾
- `+add(index: int, e: E): void` ： 添加一个新元素到指定下标处
- `+clear(): void`：删除列表中的全部元素
- `+contains(o: Object): boolean` ： 如果列表中包含o则返回true
- `+get(index: int): E` ： 返回列表中指定下标位置的元素
- `+indexOf(o: Object): int` ： 返回列表中匹配成功的第一个元素的下标
- `+isEmpty(): boolean` ： 判断列表是否为空
- `+lastIndexOf(o: Object): int` ： 返回列表中匹配成功的最后一个元素的下标
- `+remove(o: Object): boolean` ： 去除列表中的第一个元素CDT，如果该元素已经被去除，则返回true
- `+size(): int` : 返回列表中元素的个数
- `+remove(index: int): E` ： 移除指定下标位置的元素，如果该元素被去除，则返回被去除的元素
- `+set(index: int, e: E): E` ： 设置指定下标位置的元素
- `toArray(list: Array):void` : 将数组线性表内的内容复制到数组Array中

## 十一、异常类( java.lang.* )

-  **java.lang.Throwable**
    -  `+getMessage(): String` ： 获取异常的描述性字符串
    -  `+toString(): String`
    -  `+printStackTrace(): void`
    -  `+getStackTrace()L: StackTraceElement[]`
-  **java.lang.Exception**
    -  **构造方法**
        -  `+Exception()`
        -  `+Exception(message: String)`
        -  `+Exception(message: String, cause: Exception)`

## 十二、File类( java.io.File)

- **构造方法**
    -`+File(pathName: String)` ： 为一个指定路径名创建一个File对象，路径名可能是一个目录或者文件
    `+File(parent: String, child: String)` ： 在目录parent下创建一个子路径的File对象，子路径可能是一个目录或者一个文件
    `+File(parent: File, child: String)` ： 在目录parent下创建一个子路径的File对象，parent是一个File对象，之前的构造方法中，parent是一个字符串
- **文件操作**
    - `+exists(): boolean` ： File对象代表的文件存在则返回true
    - `+canRead(): boolean` :  File对象代表的文件存在且可读则返回true
    - `+canWrite(): boolean` : File对象代表的文件存在且可写则返回true
    - `+isDirectory(): boolean` : File对象代表的文件是一个文件夹则返回true
    - `+isFile(): boolean` ： File对象代表的文件是一个文件则返回true
    - `+isAbsolute(): boolean` ： File对象是采用绝对路径创建的，返回true
    - `+isHidden(): boolean` ： 如果File对象代表的文件是隐藏的，返回true。隐藏的定一个和系统相关
    - `+getAbsolutePath(): String` ： 返回File对象代表的完整的文件或者目录的绝对路径名
    - `+getCanonicalPath(): String` ： 
    - `+getName(): String` ： 返回文件名
    - `+getPath(): String` ： 返回File对象代表的文件或者文件夹的路径加名称
    - `+getParent(): String` ： 返回File对象对应的父目录
    - `+lastModified(): long` ： 返回文件的最后修改时间
    - `+length(): long` ： 获取文件的大小，单位是byte，如果不存在或者是一个目录的话，返回0
    - `+listFile(): File[]` ？： 返回一个目录File对象下的文件
    - `+delete(): boolean` ： 删除File对象对应的文件或者目录，如果删除成功则返回true
    - `+renameTo(dest: File): boolean` ：将File对象对应的文件或者目录改名为dest，如果更改成功则返回true
    - `+mkdir(): boolean` ： 创建File对象代表的目录，如果目录成功创建，则返回true
    - `+mkdirs(): boolean` ： 和mkdir()相同，除了在父目录不存在的情况下，将一并创建目录

## 十三、PrintWriter类( java.io.PrintWriter)

- **构造方法**
    - `+PrintWriter(file: File)` ： 为指定的文件对象创建一个PrintWrite对象
    - `+PrintWriter(fileName: String)` ： 为指定的文件名字符串创建一个PrintWrite对象
- **输出**
    - `+print(data: type)` : data的类型type包括String, char, char\[\], int, long, float, double, boolean，向文件内写入内容
    - `+println(data: type)`
    - `+printf(data: type)`

## 十四、Scannner类( java.util.Scanner)

- **构造方法**
    - `+Scanenr(sourse: File)` ： 从一个File对象中创建一个Scanner对象
    - `+Scanner(sourse: String)` ： 从指定的字符串中产生扫描的值，并创建一个Scanner对象
- **普通方法**
    - `close(): void` ： 关闭Scanner
    - `+hasNext(): boolean` ： 如果Scanner还有更多的数据可以读取，则返回true
    - `+useDelimiter(pattern: String):Scanner` ： 设置Scanner的分隔符，并且返回Scanner
    - `+next(): String`
    - `+nextLine(): String`
    - `+nextInt(): int`
    - `+nextDouble(): double`
    - `+nextBoolean(): boolean`
    - `+nextShort(): short`
    - `+nextLong(): long`
    - `+nextByte(): byte`
    - `+nextFloat(): float`

## 十五、抽象类：Number( java.lang.Number )

**要点** ：Number类是数值包装类以及BigInteger和BigDecimal类的抽象父类

- **方法**
    - `+byteValue(): byte`
    - `+shortValue(): short`
    - `+intValue(): int`
    - `+longValue(): long`
    - `+floatValue(): float`
    - `+doubleValue(): double`

## 十六、常用接口

-  **泛型接口**：**Comparable\<E>**(java.)
    **要点**：Comparable接口定义了方法`public int compareTo(E o)`
-  **标记接口**： **Cloneable**
	- 方法体为空，没有常量也没有方法
	- `protected native Object clone() throws CloneNotSupporedException` : 定义在java,lang.Object的方法,native表示用其他方法写的,默认是浅复制(复制引用变量时只是复制引用),继承Cloneable接口的类必须重写该方法，并把可访问性提高到public
- **泛型接口**：**Comparator\<T>**(java.util.Comparator)
	- `public int compare(T element1, T element)`:比较器方法
-  **泛型接口**： **Collection\<E>** (ja    va.util.Collection)
    -  `+add(e: E): boolean` ： 添加一个新元素到集合当中
    -  `+addAll(c: Collection<? extends E>): boolean` ： 将集合 c中元素全部添加到该集合当中
    -  `+clear(): void` ： 删除该集合全部元素
    -  `+contains(o: Object): boolean` ： 判断该集合是否包含元素o,如果包含就返回true
    -  `+containsAll(c: Collection<?>): boolean` ： 判断该集合是否包含集合c中的全部元素，如果包含则返回true
    -  `+equals(o: Object): boolean` ： 判断集合是否相等
    -  `+isEmpty(): boolean` ： 判断集合是否为空
    -  `+remove(o: Object): boolean` ： 从该集合当中移除元素o
    -  `+removeAll(c: Collection<?>): boolean` : 从该集合当中移除所有的元素o
    -  `+retains(c: Collection<?>): boolean` ： 包留该集合和集合c共有的元素
    -  `+size(): int` ： 返回该集合当中元素的个数
    -  `+toArray(): Object[]` ： 为该集合当中的元素返回一个Object数组
    -  `+toArray(a: T[]): T[]` ： 返回一个T[]类型数组
-  **泛型接口**： **Iterable\<E>**
-  -  java.lang.Iterable&lt;E&gt;
    
    -  `+iterator(): Iterator<E>` ： 为该集合中的元素返回一个迭代器
    -  `+forEach(action: Consumer<? super E>): defualt void` ： 为迭代器中的每一个元素执行一个操作
-  -  java.util.Iterable&lt;E&gt;
    
    -  `+hasNext(): boolean` ： 如果迭代器有更多的元素可以遍历，则返回true
    -  `+next(): E` ： 从迭代器中返回下一个元素
    -  `+remove(): void` ： 删除使用next()方法获得的最后一个元素
-  **泛型接口**： **List\<E>** (java.util.List)
    -  `+add(index: int, element: E): void` ： 在指定下标处增加一个新元素
    -  `+addAll(index: int, c: Collection<? extends E>): boolean` ： 在指定下标处添加集合c中的所有元素
    -  `+get(index: int): E` ： 返回线性表该下标处的元素
    -  `+indexOf(element: Object): int` ： 返回匹配到的第一个元素的下标
    -  `+lastIndexOf(element: Object): int` ： 返回匹配的最后一个元素的下标
    -  `+listIterator(): ListIterator<E>` ： 返回针对该线性表中元素的线性迭代器
    -  `+listIterator(startIndex: int): ListIterator<E>` ： 返回针对从startIndex开始的元素的迭代器
    -  `+remove(index: int): E` ： 移除指定下标的元素，并返回该元素
    -  `+subList(fromIndex: int, toIndex: int): List<E>` ： 返回从fromIndex到toIndex-1的子线性表
    -  `+set(index: int, element: E): E` ： 设置指定下标处的元素，同时返回原来的元素
    -  `+sort(comparator: Comparator)` ： 用比较器排序,如果没有提供比较器就是按照自然排序
-  **泛型接口**: **ListIterator\<E>** (java.util.ListIterator)
    -  `+add(o: E): void` ： 添加一个指定的对象到线性表当中
    -  `+hasPrevious(): boolean` ： 当往回遍历时，如果改线性表迭代器当中还有更多的元素，则返回true
    -  `+nextIndex(): int` ： 返回下一个元素的下标
    -  `+previous(): E` ： 返回该线性表迭代器的前一个元素
    -  `+previousIndex(): int` ：返回前一个元素的下标
    -  `+set(o: E): void` ： 使用指定的元素替换previous或者next方法返回的最后一个元素
 - **泛型接口**：**Queue\<E>**(java.util.Queue)
 	- `+offer(element: E): boolean` :插入一个元素到队列当中
	 - `+poll(): E` ： 获取并移除队列的头元素，如果队列为空则返回null
 	- `+remove(): E` ： 获取并移除队列的头元素，如果队列为空则抛出异常
 	- `+peek(): E` ： 获取但不移除队列的头元素，如果队列为空则返回null
 	- `+element(): E` ： 获取但不移除队列的头元素，如果队列为空则抛出异常

## 十七、泛型类：LinkedList链表类（ java.util.LinkedList ）

- `+LinkedList()` ： 创建一个默认的空链表
- `+LinkedList(c: Collection<? extends E>)` ： 从已经存在的集合中创建一个链表
- `+addFirst(element: E): void` ： 添加元素到该线性表的头部
- `+addLast(element: E): void` ： 添加元素到该线性表的尾部
- `+getFirst(): E` ： 返回线性表的第一个元素
- `+getLast(): E` ： 返回该线性表的最后一个元素
- `+removeFirst(): E` ： 从该线性表返回并移除第一个元素
- `+removeLast(): E` ： 从该线性表返回并移除最后一个元素

## 十八、Collections类（ java.util.Collections ）

**静态**

- **List**
    - `+sort(list: List): void` ： 对指定的线性表进行排序
    - `+sort(list: List, c: Comparator): void` ： 使用比较器对指定的线性表进行排序
    - `+binarySearch(list: List, key: Object): int` ： 采用二分查找法查找排好序的线性表中的键值
    - `+binarySearch(list: List, key: Object, c: Comparator): int` ： 使用比较器，采用二分查找法查找排好序的线性表中的键值
    - `+reverse(list: List): void` ： 对指定的线性表进行逆向排序
    - `+reverseOrder(): Comparator` ： 返回一个逆向排序的比较器
    - `+shuffle(list: List): void` ： 随机打乱指定的线性表
    - `+shuffle(list: List, rmd: Random): void` ： 使用一个随机对象打乱指定的线性表
    - `+copy(des: List, src: List): void` ：复制源线性表到目标线性表中
    - `+nCopies(n: int, o: Object): List` ：返回一个由n个对象副本组成的线性表
    - `+fill(list: List, o: Object): void` ： 使用对象填充线性表
- **Collection**
    - `+max(c: Collection): Object` ：返回集合中的max对象
    - `+max(c: Collection, c: Comparator): Object` ： 使用比较器返回max对象
    - `+min(c: Collection): Object` ： 返回集合中的min对象
    - `+min(c: Collection, c: Comparator): Object` ： 使用比较器返回min对象
    - `+disjoint(c1: Collection, c2: Collection): boolean` ：如果c1和c2没有共同的元素，则返回true
    - `+frequency(c: Collection, o: Object): int` :返回集合中指定元素的出现次数

## 十九、泛型类：Vector向量类(java.util.Vector)

- **构造方法**
    - ·`+Vector()` ： 创建一个初始容量为10的默认的空向量
    - `+Vector(c: Collection<? extends E>)` ： 从一个已经存在的集合中创建一个向量
    - `+Vector(initialCapacity: int)` ： 创建一个给定初始容量的向量
    - `+initCapacity: int, capacityIncr: int)` ： 创建一个给定初始容量和增量的向量
- **常用方法**
    - `+addElement(o: E): void` ： 将一个元素添加到该向量末尾
    - `+capacity(): int` ： 返回该向量的当前容量
    - `+copyInto(anArray: Object[]): void` ： 将该向量中的元素复制到数组中
    - `+elementAt(index: int): E` ： 返回指定索引位置的对象
    - `+elements(): Enumeration<E>` ： 返回该向量的一个枚举
    - `+ensureCapacity(): void` ： 增加该向量的容量
    - `+firstElement(): E` ： 返回该向量中的第一个元素
    - `+insertElementAt(o: E, index: int): void` ： 插入o到该向量中的指定索引位置
    - `+lastElement(): E` ： 返回该向量的最后一个元素
    - `+removeAllElement(): void` ： 移除该向量中的所有元素
    - `+removeElement(o: Object): boolean` ： 移除该向量中第一个匹配到元素
    - `+removeElementAt(o: Object, index: int): void` ： 移除指定索引位置的元素
    - `+setElement(o: E, index: int): void` ： 在指定索引位置设置一个新的元素
    - `+setSize(newSize: int): void` ： 为该向量设置一个新的大小
    - `+trimToSize(): void` ：裁剪该向量的容量到其大小
 ## 二十、泛型类：Stack栈类( java.util.Stack)
  - `+Stack()` ： 创建一个空的栈
  - `+empty(): boolean` ：如果栈是空的则返回true
  - `+peek(): E` : 返回栈中的顶部元素
  - `+pop(): E` ： 返回并移除栈中的顶部元素
  - `+push(o: E): E` ： 添加一个新的元素到栈的顶部
  - `+search(o: Object): int` ：返回该栈中指定元素的位置 (顶部元素的位置为1)
 ## 二十一、泛型类：PriorityQueue优先队列类(java.util.PriorityQueue)
 - **构造方法**
 	- `+PriorityQueue()` ： 创建一个初始容量为11的默认优先队列
 	- `+PriorityQueue(initialCapacity: int)` ： 创建一个初始容量为指定值的优先队列
 	- `+PriorityQueue(c: Collection<? extends<E>)` ： 使用指定集合创建一个优先队列
 	- `+PriorityQueue(initialCapacity: int, comparator: Comparator<? super E>)` ： 创建一个指定容量和比较器的优先队列
 ## 二十二、规则集: Set
 - **Hashset散列类**
 	- `+HashSet()`
 	- `+HashSet(c: Collection<? extends E>)`
 	- `+HashSet(initialCapacity: int)`
 	- `+HashSet(initialCapacity: int, loadFactor: float)`
- **LinkedHashSet链式散列集**
	- `+LinkedHashSet()`
	- `+LinkedHashSet(c: Collection<? extends E>)`
	- `+LinkedHashSet(initialCapacity: int)`
	- `+LinkedHashSet(initialCapacity: int, loadFactor: float)`
- **interface - SortedSet\<E>**
	- `+first(): E`
	- `+last(): E`
	- `+headSet(toElement: E): SortedSet<E>`
	- `+tailSet(fromElement: E): SortedSet<E>`
- **interface - Navigable\<E>**
	- `+pollFirst(): E`
	- `+pollLast(): E`
	- `+lower(e: E): E`
	- `+higher(e: E): E`
	- `+floor(e: E): E`
	- `+ceiling(e: E): E`
- **TreeSet树形集**
	- `+TreeSet()`
	- `+TreeSet(c: Collection<? extends E>)`
	- `+TreeSet(comparator: Comparator<? super E>)` ： 没有比较器情况下，默认是自然排序，即使用compareTo()方法排序
	- `+TreeSet(s: SortedSet<E>)`
## 二十三、泛型接口：Map\<K,V>( java.util.Map)
- `+clear(): void`
- 