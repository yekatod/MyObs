
---
Имеет пять контекстов:

---
[[Field]]

Нельзя изменить значение поля, оно задаётся либо при объявлении, либо в конструкторе

---

Члены экземляра (для [[Struct]])

Используется, чтобы объявить, что член экземпляра не влияет на состояние структуры

---

В возвращаемом значении

При `ref return` модификатор `readonly` показывает, что ссылка не может быть изменена

```C#
private static readonly SamplePoint s_origin = new SamplePoint(0, 0, 0); 
public static ref readonly SamplePoint Origin => ref s_origin;
```


---

