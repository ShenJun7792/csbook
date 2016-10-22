## while 循环

&emsp;&emsp;`while 循环` 非常类似于 `do 循环`，但有一个明显的区别：`while 循环` 中的布尔测试是在循环开始时进行，而不是最后。如果测试结果为 `false`，就不会执行循环。程序会直接跳转到循环之后的代码。

&emsp;&emsp;按下述方式指定 `while 循环`：

```javascript
        while (<Test>)
        {
            <code to be looped>
        }
```

&emsp;&emsp;它使用的方式几乎与 `do 循环` 完全相同，例如：

```javascript
        int i = 1;
        while (i <= 10)
        {
            Console.WriteLine("{0}", i++);
        }
```

&emsp;&emsp;这段代码的执行结果与前面的 `do 循环` 相同，它在一列中输出从 1～10 的数字。下面使用 `while 循环` 修改上一个示例。


>修改代码，如下所示：

>```javascript
        static void Main(string[] args)
        {
            double balance, interestRate, targetBalance;
            Console.WriteLine("What is your current balance?");
            balance = Convert.ToDouble(Console.ReadLine());
            Console.WriteLine("What is your current annual interest rate (in %)?");
            interestRate = 1 + Convert.ToDouble(Console.ReadLine()) / 100.0;
            Console.WriteLine("What balance would you like to have?");
            targetBalance = Convert.ToDouble(Console.ReadLine());
            int totalYears = 0;
            while(balance < targetBalance)
            {
                balance *= interestRate;
                ++totalYears;
            }
            Console.WriteLine("In {0} year{1} you'll have a balance of {2}.",
                                totalYears, totalYears == 1 ? "" : "s",
                                balance);
            if(totalYears == 0)
                Console.WriteLine("To honest, you really didn't need to use this calculator.");
            Console.ReadKey();
        }
```









🔚