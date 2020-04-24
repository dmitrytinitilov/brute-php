# Возможность вызова функции

Возьмем предыдущий пример 

```php
function sum($a,$b) {
    return $a+$b;
}

sum(5,7);// сработает ли этот вызов?
```

Описание функции идет до вызова, и вызов естественно сработает.

А что если сделать вот так?


```php
sum(5,7); //?

function sum($a,$b) {
    return $a+$b;
}
```


Кажется, что вызов невозможен, ведь описание идет после, т.е. интерпретатор языка вроде как и не должен знать о происходящем.

НО на самом деле вызов пройдет успешно. Почему? Дело в том, что до запуска выполнения, интерпретатор производит предпросмотр кода. Во время этого предпросмотра не производится выполнение кода, а все что требует выполнения кода - игнорируется. Все найденные таким образом определения функции и заносятся в кеш и становятся доступными для вызова на этапе выполнения кода.


Пример с if'ом<BR>
Пример с вложенной функцией<BR>
Пример с повторным описанием<BR>
Пример с циклом<BR>