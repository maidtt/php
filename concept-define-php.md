## 1. Lập trình hướng đối tượng là gì?

- Lập trình hướng đối tượng viết tắt OOP là viết tắt của Bbject-Briented Programming.
- Hiểu một cách đơn giản thì "Lập trình hướng đối tượng" là một kĩ thuật lập trình cho phép lập trình viên tạo ra các đối tượng trong code để trừu tượng hóa các đối tượng ngoài thế giới thực. Như mỗi sản phẩm, mỗi user… là mỗi đối tượng.

---

## 2. Một số khái niệm cơ bản trong OOP

Trong OOP có 1 vài khái niệm quan trọng cần phải nắm chắc:

- Object: đối tượng
- Class: lớp
- Properties: thuộc tính
- Methods (or Functions ) :Phương thức (hoặc hàm)

---

## 3. Ôn lại những điều quan trọng cần lưu ý

#### 3.1 Biến (variable)

- Tất cả các biến trong PHP được biểu thị bằng một ký hiệu đô la đứng đầu ($).

```php
$name // biến có tên là name
$price // biến có tên là price
```

- Giá trị của một biến là giá trị của lần gán gần đây nhất.

```php
$name = "FPT";
echo $name; // FPT
$name = "FPT Polytechnic";
echo $name; // FPT Polytechnic
```

- Các biến được gán với toán tử =
- Một biến không biết trước nó sẽ được sử dụng để lưu trữ một số hay một chuỗi ký tự.

```php
$name = "Fpoly";
var_dump($name) // string(5) "Fpoly"
$name = 1; // int(1)
```

#### 3.2 Hàm (function)

> Hiểu đơn giản thì hàm là 1 đoạn mã thực hiện xử lý 1 công việc nào đó.

- Khai báo hàm và gọi hàm

```php
// Định nghĩa hàm php
function writeMessage() {
  echo "FPT Polytechnic";
}
// Gọi hàm php
writeMessage(); // FPT Polytechnic
```

- Khai báo hàm có tham số truyền vào

```php
function Sum($num1, $num2){
  $sum = $num1 + $num2;
  echo "Tổng 2 số là: $sum";
}
Sum(10,30); // Tổng 2 số là: 40

```

- Khai báo hàm có tham số truyền vào và trả về 1 giá trị

```php
function Sum($num1, $num2){
  $sum = $num1 + $num2;
  return  $sum;
}
$returnValue = Sum(10,30);
echo "Tổng 2 số là: $returnValue"; //Tổng 2 số là: 40


```

---

## 4. Tổng quan cú pháp

- Khai báo biến và các kiểu dữ liệu thường dùng

  ```php
  // biến ở bên trái, biểu thức được đánh giá ở bên phải.
  // nên đọc, diễn tả từ phải sang trái
  $name = "FPT Polytechnic" // gán 1 chuỗi vào biến name
  $price = 2000 // gán 1 số và biến price
  ```

- Khai báo class có thuộc tính và \_\_constructor

  > \_\_constructor() là một hàm tạo cho phép khởi tạo các thuộc tính trong class khi tạo đối tượng.
  > Hàm tạo luôn chạy đầu tiên khi khởi tạo đối tượng, nếu ta không khai báo thì nó ngầm định sinh ra 1 \*\*contructor

  - Tạo class không có \_\_constructor

  ```php
  class Car{
    public $name;
  }
  ```

  - Tạo class có \_\_constructor với 3 thuộc tính

  ```php
  class Car {

    // field (thuộc tính) name với trạng thái public
    public $name;
    // field (thuộc tính) color với trạng thái protected
    protected $color;
    // field (thuộc tính) price với trạng thái protected
    private $price;
    public function __construct($name, $color, $price) {

      // $this có thể hiểu nó chính là class chứa nó
      // $this->name <=> Car->name
      $this->name = $name;
      $this->color = $color;
      $this->price = $price;
    }
  }
  ```

  Ví dụ trên ta gặp từ khóa $this. Vậy $this là gì?

  > $this cho phép ta truy cập vào các thuộc tính, phương thức trong phạm vi class

