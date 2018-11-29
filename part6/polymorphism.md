# Полиморфизм

Полиморфизм - это способность разных объектов быть одинаковыми относительно внешнего кода.

```php

class Rectangle {

	public $width;
	public $height;
	public $color;

	public function __construct($width,$height,$color='red') {
		$this->width = $width;
		$this->height= $height;
		$this->color = $color;
	}

	public function draw() {
		echo '<div style="width:'.$this->width.'px;height:'.$this->height.'px;background:'.$this->color.'"></div>';
	}
}

class Circle {

	public $width;
	public $height;
	public $color;

	public function __construct($width,$height,$color='red') {
		$this->width = $width;
		$this->height= $height;
		$this->color = $color;
	}

	public function draw() {
		echo '<div style="width:'.$this->width.'px;height:'.$this->height.'px;background:'.$this->color.';border-radius:50%"></div>';
	}
}


$r = new Rectangle(200,100,'lime');
$r->draw();

function Shift($obj,$left,$top) {
	echo '<div style="position:fixed;left:'.$left.';top:'.$top.';width:auto;">';
		$obj->draw();
	echo '</div>';
}

Shift($r,400,300);

$c = new Circle(50,50,'violet');

Shift($c,400,200);

```

В коде выше есть функция Shift, которая занимается тем, что выводит прямоугольник Rectangle со смещением.

Далее мы хотим приспособить эту функцию для вывода других фигур со смещением относительно левого верхнего угла экрана. Саму функцию мы переписывать не хотим, поэтому у новых фигур добавляем метод draw(), который используется в коде функции Shift().

Реализация класса Circle отрисовывает круг через функцию draw, но отлично передается внутрь функции Shift.

То есть Rectangle и Circle полиморфны относительно функции Shift



