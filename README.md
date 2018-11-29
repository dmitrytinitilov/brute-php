Наглый PHP
=======

Сила PHP в его простоте. Вы можете создать свой первый сайт в считанные минуты. Вам не нужно разбираться с протоколом http, писать свой http-сервер, генерировать заголовки - Вы просто можете начать. Конечно Вам стоит со всем этим разобраться, если Вы хотите заниматься Веб-разработкой, но работая с PHP, Вы можете делать это в удобное для Вас время.

Конечно не стоит делать на PHP сайты, требующие большого количество вычислений в реальном времени. В любом случае интерпретируемый на лету язык, всегда будет проигрывать заранее скомпилированному, например Java, и уж точно будет проигрывать языку, работающему без виртуальной машины, например С++. Но если Вам нужно сделать небольшой интернет-магазин (до миллиона пользователей), то PHP идеален для Вас. Эта причина, по которой большинство Web-стартапов 2000-2010 годов писались на PHP, включая Youtube и Facebook.

То есть Вы просто берете и внаглую пишите сайт!

Если Вы думаете, что PHP - это просто и несерьезно посмотрите инфографику по развитию инфраструктуры PHP
https://habrahabr.ru/company/dataart/blog/272165/

P.S. Данная книга находится в разработке. Главы с хештегом #COFFEE не написаны совсем, главы с # требуют доработки.

https://telegram.me/dmitrytinitilov

[Skype: dmitry_tinitilov](skype:dmitry_tinitilov?call)


# Введение

