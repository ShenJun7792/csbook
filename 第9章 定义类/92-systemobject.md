##System.Object

&emsp;&emsp;因为所有的类都继承于 System.Object，所以这些类都可以访问该类中受保护的成员和公共成员。下面看看可供使用的成员有哪些。System.Object 包含的方法 `如表 9-2 所示`。

|方法|返回类型|虚拟|静态|说明|
|-|-|-|-|-|
|Object()|N/A|无|无|System.Object 类型的构造函数，由派生类型的构造函数自动调用|
|～Object()（也称为Finalize()，参见下一节）|N/A|无|无|System.Object类型的析构函数，由派生类型的析构函数自动调用，不能手动调用|
|Equals(object)|bool|有|无|把调用该方法的对象与另一个对象相比，如果它们相等，就返回 `true`。默认的实现代码会查看其对象参数是否引用了同一个对象（因为对象是引用类型）。如果想以不同方式来比较对象，则可以重写该方法，例如，比较两个对象的状态。|
|Equlas(object,object)|bool|无|有|这个方法比较传送给它的两个对象，看看它们是否相等。检查时使用了 `Equals(object)` 方法。注意 ⚠️，如果两个对象都是空引用，这个方法就返回 `true`。|
|ReferenceEquals|bool|无|有|这个方法比较传送给它的两个对象，看看它们是不是同一个实例的引用。|
|ToString()|String|有|无|返回一个对应于对象实例的字符串。默认情况下，这是一个类类型的限定名称，但可以重写它，给类类型提供合适的实现方式。|
|MemberwiseClone()|object|无|无|通过创建一个新对象实例并复制成员，以复制该对象。成员复制不会得到这些成员的新实例。新对象的任何引用类型成员都将引用与源类相同的对象，这个方法是受保护的，所以只能在类或派生的类中使用。|
|GetType()|System.Type|无|无|以 System.Type 对象的形式返回对象的类型。|
|GetHashCode()|int|有|无|在需要此参数的地方，用作对象的散列函数，它返回一个以压缩形式表示的对象状态的值。|

**`表 9-2 System.Object 类的方法`**


&emsp;&emsp;这些方法是.NET Framework 中对象类型必须支持的基本用法，但我们可能从不使用其中某些类型（或者只在特殊情况下使用，如 `GetHashCode()`）

&emsp;&emsp;在利用多态性时，`GetType()` 是一个有用的方法，允许根据对象的类型来执行不同的操作，而不是像通常那样，对所有对象都执行相同的操作。例如，如果函数接受一个 `object` 类型的参数（表示可以给该函数传递任何信息），就可以在遇到某些对象时执行额外的任务。结合使用 `GetType()` 和 `typeof` （这是一个 C#运算符，可以把类名转换为 System.Type 对象），就可以进行比较，如下所示：

```javascript
        if (myObj.GetType() == typeof(MyComplexClass))
        {
            // myObj is an instance of the class MyComplexClass.
        }
```

&emsp;&emsp;返回的 System.Type 对象可以完成更多工作，这里不讨论它们。重写 `ToString()` 方法也是非常有效的，在对象的内容可以用一个人们能理解的字符串表示时，尤其如此。后续章节将反复讨论这些 System.Object 方法，现在就讨论到这里，后面在需要时再详细讨论。






🔚