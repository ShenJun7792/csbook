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

```javascript
        int myInteger = 5;
        goto myLabel;
        myInteger += 10;
    myLabel:
        Console.WriteLine("myInteger = {0}", myInteger);
```














🔚