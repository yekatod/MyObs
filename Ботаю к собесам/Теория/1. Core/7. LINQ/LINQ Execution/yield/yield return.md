
Указывает следующее значение в итерации, пример:

```C#
IEnumerable<int> ProduceEvenNumbers(int upto) { for (int i = 0; i <= upto; i += 2) { yield return i; } }
```