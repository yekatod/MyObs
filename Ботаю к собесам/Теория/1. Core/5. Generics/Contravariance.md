
Контрвариантность (`in`) — можно использовать более общий тип там, где ожидается более конкретный.

```C#
Action<object> objectAction = obj => Console.WriteLine(obj); 
Action<string> stringAction = objectAction;
```