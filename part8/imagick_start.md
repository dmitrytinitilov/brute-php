# Imagick start

Примеры использования
http://php.net/manual/ru/imagick.examples-1.php

```php
// if full path is not specified, will look for file in Apache's folder.

$im = new imagick($_SERVER['DOCUMENT_ROOT'].'/duke-nukem.png');

// resize by 200 width and keep the ratio
$im->thumbnailImage(200, 0);

// if full path is not specified, file will end up in Apache's folder.

// write to disk
$im->writeImage($_SERVER['DOCUMENT_ROOT'].'/duke-nukem-sm.jpg');

echo 'Image Thumbnail Created.';

```

**Класс Imagick**

Imagick::flipImage ( void )  - вертикальное отражение изображения

colorize

blur

http://php.net/manual/ru/imagick.adaptivesharpenimage.php

**Класс ImagickPixel**

```php
new ImagickPixel("black")
```

Создается объект ImagickPixel. Если указан цвет, то объект создается и инициализируется с этим цветом перед возвращением.

**Вырезаем куски изображения**

http://php.net/manual/ru/imagick.cropimage.php


**Полезное чтиво:**

1. Набор функций Imagick
http://php.net/manual/ru/book.imagick.php


**Практика: **

1. Грузим картинку и выдаем три различных варианта фильтра этой картинки

2. Пикселизировать изображение

3. У фотографии в портретной ориентации, нужно вырезать верх и получить уменьшенную копию

