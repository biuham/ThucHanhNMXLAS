# Nhập Môn Xử Lý Ảnh Số - Lab 4  

**Sinh viên thực hiện:** Nguyễn Hữu Thịnh **MSSV:** 2174802010323

**Môn học:** Nhập môn Xử lý ảnh số  

**Giảng viên:** Đỗ Hữu Quân

---

## Giới thiệu  
## Phân vùng ảnh là chia ảnh thành các vùng đồng nhất để tách nền và đối tượng.  
## Kết hợp với biến đổi morphology giúp loại nhiễu và lấp đầy lỗ trống, tiền xử lý cho bài toán nhận dạng.  

## 1. Phân vùng theo Histogram (Thresholding)  
## 1.1 Otsu’s Method  
## - Ý tưởng: Tự động chọn ngưỡng tối ưu để phân tách hai lớp sáng–tối.  
## - Công thức: Chọn t* minimize σ²w(t) = ω₀(t)σ₀²(t) + ω₁(t)σ₁²(t).  
## - Ví dụ: Nếu histogram có hai đỉnh tại 50 và 200, t* ≈ 125 để tách hai vùng.  

## 1.2 Adaptive Thresholding  
## - Ý tưởng: Tính ngưỡng riêng cho từng biến nhỏ (block) nhằm xử lý điều kiện ánh sáng không đồng nhất.  
## - Công thức: t(x,y) = mean(block) – C.  
## - Ví dụ: Với block 39×39 và C=10, ngưỡng động cho phép tách rõ đối tượng trên nền.  

## 2. Phân vùng theo Region (Watershed)  
## - Ý tưởng: Xem ảnh grayscale như địa hình, “ngập nước” từ các marker để phân chia vùng.  
## - Bước 1: Threshold + erosion → sure foreground.  
## - Bước 2: Distance transform để xác định marker.  
## - Bước 3: Áp watershed trên ảnh gốc với marker → phân vùng.  
## - Ví dụ: Phân tách từng hạt giống (cell) trên nền trắng thành vùng riêng.  

## 3. Biến đổi Morphology  
## - Dilation (A ⊕ B): Mở rộng vùng foreground.  
## - Erosion (A ⊖ B): Thu nhỏ vùng foreground.  
## - Opening (A ◦ B = (A ⊖ B) ⊕ B): Loại bỏ nhiễu nhỏ.  
## - Closing (A • B = (A ⊕ B) ⊖ B): Lấp đầy lỗ hổng, nối vùng tách rời.  
## - Ví dụ: Với structuring element 3×3 hình dấu cộng, dilation nở 1px mọi hướng, erosion co 1px.  

## Tài liệu tham khảo  
## - Gonzalez & Woods, _Digital Image Processing_  
## - OpenCV Docs: https://docs.opencv.org/  
## - scikit-image: https://scikit-image.org/  
