# Создание пользователя через mysql консоль

/// this part should be completely remastred
/// этот раздел должен быть полностью переписан

http://www.mysql.ru/docs/man/User_resources.html

Про командную строку  в Windows
http://habrahabr.ru/post/218759/

F3 – повтор последней команды

Подборка материалов
https://www.opennet.ru/docs/RUS/mysql_notes/

Доступ к PHPMyAdmin в OpenServer
http://localhost/openserver/phpmyadmin/index.php

mysql -u<username> -p<password -D<database> 

Для того, чтобы поменять базу данных
mysql> USE test
Database changed

Создание пользователя

CREATE USER 'newuser'@'localhost' IDENTIFIED BY 'password';

Передача ему привелегий

GRANT ALL PRIVILEGES ON * . * TO 'newuser'@'localhost';

ALL PRIVILEGES - как мы видели ранее, это даст пользователю MySQL полный доступ к заданной базе данных (если база данных не указана, то ко всем).
CREATE - позволяет создавать новые таблицы или базы данных.
DROP - позволяет удалять таблицы или базы данных.
DELETE - позволяет удалять строки из таблиц.