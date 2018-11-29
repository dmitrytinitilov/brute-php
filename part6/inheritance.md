# # Наследование классов и конструкторов

```php
class Basic {

	public $a=5;

	public function saySomething() {
        	        echo 'Something';
    }
}

class Child extends Basic{
    public function newFunction() {
		echo 'NEW!!!';
	}
}


$obj = new Child();

echo $obj->a;
$obj->saySomething();

$obj->newFunction();
```

**Перегрузка методов**

```php
class Basic {

	public $a=5;

	public function saySomething() {
        	        echo 'Something';
    }
}

class Child extends Basic{
    public function saySomething() {
         echo 'Hi!';
    }
}
```


**Наследование конструкторов**

```php
<?php
class BaseClass {
   function __construct() {
       print "Конструктор класса BaseClass\n";
   }
}

class SubClass extends BaseClass {
   function __construct() {
       parent::__construct();
       print "Конструктор класса SubClass\n";
   }
}

class OtherSubClass extends BaseClass {
    // inherits BaseClass's constructor
}

// In BaseClass constructor
$obj = new BaseClass();

// In BaseClass constructor
// In SubClass constructor
$obj = new SubClass();

// In BaseClass constructor
$obj = new OtherSubClass();
?>
```

**Спецификаторы доступа**

_public_ - свойства и методы класса доступны как внутри класса через $this, так и за пределами класса через объект

_private_ - свойства и методы класса доступны только внутри класса через $this

_protected_ - свойства и методы класса доступны только внутри класса, а также внутри классов наследников


**instanceof**

Проверяет является ли объект, объектом заданного класса.

Объект от класса наследника является объектом от базового класса.


**Практика:**

1.	От класса прямоугольник создать класс-наследник эллипс
2.	Реализуем функцию, которая выводит квадраты на экран в произвольных местах. Передаем туда массив эллипсов. 
3.	Задача про магов и рыцарей health, strength, attack




