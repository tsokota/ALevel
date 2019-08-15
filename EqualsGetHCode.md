# Сравнение объектов в C#.NET

## Полезные ссылки

[Сравнение объектов в C#.NET](https://habr.com/ru/post/137680/)
[Переопределение Equals и GetHashCode. А оно надо?](https://habr.com/ru/company/microsoft/blog/418515/)


C#.NET предлагает множество способов сравнить объекты, как экземпляры классов, так и структур. 
Способов так много, что без упорядочения этих способов и понимания их грамотного использования и
имплементации (при наличии возможности переопределения), в голове, неминуемо, образуется каша.

**Итак, класс System.Object предлагает следующие методы**:

- ```csharp  
public static bool ReferenceEquals(object objA, object objB)
{
    return objA == objB;
}
```


- ```csharp
public static bool Equals(object objA, object objB)
{
    return objA == objB || (objA != null && objB != null && objA.Equals(objB));
}
```

- ```csharp
public virtual bool Equals(object obj)
{
    return RuntimeHelpers.Equals(this, obj);
}
```

- ```csharp
public static bool operator == (Foo left, Foo right);
```

