##goto 语句

&emsp;&emsp;C#允许给代码加上标签，这样就可以使用 `goto` 语句直接跳转到这些代码上。该语句优缺点并存。主要优点是：这是控制什么时候执行哪些代码的一种简单方式。主要缺点是：过多地使用这个技巧将使代码晦涩难懂。

&emsp;&emsp;`goto` 语句的用法如下：

```javascript
        goto <labelName>;
```

&emsp;&emsp;标签用下述方式定义：

```javascript
        <labelName>:
```

>    例如，下面的代码：

>```javascript
        int myInteger = 5;
        goto myLabel;
        myInteger += 10;

>    myLabel:
        Console.WriteLine("myInteger = {0}", myInteger);
```

>    其执行过程如下：

> * `myInteger` 声明为 `int` 类型，并赋予值 5。
> * `goto` 语句中断正常的执行过程，把控制权转到标有 `myLabel:` 的代码行上。
> * `myInteger` 的值写入控制台。 


> 下面突出显示的第 3 行代码从未执行。

>```javascript
        int myInteger = 5;
        goto myLabel;
        myInteger += 10;
    myLabel:
        Console.WriteLine("myInteger = {0}", myInteger);
```

>&emsp;&emsp;实际上，如果在应用程序中加入这段代码，会发现编译代码时，`Error List` 窗口会显示一个警告 ⚠️，即 `Unreachable code detected` 和一个行号。在无法执行的代码行中，`myInteger`下面还有绿色的波浪线。


&emsp;&emsp;`goto` 语句有它们的作用，但也可能使代码陷入混乱。尽量不要使用它（使用本章后面介绍的技巧，就可以避免使用它）。

    例如，因使用 `goto` 语句而非常难懂的代码，如下所示：

```javascript
    start:
        int myInteger = 5;
        goto addVal;
    writeResult:
        Console.WriteLine("myInteger = {0}", myInteger);
        goto start;
    addVal:
        myInteger += 10;
        goto writeResult;
```

&emsp;&emsp;这是有效的代码，但非常难懂，读者可以自己试试，看看会发生什么情况。在此之前，应尝试通过阅读这些代码来理解它们完成什么任务。后面再分析这个语句，因为本章的其他一些结构将使用该语句。







🔚