# C#

### Object & Class
| Object | Class |
|:----------------|:---------------|
| Là thực thể được tạo ra từ Class | Là bản thiết kế, xác định thuộc tính và phương thức |

### Struct & Class
- Giống nhau:
    + Đều chứa `property` & `field`

|   | Struct | Class |
|:--|:----------------|:---------------|
|Lưu trữ|Ngăn xếp `Stack`|Bộ nhớ `Heap`|
|Kiểu dữ liệu|`Value type`|`Reference type`|
|Kế thừa| Không hỗ trợ | Hỗ trợ |
|Constructor không tham số| Không hỗ trợ | Hỗ trợ |

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

### Static
- ***Static Class*** (Lớp tĩnh)
    + `Không` thể khởi tạo được đối tượng (object).
    + Các thành phần bên trong (phương thức, thuộc tính) `bắt buộc phải là static`.
    + Dùng chủ yếu cho các phương thức tiện ích hoặc các hàm xử lý mà không cần lưu trữ trạng thái thông qua đối tượng.

- ***Static Method*** (Hàm tĩnh)
    + Phương thức thuộc về lớp (không phải thuộc về đối tượng như `instance method`)
    + Có thể gọi thẳng hàm mà không cần khởi tạo đối tượng (trong cả `non-static class` và `static class`).
    + Không truy cập được các thuộc tính không tĩnh (instance) trong class.


# OOP

### 4 Tính chất của OOP
- `Tính đóng gói` (Encapsulation): là tính năng `che giấu` `thông tin` của 1 đối tượng. Các đối tượng bên ngoài muốn `truy cập` hoặc `chỉnh sửa` thông tin thì phải thông qua các `phương thức công khai`.

- `Tính kế thừa` (Inheritance): các lớp con kế thừa thì sẽ thừa hưởng các `thuộc tính` và `phương thức` của lớp cha. Các lớp con có thể `mở rộng` hoặc `thay đổi hành vi` mà không cần viết lại toàn bộ mã.

- `Tính đa hình`: Các `đối tượng khác nhau` có thể thực thi 1 `hàm giống nhau` với các `cài đặt khác nhau`. 
    + Đa hình được triển khai thông qua `nạp chồng phương thức` (overloading) hoặc `ghi đè phương thức` (overriding)

- `Tính trừu tượng` (Abstraction): Thường được thực hiện thông qua `lớp trừu tượng` (Abstract Class) hoặc `giao diện` (Interface). Nó giống như 1 `bản thiết kế`, `chỉ định` các phương thức cho lớp con, nhưng chi tiết cài đặt sẽ do `lớp con triển khai`.

### SOLID là gì
- `S` (`Single` Responsibility Principle): mỗi lớp chỉ nên đảm nhận `một` `nhiệm vụ` cụ thể nào đó.

- `O` (`Open`/Closed Principle): `Không được sửa đổi` 1 class có sẵn, nhưng có thể `mở rộng` bằng kế thừa.

