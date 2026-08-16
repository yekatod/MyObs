## Частичные методы

---

Методы, которые существуют только в [[Partial Class]], которые в одной части могут быть объявлены, а в другой реализованы

Должен быть `void` и без модификатора доступа

```C#
// part containing defining partial method declarations
partial class C
{
    partial void M1();                  // implementation optional
    private partial void M2();          // required, impl. required
    protected partial bool M3();        // required, impl. required
    public partial void M4(out int i);  // required, impl. required
}

// part containing implementing partial method declarations
partial class C
{
    private partial void M2() { ... }
    protected partial bool M3() { ... }
    public partial void M4(out int i) { ... }
}
```

