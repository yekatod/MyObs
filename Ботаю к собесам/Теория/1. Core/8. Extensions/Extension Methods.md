
Методы, которые позволяют расширять функционал существующих типов без создания нового производного типа или изменения исходного кода

c `C# 14` можно объявлять блоки расширения при помощи специального синтаксиса

```C#

public static class MyExtensions
{
    extension(string str)
    {
        public int WordCount() =>
            str.Split([' ', '.', '?'], StringSplitOptions.RemoveEmptyEntries).Length;
    }
}
```

Также можно юзать [[Generics]]

```C#
public static class MyGenericExtensions
{
    extension<T>(IEnumerable<T> source)
        where T : IEquatable<T>
    {
        public IEnumerable<T> ValuesEqualTo(T threshold)
            => source.Where(x => x.Equals(threshold));
    }
}
```

Ранее экстеншны писались через следующую сигнатуру

```C#
namespace CustomExtensionMethods;

public static class MyExtensions
{
    public static int WordCount(this string str) =>
        str.Split([' ', '.', '?'], StringSplitOptions.RemoveEmptyEntries).Length;
}
```

При этом если задублировать сигнатуру метода расширения согласно уже существующему методу расширяемого класса, компилятор всегда в первую очередь вызовет метод класса (исходный), т.к. у него выше приоритет