# Cảm biến nước mưa MKE-S12 Raindrop Water Sensor

## Giới thiệu

**Cảm biến nước mưa MKE-S12 Raindrop Water Sensor** bao gồm **đầu dò (probe)** và **mạch chuyển đổi tín hiệu**, được thiết kế để phát hiện và đo lượng nước trên bề mặt đầu dò. Cảm biến hoạt động theo **nguyên lý cảm ứng điện dung**, trong đó đầu dò được phủ lớp sơn bảo vệ chống oxy hóa, không để lộ phần tiếp xúc kim loại như các loại cảm biến sử dụng nguyên lý điện trở, giúp tăng độ bền và khả năng sử dụng trong môi trường có nước. Cảm biến cung cấp **tín hiệu điện áp Analog thay đổi theo lượng nước trên đầu dò**, giúp hệ thống vi điều khiển ghi nhận và xử lý dữ liệu theo mức nước thực tế thay vì chỉ nhận trạng thái có/không có nước.

Sản phẩm phù hợp cho nhiều ứng dụng như: **phát hiện và giám sát nước mưa, đo mức độ ướt, hệ thống cảnh báo mưa, thiết bị IoT, hệ thống tự động hóa và các dự án STEM**. Mạch được thiết kế nhằm tăng **độ ổn định tín hiệu và khả năng chống nhiễu**, đảm bảo tín hiệu đầu ra ổn định trong quá trình học tập, nghiên cứu và phát triển các ứng dụng thực tế.

**Cảm biến nước mưa MKE-S12 Raindrop Water Sensor** hỗ trợ điện áp giao tiếp 3.3V và 5VDC, cho phép kết nối trực tiếp và an toàn với hầu hết các bo mạch điều khiển phổ biến hiện nay như Arduino, Raspberry Pi, Jetson Nano, Micro:bit và nhiều nền tảng khác. Sản phẩm đi kèm **cáp kết nối 3P XH2.54 – Dupont**, đảm bảo kết nối chắc chắn, ổn định và thuận tiện trong quá trình sử dụng.

## Nguyên lý hoạt động

**MKE-S12 Raindrop Water Sensor** hoạt động dựa trên **nguyên lý cảm ứng điện dung** để phát hiện và xác định lượng nước trên bề mặt **đầu dò (probe)**. Khi nước xuất hiện trên đầu dò, **điện dung của đầu dò thay đổi theo lượng nước đọng trên bề mặt**. Mạch chuyển đổi tín hiệu trên cảm biến sẽ xử lý sự thay đổi điện dung này và chuyển đổi thành **tín hiệu điện áp Analog** tại ngõ ra `S`. 

Tín hiệu tại chân `S` có điện áp trong khoảng:

```text
0VDC ~ 3.3VDC
```

Tín hiệu Analog sau đó có thể được đưa vào ngõ **ADC (Analog to Digital Converter)** của vi điều khiển để chuyển đổi thành giá trị số, từ đó chương trình có thể **ghi nhận và xử lý mức độ nước trên đầu dò**.

## Thông số kỹ thuật
- Điện áp cấp nguồn: 5VDC
- Chuẩn tín hiệu giao tiếp: Analog
- Điện áp giao tiếp: 0~3.3VDC
- Đo lượng nước mưa bám trên bề mặt đầu dò Probe bằng phương pháp điện dung.
- Khả năng tương thích:
  - Arduino
  - Raspberry Pi
  - Jetson Nano
  - Micro:bit
  - Và các board điều khiển 3.3/5VDC khác
- Thiết kế mạch:
  - Ổn định, chống nhiễu
  - Phù hợp cho ứng dụng học tập và thực tế
- Đi kèm cáp kết nối: 3P XH2.54–Dupont

## Các chân tín hiệu
<table><thead>
  <tr>
    <th>MKE-S12</th>
    <th>Ghi chú</th>
  </tr></thead>
<tbody>
  <tr>
    <td>-</td>
    <td>Chân cấp nguồn âm 0VDC</td>
  </tr>
  <tr>
    <td>+</td>
    <td>Chân cấp nguồn dương 5VDC</td>
  </tr>
  <tr>
    <td>S</td>
    <td>Chân tín hiệu Analog Out</td>
  </tr>
</tbody>
</table>

## Hướng dẫn sử dụng
### Hướng dẫn kết nối
- Cấp nguồn 5VDC cho mạch qua hai chân `-` và `+`.
- Nhận tín hiệu của cảm biến qua chân `S` (SIGNAL).
<table><thead>
  <tr>
    <th>SIGNAL (Analog Out)</th>
    <th>Trạng thái</th>
  </tr></thead>
<tbody>
  <tr>
    <td>Max</td>
    <td>3.3VDC</td>
  </tr>
  <tr>
    <td>Min</td>
    <td>0VDC</td>
  </tr>
