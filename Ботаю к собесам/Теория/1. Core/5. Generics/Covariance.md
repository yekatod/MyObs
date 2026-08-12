(Out T)

---

Ковариантность (`out`) — можно использовать более конкретный тип там, где ожидается более общий. Юзается только в возвращаемых типах

Например

```C#
IEnumerable<string> strings = ...;
IEnumerable<object> objects = strings;
```

---

Примеры

 `IEnumerable<out T>`, `IReadOnlyList<out T>`, `Func<out TResult>`