- Khởi tạo đối tượng từ class Car

  > Class Car có hàm \_\_constructor nhận vào 3 tham số nên khi khởi tạo đối tượng ta phải truyền vào 3 đối số cho nó.
  > Truyền đối số theo thứ tự khởi tạo thì ta mới có kết quả mong muốn

  ```php
  $mercedes = new Car('mercedes', 'red', 1000)
  echo mercedes->name; // mercedes
  echo mercedes->color; // Error: Cannot access protected property Car::$color
  echo mercedes->price; // Error: Cannot access protected property Car::$color
  ```

  Như ta thấy ví dụ trên ta không thể truy cập trực tiếp tới các thuộc tính có trạng thái là **protected** và **private**, đó là cách bảo mật dữ liệu bên trong đối tượng. Vậy làm như thế nào để ta có thể lấy giá trị đó ra để hiển thị hay sử dụng?

  Lúc này ta cần đến sự trợ giúp của các phương thức.

- Tạo class có thêm phương thức và khởi tạo đối tượng

  ```php
  class Car {
    public $name;
    protected $color;
    private $price;
    public function __construct($name, $color, $price) {
      $this->name = $name;
      $this->color = $color;
      $this->price = $price;
    }
    public function getColor(){
      return $this->color;
    }
    public function getPrice(){
      return $this->price;
    }
  }

  $mercedes = new Car('mercedes', 'red', 1000)
    echo mercedes->getColor(); // red
    echo mercedes->getPrice(); // 1000
  ```

  Nếu giờ ta muốn thay đổi giá trị **color** từ **_red_** thành **_green_** của đối tượng mercedes thì phải làm sao? Dễ thôi, ta chỉ cần tạo ra hành động tác động lên thuộc tính **color** bằng cách thêm phương thức setColor bên trong class **Car** như sau là được nhé:

  ```php
  // Muốn thay đổi giá trị thì chắc chắn ta phải truyền vào 1 tham số rồi,
  public function setColor($colorChange) {
    return $this->color = $colorChange;
  }
  // Thay đổi màu đối tượng mercedes, setColor là function public
  echo $mercedes->setColor("green"); // green
  ```

  Thật dễ dàng phải không nào? Ngoài đời thực thì xe sẽ có nhiều loại, như xe thể thao, xe mui trần... nếu ta tạo ra các lớp xe đó thì bị trùng lặp lại code (**\$name**, **\$price**...) rất nhiều, đó là điều tối kị trong lập trình. Vậy làm thế nào để ta sử dụng lại các thuộc tính, phương thức từ class **_Car_**?

  **Lập trình OOP** cho phép ta **_kế thừa_** lại các thuộc tính, phương thức từ class khác, như thế ta chỉ cần viết code 1 lần tromg lớp cha, sau đó sử dụng code trong cả lớp cha và lớp con.

  _Mình có ví dụ sau:_

  ```php
  // Class cha
  class Car {
  // thuộc tính private
    private $model;

    // phương thức thay đổi giá trị $model
    public function setModel($model)
    {
      $this -> model = $model;
    }

    public function hello()
    {
      return "beep! Tôi là: " . $this -> model;
    }
  }
  // Class SportsCar (clas con) kế thừa từ class Car (class cha)
  class SportsCar extends Car {

  }

  $sportsCar1 = new SportsCar();
  $sportsCar1 -> setModel('Mercedes Benz');
  echo $sportsCar1 -> hello(); // beep! Tôi là: Mercedes Benz
  ```

  Phải chăng **_kế thừa_** (**_Inheritance_**) chỉ có mỗi như trên là hết? oh Nooo.. đó chỉ là basic nhất để ta làm quen với kế thừa. Thế nó còn những thứ gì hay ho hơn không?
  Bài viết tới đây khá dài rồi nên mình xin phép phần sau mình sẽ nói rõ hơn về 4 tính chất của OOP nếu trên nhé ;)
  Các bạn cần làm về chủ đề gì trong php thì hãy comment cho mình biết nhé.

#### Cảm ơn các bạn đã theo dõi!
