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
- **Ý chính:** Đảo ngược giá trị pixel, biến vùng sáng thành tối và ngược lại.  
- **Công thức:** $$s = L - 1 - r$$.  
- **Ví dụ:** Pixel 100 → 155 (255 - 100).

### 2. Log Transformation  
- **Ý chính:** Khuếch đại pixel nhỏ, làm rõ vùng tối.  
- **Công thức:** $$s = c \times \log(1 + r)$$.  
- **Ví dụ:** Pixel 10 sáng lên nhiều hơn pixel 200.

### 3. Gamma Correction  
- **Ý chính:** Điều chỉnh độ sáng tổng thể bằng tham số γ.  
- **Công thức:** $$s = c \times r^\gamma$$.  
- **Ví dụ:** γ = 0.5 → ảnh sáng; γ = 2.0 → ảnh tối.

### 4. Histogram Equalization  
- **Ý chính:** Phân phối lại mức xám để tăng độ tương phản sử dụng CDF.  
- **Ví dụ:** Dải 50–150 mở rộng thành 0–255.

### 5. Contrast Stretching  
- **Ý chính:** Kéo giãn tuyến tính dải pixel.  
- **Công thức:** $$s = \frac{255\,(r - a)}{b - a}$$.

### 6. FFT & Butterworth Filtering  
- **FFT:** Chuyển ảnh sang miền tần số để lọc nhiễu hoặc nâng cao cạnh.  
- **Butterworth:** $$H(u,v) = \frac{1}{1 + (D(u,v)/D_0)^{2n}}$$.

---
## Hướng dẫn sử dụng  
1. Cài đặt: `pip install pillow numpy matplotlib scipy`  
2. Chạy: Mở Jupyter Notebook và thực thi các cell từng bước. 
3. Tùy chỉnh: Thay đổi tham số γ, D₀ để quan sát kết quả.

---

## Tài liệu tham khảo  
1. Gonzalez R.C., Woods R.E., Digital Image Processing.  
2. Jain A.K., Fundamentals of Digital Image Processing.  
3. Oppenheim A.V., Schafer R.W., Discrete-Time Signal Processing.  
4. Russ J.C., The Image Processing Handbook.  
5. Slide bài giảng Nhập môn Xử lý ảnh số - Văn Lang University
