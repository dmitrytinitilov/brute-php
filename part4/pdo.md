# C0FFEE PDO

[http://phpfaq.ru/pdo](http://phpfaq.ru/pdo)

[https://habrahabr.ru/post/137664/](https://habrahabr.ru/post/137664/)

```php
<?php

$pdo = new PDO("mysql:host=$host;dbname=$dbname", $user, $pass); 


$STH = $pdo->prepare('SELECT name,age,salary FROM workers');

$STH->setFetchMode(PDO::FETCH_ASSOC); 

$STH->execute();

//var_dump($STH);

while($row = $STH->fetch()) {  
    echo $row['name']." ".$row['age']." ".$row['salary'].'<br>';  
}

```

**Вариант с передачей параметра**

```php
$pdo = new PDO("mysql:host=$host;dbname=$dbname", $user, $pass); 


$limit = 20000;

$STH = $pdo->prepare("SELECT name,age,salary
					  FROM workers
					  WHERE salary > ?");

$STH->setFetchMode(PDO::FETCH_ASSOC); 

$STH->execute([$limit]);

//var_dump($STH);

while($row = $STH->fetch()) {  
    echo $row['name']." ".$row['age']." ".$row['salary'].'<br>';  
}
```


**Передача именованных параметров**

```php
$sql = 'SELECT name, colour, calories
    FROM fruit
    WHERE calories < :calories AND colour = :colour';
$sth = $dbh->prepare($sql, array(PDO::ATTR_CURSOR => PDO::CURSOR_FWDONLY));
$sth->execute(array(':calories' => 150, ':colour' => 'red'));
$red = $sth->fetchAll();
$sth->execute(array(':calories' => 175, ':colour' => 'yellow'));
$yellow = $sth->fetchAll();
```


**Получение сообщения об ошибке**

```php
$stmt = $dbh->prepare('bogus sql');
if (!$stmt) {
    echo "\nPDO::errorInfo():\n";
    print_r($dbh->errorInfo());
}
```



