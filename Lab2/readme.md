# Bài thực hành: Thao tác ảnh cơ bản với PIL và OpenCV

Sinh viên thực hiện: Nguyễn Hoàng Vương

MSSV: 2374802010574

Môn học: THỊ GIÁC MÁY TÍNH (COMPUTER VISION)


## Tổng quan
Dự án này trình bày các thao tác xử lý ảnh cơ bản gồm **lật ảnh (flip)** và **đối xứng ảnh (mirror)** bằng hai thư viện phổ biến trong Python là **PIL (Pillow)** và **OpenCV**.  

### 2.2.1. Thao tác ảnh cơ bản với PIL

#### Công nghệ sử dụng
- PIL (Pillow)
- NumPy
- Matplotlib

#### Nội dung chính
- Mở ảnh bằng `Image.open()`
- Chuyển ảnh sang ảnh xám (grayscale)
- Giảm mức xám bằng `quantize()`
- Tách các kênh màu RGB
- Ghép ảnh theo chiều ngang
- Chuyển ảnh PIL sang NumPy array
- Truy cập và phân tích giá trị pixel

#### Kết quả
- Hiểu cấu trúc ảnh RGB
- Biết cách thao tác ảnh bằng PIL và NumPy
- Quan sát được ảnh sau khi biến đổi

---

### 2.2.2. Thao tác ảnh cơ bản với OpenCV

#### Công nghệ sử dụng
- OpenCV (cv2)
- NumPy
- Matplotlib

#### Nội dung chính
- Đọc ảnh bằng `cv2.imread()`
- Chuyển hệ màu từ BGR sang RGB
- Lật ảnh theo trục x (vertical flip)
- Lật ảnh theo trục y (horizontal flip)
- Che một vùng ảnh bằng NumPy
- Vẽ hình chữ nhật lên ảnh
- Ghi chữ lên ảnh bằng OpenCV

#### Kết quả
- Hiểu sự khác biệt giữa BGR và RGB
- Thực hiện được các phép biến đổi ảnh cơ bản
- Biết cách vẽ và chú thích trực tiếp lên ảnh

---

## Kết luận (So sánh PIL và OpenCV)

- **PIL (Pillow)**:
  - Cú pháp đơn giản, dễ đọc, dễ học.
  - Phù hợp cho các thao tác cơ bản như mở ảnh, chuyển màu, crop, flip.
  - Thích hợp cho người mới và các bài xử lý ảnh nhẹ.

- **OpenCV**:
  - Mạnh hơn và linh hoạt hơn trong xử lý ảnh.
  - Hỗ trợ nhiều phép biến đổi nâng cao, thao tác pixel nhanh.
  - Thường dùng trong các bài toán thị giác máy tính và xử lý ảnh chuyên sâu.

Tóm lại: **PIL dễ dùng cho xử lý cơ bản**, còn **OpenCV phù hợp cho các bài toán phức tạp**.