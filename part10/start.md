# Быстрый старт

**Пути в CodeIgniter**

```
http://example.com/news/latest/10
```

Расшифровка этого пути следующая
http://example.com/[controller-class]/[controller-method]/[arguments]

Пример простейшего контроллера в файле news.php
application/controllers

```php
<?php
class Pages extends CI_Controller {

        public function view($page = 'home'){
            
        }
}
```

Т.е. данный контроллер будет работать по пути

```
http://example.com/index.php/pages/view
```

Тогда нужно добавить функцию index в контроллер

```php
<?php
class Pages extends CI_Controller {

        public function view($page = 'home'){
            
        }
        
        public function index($page = 'home'){
            
        }
}
```

**Подгружаем вьюхи**

В application/views создадим файлы header.php и footer.php

```php
   $this->load->view('templates/header', $data);
   $this->load->view('pages/'.$page, $data);
   $this->load->view('templates/footer', $data);
```

**Настройка путей**

Заходим в config/routes.php

$route['default_controller'] = 'pages/view';

Сейчас все запуски происходят через index.php

example.com/index.php/news/view/home2

Для того, чтобы убрать index.php из адресов создаем .htaccess в корне (а не в папке application)

```htaccess
RewriteEngine On
Options +FollowSymlinks
RewriteBase /

RewriteCond %{REQUEST_FILENAME} !-f
RewriteCond %{REQUEST_FILENAME} !-d
RewriteRule ^.*$ index.php [NC,L]
```
**Передадим данные во вьюху**

Дописываем в контроллер до загрузки вьюхи

```php
$data["x"] = 'test';
```

А во view добавляем

```php
<?php echo $x ?>
```
или можем записать короче

```
<?=$x?>
```

**Работа с моделями**

Не так вы ее себе представляли!? :)


Создаем таблицу news

В PHPMyAdmin создаем

```sql
CREATE TABLE news (
        id int(11) NOT NULL AUTO_INCREMENT,
        title varchar(128) NOT NULL,
        slug varchar(128) NOT NULL,
        text text NOT NULL,
        PRIMARY KEY (id),
        KEY slug (slug)
);
```

```php
class News_model extends CI_Model {

        public function __construct()
        {
                $this->load->database();
        }
}
```

application/config/database.php

Нам необходимо прописать

```
   'hostname' => 'localhost',
   'username' => 'root',
   'password' => '',
   'database' => 'database_name',
```



Добавим метод в news_model

```php
public function get_news($slug = FALSE)
{
        if ($slug === FALSE)
        {
                $query = $this->db->get('news');
                return $query->result_array();
        }

        $query = $this->db->get_where('news', array('slug' => $slug));
        return $query->row_array();
}
```

Модифицируем наш контролер

```php
class News extends CI_Controller {

        public function __construct()
        {
                parent::__construct();
                $this->load->model('news_model');
                $this->load->helper('url_helper');
        }

        public function index()
        {
                $data['news'] = $this->news_model->get_news();
        }

        public function view($slug = NULL)
        {
                $data['news_item'] = $this->news_model->get_news($slug);
        }
}
```


Поменяем метод index на

```php
public function index()
{
        $data['news'] = $this->news_model->get_news();
        $data['title'] = 'News archive';

        $this->load->view('header', $data);
        $this->load->view('index', $data);
        $this->load->view('footer');
}
```


Создаем во views index.php

```php
<h2><?php echo $title; ?></h2>

<?php foreach ($news as $news_item): ?>

        <h3><?php echo $news_item['title']; ?></h3>
        <div class="main">
                <?php echo $news_item['text']; ?>
        </div>
        <p><a href="<?php echo 'news/'.$news_item['slug']; ?>">View article</a></p>

<?php endforeach; ?>
```

Теперь вернемся к нашему контроллеру и изменим у него метод views

```php
public function view($slug = NULL)
{
        $data['news_item'] = $this->news_model->get_news($slug);

        if (empty($data['news_item']))
        {
                show_404();
        }

        $data['title'] = $data['news_item']['title'];

        $this->load->view('header', $data);
        $this->load->view('view', $data);
        $this->load->view('footer');
}
```


Как видите нам нужна новая вьюха view, придется создать и ее

Добавим в нее следующий код

```php
<?php
echo '<h2>'.$news_item['title'].'</h2>';
echo $news_item['text'];
```


Возвращаемся к путям application/config/routes.php

```php
$route['news/(:any)'] = 'news/view/$1';
$route['news'] = 'news';
$route['default_controller'] = 'news/index';
```

Теперь если все указали правильно – должно работать


////////////////////////////////////////

**Работа с формами**
$config['base_url'] = 'http://localhost/sms/';


**Загрузка картинок**

**Практика:**

1. Сделать контроллер, который бы считал сумму двух чисел.

2. Используя views собрать сайт с хедером и контентом.

3. Сделать контроллер, который бы выводил список работников с их заработной платой.