</tbody>
</table>

### Hướng dẫn sử dụng với Arduino / ESP32
- Cảm biến sử dụng tín hiệu đầu ra Analog đơn giản không cần cài đặt bộ thư viện.
- Cấu hình board mạch tương ứng là **Arduino Uno / ESP32**, chọn đúng cổng **COM Port** của mạch và nhấn **Upload** để nạp chương trình.
- Cấp nguồn 5VDC cho mạch, kết nối chân `S` (SIGNAL) của sensor với chân điều khiển được khai báo trong chương trình.
- Xem kết quả mạch hoạt động theo chương trình đã nạp.

#### Chương trình mẫu cho Arduino Uno:
```ino
// Đặt tên cho chân kết nối cảm biến
// These constants won't change. They're used to give names to the pins used:
const int analogInPin = A1;  // Analog input pin that the sensor is attached to

// Tạo biến số nguyên lưu giá trị cảm biến
// value read from the sensor
int sensorValue = 0;  

void setup()
{
  // Khởi động kết nối Serial UART ở tốc độ 115200 để truyền dữ liệu lên máy tính.
  // Start the Serial UART connection at 115200 to transfer data to the computer.
  Serial.begin(115200);
}

void loop()
{
  // Đọc giá trị cảm biến
  // read the analog in value:
  sensorValue = analogRead(analogInPin);

  // Hiển thị giá trị đo được của cảm biến lên máy tính.
  // Show the sensor value on Arduno Serial Monitor
  Serial.print("Value: ");
  Serial.println(sensorValue);
  
  // Chờ 500ms
  // Wait 500ms
  delay(500);
}
```

#### Chương trình mẫu cho ESP32:
```ino
// Đặt tên cho chân kết nối cảm biến
// These constants won't change. They're used to give names to the pins used:
const int analogInPin = 34;  // IO34

// Tạo biến số nguyên lưu giá trị cảm biến
// value read from the sensor
int sensorValue = 0;  

void setup()
{
  // Khởi động kết nối Serial UART ở tốc độ 115200 để truyền dữ liệu lên máy tính.
  // Start the Serial UART connection at 115200 to transfer data to the computer.
  Serial.begin(115200);
}

void loop()
{
  // Đọc giá trị cảm biến
  // read the analog in value:
  sensorValue = analogRead(analogInPin);

  // Hiển thị giá trị đo được của cảm biến lên máy tính.
  // Show the sensor value on Arduno Serial Monitor
  Serial.print("Value: ");
  Serial.println(sensorValue);
  
  // Chờ 500ms
  // Wait 500ms
  delay(500);
}
```

### Hướng dẫn lập trình với Micro:bit (kéo thả khối)

- Khởi động [Microsoft MakeCode](https://makecode.microbit.org/) và **Import** chương trình theo đường link sau: `https://github.com/makereduvn/mke_s12_raindrop_microbit/`
- Kết nối mạch Micro:bit và **Download** chương trình.
- Cấp nguồn 5VDC cho mạch, kết nối chân S (SIGNAL) của sensor với chân điều khiển được khai báo trong chương trình.
- Xem kết quả mạch hoạt động theo chương trình đã nạp.

Nếu bắt đầu tự án mới cần cài đặt Extension **MKE_ONE_MICROBIT** trên [Microsoft MakeCode](https://makecode.microbit.org/) theo [hướng dẫn tại đây](https://github.com/makereduvn/MKE_ONE_MICROBIT). Sau khi cài đặt thành công, các khối lệnh của Extension **MKE_ONE_MICROBIT** sẽ xuất hiện trong danh sách block và sẵn sàng để sử dụng.

## Kích thước sản phẩm
### Probe
![MKE-S12 RAINDROP](/extras/MKE-S12_1.jpg)

### Mạch xử lý tín hiệu
![MKE-S12 RAINDROP](/extras/MKE-S12_2.jpg)

## Hình ảnh sản phẩm

### Probe
![MKE-S12 RAINDROP](/extras/MKE-S12_3.png)

### Mạch xử lý tín hiệu
![MKE-S12 RAINDROP](/extras/MKE-S12_4.png)
![MKE-S12 RAINDROP](/extras/MKE-S12_5.png)

## Miễn trừ trách nhiệm
Sản phẩm này là bo mạch phát triển được thiết kế phục vụ cho mục đích nghiên cứu, thử nghiệm và học tập, không phải là một thiết bị hoàn chỉnh. Trong trường hợp người dùng kết hợp mạch này với các linh kiện, thiết bị hoặc phần mềm khác để tạo thành một hệ thống hoặc sản phẩm hoàn chỉnh, mọi chức năng và tính phù hợp của sản phẩm sau cùng đều thuộc trách nhiệm của người dùng.
