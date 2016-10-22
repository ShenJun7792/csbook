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








🔚