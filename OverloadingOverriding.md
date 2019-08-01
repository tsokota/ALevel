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
```php  
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
```php  
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
```php 
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
```php
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


```php  
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
```php  
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
  
  ```php  
  Sum(int, int)
  ```
## Перегрузка операторов
