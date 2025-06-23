# Nhập Môn Xử Lý Ảnh Số - Lab 2  

**Sinh viên thực hiện:** Nguyễn Hữu Thịnh **MSSV:** 2174802010323

**Môn học:** Nhập môn Xử lý ảnh số  

**Giảng viên:** Đỗ Hữu Quân

---

## Giới thiệu  
Bài lab này trình bày các phép biến đổi cường độ ảnh cơ bản để tăng cường tương phản và chi tiết hình ảnh[1].

---

## Các phép biến đổi  

### 1. Negative Transformation  
- **Ý chính:** Đảo ngược giá trị pixel, biến vùng sáng thành tối và ngược lại[2].  
- **Công thức:** $$s = L - 1 - r$$[3].  
- **Ví dụ:** Pixel 100 → 155 (255 - 100)[4].

### 2. Log Transformation  
- **Ý chính:** Khuếch đại pixel nhỏ, làm rõ vùng tối[5].  
- **Công thức:** $$s = c \times \log(1 + r)$$[6].  
- **Ví dụ:** Pixel 10 sáng lên nhiều hơn pixel 200.

### 3. Gamma Correction  
- **Ý chính:** Điều chỉnh độ sáng tổng thể bằng tham số γ[7].  
- **Công thức:** $$s = c \times r^\gamma$$[8].  
- **Ví dụ:** γ = 0.5 → ảnh sáng; γ = 2.0 → ảnh tối.

### 4. Histogram Equalization  
- **Ý chính:** Phân phối lại mức xám để tăng độ tương phản sử dụng CDF[9].  
- **Ví dụ:** Dải 50–150 mở rộng thành 0–255.

### 5. Contrast Stretching  
- **Ý chính:** Kéo giãn tuyến tính dải pixel[10].  
- **Công thức:** $$s = \frac{255\,(r - a)}{b - a}$$.

### 6. FFT & Butterworth Filtering  
- **FFT:** Chuyển ảnh sang miền tần số để lọc nhiễu hoặc nâng cao cạnh[11].  
- **Butterworth:** $$H(u,v) = \frac{1}{1 + (D(u,v)/D_0)^{2n}}$$[12].

---
## Hướng dẫn sử dụng  
1. Cài đặt: `pip install pillow numpy matplotlib scipy`[13]  
2. Chạy: Mở Jupyter Notebook và thực thi các cell từng bước[14]  
3. Tùy chỉnh: Thay đổi tham số γ, D₀ để quan sát kết quả[15].

---

## Tài liệu tham khảo  
1. Gonzalez R.C., Woods R.E., Digital Image Processing.  
2. Jain A.K., Fundamentals of Digital Image Processing.  
3. Oppenheim A.V., Schafer R.W., Discrete-Time Signal Processing.  
4. Russ J.C., The Image Processing Handbook.  
5. Slide bài giảng Nhập môn Xử lý ảnh số - Văn Lang University





# Nhập Môn Xử Lý Ảnh Số – Lab 3: Biến Đổi Hình Học [7]

**Sinh viên thực hiện:** Nguyễn Hữu Thịnh **MSSV:** 2174802010323

**Môn học:** Nhập môn Xử lý ảnh số  

**Giảng viên:** Đỗ Hữu Quân

---

## Giới thiệu [7]

Bài lab 3 tập trung vào các phép biến đổi hình học, tức là sắp xếp lại vị trí các điểm ảnh để thực hiện chọn vùng, tịnh tiến, phóng to/thu nhỏ, xoay và các biến đổi chung [7].

---

## Các phép biến đổi hình học [7]

### 1. Chọn đối tượng (Cropping) [1]
- **Ý chính:** Trích xuất một phần ảnh nhỏ từ khung ảnh gốc bằng cách xác định tọa độ vùng cắt (x₁, y₁)–(x₂, y₂) [1].  
- **Ví dụ:** Tách riêng vùng quả cam trong ảnh với tọa độ (800, 570) đến (1200, 980) [1].

