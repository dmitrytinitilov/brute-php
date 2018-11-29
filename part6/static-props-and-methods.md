# # Статические свойства и методы

Статические свойства и методы хранятся в области памяти класса, поэтому не требуют создания объекта для своего использования

Внутри класса обращаемся к свойствам


```php
class Foo {
    public static $my_static = 'foo';

    public function staticValue() {
        return self::$my_static;
    }
}


print Foo::$my_static . "\n";

$foo = new Foo();

print $foo->staticValue() . "\n";
print $foo->my_static . "\n";      // Не определено свойство my_static

print $foo::$my_static ;  // Начиная с PHP 5.3.0
```

Пример статического метода

```php
class Foo {
    public static function aStaticMethod() {
        // ...
    }
}

Foo::aStaticMethod();
$classname = 'Foo';
$classname::aStaticMethod(); // Начиная с PHP 5.3.0
```

То есть мы можем вызывать  статический метод без создания объекта от класса

Внутри статического метода мы можем обращаться только к статическим свойствам, через конструкцию self


**Практика:**
1. Сделать класс, который бы считал количество созданных от него объектов
2. В предыдущем задании учитывать клонирование и удаление объектов





