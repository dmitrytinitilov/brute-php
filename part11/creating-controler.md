#Создаем контроллер

```php
class Controller {

		public function loadModel($model_name) {

			include('model/'.strtolower($model_name).'.php');

			return new $model_name();
		}

		public function load($view_name,$data) {

			foreach ($data as $key =>$value) {
				$$key = $data[$key];
			}

			include('views/'.$view_name.'.php');
		}
	}
	
```