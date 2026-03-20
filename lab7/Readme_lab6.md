# Nhận diện khuôn mặt và các bộ phận

Sử dụng Haar Cascade của OpenCV để nhận diện khuôn mặt, mắt, mũi, miệng và nụ cười.

---

## 1. Các file XML cần tải

Tải từ: https://github.com/kipr/opencv/tree/master/data/haarcascades

| File | Công dụng |
|------|-----------|
| `haarcascade_frontalface_default.xml` | Nhận diện khuôn mặt |
| `haarcascade_eye.xml` | Nhận diện mắt |
| `haarcascade_mcs_nose.xml` | Nhận diện mũi |
| `haarcascade_mcs_mouth.xml` | Nhận diện miệng |
| `haarcascade_smile.xml` | Nhận diện nụ cười |

---

## 2. Các bước xử lý

### Bước 1: Đọc ảnh và chuyển sang ảnh xám
```python
img = cv2.imread('image.jpg')
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
img_gray = cv2.cvtColor(img, cv2.COLOR_BGR2GRAY)
```

### Bước 2: Phát hiện khuôn mặt
```py
faces = face_cascade.detectMultiScale(img_gray, scaleFactor=1.1, minNeighbors=5, minSize=(30, 30))
```
- scaleFactor: tỷ lệ thu nhỏ ảnh (1.05 - 1.2). Giảm để nhận nhiều hơn.

- minNeighbors: số vùng lân cận (3 - 10). Giảm để nhận nhiều hơn.

- minSize: kích thước tối thiểu. Giảm để nhận vật nhỏ.

### Bước 3: Trên mỗi khuôn mặt, phát hiện các bộ phận
```python
roi_gray = img_gray[y:y+h, x:x+w]  # Vùng quan tâm

# Phát hiện
eyes = eye_cascade.detectMultiScale(roi_gray, ...)
noses = nose_cascade.detectMultiScale(roi_gray, ...)
mouths = mouth_cascade.detectMultiScale(roi_gray, ...)
smiles = smile_cascade.detectMultiScale(roi_gray, ...)
```
### Bước 4: Lọc kết quả
- Mắt: chỉ lấy 2 mắt ở nửa trên khuôn mặt

- Mũi: chỉ lấy 1 mũi ở giữa khuôn mặt

- Miệng: chỉ lấy 1 miệng ở nửa dưới

- Nụ cười: chỉ lấy 1 nụ cười ở nửa dưới

### Bước 5: Vẽ khung và hiển thị
```python
cv2.rectangle(img, (x, y), (x + w, y + h), color, 2)
cv2.putText(img, 'Face', (x, y-5), cv2.FONT_HERSHEY_SIMPLEX, 0.5, color, 1)
plt.imshow(img)
plt.show()
```
Màu sắc phân biệt

- Khuôn mặt:	Xanh lá	(0, 255, 0)
- Mắt:	Xanh dương	(255, 0, 0)
- Mũi:	Vàng	(0, 255, 255)
- Miệng:	Cyan	(255, 255, 0)
- Nụ cười:	Đỏ	(0, 0, 255)

Cách chạy
- Tải các file XML về và đặt cùng folder với code

- Đặt ảnh cần nhận diện vào cùng folder (mặc định là `people.jpg`)

- Chạy code từ trên xuống dưới

- Xem kết quả hiển thị và số lượng in ra

Điều chỉnh tham số khi nhận diện sai

Vấn đề  và	Cách khắc phục
- Nhận diện thiếu:	Giảm `scaleFactor` (1.05), giảm `minNeighbors` (3)
- Nhận diện thừa:	Tăng `scaleFactor` (1.2), tăng `minNeighbors` (10)
- Không nhận vật nhỏ:	Giảm `minSize` (10, 10)
- Nhận diện sai vị trí:	Tăng `minNeighbors` để lọc nhiễu

Kết quả mong đợi

- Mỗi khuôn mặt sẽ hiển thị:

    - 2 mắt (khung xanh dương)

    - 1 mũi (khung vàng)

    - 1 miệng (khung cyan)

    - 1 nụ cười (khung đỏ) - nếu người trong ảnh đang cười

Kết quả in ra:

```text
Tìm thấy X khuôn mặt
Khuôn mặt tại (x,y): 2 mắt, 1 mũi, 1 miệng, 1 nụ cười
```
