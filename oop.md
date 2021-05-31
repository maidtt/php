## 1. Lập trình hướng đối tượng là gì?

- Lập trình hướng đối tượng viết tắt OOP là viết tắt của Bbject-Briented Programming.
- Hiểu một cách đơn giản thì "Lập trình hướng đối tượng" là một kĩ thuật lập trình cho phép lập trình viên tạo ra các đối tượng trong code để trừu tượng hóa các đối tượng ngoài thế giới thực. Như mỗi sản phẩm, mỗi user… là mỗi đối tượng.

---

## 2. Ưu điểm của lập trình hướng đối tượng

- Dễ dàng quản lý code khi có sự thay đổi chương trình.
- Dễ mở rộng dự án.
- Tiết kiệm được tài nguyên đáng kể cho hệ thống.
- Có tính bảo mật cao.
- Có tính tái sử dụng cao.

---

## 3. Một số khái niệm cơ bản trong OOP

Trong OOP có 4 khái niệm quan trọng cần phải nắm chắc:

- Object: đối tượng
- Class: lớp
- Properties: thuộc tính
- Methods (or Functions ) :Phương thức (hoặc hàm)

#### **_3.1. Object (đối tượng_**

- Đối tượng có thể hiểu là 1 thực thể: người, vật, hay 1 bảng dữ liệu...
- Một đối tượng bao gồm 2 thông tin : Thuộc tính và Phương thức - Thuộc tính là những thông tin, đặc điểm của đối tượng. Ví dụ như một người sẽ có họ tên, ngày sinh, màu da, kiểu tóc,... - Phương thức là những thao tác, hành động được thực hiện trên đối tượng đó hay đối tượng đó có thể thực hiện.
  _Ví dụ: một người sẽ có thể hành động đi, nói, ăn, uống... một ngôi nhà có thể được thay đổi màu sơn hay vị trí các đồ dùng nội thất..._ >
  > Lưu ý: một đối tượng không nhất thiết phải có thuộc tính hay phương thức, tùy vào mục đích sử dụng của lập trình viên

#### **_3.2. Class (lớp)_**

- Các đối tượng có các đặc tính tương tự nhau được gom lại thành 1 lớp đối tượng.
- Class giống như 1 bản thiết kế (khuôn mẫu) để tạo ra các đối tượng có đặc tính giống nhau.
- Bên trong class cũng có 2 thành phần chính là thuộc tính và phương thức.

> Ví dụ: Trước khi tạo ra 1 đối tượng sản phẩm, bạn cần tạo ra class có tên **product**. Trong class này bạn khai báo các **thuộc tính** có name, price... khai báo các **phương thức** như getName (lấy ra tên sản phẩm), setName (thay đổi tên sản phẩm), getPrice (lấy ra giá sản phẩm), setPrice (thay đổi giá sản phẩm)

---

## 4. Các tính chất của lập trình hướng đối tượng

#### **_4.1. Tính trìu tượng (abstraction)_**

Trong lập trình OOP, tính trừu tượng nghĩa là chọn ra các thuộc tính, phương thức của đối tượng cần cho việc giải quyết bài toán đang lập trình. Vì một đối tượng có rất nhiều thuộc tính phương thức, nhưng với bài toán cụ thể không nhất thiết phải chọn tất cả.

> Để hiểu rõ về tính trìu tượng chúng ta có thể tìm hiểu về **_Abstract class_** và **_Interface_**. Bài này đang nói về cơ bản hướng đối tượng nên mình sẽ nói chi tiết hơn về phần này ở 1 bài sau nào đó nhé.

#### **_4.2. Tính đóng gói (Encapsulation)_**

- Các dữ liệu và phương thức có liên quan với nhau được đóng gói thành các lớp để tiện cho việc quản lý và sử dụng.

- Đóng gói làm che giấu, bảo mật một số thông tin để bên ngoài không thể thay đổi hay lấy ra tùy tiện.

> Sử dụng các trạng thái - quyền truy cập (modifier) cho thuộc tính và phương thức cần được che giấu. **_public_** / **_protected_** / **_private_**
>
> - Public: có thể sử dụng phạm vi ngoài class. Nghĩa là ta có thể truy xuất trực tiếp từ 1 đối tượng được tạo ra từ class đó
> - Protected: chỉ có thể sử dụng trong các _"dòng họ"_ được **_kế thừa_** từ nó
> - Private: chỉ sử dụng được trong phạm vi class đó (được phân cách bởi dấu { } )

#### **_4.3. Tính kế thừa (Inheritance)_**

Nó cho phép xây dựng một lớp mới dựa trên một lớp có sẵn. Nghĩa là lớp cha có thể chia sẻ thuộc tính và phương thức cho lớp con, lớp con có thể mở rộng thêm các thuộc tính và phương thức riêng của nó.

> Kết hợp với tính đóng gói: Ta có **_class B_** kế thừa từ **_class A_**, **_class B_** muốn sử dụng các thuộc tính và phương thức của **_class A_** thì các thuộc tính phương thức đó phải có trạng thái là **_public_** hoặc **_protected_**

#### **_4.4 Tính đa hình (Polymorphism)_**

- Tính đa hình là một hành động có thể được thực hiện bằng nhiều cách khác nhau.
- Hiểu một cách đơn giản hơn: Tính đa hình cho phép các lớp con có thể ghi đè (override) các thuộc tính hoặc phương thức từ lớp cha.

## 5. Static methods (hàm static). Cách dùng từ khóa static::method() với self::method() - keywork: parent

- Phương thức static có thể gọi trực tiếp không cần khởi tạo đối tượng từ 1 lớp.
- $this không sử dụng được trong các phương thức static
- Static: Truy cập tới đối tượng hiện tại (có thể hiểu như $this)
- Self: Truy cập tới class khai báo nó
  _Để hiểu rõ hơn thì mình có các ví dụ sau:_

Nếu trong cùng đối tượng thì cả 2 keywords này đều như nhau

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

Ta thử tiếp ví dụ sử dụng kế thừa

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

$a = new NguoiLon();
$a->getName();
// ConNguoi
// NguoiLon
```

Ví dụ trên thì ta thấy nó cho ra 2 kết quả khác nhau. Vậy với static::method() ta có thể hiểu nó như từ khóa $this - truy cập tới class hiện tại, selt::method() thì truy cập tới class đã định nghĩa ra nó

**Các bạn có thể tìm hiểu thêm các khai niệm khác như:**

- Member Variable
- Member function
- parent::method()
- Constructor
- Destructor

Nguồn tham khảo:

- [https://viblo.asia/p/lap-trinh-huong-doi-tuong-oop-trong-php-phan-1-gGJ59gyaZX2](https://viblo.asia/p/lap-trinh-huong-doi-tuong-oop-trong-php-phan-1-gGJ59gyaZX2)
- [https://tutorials.supunkavinda.blog/php/oop-intro](https://tutorials.supunkavinda.blog/php/oop-intro)
- [https://code.tutsplus.com/tutorials/basics-of-object-oriented-programming-in-php--cms-31910](https://code.tutsplus.com/tutorials/basics-of-object-oriented-programming-in-php--cms-31910)

## Kết luận

Trên đây là một số kiến thức mình đúc kết được trong quá trình học tập và tự tìm hiểu, nếu có gì sai sót hay cần bổ sung thêm thì các bạn comment cho mình biết nha. Cảm ơn các bạn đã theo dõi.
