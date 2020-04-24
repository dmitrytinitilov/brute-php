# # Конструкторы

Добавим в наш класс конструктор

```php
class Number {

	public function __construct($num) {
		$this->num = $num;
	}
}
```


Теперь создание объекта будет выглядеть вот так

```php
$obj = new Number(5); //передаю параметр в конструктор
```


**Спецификаторы доступа**

**Занятие Бонус** реализация MVC на основе прямоугольника и выбора цвета

**Практика**
1. Добавляем в объект конструктор, который на вход получает адрес картинки, сохраняет его в свойстве объекта, и через метод выводит эту картинку на сайт.
2. Сделать класс с конструктором, для товара, который на вход получает название, описание, цену товара и адрес картинки. В классе также есть методо для отображения товара.
3.	class car  (конструктор, свойство speed, и метод Go, который получает расстояние и возвращает время)
4.	Сделать функцию Race
5.	Добавляем расход топлива
6.	Класс круг, есть радиус и цвет
7.	Класс для выведения товара на экран
8.	Сделать класс, который на вход конструктора получает соединение с базой данных. Внутри класса сделать метод, который возвращает массив имен работников.