# Lab 4 – Image Processing với OpenCV

## Giới thiệu

File notebook này là bài thực hành về xử lý ảnh bằng Python và thư viện OpenCV.  
Trong bài lab, em sử dụng ảnh `house.jpg` để thử các kỹ thuật phát hiện đặc trưng trong ảnh như corner detection, blob detection, SIFT, và một số ứng dụng khác trong computer vision.

Mục tiêu chính của bài là làm quen với cách OpenCV xử lý ảnh và hiểu cơ bản cách các thuật toán phát hiện đặc trưng hoạt động.

---

## Nội dung chính

Trong file code có các phần chính sau:

### 1. Đọc và hiển thị ảnh
Đầu tiên chương trình đọc ảnh `house.jpg` bằng OpenCV và hiển thị lại bằng matplotlib để kiểm tra ảnh có được load đúng hay không.

### 2. Harris Corner Detection
Áp dụng thuật toán Harris để tìm các điểm góc trong ảnh.  
Các điểm góc phát hiện được sẽ được đánh dấu màu đỏ trên ảnh.

### 3. Difference of Gaussians
Thực hiện làm mờ ảnh với hai kernel Gaussian khác nhau rồi lấy hiệu của hai ảnh để làm nổi bật các chi tiết.

### 4. Scale Selection
Thử áp dụng Gaussian blur với nhiều kích thước kernel khác nhau để quan sát sự thay đổi của ảnh theo scale.

### 5. SIFT Feature Detection
Sử dụng thuật toán SIFT để tìm các keypoints trong ảnh.  
Các keypoints này có thể dùng cho việc so khớp ảnh hoặc nhận dạng đối tượng.

### 6. Blob Detection
Dùng SimpleBlobDetector của OpenCV để phát hiện các vùng đặc trưng (blob) trong ảnh.

### 7. ORB Feature Extraction
Sử dụng ORB để trích xuất các đặc trưng của ảnh và đếm số lượng keypoints tìm được.

### 8. Image Panorama
Thử ghép ảnh bằng chức năng Stitcher của OpenCV để tạo ảnh panorama.

### 9. Feature Matching
Sử dụng BFMatcher để so khớp các feature giữa hai ảnh.

### 10. Stereo Vision
Tính disparity map từ hai ảnh để mô phỏng việc ước lượng độ sâu.

### 11. Histogram Feature
Tính histogram của ảnh để xem phân bố cường độ pixel.

### 12. SIFT + Histogram
Trích xuất descriptor bằng SIFT và tạo histogram để biểu diễn đặc trưng của ảnh.

---

## Thư viện sử dụng

- OpenCV
- NumPy
- Matplotlib

---

## Kết luận

Qua bài lab này đã sử dụng nhiều kỹ thuật cơ bản trong computer vision như phát hiện góc, phát hiện keypoint, blob detection, và feature matching. Những kỹ thuật này thường được dùng trong các bài toán như nhận dạng ảnh, ghép ảnh panorama hoặc tìm kiếm ảnh theo nội dung.