
---

Представляет собой типобезопасное и безопасное представление непрерывной области произвольной памяти

Является [[Struct]]

Структура ссылок, выделенная в стеке, а не в управляемой куче

Они не могут быть:
- в штучной упаковке
- `object` или `dynamic`
- Полями в ссылочных типах
- в `await` или [[ref]]

Также вызывают исключения:
- Equals
- GetHashCode

Может указывать как на управляемую память, собственную память или память в стеке

---
### Срезы

При помощи метода `Slice()` можно получить срез диапазона по указанному индексу, что помогает уменьшить производительность

```C#

    static void Run()
    {
        string contentLength = "Content-Length: 132";
        var length = GetContentLength(contentLength.ToCharArray());
        Console.WriteLine($"Content length: {length}");
    }

    private static int GetContentLength(ReadOnlySpan<char> span)
    {
        var slice = span.Slice(16);
        return int.Parse(slice);
    }
```