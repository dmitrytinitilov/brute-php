#Routes

С версии 5.3 настройка путей перенеслась в /routes/web.php


Запускаем в CarController метод show. {id} передается в качестве параметра $id в метод show

```
Route::resourse('/cars/{id}', 'CarController@show');
```
