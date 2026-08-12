
---

Ковариантность (`out`) — можно использовать более конкретный тип там, где ожидается более общий.

Например

```C#
IEnumerable<string> strings = ...;
IEnumerable<object> objects = strings;
```