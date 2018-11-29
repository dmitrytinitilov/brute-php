# Типы данных в PHP

Типы данных

http://www.php.su/learnphp/datatypes/

8 типов + 3 псевдотипа для мануала

**Boolean**

Переменная данного типа может содержать всего два значения **true** и **false**. При этом true и false можно писать в любом регистре, например TRUE или fAlSe.

**Integer**

0755 - восьмиричная запись  (права доступа к файлам в Unix'e)
0xBAD - шестнадцатиричная запись<BR>
1A = 1*16+A = 1*16+10 = 26<BR>
A1 = A*16+1 =10*16 +1 = 161<BR>

**Float**

Проблемы с некоторыми расчетами
echo floor((0.7+0.1)*10);  //дает 7, а не 8


**String**

$a=5;<BR>
echo '$a'; //$a<BR>
echo "$a";//5<BR>
echo ' "$a" '; //"$a"<BR>
echo " ' $a' "; //'5'<BR>

Пример использования псевдотипа Mixed в описании функции
http://php.net/manual/ru/function.strpos.php

**Приведение типов**

http://php.net/manual/ru/language.types.type-juggling.php

**Принудительное преоразование типов**

```php
$s = "3 little piggies ate 4 cupcakes";
$s = (int) $s;// 3
```
