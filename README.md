# 📡 Trạm Giám Sát Tiếng Ồn Thông Minh

> Đề tài môn học: Thành phố thông minh và Nông nghiệp thông minh  
> Sinh viên thực hiện: Nguyễn Tiến Đạt – Lớp CNTT 15-03  
> Trường Đại học Đại Nam – Năm 2025

---

## 🧠 Giới thiệu

Trong bối cảnh đô thị hóa nhanh chóng, ô nhiễm tiếng ồn đang trở thành một vấn đề nghiêm trọng ảnh hưởng đến sức khỏe con người và chất lượng cuộc sống. Đề tài này xây dựng một **trạm giám sát tiếng ồn thông minh** sử dụng vi điều khiển ESP32 và cảm biến âm thanh, giúp theo dõi tiếng ồn theo thời gian thực và cảnh báo khi vượt ngưỡng cho phép.

---

## 🎯 Mục tiêu

- Thiết kế hệ thống đo tiếng ồn sử dụng cảm biến KY-038 + ESP32.
- Truyền dữ liệu qua Wi-Fi về máy chủ và hiển thị biểu đồ trên web.
- Tích hợp chức năng **cảnh báo tự động** khi tiếng ồn vượt ngưỡng.
- Ứng dụng công nghệ IoT vào giám sát môi trường đô thị.

---

## 🛠️ Thành phần hệ thống

- **Cảm biến âm thanh** KY-038
- **Vi điều khiển** ESP32 (hoặc ESP8266)
- **LED cảnh báo**
- **Máy chủ** thu thập và xử lý dữ liệu
- **Giao diện web** hiển thị mức tiếng ồn và cảnh báo

---

## 🧩 Kiến trúc hoạt động


---

## 💡 Một số tính năng chính

- Ghi nhận mức độ tiếng ồn (dB) theo thời gian thực.
- Gửi dữ liệu về máy chủ qua giao thức HTTP hoặc MQTT.
- Hiển thị dữ liệu tiếng ồn dưới dạng **biểu đồ** trên web.
- Cảnh báo người dùng khi vượt ngưỡng 70 dB (ngày) hoặc 55 dB (đêm).

---

## 🖥️ Mã nguồn ví dụ trên ESP32

```cpp
const int soundPin = 27;
const int ledPin = 26;

void setup() {
  Serial.begin(115200);
  pinMode(soundPin, INPUT);
  pinMode(ledPin, OUTPUT);
}

void loop() {
  int soundState = digitalRead(soundPin);
  if (soundState == HIGH) {
    Serial.println("🔊 Phát hiện tiếng ồn!");
    digitalWrite(ledPin, HIGH);
  } else {
    Serial.println("... Yên tĩnh.");
    digitalWrite(ledPin, LOW);
  }
  delay(200);
}
