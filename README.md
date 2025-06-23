Nhập Môn Xử Lý Ảnh Số - Lab 2

Biến Đổi Cường Độ Ảnh Grayscale

Sinh viên thực hiện: Nguyễn Hữu Thịnh MSSV: 2174802010323

Môn học: Nhập môn Xử lý ảnh số

Giảng viên: Đỗ Hữu Quân

Giới thiệu
Bài lab này thực hiện các phép biến đổi cường độ cơ bản trên ảnh xám để:

Tăng cường độ tương phản và chất lượng ảnh

Làm nổi bật chi tiết trong vùng tối/sáng

Áp dụng lọc tần số với biến đổi Fourier

Công nghệ sử dụng
Python: Ngôn ngữ chính

PIL/NumPy: Xử lý ảnh và mảng

SciPy: Biến đổi Fourier

Matplotlib: Hiển thị kết quả

Chi tiết các phép biến đổi
1. Biến đổi ảnh đảo ngược (Negative Transformation)
Ý chính: Đảo ngược giá trị pixel để biến vùng sáng thành tối

Ví dụ: Pixel 100 → 255 - 100 = 155

Ứng dụng: Ảnh X-ray, CT scan

2. Biến đổi logarit (Log Transformation)
Ý chính: Khuếch đại pixel nhỏ, làm rõ vùng tối

s=c×log(1+r)

Ví dụ: Pixel tối (10) được làm sáng nhiều hơn pixel sáng (200)

Ứng dụng: Ảnh vệ tinh, ảnh y khoa

3. Biến đổi Gamma (Power-law Transformation)
Ý chính: Điều chỉnh độ sáng tổng thể

Ví dụ:

γ < 1 (0.5): ảnh sáng lên

γ > 1 (2.0): ảnh tối đi

Ứng dụng: Hiệu chỉnh màn hình

4. Cân bằng Histogram
Ý chính: Phân bố lại mức xám để tăng tương phản

Nguyên lý: Sử dụng hàm phân phối tích lũy (CDF)

Ví dụ: Ảnh tối (50-150) → mở rộng (0-255)

5. Kéo giãn tương phản (Contrast Stretching)
Ý chính: Mở rộng dải pixel tuyến tính
 
Ví dụ: Dải (50-200) → (0-255)

6. Biến đổi Fourier & Lọc Butterworth
Ý chính:

FFT: Chuyển sang miền tần số
Lọc thông thấp: Làm mịn, khử nhiễu
Lọc thông cao: Làm nổi cạnh
Ví dụ: D₀ = 30 quyết định ngưỡng lọc
   
Hướng dẫn sử dụng
Cài đặt: pip install pillow numpy matplotlib scipy

Chạy: Mở Jupyter Notebook và thực thi từng cell

Tùy chỉnh: Thay đổi tham số gamma, D₀ để quan sát hiệu ứng

Tài liệu tham khảo
Digital Image Processing - Rafael C. Gonzalez

Slide bài giảng - Văn Lang University

SciPy Documentation
