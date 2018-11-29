#Создаем модель


```php
<?php

class WorkerModel {

	public function __construct() {
		$this->db = mysqli_connect('localhost','root','',"world_db");

	}

	public function getWorkers() {
		$query = "SELECT *
				  FROM workers
				  ";

		$result = $this->db->query($query);
		return $result->fetch_all();
	}
}

?>

```