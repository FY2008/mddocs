C# 字符串



## # string.Contains 方法

这个函数有多个重载版本，前两个是一个参数的 string和char，两个参数的是后面加了一个 StringComparison 类型的

```c#
public enum StringComparison
    {
        //
        // 摘要:
        //     Compare strings using culture-sensitive sort rules and the current culture.
        CurrentCulture = 0,
        //
        // 摘要:
        //     Compare strings using culture-sensitive sort rules, the current culture, and
        //     ignoring the case of the strings being compared.
        CurrentCultureIgnoreCase = 1,
        //
        // 摘要:
        //     Compare strings using culture-sensitive sort rules and the invariant culture.
        InvariantCulture = 2,
        //
        // 摘要:
        //     Compare strings using culture-sensitive sort rules, the invariant culture, and
        //     ignoring the case of the strings being compared.
        InvariantCultureIgnoreCase = 3,
        //
        // 摘要:
        //     Compare strings using ordinal (binary) sort rules.
        Ordinal = 4,
        //
        // 摘要:
        //     Compare strings using ordinal (binary) sort rules and ignoring the case of the
        //     strings being compared.
        OrdinalIgnoreCase = 5
    }
```

