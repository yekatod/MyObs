
---

Событие - элемент, позволяющий объекту активировать уведомление. При помощи него можно присоединять исполняемый код для событий. Имеет тип делегата. Событие вызывает все представленные обработчики событий

Пример
```C#
public class Publisher
{
    public delegate void SampleEventHandler(object sender, SampleEventArgs e);
    public event SampleEventHandler SampleEvent;
    protected virtual void RaiseSampleEvent()
    {
        SampleEvent?.Invoke(this, new SampleEventArgs("Hello"));
    }
}
```

Т.е. сначала мы прописываем сигнатуру делегата, далее - сам ивент. При выполнении события инвокается ивент.

Событие - делегат многоадресной рассылки, который можно вызывать только из класса или из производных классов или из структур (т.е. только там, где ивент оюъявлен)