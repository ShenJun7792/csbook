##System.Object

&emsp;&emsp;因为所有的类都继承于 System.Object，所以这些类都可以访问该类中受保护的成员和公共成员。下面看看可供使用的成员有哪些。System.Object 包含的方法 `如表 9-2 所示`。

|方法|返回类型|虚拟|静态|说明|
|-|-|-|-|-|
|Object()|N/A|无|无|System.Object 类型的构造函数，由派生类型的构造函数自动调用|
|～Object()（也称为Finalize()，参见下一节）|N/A|无|无|System.Object类型的析构函数，由派生类型的析构函数自动调用，不能手动调用|

**`表 9-2 System.Object 类的方法`**































🔚