* [Введение](README.md)
* [Глава I - Старт](part1/README.md)
  * [Hello World!](part1/helloworld_md.md)
  * [\# Типы данных в PHP](part1/php-types.md)
  * [\# Конструкция if](part1/if.md)
  * [\# Применение флагов](part1/flags.md)
  * [\#COFFEE Логические операторы](part1/logicaloperators.md)
  * [\# Цикл while](part1/while.md)
  * [\#Циклы с неизвестным количеством итераций](part1/unknowncycles.md)
  * [Цикл for](part1/for.md)
* [Глава II - Массивы](part2/README.md)
  * [\# Простейшие массивы](part2/arrays.md)
  * [\# Ассоциативные массивы и foreach](part2/Ассоциативные массивы.md)
  * [\# Двумерные массивы](part2/multidimensional_arrays.md)
  * [\#Массивы $\_GET и $\_POST](part2/getpost_arrays.md)
  * [\# Метод POST. Золотое правило Web-разработки](part2/post.md)
  * [\#COFFEE Немного AJAX'a](part2/ajax.md)
  * [\#COFFEE JSON](part2/json.md)
* [Глава III - Функции](part3/readme.md)
  * [\# Основы](part3/basics.md)
  * [\# Локальные и глобальные переменные](part3/local-global.md)
  * [\# Возвращение нескольких значений. Конструкция list](part3/mass-return.md)
  * [\# Возможность вызова функции](part3/function-execution.md)
  * [\# Статические переменные](part3/static-variables.md)
  * [\# Парамметры по умолчанию](part3/default-parameters.md)
  * [\# Подключение внешних файлов. include, require](part3/include.md)
  * [\#COFFEE Проблемы с подключением. include\_once, require\_once](part3/includeonce.md)
  * [\#COFFEE Передаем параметры в подключаемый файл](part3/making-view.md)
  * [\#COFFEE Возвращение значений из подключаемых файлов](part3/return-from-outer.md)
* [Глава IV - Добавляем базу данных](part4/readme.md)
  * [\#COFFEE Работаем с базой данных через PHPMyAdmin](part4/phpmyadmin.md)
  * [\# Подключение к MySQL базе данных](part4/dbconnect.md)
  * [\# SELECT](part4/select.md)
  * [\# INSERT, LAST\_INSERT\_ID](part4/insert.md)
  * [\# UPDATE, DELETE](part4/update-delete.md)
  * [\#COFFEE Хранение паролей на сервере](part4/password-keeper.md)
  * [\# Загружаем картинку на сервер](part4/picture-upload.md)
  * [\# ORDER BY, LIMIT](part4/orderby_-limit.md)
  * [\# Связи между таблицами. JOIN](part4/join.md)
  * [\# Агрегатные функции. GROUP BY, HAVING](part4/group-by.md)
  * [\# SQL-инъекции](part4/sql-injection.md)
  * [\# Создание пользователя через mysql консоль](part4/grant-revoke.md)
  * [\# COFFEE Оптимизация запросов и БД](part4/database_optimization.md)
  * [PDO](part4/pdo.md)
* [Глава V - Идентификация и авторизация](part5/readme.md)
  * [\# COOKIES](part5/cookies.md)
  * [\# Понятие хеша](part5/hash.md)
  * [\#COFFEE Авторизация. Хранение паролей в базе данных](part5/authorization.md)
  * [\#Сессии](part5/session.md)
  * [\#COFFEE Альтернативные способы идентификации пользователей](part5/identification.md)
* [Глава VI - Добавляем ООП](part6/readme.md)
  * [\# Понятие классов и объектов](part6/classes-and-objects.md)
  * [\# this](part6/this.md)
  * [\# Конструкторы](part6/constructors.md)
  * [\# Хранение, удаление и клонирование объектов](part6/use-delete-clone.md)
  * [\# Статические свойства и методы](part6/static-props-and-methods.md)
  * [\# Наследование классов и конструкторов](part6/inheritance.md)
  * [\# Полиморфизм](part6/polymorphism.md)
  * [\# Интерфейсы и абстрактные классы](part6/interfaces-and-abstract-classes.md)
* [Глава VII - Работа со строками.ЧПУ](part7/readme.md)
  * [\#COFFEE strlen,strpos,substr](part7/strlen-strpos-substr.md)
  * [\#COFFEE регулярные выражения](part7/regular-expressions.md)
  * [\#COFFEE функции регулярных выражений](part7/regular-expressions-functions.md)
  * [\#COFFEE ЧПУ, канонизация, 404](part7/prettyuri_canonization_404.md)
  * [\#COFFEE Настройка мультиязычности](part7/multilingual-support.md)
* [Глава VIII - Работа с графикой](part8/readme.md)
  * [Imagick start](part8/imagick_start.md)
  * [Создаем капчу](part8/a-from-site.md)
* [Глава IX - Работа с файлами и потоками](part9/readme.md)
  * [Чтение данных из файла](part9/reading_data_from_file.md)
  * [Считывание данных с удаленного сайта](part9/read-data-from-site.md)
  * [Запись данных в файл](part9/writing_data_to_file.md)
  * [Работа с директориями](part9/working_with_directories.md)
* [Глава X - Работа с фреймворком на примере CodeIgniter](part10/readme.md)
  * [Быстрый старт](part10/start.md)
  * [Создаем базовое приложение](part10/basic_app.md)
* [Глава XI - Пишем свой фреймворк на PHP](part11/readme.md)
  * [\#COFFEE Паттерн MVC](part11/mvc.md)
  * [\#Создаем контролер](part11/creating-controler.md)
  * [\#COFFEE Настраиваем ЧПУ](part11/creating-pretty-URI.md)
  * [\# Создаем модель](part11/creating-model.md)
* [Глава XII - Laravel](laravel/README.md)
  * [Старт](laravel/start.md)
  * [Первое приложение](laravel/first_steps.md)
  * [Миграции](laravel/migration.md)
  * [Routes](laravel/routes.md)
* [Глава XIII PHPUnit](phpunit/README.md)
* [Дополнения](addition/readme.md)
  * [\#COFFEE Настраиваем Sublime для PHP](addition/sublime_for_php.md)
  * [Идеи проектов](addition/project_ideas.md)












