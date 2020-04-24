# \# Интерфейсы и абстрактные классы

**Абстрактные классы**

Абстрактный класс – класс, который содержит хотя бы один абстрактный метод, то есть метод без реализации.

```php
abstract class AbstractClass
{
   /* Данный метод должен быть определён в дочернем классе */
    abstract protected function getValue();
    abstract protected function prefixValue($prefix);

   /* Общий метод */
    public function printOut() {
        print $this->getValue() . "\n";
    }
}
```

От абстрактного класса мы не можем создать объект, но можем создать неабстрактного наследника. При этом нужно «реализовать» абстрактный метод.

Из-за невозможности создать объект от абстрактного класса следует и отсутствие возможности определить конструктор в абстрактном классе.

```php
class ConcreteClass1 extends AbstractClass
{
    protected function getValue() {
        return "ConcreteClass1";
    }

    public function prefixValue($prefix) {
        return "{$prefix}ConcreteClass1";
    }
}
```

**Интерфейсы**

Задача интерфейсов определить public-методы классов наследников(это будет крайне важно, если речь идет о полиморфизме объектов).

```php
interface iTemplate
{
    public function setVariable($name, $var);
    public function getHtml($template);
}


Мы можем создать от интерфейса класс, при этом говорят, что класс "реализует" интерфейс

class Template implements iTemplate
{
    private $vars = array();

    public function setVariable($name, $var)
    {
        $this->vars[$name] = $var;
    }

    public function getHtml($template)
    {
        foreach($this->vars as $name => $value) {
            $template = str_replace('{' . $name . '}', $value, $template);
        }

        return $template;
    }
}
```

Обратите внимание, что в интерфейсе мы не можем задавать свойства, что было доступно нам в абстрактных классах.

**Практика:**  
1.    Interface Unit -&gt;abstract class Warrior -&gt; Knight, Mage

