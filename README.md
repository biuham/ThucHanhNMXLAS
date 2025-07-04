# Nhập Môn Xử Lý Ảnh Số - Lab 5  
## **Xác Định Đối Tượng Trong Ảnh**  
**Sinh viên thực hiện:** Nguyễn Hữu Thịnh

**MSSV:** 2174802010323  

**Môn học:** Nhập môn Xử lý ảnh số  

**Giảng viên:** Đỗ Hữu Quân

---

## Mục tiêu

- Gán nhãn các vùng ảnh để phân biệt đối tượng  
- Phân vùng ảnh theo Region  
- Dò tìm cạnh và hình dạng đối tượng  
- Nhận diện hình học (đường thẳng, đường tròn)  
- So khớp ảnh (image matching)  

---

## Công cụ sử dụng

- Python + OpenCV  
- NumPy  
- Matplotlib  

---

## Các kỹ thuật chính & công thức

### 1. Gán nhãn ảnh (Labeling)

**Mục đích:**  
- Phân biệt các đối tượng riêng biệt trong ảnh nhị phân

**Nguyên lý:**  
- Mỗi vùng liên thông (connected component) được gán một nhãn khác nhau  
- Các pixel thuộc cùng một đối tượng có cùng giá trị

**Ứng dụng:**  
- Đếm số lượng đối tượng, phân tích hình dạng

---

### 2. Dò cạnh theo chiều dọc

**Ý tưởng:**  
- Dò sự thay đổi cường độ pixel theo chiều dọc bằng phép trừ hoặc dịch ảnh

**Ví dụ:**  
- Dùng `shift` ảnh 1 pixel theo trục y, sau đó lấy hiệu để phát hiện biên

---

### 3. Sobel Filter

**Mục đích:**  
- Dò cạnh theo hướng x, y bằng toán tử tích chập (convolution)

**Kernel Sobel:**  
- Dọc (Gy):  
  ```
  [-1 -2 -1]
  [ 0  0  0]
  [ 1  2  1]
  ```
- Ngang (Gx):  
  ```
  [-1  0  1]
  [-2  0  2]
  [-1  0  1]
  ```

**Công thức biên độ gradient:**  
```math
G = \sqrt{G_x^2 + G_y^2}
```

---

### 4. Xác định góc của đối tượng

**Ý tưởng:**  
- Dựa vào biên và hình dạng để tính toán góc nghiêng hoặc hướng của đối tượng  
- Có thể dùng moment hoặc vector gradient

---

### 5. Hough Transform

#### a. Dò đường thẳng

**Công thức đường thẳng:**  
```math
\rho = x \cos\theta + y \sin\theta
```

**Ý tưởng:**  
- Mỗi điểm ảnh biên sẽ biểu diễn thành một đường trong không gian Hough  
- Giao điểm của nhiều đường → đường thẳng thực sự

#### b. Dò đường tròn

**Công thức đường tròn:**  
```math
(x - a)^2 + (y - b)^2 = r^2
```

**Ý tưởng:**  
- Tìm các tập hợp điểm biên tạo thành đường tròn với bán kính r

---

### 6. Image Matching

**Mục tiêu:**  
- Tìm điểm tương đồng giữa hai ảnh

**Các bước:**

1. Phát hiện điểm đặc trưng (Harris Corner Detector)  
2. Xây vùng chọn (patch) quanh điểm đặc trưng  
3. Tính mô tả đặc trưng (descriptor)  
4. So khớp descriptor giữa hai ảnh (dùng SSD, NCC, hoặc SIFT/ORB)

---


## Ghi chú

- Gán nhãn giúp phân biệt các đối tượng riêng biệt trong ảnh nhị phân  
- Sobel và Hough là công cụ mạnh để phát hiện biên và hình học  
- Image Matching là nền tảng cho nhận diện ảnh, theo dõi đối tượng  

---

## Tài liệu tham khảo

- Slide bài giảng Xử lý ảnh số – Văn Lang University  
- [OpenCV Documentation](https://docs.opencv.org/)  
- [Digital Image Processing – Gonzalez & Woods](https://www.amazon.com/Digital-Image-Processing-Rafael-Gonzalez/dp/013168728X)  
