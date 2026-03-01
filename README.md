# Phân loại động vật bằng mô hình CNN

## Mục tiêu đặt ra
- Xây dựng được 1 mô hình CNN cơ bản với kiến trúc gồm convolution layer(Conv), MaxPooling Layer, Fully connected Layer(fc) và Batch Norm
- Xây dựng mô hình để phân loại hình ảnh động vật với 10 class gồm: Bướm, mèo, gà, bò, chó, voi, ngựa, cừu, nhện và sóc.
- Mục tiêu chính: Hiểu được cấu trúc của một mô hình CNN cơ bản.

## Dataset
- 26200 ảnh.
- Hơn 24700 ảnh để train, 1440 ảnh để test.
- Tất cả ảnh được lấy trên trang Kaggle và khi train đã được Resize về 224x224 tại file dataset1.

## Model
- CNN cơ bản
- Optimizer: SGD
- Loss: CrossEntropyLoss

## Training
- Epochs: 100
- Batch size: 64
- Learning rate: 0.001

## Khó khăn gặp phải và bài học rút ra

### Những sai sót ban đầu
Khi mới bắt đầu xây dựng mô hình, mình đã gặp một số sai sót trong quá trình thiết kế kiến trúc:
- Thiết kế quá nhiều lớp Fully Connected (FC).
- Sử dụng số lượng tham số quá lớn trong các lớp FC.
- Xây dựng lớp FC với số chiều đầu vào rất cao trong khi dataset lại không đủ lớn.
Những điều này làm cho mô hình có độ phức tạp quá cao so với dữ liệu hiện có, dẫn đến tình trạng **overfitting**: độ chính xác trên tập train cao nhưng hiệu năng trên tập validation/test lại thấp.
Điều này cho thấy rằng máy chỉ đang ghi nhớ dữ liệu train thay vì học các đặc trưng của ảnh.

### Cách xử lý
Sau khi nhận thấy hiện tượng overfitting, mình đã:
- Giảm số lượng lớp Fully Connected.
- Giảm số neuron trong các lớp FC để hạn chế số lượng tham số.
- Điều chỉnh lại kiến trúc mô hình sao cho phù hợp với quy mô dataset.
- Theo dõi kỹ hiệu năng trên tập validation thay vì chỉ nhìn vào kết quả train.

### Bài học rút ra
- Độ phức tạp của mô hình phải tương xứng với kích thước và chất lượng dataset.
- Không phải cứ tăng số lớp hay tăng tham số là mô hình sẽ tốt hơn.
- Overfitting thường là dấu hiệu của việc mô hình quá phức tạp.
- Thiết kế kiến trúc hợp lý quan trọng hơn việc chỉ tập trung tăng độ sâu hoặc số tham số.
- Luôn đánh giá mô hình trên tập validation để có cái nhìn khách quan về khả năng tổng quát hóa.

## Kết quả 
- Validation Accuracy (Max - Last): 77.43% - 75.69%
- Test Accuracy:17/19 -> 89.47%
- Loss: 0.0038
### Kết quả dự đoán trên tập test
<p align="center">
  <img width="300" height="500" alt="image" src="https://github.com/user-attachments/assets/e106ac56-9cc3-4573-b69c-2607bab99334" />
  <img width="300" height="500" alt="image" src="https://github.com/user-attachments/assets/5ccc0c56-2df8-40eb-bdc0-54621a23c3cf" />
  <img width="300" height="500" alt="image" src="https://github.com/user-attachments/assets/0f20fd8e-179e-40ba-ac1b-45460b836746" />
</p>

<p align="center">
  <img width="300" height="500" alt="image" src="https://github.com/user-attachments/assets/801c8b70-4c77-42ae-b36f-0e3b3a2e504b" />
  <img width="300" height="500" alt="image" src="https://github.com/user-attachments/assets/3cca09d3-55df-4b54-a4e4-ed86f0e28ec7" />
  <img width="300" height="500" alt="image" src="https://github.com/user-attachments/assets/128bec72-ab63-4288-8c10-40bb1141eb62" /> (sai)
</p>

<p align="center">
  <img width="300" height="500" alt="image" src="https://github.com/user-attachments/assets/1ecf4b7b-29ae-4077-978e-fb71c5036b0a" />
  <img width="300" height="500" alt="image" src="https://github.com/user-attachments/assets/62984824-f36f-4833-aadc-8f6c4b217993" />
  <img width="300" height="500" alt="image" src="https://github.com/user-attachments/assets/ad9eb981-924a-45a6-8576-54c24f949230" />
</p>

<p align="center">
  <img width="300" height="500" alt="image" src="https://github.com/user-attachments/assets/85c5ba3e-3ba6-4b6b-9082-4629a66d1ad8" />
  <img width="300" height="500" alt="image" src="https://github.com/user-attachments/assets/9ad111ac-2540-4c6a-a120-707a5bf8c96f" />
  <img width="300" height="500" alt="image" src="https://github.com/user-attachments/assets/f35d3052-b332-4dd4-99d8-4d8c2dacf36b" />
</p>

<p align="center">
  <img width="300" height="500" alt="image" src="https://github.com/user-attachments/assets/9c4e13fe-5942-4d31-ba41-0fbfb464e6f1" />
  <img width="300" height="500" alt="image" src="https://github.com/user-attachments/assets/b8e2f4c6-8fd3-40e5-a1bb-1745c9938b33" />
  <img width="300" height="500" alt="image" src="https://github.com/user-attachments/assets/48dfb112-7951-42a9-97b0-edb3ff478def" />
</p>

<p align="center">
  <img width="300" height="500" alt="image" src="https://github.com/user-attachments/assets/b91da59c-b222-40f2-b10a-aeb40c05af5c" />
  <img width="300" height="500" alt="image" src="https://github.com/user-attachments/assets/5dbc25f7-9a2d-455a-94d8-f2770d39f420" /> (sai)
  <img width="300" height="500" alt="image" src="https://github.com/user-attachments/assets/b35dbf99-5556-43c7-b9aa-5796414adcf0" />
</p>
<img width="300" height="500" alt="image" src="https://github.com/user-attachments/assets/2aa12ee4-b94e-461e-8fbb-6521d26d03cc" />