### 2. Tịnh tiến (Translation) [2]
- **Ý chính:** Dịch chuyển ảnh theo vectơ (Δx, Δy) mà không đổi góc hay kích thước [2].  
- **Công thức:**  
  $$x' = x + \Delta x,\quad y' = y + \Delta y$$ [2].  
- **Ví dụ:** Dịch quả cam 100 px theo trục x và 25 px theo trục y [2].

### 3. Phóng to/Thu nhỏ (Scaling) [3]
- **Ý chính:** Thay đổi kích thước ảnh theo tỉ lệ nhân (sₓ, sᵧ), đồng nhất hoặc khác nhau giữa hai chiều [3].  
- **Công thức:**  
  $$x' = s_x \times x,\quad y' = s_y \times y$$ [3].  
- **Ví dụ:** Phóng to ảnh màu gấp đôi hoặc thu nhỏ ảnh xám xuống nửa kích thước [3].

### 4. Xoay (Rotation) [4]
- **Ý chính:** Quay ảnh quanh tâm theo góc θ mà không làm biến dạng hình gốc [4].  
- **Công thức:**  
  $$x' = x\cos\theta - y\sin\theta,\quad y' = x\sin\theta + y\cos\theta$$ [4].  
- **Ví dụ:** Xoay ảnh 20° ngược chiều kim đồng hồ [4].

### 5. Dilation & Erosion (Morphological) [5]
- **Ý chính:** Dùng phép morphology để loại bỏ nhiễu hoặc làm nổi bật cấu trúc ảnh nhị phân [5].  
- **Dilation:** Mở rộng vùng sáng bằng cách gán giá trị cực đại trong vùng lân cận [5].  
- **Erosion:** Co vùng sáng bằng cách gán giá trị cực tiểu trong vùng lân cận [5].  
- **Ví dụ:** Thực hiện 3 lần dilation để làm mịn biên cạnh [5].

### 6. Ánh xạ tọa độ (Coordinate Mapping) [6]
- **Ý chính:** Tạo ma trận tọa độ mới cho mỗi pixel, có thể kết hợp nhiễu để tạo hiệu ứng đặc biệt [6].  
- **Phương pháp:** Lấy ma trận chỉ số M và cộng nhiễu q ngẫu nhiên, sau đó ánh xạ ngược lại ảnh gốc [6].  
- **Ví dụ:** Tạo hiệu ứng “rối” bằng cách thêm nhiễu ngẫu nhiên vào tọa độ [6].

### 7. Biến đổi chung (Generic Transformation) [7]
- **Ý chính:** Cho phép người dùng định nghĩa hàm ánh xạ tọa độ cá nhân hóa và áp dụng cho toàn ảnh [7].  
- **Nguyên lý:** Hàm GeoFun(outcoord) trả về (a, b) để xác định pixel đầu ra mới [7].  
- **Ví dụ:**  
  $$a = 10\cos(i/10)+i,\quad b = 10\cos(j/10)+j$$  
  tạo hiệu ứng đường sóng trên ảnh [7].

---


---

## Hướng dẫn sử dụng [9]

1. **Cài đặt:**  
2. **Chạy bài lab:** Mở `main.ipynb` và thực thi từng cell để xem kết quả [9].  
3. **Tùy chỉnh:** Thay đổi tham số vectơ dịch, tỉ lệ zoom, góc xoay, số lần dilation/erosion hoặc hàm GeoFun để quan sát các hiệu ứng khác nhau [9].

---

## Tài liệu tham khảo [9]

- Wikipedia: Image cropping [1]  
- Wikipedia: Image translation [2]  
- Wikipedia: Image scaling [3]  
- Wikipedia: Image rotation [4]  
- Slide bài giảng Nhập môn Xử lý ảnh số - Văn Lang University

