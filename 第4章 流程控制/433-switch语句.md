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


























🔚