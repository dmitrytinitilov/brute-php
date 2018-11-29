# # Парамметры по умолчанию

```php
<?php
function makecoffee($type = "капуччино")
{
    return "Готовим чашку $type.\n";
}
echo makecoffee();
echo makecoffee(null);
echo makecoffee("эспрессо");
?>
```