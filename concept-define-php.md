## 1. Lập trình hướng đối tượng là gì?

- Lập trình hướng đối tượng viết tắt OOP là viết tắt của Object-Oriented Programming.
- Hiểu một cách đơn giản thì "Lập trình hướng đối tượng" là một kĩ thuật lập trình cho phép lập trình viên tạo ra các đối tượng trong code để trừu tượng hóa các đối tượng ngoài thế giới thực. Như mỗi sản phẩm, mỗi user… là mỗi đối tượng.

---

## 2. Ưu điểm của lập trình hướng đối tượng

- Dễ dàng quản lý code khi có sự thay đổi chương trình.
- Dễ mở rộng dự án.
- Tiết kiệm được tài nguyên đáng kể cho hệ thống.
- Có tính bảo mật cao.
- Có tính tái sử dụng cao.

---

## 3. Một số khái niệm (thuật ngữ) cơ bản trong OOP

Trong OOP có 1 vài khái niệm quan trọng cần phải nắm chắc:

- **Object**: đối tượng
- **Class**: lớp
- **Properties**: thuộc tính
- **Methods** (or Functions ) :Phương thức (hoặc hàm)
- keyword **$this**
- Hàm tạo **\_\_construct()**

### <span style="color:green">Class: lớp</span>

- Class giống như 1 bản thiết kế (khuôn mẫu) để tạo ra các đối tượng có đặc tính giống nhau
- Class gồm có 2 thàh phần chính là: Thuộc tính (properties) và phương thức (methods)

<span style="color:blue; font-size:19px">Tạo class.</span>

```php
class Car {
  // The code
}
```

<span style="color:blue; font-size:19px">Thêm thuộc tính vào class.</span>

```php
class Car {
  // Tạo thuộc tính name, price cho class Car
  var $name;
  var $price;
}
```

<span style="color:blue; font-size:19px">Thêm phương thức vào class.</span>

```php
class Car {
  // Tạo thuộc tính name, price cho class Car
  var $name;
  var $price;

  // Tạo phương thức hello class Car
  public function hello(){

  }
}
```

### <span style="color:green">Object: đối tượng</span>

- Đối tượng có thể hiểu là 1 thực thể: người, vật, hay 1 bảng dữ liệu...
- Một đối tượng bao gồm 2 thông tin : Thuộc tính và Phương thức
  - Thuộc tính là những thông tin, đặc điểm của đối tượng. _Ví dụ như một người sẽ có họ tên, ngày sinh, màu da, kiểu tóc,..._
  - Phương thức là những thao tác, hành động được thực hiện trên đối tượng đó hay đối tượng đó có thể thực hiện. _Ví dụ: một người sẽ có thể hành động đi, nói, ăn, uống..._

> Lưu ý: một đối tượng không nhất thiết phải có thuộc tính hay phương thức, tùy vào mục đích sử dụng của lập trình viên

<span style="color:blue; font-size:19px">Tạo object (đối tượng) từ class (lớp).</span>

- Ta dùng từ khóa **new** để khởi tạo object từ 1 class

```php
class Car {
  // Tạo thuộc tính name, price cho class Car
  var $name = "bwm";
  var $price = "black";

  // Tạo phương thức hello class Car
  public function hello(){

  }
}
$bwm = new Car();
```

<span style="color:blue; font-size:19px">Lấy ra các thuộc tính và phương thức từ object.</span>

- Các **_thuộc tính_** và **_phương thức_** của **_class_** được chia sẻ cho các **_object_** tạo ra từ nó.

```php
class Car {
  // Tạo thuộc tính name, price cho class Car
  var $name = "bwm";
  var $price = "black";

  // Tạo phương thức hello class Car
  public function hello(){
    echo "Tôi tên là: " . $this->name;
  }
}
$bwm = new Car();
echo $bwm->name; // bwm
echo $bwm->hello(); // Tôi tên là: bwm
```

### <span style="color:green">Từ khóa $this</span>

- Từ khóa **$this** cho phép ta có quyền truy cập và sử dụng các thuộc tính và phương thức trong phạm vi của **class**.
- Hiểu đơn giản thì nó tượng trưng cho chính class chứa nó.

```php
class Car {
  var $price = 10000;

  public function hello(){
    echo "Tôi có giá: $" . $this->price;
  }
}
$bwm = new Car();
echo $bwm->hello(); // Tôi có giá: $10000
```

### <span style="color:green">Hàm tạo \_\_constructor</span>

- **\_\_construct()** kiểu hàm đặc biệt mà sẽ được gọi tự động bất cứ khi nào có một sự tạo thành đối tượng từ một Class. Hay hiểu đơn giản thì nó là khuôn mẫu để tạo ra các đối tượng từ class
- Hàm tạo luôn chạy đầu tiên khi khởi tạo đối tượng, nếu ta không khai báo thì nó ngầm định sinh ra hàm **\_\_contruct**.

<span style="color:blue; font-size:19px">Tạo class không có \_\_constructor().</span>

```php
class Car{
  var $name = "Mercedes";
}
$mercedes = new Car();
echo $mercedes->name; //Mercedes
```

<span style="color:blue; font-size:19px">Tạo class có \_\_constructor().</span>

```php
class Car{
  var $name;
  public function __construct($name){

    // Gán tham số truyền vào cho thuộc tính name của class Car
    $this->name = $name;
  }
}
// Nếu khai báo k truyền đủ đối số như hàm tạo __construc thì sẽ báo lỗi
$mercedes = new Car(); // Uncaught ArgumentCountError: Too few arguments to function Car::__construct()

// Vì thế ta cần chú ý khi khởi tạo đối tượng
$mercedes = new Car("Audi");
echo $mercedes->name; // Auti
```

<span style="color:blue; font-size:19px">Cách viết hàm \_\_contruct không bị lỗi khi khởi tạo</span>

```php
class Car{
  var $name;

  // Ta sử dụng tham số mặc định cho hàm khởi tạo
  public function __construct($name = null){
    $this->name = $name;
  }
}
$mercedes = new Car();
echo $mercedes->name; //
```

> - Hàm tạo \_\_construct giúp chúng ta khởi tạo nhiều đối tượng với các thuộc tính khác nhau.
> - Vì hàm tạo luôn được chạy đầu tiên khi khởi tạo 1 đối tượng mới nên nó được sử dụng rất nhiều để giải nhiều bài toán khác nhau. Để hiểu rõ hơn mình sẽ nói ở phần khác nhé!

---

## 4. Bài tập rèn luyện

- Bài 1: Viết một class đơn giản in ra màn hình "Xin chào tôi đến từ FPT Polytechnic", trong đó "FPT Polytechnic" là đối số truyền vào của 1 phương thức.
- Bài 2: Viết một class Student gồm các thuộc tính như name, age, phone, address, majored, class... và các phương thức lấy in ra màn hình giá trị các thuộc tính đó
- Bài 3: Viết một Class Calculator, khởi tạo với 2 tham số truyền vào, sau đó thêm các phương thức tính phép cộng, trừ , nhân, chia và trả về kết quả.

### Chúc các bạn học tập thật tốt!!!

### Cảm ơn các bạn đã theo dõi!
