
явный сигнал о завершении операции

```C#
IEnumerable<int> TakeWhilePositive(IEnumerable<int> numbers) { foreach (int n in numbers) { if (n > 0) { yield return n; } else { yield break; } } }
```