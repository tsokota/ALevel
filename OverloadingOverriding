# Overloading and Overriding

## Полезные ссылки

[Перегрузка методов](https://metanit.com/sharp/tutorial/3.5.php)

[Перегрузка операций преобразования типов](https://metanit.com/sharp/tutorial/3.37.php)

[Перегрузка операторов](https://metanit.com/sharp/tutorial/3.36.php)


## Перегрузка методов

![HTTP request](/images/http-requeest-under-the-hood.png)
Иногда возникает необходимость создать один и тот же метод, но с разным набором параметров. 
И в зависимости от имеющихся параметров применять определенную версию метода. 
Такая возможность еще называется перегрузкой методов.

В языке C# мы можем создавать в классе несколько методов с одним и тем же именем, но разной сигнатурой. Что такое сигнатура? Сигнатура складывается из следующих аспектов:

* Имя метода

* Количество параметров

* Типы параметров

*  Порядок параметров

* Модификаторы параметров

Но названия параметров в сигнатуру НЕ входят. Например, возьмем следующий метод:
### Установка IIS

![Установка IIS](/Module-5/images/iis-setup.png)

### Настройка сайта

## Практика

Деплоим на IIS - Phonebook & Phonebook.API. Для обоих вариантов используем именнованный инстанс.

## Коды ответов HTTP

* **200** - OK
* **400** - Bad Request
* **401** - нет доступа
* **404** - не найден
* **500** - внутренняя ошибка сервера

## Форматирование результата

![Formatters](/Module-5/images/web-api-formatters.png)

* **FormUrlEncodedFormatter** – возвращает объект, который парсит данные формы в процессе привязки модели
* **JsonFormatter** – сериализует данные в JSON
* **XmlFormatter** – сериализует данные в XML

## Routing (маршрутизация)

### Как это работает?

1. Если данные маршрута содержат ключ "action", то метод действия будет искаться по значению этого ключа. 
В отличии от ASP.NET MVC, в основном маршруты Web API не используют имена методов действия в маршрутизации.
Собираются все методы действия, у которых имя совпадает со значением ключа «action» Каждый метод действия может поддерживать один или 
несколько типов HTTP-запросов (GET, POST, PUT и т.д.) Исключаются те методы действия, для которых не подходит 
HTTP-запрос.

![Routing](/Module-5/images/routing-1.png)

![Routing](/Module-5/images/routing-2.png)

2. Если данные маршрута не содержат ключ "action", тогда метод действия будет найден по HTTP-запросу.
3. Для выбранных действий в обоих шагах, производится проверка на соответствие параметров. Исключаются все действия, которые не соответствуют всем параметрам в данных маршрута.
4. Исключаются методы действия, которые имеют атрибут "NonAction". 
Если методов осталось больше одного, выдается ошибка HTTP 500. (Внутренняя ошибка HttpResponseException)
Если методов не осталось совсем, то возвращается ошибка HTTP 404.

![HttpRoutingDispatcher](/Module-5/images/http-routing-dispatcher.png)

Роутинг в Web API реализован классом HttpRoute.

* **RouteTemplate** – шаблон URL

* **Defaults** – словарь из набора параметров и их значений (Dictionary<string, object>)

* **Constraints** – ограничения маршрута (Dictionary<string, object>)

* **DataTokens**

* **Handlers** – обработчик маршрута

### Управление маршрутами

Используемый шаблон

«api/{controller}/{id}»

Может соответствовать

“api/products” или “api/products/5”

![Routing](/Module-5/images/routing-default.png)

Используемый шаблон

«api/{controller}/{action}»

Может соответствовать

“api/products/getproduct”

![Routing](/Module-5/images/routing-custom.png)

В маршруте могут быть заданы дефолтные параметры

![Routing](/Module-5/images/routing-default-params.png)

**[NonAction]** – метод больше не сопоставляется с подходящим маршрутом

### Ограничения маршрутов

* **AlphaRouteConstraint** – сегмент состоит только из алфавитных символов

* **BoolRouteConstraint**

* **DateTimeRouteConstraint**

* **DecimalRouteConstraint**

* **DoubleRouteConstraint**

* **FloatRouteConstraint**

* **IntRouteConstraint**

* **LongRouteConstraint**

* **HttpMethodConstraint** – ограничение по методу HTTP-запроса

* **MaxLengthConstraint**

* **MinLengthConstraint**

* **RangeRouteConstraint**

* **RegexRouteConstraint** – сегмент должен соответствовать регулярному выражению

![Routing Restrictions](/Module-5/images/route-restrictions.png)

### Применение кастомного роутинга

![Routing Attributes](/Module-5/images/routing-through-attributes.png)

## Action Filters

Иногда нам необходимо добавить некоторую логику до или после выполнения метода action.

![Action Filters](/Module-5/images/filters-general.png)

### Типы Action Filters

![Action Filters](/Module-5/images/action-filters-types-1.png)
![Action Filters](/Module-5/images/action-filters-types-2.png)

### AllowMultiple property

![AllowMultiple](/Module-5/images/aloow-multiple-property.png)

### Жизненный цикл  Action Filters

![Action Filters](/Module-5/images/action-filters-pipeline.png)

### Authentication Filters

![Authentication Filters](/Module-5/images/iauthentication-filter.png)

Метод **AuthenticateAsync** вызывается до обработки запроса аутентификации пользователя.

Метод **ChallengeAsync** вызывается во время обработки ответа Клиенту.

### Authorization Filters

![Authorization Filters](/Module-5/images/authorization-filter.png)

Цель фильтров авторизации – определение роли в системе аутентифицированного пользователя.

![Authorization Filters](/Module-5/images/iauthorization-filter.png)

### Фильтры действий

![Action Filters](/Module-5/images/iactionfilter.png)

**actionContext** содержит информацию о методе контроллера,а также информацию о  запросе.

![Action Filters](/Module-5/images/actionfilterattribute.png)

**OnActionExecutingAsync** – до выполнения action
**OnActionExecutedAsync** – после выполнения action

### Фильтры исключения

![Exception Filters](/Module-5/images/exception-filter.png)

### Глобальные фильтры

Области видимости фильтра:

* Метод (action)
* Контроллер
* Все приложение (глобальный фильтр)

![Global Filters](/Module-5/images/global-filters.png)

### Переопределение фильтров

Отключает действие фильтра для определенного метода.

Встроенные реализации фильтров переопределения.

* **OverrideAuthentication** – отключает аутентификацию

* **OverrideAuthorization** – отключает авторизацию

* **OverrideAction** – отключает фильтры методов

* **OverrideException** – отключает фильтры исключений

## Домашнее задание

1. **Теория**
2. Работа с атрибутами в C#

3. Расширить созданный на уроке Phonebook API

* Сделать guard-валидацию входных параметров, в случае ошибки возвращать 400-код и некоторое сообщение
* Реализовать кастомное исключение на проверку формата телефона (+38-067-000-00-00)
* Повесить глобальный фильтр исключения при неправильном формате телефона
* Отключить его для метода Update (PUT)
