# Composer

Находим php.exe в модулях OpenServer'a, добавляем этот путь в переменную среды PATH

Далее в папке проекта устанавливаем composer

```php
php -r "readfile('https://getcomposer.org/installer');" | php
```

Если Вам вывелось

```cli
Warning: readfile(): Unable to find the wrapper "https" - did you forget to enab
le it when you configured PHP? in Command line code on line 1

Warning: readfile(https://getcomposer.org/installer): failed to open stream: Inv
alid argument in Command line code on line 1
```
То найдите php.ini и поменяйте в нем

```
;extension=php_openssl.dll
```

на
```
extension=php_openssl.dll
```

Если всё прошло нормально, то получим что-то вроде

```cli
All settings correct for using Composer
Downloading...

Composer (version 1.8.5) successfully installed to: C:\theproject\composer.phar
Use it: php composer.phar
```

Запуск

```cli
php composer.phar -V
```




**Полезное чтиво:**

1. Composer для самых маленьких
https://habr.com/ru/post/439200/

2. Как установить composer на OpenServer
http://nikolaev-web.ru/blog/installing_the_composer_on_openServer/