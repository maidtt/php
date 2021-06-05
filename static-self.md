## 1. Static keyword

Việc khai báo các thuộc tính hoặc phương thức của lớp với từ khóa static làm cho chúng có thể truy cập được mà không cần khởi tạo lớp. Chúng cũng có thể được truy cập trong một đối tượng được khởi tạo.

Thuộc tính và phương **static** được truy cập bằng [toán tử **::**](https://www.php.net/manual/en/language.oop5.paamayim-nekudotayim.php) và không thể truy cập thông qua toán tử đối tượng ( -> ).

### 1.1 Static method

Vì các **phương thức staic** có thể gọi được mà không cần khởi tạo 1 dối tượng nên từ khóa **$this** khôn g sử dụng được bên trong các phương thức được khai báo là **static**.

```php
class Product {
    public static function aStaticMethod() {
      echo "Hello world"
    }
}

Product::aStaticMethod(); // Hello World
```

### 1.2 Static properties

Có thể tham chiếu đến lớp bằng cách sử dụng một biến. Giá trị của biến không được là từ khóa (ví dụ: self, mẹ và static).

```php
class Foo
{
    public static $my_static = 'foo';

    public function staticValue() {
        return $this->$my_static; // Undefined "variable": my_sta  tic
    }
}

echo Foo::$my_static . "\n"; // foo

$foo = new Foo();
print $foo->staticValue() . "\n"; // Undefined property: Foo::$
print $foo->my_static . "\n";      // Undefined "Property" my_static
```

> Từ khóa $this không sử dụng với thuộc tính và phương thức **static**

## 2. Self keyword

Như ví dụ trên ta thấy không truy cập được vào **thuộc tính static** với **$this**. Vậy làm thế nào để tiếp cận (sử dụng) các thuộc tính **static** trong lớp? lúc này ta cần sử dụng **static** và **self**

_Ví dụ với self_

```php
class Number {
  public static $num = 0;
  public $numNotStatic = 1;
  public function get(){
      echo "tôi là function không static \n";
  }
  static public function getWithStatic(){
      echo "tôi là function static \n";
  }

  static public function getUseSelf()
  {
    echo self::$num; // 0
    echo static::$num; // 0

    echo self::get(); // tôi là function không static
    echo static::get(); // tôi là function không static

    echo self::getWithStatic(); // tôi là function static
    echo static::getWithStatic(); // tôi là function static

    echo self::$numNotStatic; // Uncaught Error: Access to undeclared static property: Number::$numNotStatic
    echo static::$numNotStatic; // Uncaught Error: Access to undeclared static property: Number::$numNotStatic
  }
}

Number::getUseSelf();


```

> **self** và **static** có thể gọi các phương thức không phải là static (non-static) và các hằng số **const**. Nó không thể truy cập tới **Thuộc tính** không phải là static.

## 3. Khác nhau giữa static và self

_Mình có ví dụ sau:_

```php
class ConNguoi
{
    private static $name = 'ConNguoi';

    public static function getName()
    {
        echo self::$name;
        echo '<br>';
        echo static::$name;
    }
}

ConNguoi::getName();

//ConNguoi
//ConNguoi
```

Mình sử dụng **static** và **self** trong cùng 1 class thì kết quả đều cho giá trị giống nhau. Chúng đều truy cập được vào thuộc tính **static**. Phải chẳng 2 keyword này có ý nghĩa như nhau?

Ví dụ dưới đây theo mình xin sử dụng 1 chút về tính chất **Kế Thừa** trong OOP để các bạn thấy rõ hơn sự khác nhau của **static** và **self**

```php
class ConNguoi
{
    protected static $name = 'ConNguoi';

    public function getName()
    {
        echo self::$name;
        echo '<br>';
        echo static::$name;
    }
}

class NguoiLon extends ConNguoi
{
// ghi đè (override) thuộc tính của lớp cha
    protected static $name = 'NguoiLon';
}

$person = new NguoiLon();
$person->getName();
// ConNguoi
// NguoiLon
```

Các bạn thấy khác nhau rồi chứ?

- Ta thấy function **getName** trong class **ConNguoi** thực hiện hiển thị ra màn hình giá trị thuộc tính **static $name**.
- Tiếp theo mình tạo ra class **NguoiLon** kế thừa từ class **ConNguoi** nên mình có thể sử dụng được các **thuộc tính** và **phương thức** từ class **ConNguoi**
- Sau đó khởi tạo đối tượng **person** từ class **NguoiLon** và gọi phương thức **getName()**.
- Kết quả in ra ta có thể biết
  - **self** truy cập tới các **thuộc tính** và **phương thúc** bên trong **class định nghĩa ra nó**
  - **static** truy cập tới các **thuộc tính** và **phương thúc** bên trong **class hiện tại của nó** (cách hoạt động giống như từ khóa **$this**)

> - Thuộc tính và Phương thức static có thể gọi trực tiếp không cần khởi tạo đối tượng từ 1 lớp.
> - **$this** không sử dụng được trong các phương thức static
> - **Static**: Truy cập (tham chiếu) tới class hiện tại (có thể hiểu như $this)
> - **Self**: Truy cập tới class khai báo (định nghĩa) ra nó

## 4. Parent keyword

- **$this** đại diện cho của **lớp hiện tại**
- **self::** đại diện cho chính **lớp tạo ra nó**.
  Bạn không thể sử dụng toán tử $this bên ngoài lớp và cả trong lớp mở rộng để nhận các giá trị của lớp cha.

```php
class ParentClass {
    const CLSPARENT = "Parent";
    const A = 1;
    function __construct()
    {
        echo "Tôi là Constructor " . self::CLSPARENT . "\n";
    }
}

class ChildClass extends ParentClass {
    const CLSCHILD = "Child";
    const A = 2;
    function __construct()
    {
        // self::__construct(); // nó gọi tới chính __construct trong class chứa nó nên sẽ rơi vào tình trạng đệ quy và có thể bị treo máy đó nhé, bạn có thể thử :)))

        parent::__construct(); // Gọi tới phương thức cha của nó
        echo "Gọi tới class " . parent::CLSPARENT . "\n";
        echo "Tôi là constructor " . self::CLSCHILD ."\n";
        echo parent::A ."\n";
        echo self::A;
    }
}
$obj = new ChildClass();

// Tôi là Constructor Parent
// Gọi tới class Parent
// Tôi là constructor Child
// 1
// 2
```

> Để truy cập một thuộc tính hoặc phương thức trong lớp cha đã bị ghi đè trong lớp con bằng cách sử dụng từ khóa **parent::**.

_Mình có ví dụ cụ thể hơn dưới đây:_

```php
class ParentClass{
    var $name;
    public function __construct($name){
        $this->name = $name;
    }
    public function getInfo() {
        return $this->name;
    }
}
class ChildClass extends ParentClass {
    var $age;
    public function __construct($name, $age){
        parent::__construct($name);
        $this->age = $age;
    }
    public function getInfo() {
        return "Tôi tên là : " . $this->name . ". Năm nay tôi: " . $this->age;
    }
}
$person = new ChildClass('john', 20);
echo $person->getInfo();
// Tôi tên là : john. Năm nay tôi: 20
```

## 5. Khác nhau giữa $this self:: và parent::

- **$this**

  - $this đề cập (truy cập) đến đối tượng
  - $this không trỏ đến bất kỳ đối tượng hoặc lớp nào khác.

- **self::**

  - self:: tham chiếu đến chính lớp tạo ra nó, không trỏ đến bất kỳ đối tượng nào.

  - self:: bạn có thể truy cập các thuộc tính tĩnh và phương thức tĩnh của lớp hiện tại.

- **parent::**

  - parent:: là tham chiếu đến lớp cha.
  - parent:: giúp bạn có thể truy cập các thuộc tính tĩnh và phương thức tĩnh của lớp cha.

> Với việc sử dụng self và parent, bạn cho phép tránh tham chiếu rõ ràng lớp theo tên.
