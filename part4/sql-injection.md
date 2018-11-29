# SQL-инъекции

Пример SQL-инъекции на борту самолета
https://habrahabr.ru/post/318228/

/// this part should be completely remastred
/// этот раздел должен быть полностью переписан

```php
$id = $_GET["id"];
```

// 5 OR 1=1<BR>
// 5' OR '1'='1<BR>
// 5\' OR \'1\'=\'1<BR>


$s_id= addslashes($id)

```sql
SELECT name, credit_card
FROM profile
WHERE id = '$s_id'
```

```sql
SELECT name, credit_card
FROM profile
WHERE id = (DROP DATABASE )
```

**mysqli_real_escape_string**

http://stackoverflow.com/questions/5741187/sql-injection-that-gets-around-mysql-real-escape-string/12118602#12118602

http://habrahabr.ru/post/148701/

```php
$stmt = $dbh->prepare("SELECT * FROM REGISTRY where name LIKE ?"); 
$stmt->execute(array("%$_GET[name]%")); $data = $stmt->fetchAll();
```

**mysqli_prepare**

```php
if ($stmt = $mysqli->prepare("SELECT District FROM City WHERE Name=?"))
{
    $stmt->bind_param("s", $city);
    $stmt->execute();

    $stmt->bind_result($district);
    $stmt->fetch();

    printf("%s is in district %s\n", $city, $district);

    $stmt->close();
}
```


```php
$query = "SELECT Name, CountryCode FROM City ORDER by ID DESC LIMIT 150,5";

if ($stmt = $mysqli->prepare($query)) {

    /* Запустить выражение */
    $stmt->execute();

    /* Определить переменные для результата */
    $stmt->bind_result($name, $code);

    /* Выбрать значения */
    while ($stmt->fetch()) {
        printf ("%s (%s)\n", $name, $code);
    }

    /* Завершить запрос */
    $stmt->close();
}
```

**Множественные параметры**

```php
$stmt = $mysqli->prepare("INSERT INTO CountryLanguage VALUES (?, ?, ?, ?)");
$stmt->bind_param('sssd', $code, $language, $official, $percent);


$code = 'DEU';
$language = 'Bavarian';
$official = "F";
$percent = 11.2;

/* выполнение подготовленного запроса */
$stmt->execute();
```


**Вывод нескольких строк**

```php
/* prepare statement */
if ($stmt = $mysqli->prepare("SELECT Code, Name FROM Country ORDER BY Name LIMIT 5")) {
    $stmt->execute();

    /* bind variables to prepared statement */
    $stmt->bind_result($col1, $col2);

    /* fetch values */
    while ($stmt->fetch()) {
        printf("%s %s\n", $col1, $col2);
    }

    /* close statement */
    $stmt->close();
}
```