
---

Механизм, который определяет отношения между типами при использовании [[Generics]]

То есть:

> **Variance отвечает на вопрос: если `string` является `object`, можем ли мы считать `Something<string>` разновидностью `Something<object>`?**

В C# есть три варианта:

|Вид|Что происходит|C#|
|---|---|---|
|**Invariant**|Никакого преобразования|`Generic<T>`|
|**Covariant**|Направление сохраняется|`Generic<out T>`|
|**Contravariant**|Направление переворачивается|`Generic<in T>`|

Для примера например с `string` и `object`

1. Инвариантность
```C#
List<object> objects = List<string> [...];
```
2. [[Covariance]]
```C#
IEnumerable<object> objects = IEnumerable<string> [...];
```
3. [[Contravariance]]
```C#
Action<string> stringHandler = Action<object>
```