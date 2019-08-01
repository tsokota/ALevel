# Overloading and Overriding

## Полезные ссылки

[Перегрузка методов](https://metanit.com/sharp/tutorial/3.5.php)

[Перегрузка операций преобразования типов](https://metanit.com/sharp/tutorial/3.37.php)

[Перегрузка операторов](https://metanit.com/sharp/tutorial/3.36.php)


## Перегрузка методов


Иногда возникает необходимость создать один и тот же метод, но с разным набором параметров. 
И в зависимости от имеющихся параметров применять определенную версию метода. 
Такая возможность еще называется перегрузкой методов.

В языке C# мы можем создавать в классе несколько методов с одним и тем же именем, но разной сигнатурой. Что такое сигнатура? Сигнатура складывается из следующих аспектов:

* Имя метода

* Количество параметров. Пример:
```csharp  
  int Sum(int x, int y)
  {
      return x + y;
  }
  void Sum(int x, int y, int z)
  {
      Console.WriteLine(x + y+z);
  }
  ```
* Типы параметров. Пример:
```csharp  
  int Sum(int x, int y)
  {
      return x + y;
  }
  void Sum(int x, double y)
  {
      Console.WriteLine(x + y);
  }
  ```

*  Порядок параметров
```csharp 
  int Sum(int x, double y)
  {
      return x + y;
  }
  void Sum(double y, int x)
  {
      Console.WriteLine(x + y);
  }
  ```

* Модификаторы параметров
```csharp
  void Increment(ref int val)
  {
    val++;
    Console.WriteLine(val);
  }

  void Increment(int val)
  {
    val++;
    Console.WriteLine(val);
  }
```
Но названия параметров в сигнатуру НЕ входят. Например, возьмем следующий метод, КОТОРЫЙ СОДЕРЖИТ ОШИБКУ:


```csharp  
  int Sum(int x1, int y1)
  {
      return x + y;
  }
  void Sum(int x2, int y2)
  {
      Console.WriteLine(x + y);
  }
  ```
Отличие методов по возвращаемому типу или по имени параметров не является основанием для перегрузки. Например, возьмем следующий набор методов:
```csharp  
  int Sum(int x, int y)
  {
      return x + y;
  }
  int Sum(int number1, int number2)
  {
      return x + y;
  }
  void Sum(int x, int y)
  {
      Console.WriteLine(x + y);
  }
  ```
  
  Сигнатура у всех этих методов будет совпадать:
  
  ```csharp  
  Sum(int, int)
  ```
## Перегрузка операторов
Наряду с методами мы можем также перегружать операторы. Например, пусть у нас есть следующий класс Counter:
```csharp  
  class Counter
  {
      public int Value { get; set; }
  }
  ```
Данный класс представляет некоторый счетчик, значение которого хранится в свойстве Value.

И допустим, у нас есть два объекта класса Counter - два счетчика, которые мы хотим сравнивать или складывать на основании их свойства Value, используя стандартные операции сравнения и сложения:
```csharp  
Counter c1 = new Counter { Value = 23 };
Counter c2 = new Counter { Value = 45 };
 
bool result = c1 > c2;
Counter c3 = c1 + c2;
  ```


