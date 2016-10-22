## switch 语句


&emsp;&emsp;`switch` 语句非常类似于 `if` 语句，因为它也是根据测试的值来有条件地执行代码。但是，`switch` 语句可以一次将测试变量与多个值进行比较，而不是仅测试一个条件。这种测试仅限于离散的值，而不是像 “大于X”这样的子句，所以它的用法有点不同，但它仍是一种强大的技术。

    switch 语句的基本结构如下：

```javascript
        switch(<testVar>)
        {
            case <comparisonVal1>:
            <code to execute if <testVar> == <comparisonVal1> >
            break;
            case <comparisonVal2>:
             <code to execute if <testVar> == <comparisonVal2> >
            break;
            ...
            case <comparisonValN>:
            <code to execute if <testVar> == <comparisonValN> >
            break;
            default:
            <code to execute if <testVar> != comparisonVals>
            break;
        }
```

&emsp;&emsp;`<testVar>` 中的值与每个 `<comparisonValX>` 值（在 `case` 语句中指定）进行比较，如果有一个匹配，就执行为该匹配提供的语句。如果没有匹配，但有 `default` 语句，就执行 `default` 部分中的代码。

&emsp;&emsp;执行完每个部分中的代码后，还需有另一个语句 `break`。在执行完一个 `case` 块后，再执行第二个 `case` 语句是非法的。

>&emsp;&emsp;在此，C#与C++是有区别的，在C++中，可以在运行完一个 `case` 语句后，运行另一个 `case` 语句。

&emsp;&emsp;在这里的 `break` 语句将中断 `switch` 语句的执行，而执行该结构后面的语句。

&emsp;&emsp;在C#代码中，还有其他方法可以防止程序流程从一个 `case` 语句转到下一个 `case` 语句。可以使用 `return` 语句，中断当前函数的运行，而不是仅中断 `switch` 结构的执行（详见第6章）。也可以使用 `goto` 语句（如前所述），因为 `case` 语句实际上是在C#代码中定义的标签。例如：

```javascript
        switch(<testVar>)
        {
            case <comparisonVal1>:
            <code to execute if <testVar> == <comparisonVal1> >
            goto case<comparisonVal2>;
            case <comparisonVal2>:
            <code to execute if <testVar> == <comparisonVal2> >
            break;
            ...
```

&emsp;&emsp;一个 `case` 语句处理完后，不能自由进入下一个 `case` 语句，但这个规则有一个例外。如果把多个 `case` 语句放在一起（堆叠它们），其后加一个代码块，实际上是一次检查多个条件。如果满足这些条件中的任何一个，就会执行代码，例如：

```javascript
        switch(<testVar>)
        {
            case <comparisonVal1>:
            case <comparisonVal2>:
                <code to execute if <testVar> == <comparisonVal1> or
                                    <testVar> == <comparisonVal2> >
                break;
            ...      
```


&emsp;&emsp;注意 ⚠️，这些条件也适用于 `default` 语句。`default` 语句不一定要放在比较操作列表的最后，还可以把它和 `case` 语句放在一起。用 `break`、`goto` 或 `return` 添加一个断点，可确保在任何情况下，该结构都有一个有效的执行路径。



&emsp;&emsp;每个 `<comparisonValX>` 都必须是一个常数值。一种方法是提供字面值，例如：

```javascript
        switch(myInteger)
        {
            case 1:
                <code to execute if myInteger == 1>
                break;
            case -1:
                <code to execute if myInteger == -1>
                break;
            default:
                <code to execute if myInteger != comparisons>
                break;
        }
```

&emsp;&emsp;另一种方式是使用常量。常量与其他变量一样，但有一个重要区别：它们包含的值是固定不变的。一旦给常量指定一个值，该常量在代码执行的过程中，其值一直不变。在这里使用常量是很方便的，因为它们通常更便于阅读，使得在进行比较时，看不到要比较的实际值。

&emsp;&emsp;声明常量需要指定变量类型和关键字 `const`，同时必须给它们赋值，例如：

```javascript
        const int intTwo = 2;
```

&emsp;&emsp;这行代码是有效的，但如果编写如下代码：

```javascript
        const int intTwo;
        intTwo = 2; ❌
```

&emsp;&emsp;就会产生一个编译错误。如果在最初的赋值之后，试图通过任何方式改变常量的值，也会产生编译错误。


    在下面的示例中，将使用 `switch` 语句，根据用户为测试字符串输入的值，将不同字符串写到控制台上。
    把以下代码添加到 `Program.cs` 中：
    
```javascript
        static void Main(string[] args)
        {
            const string myName = ""karli;
            const string sexyName = "angelina";
            const string sillyName = "ploppy";
            string name;
            Console.WriteLine("What is your name?");
            name = Console.ReadLine();
            switch(name.ToLower())
            {
                case myName:
                    Console.WriteLine("You have the same name as me!");
                    break;
                case sexyName:
                    Console.WriteLine("My, what a sexy name you have!");
                    break;
                case sillyName:
                    Console.WriteLine("That's a very silly name");
                    break;
            }
            Console.WriteLine("Hello {0}!", name);
            Console.ReadKey();
        }
```

>**示例的说明**

>&emsp;&emsp;这段代码建立了 3 个常量字符串，接受用户输入的一个字符串，再根据输入的字符串把文本写到控制台上。这里，字符串是用户输入的姓名。

&emsp;&emsp;在比较输入的姓名（在变量 `name` 中）和常量值时，首先要用

 `name.ToLower()` 把输入的姓名转换为小写。`name.ToLower()` 是一个标准命令，可用于处理所有的字符串变量，在不能确定用户输入的内容时，使用它是很方便的。使用这个技术，字符串 `Karli`、`kArLi`、`karli` 等就会与测试字符串 `karli` 匹配了。&emsp;&emsp;`switch` 语句尝试将输入的字符串与定义的常量值进行匹配，如果成功，就会用一条个性化的消息问候用户。如果不匹配，则只简单地问候用户。&emsp;&emsp;`switch` 语句对 `case` 语句的数量上没有限制，所以可以扩展这段代码，使其包含自己能想到的每个姓名，但这需要耗费一些时间。













🔚