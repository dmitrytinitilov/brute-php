# # Интерфейсы и абстрактные классы

Абстрактный класс – класс, который содержит хотя бы один абстрактный метод, то есть метод без реализации.



```php
abstract class AbstractClass
{
   /* Данный метод должен быть определён в дочернем классе */
    abstract protected function getValue();
    abstract protected function prefixValue($prefix);

   /* Общий метод */
    public function printOut() {
        print $this->getValue() . "\n";
    }
}
```

От абстрактного класса мы не можем создать объект, но можем создать неабстрактного наследника. При этом нужно «реализовать» абстрактный метод

```php
class ConcreteClass1 extends AbstractClass
{
    protected function getValue() {
        return "ConcreteClass1";
    }

    public function prefixValue($prefix) {
        return "{$prefix}ConcreteClass1";
    }
}
```


```php
interface iTemplate
{
    public function setVariable($name, $var);
    public function getHtml($template);
}


// Реализуем интерфейс
// Это сработает нормально
class Template implements iTemplate
{
    private $vars = array();
  
    public function setVariable($name, $var)
    {
        $this->vars[$name] = $var;
    }
  
    public function getHtml($template)
    {
        foreach($this->vars as $name => $value) {
            $template = str_replace('{' . $name . '}', $value, $template);
        }
 
        return $template;
    }
}
```

**Практика:**
1.	Interface Unit ->abstract class Warrior -> Knight, Mage	