- `L` (`Liskov` Substituition Priciple): Thiết kế để các đối tượng `lớp con` có thể thay thế đối tượng `lớp cha` mà không gây ra lỗi.

    + ![alt](https://topdev.vn/blog/wp-content/uploads/2019/07/Liskov-substitution-principle.png)
    + Ở trường hợp trên `CleanerStaff` kế thừa `Employee` nhưng lại không được dùng method `checkAttendance()` do quy tắc thiết kế => `lỗi`
    + Có thể tách method `checkAttendance()` qua 1 class riêng.

- `I` (`Interface` Segregation Principle): Nên `chia nhỏ` thành nhiều interface thay vì thiết kế một interface lớn.

- `D` (`Dependency` Inversion Principle): 
    + Các module cấp cao không nên phụ thuộc vào các module cấp thấp mà `cả hai` nên phụ thuộc vào `abstraction`.
    + Các class giao tiếp với nhau thông qua `interface`, không phải `implementation`
    ---
    + ***Những cái trừu tượng (abstraction) là những cái ít biến động, tập hợp những đặc điểm chung nhất của những cái cụ thể. Việc phụ thuộc vào cái trừu tượng sẽ giúp chương trình linh động và thích ứng tốt với các sự thay đổi diễn ra liên tục.***
    + ***`Điểm khác biệt` giữa phụ thuộc vào `interface` và phụ thuộc `trực tiếp` là interface giúp chỉ cần quan tâm đến `hành vi chung`, `không` cần quan tâm đến `chi tiết` thực thi của dịch vụ. Như vậy việc sửa đổi mã nguồn sẽ độc lập và dễ bảo trì hơn.***
    ---
    + Ví dụ có 1 module cấp cao là `OrderProcessor` và module cấp thấp là `EmailService`
    + `Vi phạm nguyên tắc`: Implement thẳng EmailService vào OrderProcessor.
    + `Tuân theo nguyên tắc`: 
        + Tạo 1 interface `INotificationService` và `EmailService` sẽ kế thừa interface này. `OrderProcessor` chỉ việc inject interface này vào và sử dụng `EmailService`. 
        + Như vậy khi ta muốn thêm 1 service nào mới (như `SmsService`) thì ta chỉ việc kế thừa từ `INotificationService`, hạn chế thay đổi mã nguồn nhiều nơi.



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
        - DHCP: giao thức cấp IP và các thông số mạng tự động cho thiết bị
        - DNS: hệ thống phân giải tên miền thành IP
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
- Là 1 chuỗi các thao tác tương tác với cơ sở dữ liệu.

- Tuân theo tính chất `ACID`:
    + `Tính nguyên tử` (`Atomicity`): Toàn bộ giao dịch được coi như `một khối duy nhất`. Hoặc là thành công hoặc là rollback.
    + `Tính nhất quán` (`Consistencty`): Sau bất kì transaction nào thì mối liên kết dữ liệu vẫn không thay đổi.
    + `Tính độc lập` (`Isolation`): Một giao dịch được thực thi không ảnh hưởng đến các giao dịch khác.  
    + `Tính bền vững` (`Durability`): Sau khi các giao dịch diễn ra thành công thì dữ liệu sẽ không bị mất dù gặp bất kì trục trặc gì.

- Quy trình xử lý giao dịch:
    + Bắt đầu giao dịch (BEGIN TRANSACTION).
    + Thực thi các thao tác như thêm, sửa, xóa dữ liệu.
    + Kiểm tra các điều kiện đảm bảo không vi phạm các ràng buộc dữ liệu.
    + `COMMIT` nếu thành công và `ROLLBACK` nếu có lỗi trong quá trình thực thi.

- Các trường hợp có thể xảy ra:
    + `Deadlock`: khi 2 hoặc nhiều giao dịch cùng giữ khóa mà các giao dịch khác cần và đều chờ nhau giải phóng khóa. Từ đó sẽ dẫn đến chờ vô hạn.
    + `Giao dịch đồng thời`: Khi nhiều giao dịch xảy ra đồng thời, cần có phương pháp kiểm soát. Tiêu biểu là `locking`.
    + `Giao dịch thất bại` 

### SQL và NoSQL khác gì nhau?
|   | SQL | NoSQL |
|:--|:----------------|:---------------|
| Kiến trúc dữ liệu | - Sử dụng mô hình dữ liệu quan hệ, được tổ chức trong bảng với các hàng và cột <br/> - Có các ràng buộc dữ liệu (PK, FK, NOT NULL, UNIQUE, ...) <br/> - Có thể quan hệ giữa các bảng với khóa ngoại (Foreign Key)<br/> | - Hỗ trợ nhiều mô hình dữ liệu khác nhau: <br/>&nbsp;&nbsp; + Tài liệu (Document): MongoDB <br/> &nbsp;&nbsp; + Các cặp key-value: Redis <br/>&nbsp;&nbsp; + Column: Cassandra <br/> - Cho phép lưu dữ liệu mà không cần xác định trước cấu trúc |

### Đánh index là gì? Khi nào đánh khi nào không?
- `Đánh index` là đánh chỉ mục trên một hoặc nhiều cột nào đó giúp tăng tốc độ truy vấn mà không cần quét toàn bộ bảng

- Khi nào nên đánh index:
    + Khi bảng dữ liệu có nhiều bản ghi và thường xuyên truy vấn `SELECT`
    + Truy vấn trên cột thường xuyên sử dụng trong điều kiện lọc
    + Các nhóm cột thường xuyên sử dụng hàm nhóm (COUNT, AVG, SUM)

- Khi nào không nên đánh index:
    + Với `bảng nhỏ` (dưới 1000 bản ghi) vì thời gian quét toàn bộ bảng thường không tốn thời gian.
    + Với các bảng thường xuyên thay đổi (INSERT, UPDATE, DELETE) vì bảng sẽ cần cập nhật lại index.
    + Chỉ mục sẽ chiếm không gian lưu trữ.

### Shard & View
- `Shard`: Sharding là kĩ thuật phân mảnh dữ liệu để lưu trữ trên nhiều máy chủ khác nhau để tăng khả năng mở rộng và hiệu suất của CSDL.

![alt](https://images.viblo.asia/c3f91483-4ac3-4a18-a7b4-c604f059e64c.png)

- `View`: Là bảng ảo trong CSDL, không lưu dữ liệu. Thay vì JOIN 2 bảng với nhau trên mỗi lần truy vấn thì ta có thể dùng `VIEW` để thay thế, rút ngắn câu lệnh.

![alt](https://winzone.vn/images/blog/13/view_example.png)

### Event Store là gì? Các loại Event Store?
***Event Store là gì***
- `Event Store`: là 1 loại cơ sở dữ liệu lưu trữ dữ liệu theo sự kiện (event). 
- `Event Sourcing`: Kỹ thuật lưu trạng thái của dữ liệu `trên sự kiện`. Thay vì lưu trạng thái hiện tại của dữ liệu, nó lưu trữ toàn bộ lịch sử các sự kiện xảy ra. 

***Các loại EventStore phổ biến***
- `EventStoreDB`
- `ApacheKafka`
- `RDM` hay `NoSQL DB` đều có thể sử dụng như 1 EventStore bằng cách lưu các sự kiện trong bảng. 

### Cache là gì? Cache bằng công cụ nào?
***Cache là gì***
- Cache lưu trữ bản sao của dữ liệu để tránh việc truy cập dữ liệu gốc nhiều lần, đặc biệt với những dữ liệu tĩnh và ít thay đổi thường xuyên.

- Các loại cache:
    + Client-side Cache
    + Server-side Cache
    + Distributed Cache

- Các thành phần của cache:
    + Key 
    + Value
    + TTL (Time To Live)

***Dùng gì để cache***
| Công nghệ | Công cụ |
|:----------------|:---------------|
| Memory-based caching | Redis |
| Application-level cache | + ASPNET Cache: `MemoryCache` & `OutputCache` <br/> + Spring Cache (Java)
| HTTP Caching | Browser Cache |
| Database Caching | `MySQL` hoặc `PostgreSQL` |

# Web

### Session & Cookies
| Session | Cookies |
|:----------------|:---------------|
| Lưu dữ liệu trên server | Lưu dữ liệu ở phía client |
| Bị xóa khi `timeout` hoặc xóa thủ công | `session cookies` bị xóa khi đóng trình duyệt, `persistent cookies` được cài đặt thời gian sống và tồn tại đến khi timeout |

- `Session ID` được gửi kèm trong mỗi request đến server, được lưu dưới dạng `session cookies` trên trình duyệt (thường chỉ tồn tại trong phiên làm việc của trình duyệt).

### Local Storage & Session Storage
- Đều lưu trữ phía `client` trong trình duyệt web

| | Local Storage | Session Storage |
|:---|:----------------|:---------------|
| `Phạm vi lưu trữ` | Được chia sẻ giữa các tab và cửa sổ trình duyệt của cùng 1 trang web | Mỗi tab hoặc cửa sổ trình duyệt sẽ có 1 session storage riêng biệt |
| `Thời gian sống` | Tồn tại vĩnh viễn cho đến khi được xóa thủ công bằng code hoặc từ người dùng xóa ở trình duyệt | Bị xóa khi tab hoặc cửa sổ trình duyệt đóng |

### Quản lý phiên làm việc ở server
- `Sử dụng session`: Mỗi khi người dùng đăng nhập sẽ có 1 `Session ID` đặt trong `session cookies`. Người dùng sẽ gắn cookies này trong request để lấy dữ liệu từ server. Server sẽ kiểm tra xem `Session ID` trong request có trùng với `Session ID` được lưu ở Server hay không.

- `Sử dụng JWT Token`: Mỗi khi người dùng đăng nhập sẽ được cấp 1 `Access Token`. Người dùng sẽ gắn token này trong `headers` của request và server sẽ kiểm tra token, nếu hợp lệ sẽ cho sử dụng các dịch vụ ở server. 

# .NET

### Phân biệt .NET Core và .NET Framework
- `Nền tảng`:
    + `.NET Framework`:
        + Ra mắt 2002
        + Chỉ chạy trên `Windows`
        + Thiết kế cho ứng dụng desktop (WinForms, WPF, WinUI) và ứng dụng web (ASPNET MVC, ASPNET Web Form)
    + `.NET Core`:
        + Ra mắt 2016
        + Đa nền tảng (MacOS, Linux, Windows)
        + Phiên bản nâng cấp của .NET Framework
        + Hỗ trợ `container`, `cloud`
