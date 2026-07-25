# ✅ Hệ Thống Thi HSK 1 - Hoàn Toàn Tự Động

## 🎯 Quy Trình Học Sinh

Học sinh **KHÔNG cần đăng nhập** - Chỉ cần 4 bước:

```
1️⃣ Mở link → 2️⃣ Điền tên + lớp → 3️⃣ Chọn đề → 4️⃣ Làm bài → Nộp → Xong!
```

---

## 📊 Luồng Dữ Liệu

```
[Học sinh]
    ↓
[index.html - Chọn đề thi]
    ↓
[exam-v2.html - Làm bài]
  Nhập: Tên + Lớp + Email (tùy chọn)
  Làm: 15 phút nghe (20 câu) + 17 phút đọc (20 câu)
    ↓
[exam-v2.js - Tính điểm & lưu]
  Điểm: 2.5/câu × 40 câu = 100 điểm
  Xếp loại: Xuất sắc / Tốt / Khá / Đạt / Cần cố gắng
    ↓
[Google Apps Script - Backend API]
  doPost() - Nhận kết quả từ học sinh
  Validation - Kiểm tra dữ liệu
  Lưu vào Google Sheet
    ↓
[Google Sheet - "Kết quả thi"]
  STT | Tên | Lớp | Email | Mã đề | Điểm Nghe | Điểm Đọc | Tổng | Xếp loại | Ngày thi
```

---

## 🔄 Các Thay Đổi Vừa Thêm (Class Field)

### exam-v2.html
✅ Thêm input "Lớp" giữa Tên và Email
- Học sinh **bắt buộc** phải nhập lớp
- Placeholder: "VD: 10A1, 10A2, ..."

### exam-v2.js
✅ Capture `studentClass` từ input
✅ Validate lớp (bắt buộc phải có)
✅ Gửi lớp trong payload tới Google Apps Script

### google_apps_script_complete.gs
✅ Nhận `studentClass` từ payload
✅ Lưu vào Google Sheet (cột 3 - sau tên)
✅ Update header: STT | Tên | **Lớp** | Email | Mã đề | ...
✅ viewResults() hiển thị cột Lớp

---

## 📋 Google Sheet Structure (Updated)

### Sheet "Kết quả thi" - Headers
| STT | Tên học sinh | Lớp | Email | Mã đề | Điểm Nghe | Điểm Đọc | Tổng điểm | Xếp loại | Ngày thi |
|-----|--------|------|-------|-------|-----------|----------|-----------|---------|----------|
| 1   | Nguyễn Văn A | 10A1 | a@example.com | H11115 | 42 | 45 | 87 | ✅ Tốt | 25/07/2026 |
| 2   | Trần Thị B | 10A2 | b@example.com | H11116 | 40 | 38 | 78 | 👍 Khá | 25/07/2026 |

---

## 🚀 Các Bước Deploy

### Bước 1: Copy Google Apps Script
1. Mở Google Sheet
2. Tools → Script Editor
3. Xoá code cũ
4. Copy toàn bộ code từ `google_apps_script_complete.gs`
5. Paste vào Script Editor
6. Ctrl+S để lưu

### Bước 2: Chạy Test
1. Click Run → testAPI()
2. Cấp quyền nếu được hỏi
3. Kiểm tra Executions → Success

