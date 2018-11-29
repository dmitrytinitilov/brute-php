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

вариант с передачей параметра

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




