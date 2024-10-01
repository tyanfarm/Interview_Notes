# C#

### Object & Class
| Object | Class |
|:----------------|:---------------|
| Là thực thể được tạo ra từ Class | Là bản thiết kế, xác định thuộc tính và phương thức |

### Property & Field
- `Field (trường dữ liệu)`: là biến để lưu dữ liệu trong Struct và Class, có các quyền truy cập (public, protected, private, ...).

    + ```
        private string _name;
- `Property (Thuộc tính)`: Cung cấp getter và setter để đọc ghi dữ liệu từ `Field` an toàn.
    + ```
        public string Name {
            get { return _name; }  
            set { _name = value; }  
        }

- Với `C#` thì đã có `auto-implemented properties` (thuộc tính tự động).
    + ```
        public string Name {get; set;}



### Abstract Class & Interface 
- `Abstract Class` vừa giống `Class` vừa giống `Interface`. Giống `Class` ở chỗ có thể khai báo `field, const`, có thể implement thân hàm, có thể hỗ trợ `kế thừa & đa hình` (bằng `virtual method`). Giống `Interface` ở chỗ có thể khai báo các `phương thức ảo` (`abstract method`) để lớp con triển khai, là 1 bản thiết kế.

- Giống nhau: 
    + Đều không thể khởi tạo trực tiếp mà phải được thực thi bởi các lớp con kế thừa.
    + Đều có thể khai báo phương thức nhưng không thực hiện.
    + Đều có thể kế thừa nhiều interface.
- Khác nhau:

| Abstract Class | Interface |
|:----------------|:---------------|
| Khai báo được const, property  | Không khai báo được const, property |
| Có constructor, destructor | Không có constructor, destructor |
| Được dùng từ khóa `abstract` hoặc `virtual` ở method | `Không` được dùng từ khóa `abstract` hoặc `virtual` ở method |
| Implement các `abstract method` phải dùng từ khóa `override` | Khi lớp con kế thừa không dùng `override` để implement |
| Các phương thức có thể có thân hàm với `method thường` và không có thân hàm với `abstract method`. Method có từ khóa `access modifier` | Bắt đầu từ C# 8.0 trở đi thì các method của `Interface` có thể có các từ khóa `access modifier` và `khai báo thân hàm` |


### Virtual method & Abstract method
| Abstract method | Virtual method |
|:----------------|:---------------|
| Không được phép cài đặt | Được phép cài đặt |
| Các lớp con `bắt buộc` phải override | Các lớp con `không` bắt buộc phải override |
| Method phải nằm trong Abstract Class | Có thể ở bất kì class nào |

### Override & Overload & Hiding
| Override | Overload | Hiding
|:----------------|:---------------|:---------------|
| Kĩ thuật ghi đè phương thức ở `lớp cha` khi muốn định nghĩa lại ở lớp con. | Kĩ thuật cho phép có nhiều phương thức `cùng tên` nhưng `khác số lượng, kiểu dữ liệu` `tham số đầu vào` và có thể có `quyền truy cập` khác nhau. | Phương thức ở lớp con cùng tên với phương thức ở lớp cha và không ghi đè bằng `override` |
| Phương thức ở lớp cha cần có từ khóa `virtual`, `abstract` hoặc `override` | Xảy ra trong cùng 1 `class`. | Phương thức ở lớp cha là `virtual` hoặc `method thường` (vì abstract method bắt buộc phải override). 

- Ví dụ 1 class cha `Dog` và class con `BullDog`. Xét trường hợp `method` đều có ở class cha và class con. (`Dog dog = new BullDog()`).
- Khi `override` thì method ở lớp con là method của chính nó, nếu đứng ở class cha và gọi phương thức `override` ở lớp con thì method ở lớp con sẽ được gọi.
- Nhưng với `hiding` thì nếu gọi phương thức ở class cha thì phương thức ở `class cha` sẽ được gọi.

# Network

### 7 tầng mô hình OSI
- Physical (Tầng Vật Lý)
    + Xử lý truyền qua cáp quang hoặc vô tuyến

- Data Link (Tầng Liên Kết)
    + Đánh địa chỉ vật lý (địa chỉ MAC)
    + Thiết bị: Switch, Bridge

- Network (Tầng mạng)
    + Xử lý việc đánh địa chỉ IP
    + Định tuyến (routing)
    + Chuyển tiếp gói tin giữa các mạng khác nhau
    + Thiết bị: Router

- Transport (Tầng vận chuyển)
    + Đảm bảo dữ liệu được chuyển đi đáng tin cậy và không lỗi. 
    + Chia dữ liệu thành các đoạn nhỏ (segmentation)
    + Kiểm soát luồng dữ liệu (flow control)
    + Xử lý các yêu cầu về độ tin cậy (TCP) hoặc tốc độ (UDP)
    + Giao thức:
        + TCP (Transmission Control Protocol)
        + UDP (User Datagram Protocol)

- Session (Tầng phiên)
    + Quản lý các phiên làm việc giữa các thiết bị khác nhau
    + Giao thức:
        + NetBIOS (Network Basic Input/Output System)

- Presentation (Tầng trình bày)
    + Thực hiện mã hóa/giải mã, nén/giải nén, chuyển đổi định dạng dữ liệu giữa các hệ thống.
    + Giao thức:
        + SSL/TLS (Secure Socker Layer / Transport Layer Security)
        + ASCII
        + Các định dạng file (JPEG, JPG, PNG, ...)

- Application (Tầng ứng dụng)
    + Tầng để người dùng tương tác trực tiếp với ứng dụng
    + Giao thức: 
        - SMTP (Simple Mail Transfer Protocol)
        - FTP (File Transfer Protocol)
        - HTTP (HyperText Transfer Protocol)

### SSL / TLS là gì
- Đều là các giao thức dùng để mã hóa và bảo mật dữ liệu truyền qua mạng, đặc biệt là Internet.
- TLS là phiên bản nâng cấp của SSL, sửa các lỗ hổng và cung cấp các thuật toán mã hóa tốt hơn.
- Các chức năng:
    + Mã hóa
    + Xác thực thông qua chứng chỉ số (digital certificate)
    + Bảo vệ toàn vẹn dữ liệu bằng các mã băm như SHA (Secure Hash Algorithm)

### HTTP khác HTTPS như thế nào
- HTTP - HyperText Transfer Protocol
    + Dữ liệu không được mã hóa, không được xác thực
    + Giao tiếp qua cổng 80
- HTTPS - HyperText Transfer Protocol Secure
    + Là phiên bản bảo mật hơn của HTTP
    + Dữ liệu được mã hóa bằng SSL/TLS, được xác thực bằng chứng chỉ số (digital certificates)
    + Giao tiếp qua cổng 443
- HTTPS có thể chậm hơn HTTP vì phải qua các bước mã hóa và xác thực nhưng không đáng kể.

### TCP và UDP là gì
- TCP (Transmission Control Protocol)
    + Là giao thức hướng kết nối. Trước khi truyền dữ liệu, nó sẽ thiếp lập một kết nối giữa 2 thiết bị sau đó dữ liệu mới được truyền đi.
    + Đảm bảo dữ liệu được truyền tin toàn vẹn và đúng thứ tự. Nếu sai thì sẽ gửi lại gói tin.
    + Có kiểm soát luồng (flow control) và kiểm tra lỗi (error detection)
    + Thường được dùng cho các ứng dụng yêu cầu độ chính xác cao như STMP, FTP, HTTP/HTTPS

- UDP (User Datagram Protocol)
    + Là giao thức không kết nối. Nghĩa là không thiết lập kết nối trước khi truyền dữ liệu và các gói tin sẽ được gửi độc lập, không quan tâm có đến đích hay không.
    + Không đảm bảo thứ tự và toàn vẹn
    + Thường được dùng cho các ứng dụng yêu cầu tốc độ cao như livestream video, DNS, ...

### Socket & WebSocket
- `Socket` là 1 `giao diện ứng dụng` giúp các ứng dụng giao tiếp qua mạng, sử dụng các giao thức TCP hoặc UDP để truyền dữ liệu.
- `WebSocket` là 1 giao thức kết nối 2 chiều giữa máy chủ và máy khách qua 1 TCP duy nhất. Điểm khác so với `HTTP` là WebSocket cho phép truyền dữ liệu 2 chiều mà không cần đóng mở kết nối liên tục.

### Bắt tay 3 bước diễn ra như thế nào
- B1: Máy khách gửi gói `SYN` tới máy chủ để yêu cầu kết nối.
- B2: Máy chủ gửi gói `SYN-ACK` chứa 1 thông báo `ACK` xác nhận gói tin SYN của máy khách và 1 gói `SYN` mới từ máy chủ.
- B3: Máy khách gửi gói `ACK` để xác nhận đã nhận gói `SYN` từ máy chủ

- Sau 3 bước này thì kết nối TCP được thiết lập.

# Database

### UUID là gì
- UUID (Universally Unique Identifier) - định danh duy nhất
- Kích thước 16 bytes - 32 kí tự

### Transaction Database - Giao dịch cơ sở dữ liệu là gì
- Tuân theo tính chất `ACID`:
    + `Tính nguyên tử` (`Atomicity`): Tất cả các thao tác bên trong giao dịch phải thành công. Nếu lỗi thì rollback.
    + `Tính nhất quán` (`Consistencty`): Sau bất kì transaction nào thì mối liên kết dữ liệu vẫn không thay đổi.
    + `Tính độc lập` (`Isolation`): Một giao dịch được thực thi không ảnh hưởng đến các giao dịch khác.  
    + `Tính bền vững` (`Durability`): Sau khi các giao dịch diễn ra thành công thì dữ liệu sẽ không bị mất dù gặp bất kì trục trặc gì.

- Quy trình xử lý giao dịch:
    + Bắt đầu giao dịch (BEGIN TRANSACTION).
    + Thực thi các thao tác như thêm, sửa, xóa dữ liệu.
    + Kiểm tra các điều kiện đảm bảo không vi phạm các ràng buộc dữ liệu.
    + `COMMIT` nếu thành công và `ROLLBACK` nếu có lỗi trong quá trình thực thi.

- Các trường hợp có thể xảy ra:
    + 