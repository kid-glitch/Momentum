LINK BÀI LAB:

Tiến hành Scan:

![image](https://user-images.githubusercontent.com/72652376/126104437-0f145748-b39e-4b97-8019-cce24862455f.png)


![image](https://user-images.githubusercontent.com/72652376/126104474-87a61cdb-e8b2-4c8c-8aaa-045e7a524d85.png)

![image](https://user-images.githubusercontent.com/72652376/126119899-eb799d61-47df-4bd9-a7c8-833f54fe0c91.png)

Ở đây có 1 đường dẫn mới và 1 đoạn code 

Phân tích kỹ đoạn code
<code>

var CryptoJS = require("crypto-js"); //

var decrypted = CryptoJS.AES.decrypt(encrypted, "SecretPassphraseMomentum");// khai báo biến decrypted(giải mã) bằng cách gọi đến hàm CryptoJS.AES.decrypt() với 2 tham số là encrypted và một key SecretPassphraseMomentum

console.log(decrypted.toString(CryptoJS.enc.Utf8)); // hiển thị lên một cửa sổ console chuỗi đã đưa về dạng strings
  
</code>

Nghĩa là đầu vào của hàm giải mã bao gồm một chuỗi đóng vai trò là bản mã(encrypted hay là bản đã bị mã hóa) và khóa trong thuật toán AES. Khóa đã có sẵn nhiệm vụ là đi tìm bản đã bị mã hóa ở đâu

Thay đổi đường dẫn thấy hiển thị trên giao diện. Có thể chèn XSS thử 

![image](https://user-images.githubusercontent.com/72652376/126121162-bf0203cc-1b8c-49a6-ae7e-7bb234c88116.png)

![image](https://user-images.githubusercontent.com/72652376/126121451-d9a0cfc0-bddb-4099-b505-27ffabf6d480.png)

Có đoạn mã cookie

Tiến hành giải mã:

1 source tìm được trên mạng về CryptoJS v3.1.2 https://cdnjs.cloudflare.com/ajax/libs/crypto-js/3.1.2/rollups/aes.js

Truyền vào 2 tham số như đã phân tích ở trên thu được chuỗi:

![image](https://user-images.githubusercontent.com/72652376/126122429-f394b2c2-5b81-455e-baf3-9b1aae3e454b.png)

Trông giống user login SSH, tiến hành thử

![image](https://user-images.githubusercontent.com/72652376/126122694-9c3fb587-888e-4ea7-a8c8-4139bbbaccf3.png)

Có thể đăng nhập là lấy được 1 cờ user

Tìm cách leo thang đặc quyền nhưng không thể up root nên kiểm tra các tiến trình, port đang mở xem có gì đặc biệt

![image](https://user-images.githubusercontent.com/72652376/126124930-310759b5-6ccf-45fa-9ea9-7cf5d773b92f.png)

Port 6379 là dịch vụ redis-cli thử tiến hành truy cập

![image](https://user-images.githubusercontent.com/72652376/126124996-523157e5-1317-4837-b0e6-a119775546d3.png)

Tìm được thêm một mật khẩu để truy cập root

![image](https://user-images.githubusercontent.com/72652376/126125351-715de41b-be26-4480-8165-1b1ed74d26b5.png)

DONE!!!
