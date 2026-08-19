
---

Принцип ООП, согласно которому класс не запрашивает данные другого объекта через методы доступа, а вызывает методы поведения этого класса

Это плохо
```C#
public class Cart 
{
    public decimal Total { get; set; }
    public bool HasDiscountApplied { get; set; }
}

// Код снаружи
if (cart.Total > 1000 && !cart.HasDiscountApplied) 
{
    cart.Total -= 100;
    cart.HasDiscountApplied = true;
}
```

Это хорошо!
```C#
public class Cart 
{
    private decimal _total;
    private bool _hasDiscountApplied;

    public void ApplyDiscount() 
    {
        if (_total > 1000 && !_hasDiscountApplied) 
        {
            _total -= 100;
            _hasDiscountApplied = true;
        }
    }
}

// Код снаружи
cart.ApplyDiscount();

```