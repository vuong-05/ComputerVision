# Phân đoạn ảnh - Các kỹ thuật cơ bản

Code thực hiện 6 phương pháp phân đoạn ảnh trên ảnh `dog.jpg` và `vantay.webp`.

## Các phương pháp

### 1. Thresholding
Dùng ngưỡng cố định 127 và ngưỡng thích ứng để phân tách đối tượng khỏi nền. Cách đơn giản nhất.

```python
# Ngưỡng cố định: pixel > 127 thành trắng, còn lại đen
ret, thresh_binary = cv.threshold(img_gray, 127, 255, cv.THRESH_BINARY)

# Ngưỡng thích ứng: ngưỡng thay đổi theo vùng
thresh_adaptive = cv.adaptiveThreshold(img_gray, 255, cv.ADAPTIVE_THRESH_GAUSSIAN_C, cv.THRESH_BINARY, 11, 2)
```

### 2. Otsu
Tự động tìm ngưỡng tối ưu dựa trên histogram. Thường dùng cho ảnh vân tay.

```py
# Otsu tự tính ngưỡng, không cần nhập số
ret_otsu, thresh_otsu = cv.threshold(img_gray, 0, 255, cv.THRESH_BINARY + cv.THRESH_OTSU)
```

### 3. K-means Clustering
Gom nhóm các pixel có màu giống nhau thành K cụm.

```py
# Chuyển ảnh thành mảng pixel
pixel_vals = img_rgb.reshape((-1, 3))
pixel_vals = np.float32(pixel_vals)

# K-means với K=3 cụm
k = 3
criteria = (cv.TERM_CRITERIA_EPS + cv.TERM_CRITERIA_MAX_ITER, 100, 0.2)
retval, labels, centers = cv.kmeans(pixel_vals, k, None, criteria, 10, cv.KMEANS_RANDOM_CENTERS)

# Gán màu cho từng pixel theo cụm
segmented_data = centers[labels.flatten()]
segmented_image = segmented_data.reshape(img_rgb.shape)
```

### 4. Region Growing
Chọn 1 điểm gốc, lan sang các pixel lân cận có giá trị tương tự.

```py
seed_value = img[seed[1], seed[0]]
if abs(int(img[y, x]) - int(seed_value)) <= threshold:
    segmented[y, x] = 255
```

- lấy giá trị tại điểm gốc `seed_value`

- so sánh pixel lân cận, nếu chênh lệch trong ngưỡng thì tô trắng

- dùng hàng đợi để duyệt các pixel xung quanh


### 5. Split and merge

```py
std_val = np.std(block)
if std_val < threshold:
    segmented[y:y+min_block_size, x:x+min_block_size] = 255
```

- `np.std`: tính độ lệch chuẩn của khối, đo độ đồng nhất

- độ lệch chuẩn nhỏ → khối đồng nhất → gộp lại

### 6. Edge-based
```py
edges = cv.Canny(img_gray, 50, 150)
contours, hierarchy = cv.findContours(edges, cv.RETR_EXTERNAL, cv.CHAIN_APPROX_SIMPLE)
cv.drawContours(img_contour, contours, -1, (255, 0, 0), 2)
```

- `Canny`: phát hiện biên cạnh

- `findContours`: tìm đường bao từ biên

- `drawContours`: vẽ đường bao lên ảnh

 