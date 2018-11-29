# ЧПУ, канонизация, 404

**ЧПУ и .htaccess**

Сделаем первый тестовый .htaccess

```apacheconf
RewriteEngine On
Options +FollowSymlinks
RewriteBase /

RewriteCond %{REQUEST_FILENAME} !-f
RewriteCond %{REQUEST_FILENAME} !-d
RewriteRule ^.*$ index.php [NC,L]
```

////////////////////////////////////
В index.php

```php
echo $_SERVER['HTTP_HOST']; //имя домена
echo $_SERVER['REQUEST_URI']; //адрес после домена
```

**Устанавливаем альтернативную страницу по-умолчанию**
```apacheconf
DirectoryIndex about.html
```


В CodeIgniter исключить директорию css из интерпретации

```apacheconf
RewriteEngine on

RewriteCond $1 !^(index\.php)
RewriteCond $1 !\.css$
RewriteRule ^(.*)$ /index.php/$1 [L]

RewriteCond $1 \.css$
RewriteCond $1 !^application/views/
RewriteRule ^(.*)$ application/views/$1 [L]
```

http://www.phpinfo.su/articles/practice/chpu_na_php.html#ixzz3h74Zok4a

http://phpguru.com.ua/posts.php?id=112
RewriteBase /xyz/  Устанавливает базовый URL для преобразований в контексте каталога

```apacheconf
RewriteCond %{REQUEST_FILENAME} !-f
RewriteCond %{REQUEST_FILENAME} !-d
```
что правила выполнятся только тогда, если нет этого файла или папки. Разберем буквы в конце<BR>
-d	проверяет путь и является ли имя файла каталогом<BR>
-f	проверяет, является ли файлом<BR>
-s	аналогично -f, только еще проверяет чтобы размер файла был больше нуля<BR>
-l	проверяет, является ли путь символической ссылкой<BR>
-F	можно сказать, "аналог" -f, но проверяет внутренне (нехило ложит сервер)<BR>
-U	проверяет URL на существование, также отправляя внутренний подзапрос - тоже здравствуй сервер))

Если вначале (перед дефисом) поставить восклицательный знак, то будет отрицание (т.е. наоборот) Чаще всего используют только -f и -d (вернее, !-f и !-d)

```apacheconf
RewriteEngine On
#если запрошенного файла или папки не существует
RewriteCond %{REQUEST_FILENAME} !-d
RewriteCond %{REQUEST_FILENAME} !-f
```

///////////////////////////////////

```apacheconf
RewriteEngine On
#если запрошенного файла или папки не существует
RewriteCond %{REQUEST_FILENAME} !-d
RewriteCond %{REQUEST_FILENAME} !-f
#регулярим)
RewriteRule ^posts-([0-9]+)/?$ /posts.php?id=$1 [L,QSA]
```	

**L**	останавливает процесс преобразования на этой строчке и не выполнять последующие за ней преобразования адреса (last)<BR>
**R=**	внешний редирект (после равно пишется адрес или цифра-статус). Если ничего не указать вылетит 302 "Временно перемещен"<BR>
**QSA**	параметры ссылки ($_GET). Если его не указывать, они "потеряются"<BR>
**NC**	регистронезависимо (т.е. CATEGORY и category одинаковы для правила)  (no case)<BR>
**F**	ошибка доступа (403 доступ запрещен)<BR>
**S=**	пропустить правила (после равно количество правил)<BR>
**G**	"умертвляет" URL-адрес (410 GONE)<BR>
**N**	перезапускает заново правила преобразования, но уже работает с полученным в результате предыдущих действий адресом<BR>
**E=**	присваивает переменным окружения значения (после равно пишут, вида переменная:значение)<BR>

**[L,QSA]** или вот еще ситуация когда нужно несколько
**[R=301,L]** - если не остановить преобразования (L) то они будут продолжать выполняться дальше. А это уже лишнее

**Канонизация или склейка домена**  
http://www.lucky-seo.com/seo/htaccess<BR>
Для склейки домена с www на без www:
```apacheconf
RewriteCond %{HTTP_HOST} ^www.site\.com$ [NC]
RewriteRule ^(.*)$ http://site.com/$1 [R=301,L]
```
Для склейки домена с без www на с www:
```apacheconf
RewriteCond %{HTTP_HOST} ^site.com$ [NC]
RewriteRule ^(.*)$ http://www.site.com/$1 [R=301,L]
```

Для правильного выбора метода склейки нужно рассмотреть такие факторы:
•	У какого варианта выше индексация;
•	У какого варианта выше позиции в выдаче;
•	Канонизация слэша в конце адреса.
При создании проекта сайта нужно решить, использовать ли слэш в конце адреса. Для поисковых систем адреса вида:
•	http://www.site.com/category1
•	http://www.site.com/category1/
Являются разными URL. Поэтому когда решите, какого вида будут адреса у вас на сайте, нужно прописать такой код для того, чтобы убрать слэш в конце:

```apacheconf
RewriteEngine On
RewriteCond %{HTTP_HOST} (.*)
RewriteCond %{REQUEST_URI} /$ [NC]
RewriteRule ^(.*)(/)$ $1 [L,R=301]
#или такой, чтобы добавить его:
RewriteCond %{REQUEST_FILENAME} !-f
RewriteCond %{REQUEST_URI} !(.*)/$
RewriteRule ^(.*[^/])$ $1/ [L,R=301]
#Для редиректа 301 одной страницы на другую:
Redirect 301 /oldpage.html http://www.site.com/newpage.html
```

**Ошибка 404**

```apacheconf
ErrorDocument 404 http://www.domain.com/your-custom-404.php
```

или

```php
header($_SERVER["SERVER_PROTOCOL"]." 404 Not Found");
include("notFound.php");
```

http://blogerator.ru/page/fajl-primery-htaccess-redirekt-dostup
http://www.proofsite.com.ua/article-2242.html

Практика:
1. Сделать трехстраничный сайт
