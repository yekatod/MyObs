## Записи

---

Модификатор `record` используется для реализации встроенного инкапсулирования данных.

`record` в [[Class]]:

```C#
public record Human(string Name, string LastName);
```
или
```C#
public record Human
{
	public required string Name {get; init;}
	public required string LastName {get; init;}
}
```

Аналогично с [[Struct]], НО ОЧЕНЬ ВАЖНО неизменяемыми значения в record struct будут только при использовании `readonly record struct`

Также возможно создавать записи с изменяемыми полями, но это немножко логический смысл перебивает.

---

Основные преимущества:
- Краткий синтаксис для объявления класса
- Равенство по значениям
- Краткий синтаксис для обратимого изменения (c `with`)
- Форматирование для отображения
- Поддержка наследования

---

Позиционный синтаксис (юзает позиционный конструктор)
```C#
public record Person(string FirstName, string LastName);
```

Реализует:
- Общедоступные свойства (readonly для всего, кроме голого `record struct`)
- Основной конструктор
- Можно юзать атрибуты, пример:
```C#
public record Person([property: JsonPropertyName("firstName")] string FirstName, [property: JsonPropertyName("lastName")] string LastName);
```

Есть возможность переопределить свойство через конструктор (например чтобы поменять модификатор доступа, прописать какую-то логику и тд или даже поле задать вместо свойства или даже просто объявить свойства как вам это надо)
```C#
public record Person(string FirstName, string LastName, string Id) 
{ 
	internal string Id { get; init; } = Id; 
}
```

---

Свойства инициализированные и непереопределённые конструктором в `record` являются неизменяемыми, НО можно поменять значение по ссылке, например:
```C#
  
public static void Main() 
{ 
	Person person = new("Nancy", "Davolio", new string[1] { "555-1234" }); 
	Console.WriteLine(person.PhoneNumbers[0]); // output: 555-1234 person.PhoneNumbers[0] = "555-6789"; Console.WriteLine(person.PhoneNumbers[0]); // output: 555-6789 
}
```
---

Равенство значений при операторе `==` будет определяться равенством значений свойств, содержащихся в record объекте 

---

Обратимое изменение - создание нового объекта на основе существующего с изменением данных

```C#

Person person2 = person1 with { FirstName = "John" };
```
Это неглубокая копия

---

`ToString()` будет возвращать
`<имя> типа записи { <имя свойства> = <значение>, <имя> свойства = <значение>, ...}`

Компилятор синтезируют виртуальный метод `PrintMembers` и переопределение `ToString()`
При желании `ToString()` можно переопределить самостоятельно

---

Поддерживает наследование, но исключительно от другого `record class`
Также имеет аналог `sealed` - `closed` модификатор доступа

---

`record class` может быть абстрактным