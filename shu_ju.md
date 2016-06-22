# 数据


数据的作用

数据用来描述程序中所有的事物。比如一个英雄，一只老虎。

基本数据类型

描述一个英雄对我们来说还太复杂，我们可以描述下他的基本信息，“他叫李康，今年18岁，身高1.81，性别N，是不是长的很帅呢？是的。”。其中哪些是数据呢？

C#是强类型语言。每个数据都要有明确的数据类型。
C#中有5种基本数据类型：
数据	数据类型	数据的表示	C#基本数据类型
李康	字符串	“李康”	string
N	字符	‘N’	char
18	整数	18	int
1.81	小数，浮点数	1.81	double
是	布尔	true false	bool
数据的基本运算

数字间可以进行算数运算。

Console.WriteLine(1 + 2); // 输出：3
Console.WriteLine(2 * 3); // 输出：6
Console.WriteLine(2 - 3.2); // 输出：-1.2
Console.WriteLine(10.0 / 2); // 输出：5
两个字符串之间可以用+连接。

Console.WriteLine("Li" + "Kang"); // 输出：LiKang
Console.WriteLine("1" + "2"); // 输出：12
其他数据类型与字符串可以用+连接

Console.WriteLine("LiKang have " + 3 + " Books"); // 输出：LiKang have 3 Books;
数据的本质

计算机中所有的数据都是由0、1组成的二进制表示的。一张图片、一份文件、一部电影，以及刚刚提到的整数、浮点、字符串、布尔等，在计算机中都是用二进制表示。