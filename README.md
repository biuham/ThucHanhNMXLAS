# Nhập Môn Xử Lý Ảnh Số - Lab 4  
## **Phân Vùng Ảnh & Biến Đổi Đối Tượng**  
**Sinh viên thực hiện:** Nguyễn Hữu Thịnh

**MSSV:** 2174802010323

**Môn học:** Nhập môn Xử lý ảnh số  

**Giảng viên:** Đỗ Hữu Quân  

---

## Giới thiệu

Bài lab tập trung vào các kỹ thuật **phân vùng ảnh (image segmentation)** và **biến đổi hình thái học (morphological transformations)**. Qua bài này, sinh viên sẽ:

- Hiểu và thực hành phân vùng ảnh theo histogram và region
- Áp dụng các phép biến đổi hình thái học cơ bản
- Thực hiện các thao tác chọn và biến đổi đối tượng trong ảnh

---

## Công nghệ sử dụng

- **Python**: Ngôn ngữ chính
- **OpenCV**: Xử lý ảnh máy tính
- **Pillow (PIL)**: Đọc và ghi ảnh
- **NumPy**: Xử lý mảng dữ liệu ảnh
- **SciPy**: Biến đổi hình thái học
- **scikit-image**: Lọc và phân ngưỡng
- **Matplotlib**: Hiển thị ảnh

---

## Chi tiết phương pháp & kỹ thuật

### 1. Phân vùng ảnh theo Histogram

#### Otsu’s Thresholding

**Ý tưởng:** Tìm ngưỡng tự động sao cho độ chênh lệch giữa các lớp được tối đa.

**Code mẫu:**
```python
from skimage.filters.thresholding import threshold_otsu

thres = threshold_otsu(image_array)
segmented = image_array > thres
```

#### Adaptive Thresholding

**Ý tưởng:** Tính ngưỡng cục bộ theo từng vùng nhỏ thay vì dùng một ngưỡng toàn ảnh.

**Code mẫu:**
```python
from skimage.filters import threshold_local

local_thresh = threshold_local(image_array, 39, offset=10)
binary_adaptive = image_array > local_thresh
```

---

### 2. Phân vùng ảnh theo Region - Thuật toán Watershed

**Quy trình:**
- Chuyển ảnh sang grayscale
- Phân ngưỡng nhị phân với Otsu
- Tính biến đổi khoảng cách (distance transform)
- Áp dụng Watershed

**Code mẫu:**
```python
import cv2
from scipy.ndimage import label

gray = cv2.cvtColor(data, cv2.COLOR_BGR2GRAY)
_, binary = cv2.threshold(gray, 0, 255, cv2.THRESH_BINARY_INV + cv2.THRESH_OTSU)

dist_trans = cv2.distanceTransform(binary, cv2.DIST_L2, 3)
labelled, n_obj = label(dist_trans)

cv2.watershed(data, labelled)
```

---

### 3. Biến đổi hình thái học (Morphological Transformations)

| Phép toán     | Mục đích            | Code mẫu |
|---------------|---------------------|----------|
| **Dilation**  | Mở rộng đối tượng   | `nd.binary_dilation(data, iterations=50)` |
| **Erosion**   | Thu nhỏ đối tượng   | `nd.binary_erosion(data, structure=s, iterations=50)` |
| **Opening**   | Loại bỏ nhiễu       | `nd.binary_opening(data, structure=s, iterations=25)` |
| **Closing**   | Lấp lỗ hổng         | `nd.binary_closing(data, structure=s, iterations=50)` |

#### Structuring Element (Cấu trúc phần tử)

```python
s = [[0, 1, 0],
     [1, 1, 1],
     [0, 1, 0]]
```

---

## Tài liệu tham khảo

- [Digital Image Processing - Rafael C. Gonzalez](https://www.amazon.com/Digital-Image-Processing-Rafael-Gonzalez/dp/013168728X)  
- [Scikit-image Documentation](https://scikit-image.org/)  
- [OpenCV Documentation](https://docs.opencv.org/)  
- Slide bài giảng Nhập môn Xử lý ảnh số - Văn Lang University
