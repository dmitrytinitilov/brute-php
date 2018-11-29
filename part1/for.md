# Цикл for


Выведем 10 блоков на экран

```php
echo '
<style>
    .block {
        width:100px
        height:100px;
        background:black;
        display:inline-block;
        margin-left:20px;
    }
</style>';


for ($i=0;$i<10;$i++) {
    echo '<div class="block"></div>';
}


```