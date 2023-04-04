# 变量

## 1.为什么需要变量

>1、一个程序就是一个世界
>
>2、变量是程序的基本组成单位

## 2.变量的介绍

>概念：**变量相当于内存中一个数据存储空间**的表示，你可以把变量看做是一个房间的门牌号，通过**门牌号**我们可以找到房间，而通过变量名可以访问到变量(值)。

### 2.1 变量使用的基本步骤

| 声明变量 | int a;       |
| -------- | ------------ |
| 赋值     | 把 60 赋给 a |

### 2.2  变量使用注意事项 

| ID   | 说明                                                         |
| ---- | ------------------------------------------------------------ |
| 1    | 变量表示内存中的一个存储区域，不同变量，类型不同，占用空间不同 |
| 2    | 该区域有自己的名称                                           |
| 3    | 变量必须声明，后使用，即有顺序                               |
| 4    | 该区域的数据/值，可以在同一范围内不断变化                    |
| 5    | 变量在同一个作用域内不能重名                                 |
| 6    | 变量=变量名+值+数据类型                                      |

### 2.3 数据类型

![image-20230330110555580](https://typora-1309726340.cos.ap-shanghai.myqcloud.com/typora/image-20230330110555580.png)

### 2.4 API文档

![image-20230330111620169](https://typora-1309726340.cos.ap-shanghai.myqcloud.com/typora/image-20230330111620169.png)

### 2.5 字符类型(char)

#### 2.5.1 基本介绍

> 字符类型可以表示单个字符,字符类型是 char，char 是两个字节(可以存放汉字)，多个字符我们用字符串 String

#### 2.5.2 案例演示

```java
#代码 
char c1 = 'a'; 
char c2 = '\t'; 
char c3 = '韩'; 
char c4 = 97;
```

#### 2.5.3 字符类型使用细节

![image-20230330112131873](https://typora-1309726340.cos.ap-shanghai.myqcloud.com/typora/image-20230330112131873.png)

```java
//在 java 中，char 的本质是一个整数，在默认输出时，是 unicode 码对应的字符 
//要输出对应的数字，可以(int)字符 
char c1 = 97; 
System.out.println(c1); //a

char c2 = 'a'; //输出'a' 对应的数字 
System.out.println((int)c2); 

char c3 = '韩';
System.out.println((int)c3);//38889 

char c4 = 38889; 
System.out.println(c4);//韩

//char 类型是可以进行运算的，相当于一个整数，因为它都对应有 Unicode 码
System.out.println('a' + 10);//107
```

![image-20230330112626374](https://typora-1309726340.cos.ap-shanghai.myqcloud.com/typora/image-20230330112626374.png)

### 2.6 布尔类型

![image-20230330112810024](https://typora-1309726340.cos.ap-shanghai.myqcloud.com/typora/image-20230330112810024.png)

### 2.7 基本数据类型转换

#### 2.7.1 自动类型转换

![image-20230330113025837](https://typora-1309726340.cos.ap-shanghai.myqcloud.com/typora/image-20230330113025837.png)

#### 2.7.2 自动类型转换注意和细节

![image-20230330113158322](https://typora-1309726340.cos.ap-shanghai.myqcloud.com/typora/image-20230330113158322.png)

```java
//细节 1： 有多种类型的数据混合运算时， 
//系统首先自动将所有数据转换成容量最大的那种数据类型，然后再进行计算 
int n1 = 10; //ok 
float d1 = n1 + 1.1;//错误 n1 + 1.1 => 结果类型是 double
double d1 = n1 + 1.1;//对 n1 + 1.1 => 结果类型是 double 
float d1 = n1 + 1.1F;//对 n1 + 1.1 => 结果类型是 float


//细节 2: 当我们把精度(容量)大 的数据类型赋值给精度(容量)小 的数据类型时， 
//就会报错，反之就会进行自动类型转换。 
int n2 = 1.1;//错误 double -> int


//细节 3: (byte, short) 和 char 之间不会相互自动转换 
//当把具体数赋给 byte 时，(1)先判断该数是否在 byte 范围内，如果是，就可以 
byte b1 = 10; //对 , -128-127 
int n2 = 1; //n2 是 int 
byte b2 = n2; //错误，原因：如果是变量赋值，判断类型
char c1 = b1; //错误， 原因 byte 不能自动转成 char


//细节 4: byte，short，char 他们三者可以计算，在计算时首先转换为 int 类型 
byte b2 = 1; 
byte b3 = 2; 
short s1 = 1; 
short s2 = b2 + s1;//错, b2 + s1 => int 
int s2 = b2 + s1;//对, b2 + s1 => int 
byte b4 = b2 + b3; //错误: b2 + b3 => int 

//boolean 不参与转换 
boolean pass = true; 
int num100 = pass;// boolean 不参与类型的自动转换
```

#### 2.7.3 强制类型转换

>介绍：自动类型转换的逆过程，**将容量大的数据类型转换为容量小的数据类型**。使用时要加上强制转换符 ( )，但可能造成 **精度降低或溢出**,格外要注意。 

```java
int i = (int)1.9;
sout(i);//1

int j = 100;
byte b1 = (byte)j;
sout(b1);//100
```

#### 2.7.4 强制类型转换细节

![image-20230330114538053](https://typora-1309726340.cos.ap-shanghai.myqcloud.com/typora/image-20230330114538053.png)

```java
//演示强制类型转换 
//强转符号只针对于最近的操作数有效，往往会使用小括号提升优先级 
int x = (int)10*3.5+6*1.5;//编译错误： double -> int 
int x = (int)(10*3.5+6*1.5);// (int)44.0 -> 44 
System.out.println(x);//44


char c1 = 100; //ok 
int m = 100; //ok 
char c2 = m; //错误 
char c3 = (char)m; //ok 
System.out.println(c3);//100 对应的字符, d 字符
```

### 2.8 基本数据类型和String的转换

#### 2.8.1 介绍

![image-20230330114909162](https://typora-1309726340.cos.ap-shanghai.myqcloud.com/typora/image-20230330114909162.png)

```java
//基本数据类型->String 
int n1 = 100; 
float f1 = 1.1F; 
double d1 = 4.5; 
boolean b1 = true; 
String s1 = n1 + ""; 
String s2 = f1 + ""; 
String s3 = d1 + ""; 
String s4 = b1 + ""; 
System.out.println(s1 + " " + s2 + " " + s3 + " " + s4);


//String->对应的基本数据类型 
String s5 = "123"; 
//会在 OOP 讲对象和方法的时候回详细 
//解读 使用 基本数据类型对应的包装类，的相应方法，得到基本数据类型 
int num1 = Integer.parseInt(s5); //123 
double num2 = Double.parseDouble(s5); //123.0 
float num3 = Float.parseFloat(s5); //123.0 
long num4 = Long.parseLong(s5); //123 
byte num5 = Byte.parseByte(s5); //123 
boolean b = Boolean.parseBoolean("true"); //123 
short num6 = Short.parseShort(s5);//true

//怎么把字符串转成字符 char -> 含义是指 把字符串的第一个字符得到 
//解读 s5.charAt(0) 得到 s5 字符串的第一个字符 '1' 
System.out.println(s5.charAt(0));
```

#### 2.8.2 注意事项

>1) 在将 String 类型转成 基本数据类型时，**要确保String类型可以转换成有效数据**，比如 我们可以把 "123" , 转成一个整数，但是不能把 "hello" 转成一个整数
>2) 如果格式不正确，就会**抛出异常，程序就会终止**

```java
String str = "hello"; //转成 int 
int n1 = Integer.parseInt(str); 
System.out.println(n1);
```



## 3.运算符

### 3.1 运算符号介绍

| ID   | 名称                      |
| ---- | ------------------------- |
| 1    | 算术运算符                |
| 2    | 赋值运算符                |
| 3    | 关系运算符 [比较运算符]   |
| 4    | 逻辑运算符                |
| 5    | 位运算符 [需要二进制基础] |
| 6    | 三元运算符                |



### 3.2 算数运算符

>算术运算符是对数值类型的变量进行运算的，在 Java 程序中使用的非常多。 

![image-20230330120517589](https://typora-1309726340.cos.ap-shanghai.myqcloud.com/typora/image-20230330120517589.png)

```java
System.out.println(10 / 4); //从数学来看是 2.5, java 中 2 
System.out.println(10.0 / 4); //java 是 2.5

double d = 10 / 4;//java 中 10 / 4 = 2, 2=>2.0 
System.out.println(d);// 是 2.0

System.out.println(10 % 3); //1 
System.out.println(-10 % 3); // -1 
System.out.println(10 % -3); //1 
System.out.println(-10 % -3);//-1

//++的使用 
int i = 10; 
i++;//自增 等价于 i = i + 1; => i = 11
++i;//自增 等价于 i = i + 1; => i = 12 
System.out.println("i=" + i);//12

/*作为表达式使用 前++：++i 先自增后赋值 后++：i++先赋值后自增 */ 
int j = 8; 
//int k = ++j; //等价 j=j+1;k=j; 
int k = j++; // 等价 k =j;j=j+1; 
System.out.println("k=" + k + "j=" + j);//8 9


```

### 3.3 关系运算符(比较运算符)

>介绍：关系运算符的结果都是 boolean 型，也就是要么是 true，要么是 false
>
>关系表达式 经常用在 if 结构的条件中或循环结构的条件中 

![image-20230330140221091](https://typora-1309726340.cos.ap-shanghai.myqcloud.com/typora/image-20230330140221091.png)

### 3.4 逻辑运算符

>用于连接多个条件（多个关系表达式），最终的结果也是一个 boolean 值

![image-20230330140325844](https://typora-1309726340.cos.ap-shanghai.myqcloud.com/typora/image-20230330140325844.png)

>1) a&b : & 叫逻辑与：规则：当 a 和 b 同时为 true ,则结果为 true, 否则为 false 
>2) a&&b : && 叫短路与：规则：当 a 和 b 同时为 true ,则结果为 true,否则为 false 
>3) a|b : | 叫逻辑或，规则：当 a 和 b ，有一个为 true ,则结果为 true,否则为 false 
>4) a||b : || 叫短路或，规则：当 a 和 b ，有一个为 true ,则结果为 true,否则为 false 
>5) !a : 叫取反，或者非运算。当 a 为 true, 则结果为 false, 当 a 为 false 是，结果为 true 
>6) a^b: 叫逻辑异或，当 a 和 b 不同时，则结果为 true, 否则为 false 

### 3.5 三元运算符

>条件表达式 ? 表达式 1: 表达式 2; 
>
>运算规则： 
>
>1. 如果条件表达式为 true，运算后的结果是表达式 1； 
>2. 如果条件表达式为 false，运算后的结果是表达式 2； 

```java
int a = 10; 
int b = 99; 
// 解读 
// 1. a > b 为 false 
// 2. 返回 b--, 先返回 b 的值,然后在 b-1 
// 3. 返回的结果是 99 
int result = a > b ? a++ : b--; 
System.out.println("result=" + result); 
System.out.println("a=" + a); 
System.out.println("b=" + b);
```

### 3.6 运算符优先级

>1) 运算符有不同的优先级，所谓优先级就是表达式运算中的运算顺序。如右表，上一行运算符总优先于下一行。 
>2) 只有单目运算符、赋值运算符是从右向左运算的。 

<img src="https://typora-1309726340.cos.ap-shanghai.myqcloud.com/typora/image-20230330141522981.png" alt="image-20230330141522981" style="zoom: 50%;" />

### 3.7 进制

>对于整数，有四种表示方式： 
>
>二进制：0,1 ，满 2 进 1.以 0b 或 0B 开头。 
>
>十进制：0-9 ，满 10 进 1。 
>
>八进制：0-7 ，满 8 进 1. 以数字 0 开头表示。 
>
>十六进制：0-9 及 A(10)-F(15)，满 16 进 1. 以 **0x** **或** **0X** 开头表示。此处的 A-F 不区分大小写。 

```java
//n1 二进制 
int n1 = 0b1010;

//n2 10 进制 
int n2 = 1010;

//n3 8 进制
int n3 = 01010;

//n4 16 进制 
int n4 = 0X10101;
```

![image-20230330143015597](https://typora-1309726340.cos.ap-shanghai.myqcloud.com/typora/image-20230330143015597.png)

#### 3.71 进制的转换

##### 3.7.1.1 二进制转换成十进制示例 

![image-20230330143502125](https://typora-1309726340.cos.ap-shanghai.myqcloud.com/typora/image-20230330143502125.png)



##### 3.7.1.2 八进制转换成十进制示例 

![image-20230330143545460](https://typora-1309726340.cos.ap-shanghai.myqcloud.com/typora/image-20230330143545460.png)



##### 3.7.1.3 十六进制转换成十进制示例 

>规则：从最低位(右边)开始，将每个位上的数提取出来，乘以 16 的(位数-1)次方，然后求和。 
>
>案例：请将 0x23A 转成十进制的数 
>
>0x23A = 10 * 16^0 + 3 * 16 ^ 1 + 2 * 16^2 = 10 + 48 + 512 = 570 



##### 3.7.1.3 十进制转换成二进制 

>规则：将该数不断除以 2，直到商为 0 为止，然后将每步得到的余数倒过来，就是对应的二进制。 
>
>案例：请将 34 转成二进制 = 0B00100010
>
>![image-20230330143907229](https://typora-1309726340.cos.ap-shanghai.myqcloud.com/typora/image-20230330143907229.png)



##### 3.7.1.4 十进制转换成八进制 

>规则：将该数不断除以 8，直到商为 0 为止，然后将每步得到的余数倒过来，就是对应的八进制。 
>
>案例：请将 131 转成八进制 => 0203



##### 3.7.1.5 十进制转换成十六进制 

>规则：将该数不断除以 16，直到商为 0 为止，然后将每步得到的余数倒过来，就是对应的十六进制。 
>
>案例：请将 237 转成十六进制 => 0xED 



##### 3.7.1.6 二进制转换成八进制 

>规则：从低位开始,将二进制数每三位一组，转成对应的八进制数即可。 
>
>案例：请将 ob11010101 转成八进制 
>
>ob11(3)010(2)101(5) => 0325 



##### 3.7.1.7 二进制转换成十六进制 

>规则：从低位开始，将二进制数每四位一组，转成对应的十六进制数即可。 
>
>案例：请将 ob11010101 转成十六进制 
>
>ob1101(D)0101(5) = 0xD5 



##### 3.7.1.8 八进制转换成二进制 

>规则：将八进制数每 1 位，转成对应的一个 3 位的二进制数即可。 
>
>案例：请将 0237 转成二进制 
>
>02(010)3(011)7(111) = 0b10011111 



##### 3.7.1.9 十六进制转换成二进制

>规则：将十六进制数每 1 位，转成对应的 4 位的一个二进制数即可。 
>
>案例：请将 0x23B 转成二进制 
>
>0x2(0010)3(0011)B(1011) = 0b001000111011



#### 3.7.2 二进制在运算中的说明

![image-20230330144833613](https://typora-1309726340.cos.ap-shanghai.myqcloud.com/typora/image-20230330144833613.png)



#### 3.7.3 **原码、反码、补码**

![image-20230330144947818](https://typora-1309726340.cos.ap-shanghai.myqcloud.com/typora/image-20230330144947818.png)

# 程序控制结构



## 1.程序流程控制介绍

>在程序中，程序运行的流程控制决定程序是如何执行的，是我们必须掌握的，主要有三大流程控制语句。 
>
>1) 顺序控制 
>2) 分支控制 
>3) 循环控制 



## 2.顺序控制

![image-20230330151036459](https://typora-1309726340.cos.ap-shanghai.myqcloud.com/typora/image-20230330151036459.png)



## 3.分支控制if-else 

```java
Scanner myScanner = new Scanner(System.in); 
System.out.println("请输入年龄"); //把年龄保存到一个变量 int age
int age = myScanner.nextInt(); //使用 if 判断，输出对应信息 
if(age > 18) { 
  System.out.println("你年龄大于 18,要对自己的行为负责,送入监狱"); 
}
System.out.println("程序继续...");
```



## 4.switch 分支结构 

```java
/*案例：Switch01.java 
请编写一个程序，该程序可以接收一个字符，比如:a,b,c,d,e,f,g 
a 表示星期一，b 表示星期二 … 
根据用户的输入显示相应的信息
要求使用 switch 语句完成 

思路分析 
1. 接收一个字符 , 创建 Scanner 对象 
2. 使用 switch 来完成匹配,并输出对应信息 代码

*/

Scanner myScanner = new Scanner(System.in); 
System.out.println("请输入一个字符(a-g)"); 
char c1 = myScanner.next().charAt(0);

switch(c1) { 
  case 'a' :
    System.out.println("今天星期一,猴子穿新衣"); 
    break; 
  case 'b' : 
    System.out.println("今天星期二,猴子当小二");
    break; 
  case 'c' : 
    System.out.println("今天星期三,猴子爬雪山.."); 
    break; //..... 
  default: 
    System.out.println("你输入的字符不正确，没有匹配的"); 
}

System.out.println("退出了 switch ,继续执行程序");
```



## 5.for循环

> 基本介绍:听其名而知其意,就是让你的代码可以循环的执行
>
> for(循环变量初始化；循环条件；循环变量迭代){
>
> ​	循环操作（可以多条语句）
>
> }



## 6.while循环

```java
int i = 1; //循环变量初始化 
while( i <= 10 ) {//循环条件 
  System.out.println("你好，韩顺平教育" + i);//执行语句 
  i++;//循环变量迭代 
}
System.out.println("退出 while ，继续.." + i); // 11
```



### 6.1 do while 语句

>**循环变量初始化****;** 
>
>**do{** 
>
>**循环体****(****语句****);** 
>
>**循环变量迭代****;** 
>
>**}while(****循环条件****);** 

```java
int i = 1; 
int count = 0; //统计满足条件的个数 
do {
  if( i % 5 == 0 && i % 3 != 0 ) {
    System.out.println("i=" + i); count++; 
  }
  i++; 
}
while(i <= 200); 
System.out.println("count=" + count);
```

# 数组、排序和查找

## 1.为什么需要数组

>一个养鸡场有6只鸡，它们的体重分别是 3kg,5kg,1kg,3.4kg,2kg,50kg 。请问这六只鸡的总体重是多少?平均体重是多少? 请你编一个程序。 Array01.java 
>
>思路： 
>
>定义 6 个变量 , 加起来 总体重， 求出平均体重.引出 -> 数组
>
>
>
>数组可以存放多个**同一类型**的数据。数组也是一种数据类型，是**引用类型**。 
>
>即：数(数据)组(一组)就是一组数据

```java
double[] hens = {3, 5, 1, 3.4, 2, 50, 7.8, 88.8,1.1,5.6,100};
double totalWeight = 0;
//遍历数组得到数组的所有元素的和， 使用 for
for(int i = 0; i < hens.length; i++){
  totalWeight += hens[i];
}
System.out.println("总体重=" + totalWeight + "平均体重=" + (totalWeight / hens.length));
```



## 2.数组的使用

```java
//1. 创建一个 double 数组，大小 5
//(1) 第一种动态分配方式 
double scores[] = new double[5];

//(2) 第 2 种动态分配方式,先声明数组，再new 分配空间 
double scores[] ; //声明数组，这时 scores是null 
scores = new double[5]; // 分配内存空间，可以存放数据


//2. 循环输入 
// scores.length 表示数组的大小/长度 
Scanner myScanner = new Scanner(System.in); 
for( int i = 0; i < scores.length; i++) { 
  System.out.println("请输入第"+ (i+1) +"个元素的值"); 
  scores[i] = myScanner.nextDouble(); 
}

//输出，遍历数组 
System.out.println("==数组的元素/值的情况如下:==="); 
for( int i = 0; i < scores.length; i++) { 
  System.out.println("第"+ (i+1) +"个元素的值=" + scores[i]);
}
```



## 3.数组拷贝

```java
//将 int[] arr1 = {10,20,30}; 拷贝到arr2数组
//要求数据空间是独立的
int[] arr1 = {10, 20, 30};
int[] arr2 = new int[arr1.length];

//遍历arr1
for(int i = 0;i < arr1.length; i++){
		arr2.[i] = arr1.[i];
}

```



## 4.数组反转

```java
//要求：把数组的元素内容反转

int[] arr = {11, 22, 33, 44, 55, 66};
int temp = 0;
int len = arr.length;

for(int i = 0;i < len/2; i++){
  temp = arr[len - 1 - i];
  arr[len - 1 -i] = arr[i];
  arr[i] = temp;
}


for(int i = arr.length - 1, j = 0; i >= 0; i--, j++) { 
  arr2[j] = arr[i]；
}

```



# JavaWeb





















## 8.服务器渲染Jsp

### jsp内置对象

>

