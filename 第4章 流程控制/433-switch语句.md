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








🔚