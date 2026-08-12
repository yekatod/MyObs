
---

Оператор `delegate` создает анонимный метод, который можно преобразовать в тип делегата.

Может преобразоваться в [[Action]] или [[Func]]

Пример
```C#
Func<int, int, int> sum = delegate (int a, int b) { return a + b; }; Console.WriteLine(sum(3, 4)); // output: 7
```

