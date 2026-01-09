# Bài thực hành: Xử lý ảnh với Pillow và OpenCV 
Sinh viên thực hiện: Nguyễn Hoàng Vương

MSSV: 2374802010574

Môn học: Thị giác máy tính (Computer Vision)

## Tổng quan
Dự án này bao gồm các bài thực hành giới thiệu về xử lý ảnh kỹ thuật số sử dụng ngôn ngữ lập trình Python. Nội dung tập trung vào việc làm quen, thao tác cơ bản với ảnh thông qua hai thư viện phổ biến nhất hiện nay là Pillow (PIL) và OpenCV.


### Cấu trúc thư mục
#### 2.1.1. PIL Library
Nội dung chính:

Notebook này giới thiệu cách xử lý ảnh cơ bản bằng thư viện PIL (Pillow), bao gồm:
- Mở và lưu ảnh
- Thay đổi kích thước, cắt ảnh
- Xoay và biến đổi ảnh cơ bản  
Phù hợp cho người mới bắt đầu làm quen với xử lý ảnh trong Python.

- Giới thiệu về thư viện Pillow (Python Imaging Library).

- Cách tải và quản lý đường dẫn file ảnh.

- Tải ảnh vào Python sử dụng module Image của PIL.

- Chuyển đổi ảnh sang ảnh xám (Gray Scale), lượng tử hóa (Quantization) và các kênh màu.

- Chuyển đổi ảnh PIL sang mảng NumPy để xử lý.

- Sử dụng hàm hỗ trợ get_concat_h để ghép ảnh.

#### 2.1.2. OpenCV Library


Nội dung chính:

Giới thiệu về thư viện OpenCV (Open Source Computer Vision Library).

- Đọc và hiển thị ảnh bằng OpenCV
- Xử lý ảnh dưới dạng ma trận NumPy
- Thực hiện các thao tác xử lý ảnh hiệu quả hơn so với PIL
- So sánh đặc điểm giữa OpenCV và PIL  



Dữ liệu (Images)
Các notebook được thiết kế để tự động tải các ảnh mẫu cần thiết từ Internet thông qua lệnh wget. Các ảnh sử dụng bao gồm:

lenna.png

baboon.png

barbara.png

