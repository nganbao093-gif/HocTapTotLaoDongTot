# Bàn Việc

To-do list vui: gõ việc như chat, tự xếp nhóm, ma trận Eisenhower, Top 3 hôm nay, việc lặp lại, bước nhỏ, bấm giờ 25 phút, tổng kết tuần và thi đua với bạn bè bằng mã 6 ký tự.

Website gồm 2 phần:

- **Bản cơ bản** (chỉ cần GitHub): dùng được ngay, việc lưu trên trình duyệt của từng người.
- **Đồng bộ + thi đua** (thêm Firebase, miễn phí): đăng nhập Google, dùng trên nhiều máy, kết nối bạn bè, bảng xếp hạng tuần.

---

## Bước 1. Đưa website lên GitHub (khoảng 5 phút)

1. Đăng nhập [github.com](https://github.com), bấm **New repository**.
2. Đặt tên, ví dụ `ban-viec`, chọn **Public**, bấm **Create repository**.
3. Trong repo mới, bấm **uploading an existing file**, kéo thả **toàn bộ file** trong thư mục này (`index.html`, `firebase-config.js`, `manifest.json`, `icon.svg`, `firestore.rules`, `README.md`), rồi bấm **Commit changes**.

## Bước 2. Bật GitHub Pages

1. Trong repo, vào **Settings → Pages**.
2. Ở **Source**, chọn **Deploy from a branch**; Branch chọn **main**, thư mục **/ (root)**, bấm **Save**.
3. Đợi 1–2 phút, tải lại trang. Link website hiện ở đầu trang, dạng:
   `https://<tên-github-của-bạn>.github.io/ban-viec/`

Đến đây website đã chạy được. Gửi link cho bạn bè là họ dùng được, việc lưu trên trình duyệt của mỗi người.

---

## Bước 3. Bật đồng bộ và thi đua với Firebase (khoảng 10 phút, miễn phí)

### 3.1. Tạo dự án
1. Vào [console.firebase.google.com](https://console.firebase.google.com), bấm **Create a project** (hoặc **Add project**), đặt tên `ban-viec`, có thể tắt Google Analytics.
2. Trong dự án, bấm biểu tượng **Web `</>`** để thêm ứng dụng web, đặt tên bất kỳ, bấm **Register app**.
3. Firebase hiện một đoạn `firebaseConfig = { apiKey: ..., ... }`. Chép 6 giá trị đó vào file **`firebase-config.js`** (thay chỗ để trống).

> Các giá trị này được thiết kế để công khai trên website, không phải mật khẩu. Dữ liệu được bảo vệ bằng quy tắc ở bước 3.3.

### 3.2. Bật đăng nhập Google
1. Menu trái: **Build → Authentication → Get started**.
2. Tab **Sign-in method** → chọn **Google** → bật **Enable**, chọn email hỗ trợ → **Save**.
3. Tab **Settings → Authorized domains** → **Add domain** → nhập `<tên-github-của-bạn>.github.io` (không có `https://` và không có `/ban-viec`).

### 3.3. Tạo cơ sở dữ liệu
1. Menu trái: **Build → Firestore Database → Create database**, chọn vị trí gần nhất (ví dụ `asia-southeast1`, Singapore), chọn **Start in production mode**.
2. Tab **Rules**: xóa hết nội dung cũ, dán toàn bộ nội dung file **`firestore.rules`**, bấm **Publish**.

### 3.4. Cập nhật lên GitHub
Vào repo, mở file `firebase-config.js` → biểu tượng bút chì → dán cấu hình → **Commit changes**. Đợi 1–2 phút rồi mở lại website.

Trên website sẽ xuất hiện nút **👤**: bấm để đăng nhập Google. Việc đang có trên trình duyệt sẽ tự chuyển lên tài khoản ở lần đăng nhập đầu tiên.

---

## Thi đua với bạn bè
1. Mở mục **🏁 Thi đua với bạn bè** ở cuối trang, sao chép **mã 6 ký tự** của bạn và gửi cho bạn bè.
2. Nhập mã của họ vào ô **Kết nối**. Hai người cần nhập mã của nhau để cùng thấy nhau.
3. Điểm tuần = số việc xong + 1 điểm thưởng nếu việc quan trọng + 1 điểm thưởng nếu việc nằm trong Top 3 hôm nay. Reset mỗi thứ Hai.

**Riêng tư:** danh sách việc chỉ chủ tài khoản đọc được. Bảng thi đua chỉ chứa tên hiển thị, mã và điểm số; người đã đăng nhập vào website có thể đọc phần này.

## Cài như app trên điện thoại
Mở website bằng Safari (iPhone) hoặc Chrome (Android) → **Chia sẻ / Menu → Thêm vào Màn hình chính**.

## Giới hạn
- Tự phân nhóm dựa vào từ khóa và học từ những lần bạn tự đổi nhóm (bản trong Claude có thêm AI, bản website thì không).
- Bộ đếm 25 phút chỉ chạy khi trang đang mở; website không gửi thông báo nhắc việc.
- Gói Firebase miễn phí (Spark) dư sức cho vài chục người dùng.