### Bước 3: Deploy Web App
1. Click Deploy → Select type → Web app
2. Execute as: Tài khoản Google của bạn
3. Who has access: Anyone
4. Click Deploy
5. **📋 Copy URL deployment** (dài như: https://script.google.com/macros/d/ABC123/usercripts)

### Bước 4: Tạo Link Thi
Thay `YOUR_DEPLOYMENT_URL` vào link:
```
https://tiengtrungthaoNguyen.github.io/Thi-HSK1/?scriptUrl=YOUR_DEPLOYMENT_URL
```

**Ví dụ:**
```
https://tiengtrungthaoNguyen.github.io/Thi-HSK1/?scriptUrl=https://script.google.com/macros/d/1ABC2XYZ-def456/usercripts
```

---

## ✅ Test Hệ Thống (3 Bước)

### Test 1: Link Load
- Mở link thi
- ✅ Hiển thị trang chủ với 5 đề thi

### Test 2: Làm Bài
- Chọn đề H11115
- Nhập: Tên = "Test", Lớp = "10A1"
- Click "Bắt Đầu"
- ✅ Hiển thị câu hỏi (hoặc "No questions" nếu chưa thêm)

### Test 3: Kiểm Tra Google Sheet
- Quay lại Google Sheet
- Mở sheet "Kết quả thi"
- ✅ Có 1 hàng mới với: Tên = "Test", Lớp = "10A1"

---

## 📝 Hệ Thống Ghi Nhận Gì?

Mỗi lần học sinh nộp bài, Google Sheet sẽ tự động lưu:

1. **STT** - Số thứ tự
2. **Tên học sinh** - Tên nhập vào
3. **Lớp** - Lớp nhập vào (NEW!)
4. **Email** - Email (nếu có)
5. **Mã đề** - Đề thi chọn
6. **Điểm Nghe** - Phần nghe (0-50)
7. **Điểm Đọc** - Phần đọc (0-50)
8. **Tổng điểm** - Tổng (0-100)
9. **Xếp loại** - Grade (Xuất sắc / Tốt / Khá / Đạt / Cần cố gắng)
10. **Ngày thi** - Thời gian nộp

---

## 🎓 Chia Link Cho Học Sinh

Sau khi deploy, chia link này với học sinh:

```
https://tiengtrungthaoNguyen.github.io/Thi-HSK1/?scriptUrl=[YOUR_DEPLOYMENT_URL]
```

**Lưu ý:**
- Đừng quên thay `[YOUR_DEPLOYMENT_URL]`
- Chia link qua email / Zalo / Facebook / ...
- Học sinh không cần đăng nhập - chỉ cần mở link
- Kết quả tự động lưu vào Google Sheet của bạn

---

## ⚙️ File Cần Deploy

### GitHub (Đã có tất cả)
- ✅ index.html - Trang chủ
- ✅ exam-v2.html - Trang thi (+ input Lớp)
- ✅ js/exam-v2.js - Logic thi (+ handle Lớp)
- ✅ css/style.css - Styling

### Google Sheet
- ✅ google_apps_script_complete.gs - Backend API (+ handle Lớp)
- ✅ "Danh_sach" sheet - Danh sách đề
- ✅ H11115-H11119 sheets - Nội dung câu hỏi (40 câu/sheet)
- ✅ "Kết quả thi" sheet - Tự động tạo (+ Lớp column)

---

## 🔐 Bảo Mật & Quyền Riêng Tư

**Không có:**
- ❌ Đăng nhập / Tài khoản
- ❌ Cookie / Session
- ❌ Lưu dữ liệu cục bộ (lưu vào Google Sheet)
- ❌ Theo dõi cá nhân

**Có:**
- ✅ Lưu tên + lớp + email (để quản lý kết quả)
- ✅ Lưu điểm + xếp loại (để đánh giá)
- ✅ Lưu timestamp (để biết khi nào nộp)

---

## 💡 Tips Quản Lý Lớp

### Cách 1: Grouping Học Sinh Bằng Lớp
Sau khi thi xong, bạn có thể:
1. Sắp xếp Google Sheet theo cột "Lớp"
2. Dễ dàng xem kết quả từng lớp
3. Tính trung bình lớp bằng hàm AVERAGE()

### Cách 2: Filter Theo Lớp
Google Sheet → Data → Filter
- Click "Lớp"
- Chọn lớp để xem

### Cách 3: Biểu Đồ Theo Lớp
- Insert → Chart
- X-axis: Lớp
- Y-axis: Trung bình điểm

---

## 🎉 Done!

Hệ thống thi HSK 1 **hoàn toàn tự động** sẵn sàng:
- ✅ Học sinh không cần login
- ✅ Kết quả tự động lưu
- ✅ Quản lý theo lớp dễ dàng
- ✅ Không cần phải thu bài thủ công

**Tất cả bạn cần làm:**
1. Deploy Google Apps Script
2. Copy URL deployment
3. Chia link cho học sinh
4. Chờ kết quả chảy vào Google Sheet 📊

---

**Status:** ✅ **READY TO DEPLOY!**

