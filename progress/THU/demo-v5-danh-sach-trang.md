# Danh sách trang – Demo v5 "Summit Your Drawing" (Thảo Cầm Viên)

Liệt kê theo đúng thứ tự flow đang chạy trong demo v5 (`/workspace/summit-demo/`). Ảnh chụp nằm ở `/workspace/summit-demo/screenshots/v5/`. Style chung: nền trắng, nét đen mảnh, nút bo tròn viền đen, điểm nhấn vàng nhạt (#fff3a6). Bản đồ giữ nguyên art v4.

## Bước 1 – Mở app

### 1. Màn chào (Welcome)
- Flow: điểm bắt đầu, trước lần quét NFC đầu tiên
- Thành phần:
  - Badge "Demo v5 · Thảo Cầm Viên"
  - Tiêu đề "Summit Your Drawing", 1 dòng mô tả
  - Hình minh họa line art đen (capybara, voi, hồng hạc) đứng trên một đường kẻ
  - Dòng chú thích nhỏ "Demo giả lập NFC · lần đầu mở chuồng Capybara"
  - Nút chính "Quét NFC" (vàng nhạt)
  - Link "Reset demo" (có hộp xác nhận); giữ lâu vào tiêu đề cũng reset
- Ảnh: `screenshots/v5/01-welcome.png`

### 2. Chọn chuồng (giả lập NFC)
- Flow: chỉ hiện khi bấm "Quét NFC" ở màn chào mà đã có tranh (lần đầu thì vào thẳng bảng vẽ Capybara)
- Thành phần:
  - Tiêu đề "Chọn chuồng", mô tả
  - Lưới 2 cột 15 thẻ con vật; mỗi thẻ có trạng thái "Đã vẽ" / "Chưa vẽ" (thẻ đã vẽ tô vàng nhạt)
  - Nút "Quay lại"
- Ảnh: chưa chụp ở v5 (màn phụ của demo, ít dùng)

## Bước 2 – Quét NFC lần đầu và vẽ

### 3. Bảng vẽ + onboarding lần đầu (popup tối)
- Flow: lần quét NFC đầu tiên. Chỉ hiện 1 lần (lưu cờ `onboarded`, Reset demo sẽ hiện lại)
- Thành phần:
  - Lớp tối phủ toàn màn bảng vẽ
  - Card giữa màn: "Bạn có 60s để vẽ hình con vật [tên con vật]"
  - 2 nút: "Bỏ qua" (viền trắng) → vào thẳng bảng vẽ, "Tiếp theo" (vàng) → bắt đầu hướng dẫn
  - Thời gian chưa chạy trong lúc onboarding
- Ảnh: `screenshots/v5/02-first-scan-intro.png`

### 4. Bảng vẽ – hướng dẫn từng bước (coach-mark)
- Flow: sau khi bấm "Tiếp theo" ở popup lần đầu
- Thành phần chung mỗi bước: màn tối, vòng sáng khoanh đúng thành phần, bong bóng note có mũi nhọn chỉ vào thành phần, 5 chấm báo bước, nút "Bỏ qua" và "Tiếp theo". Bấm "Tiếp theo" ở bước 5 thì vào bảng vẽ và đồng hồ bắt đầu chạy
- 5 trạng thái:
  - a) Thanh thời gian – "Thời gian còn lại của bạn" → `screenshots/v5/03-coach-1.png`
  - b) Bút vẽ – "Dùng để vẽ" → `screenshots/v5/03-coach-2.png`
  - c) Hoàn tác – "Hoàn tác phần bạn vừa vẽ" → `screenshots/v5/03-coach-3.png`
  - d) Tẩy – "Dùng để xóa" → `screenshots/v5/03-coach-4.png`
  - e) Hoàn thành – "Dùng khi bạn đã hoàn thành bức vẽ" → `screenshots/v5/03-coach-5.png`

### 5. Bảng vẽ (Artboard)
- Flow: vẽ con vật trong 60 giây (lần đầu sau onboarding, các lần sau vào thẳng)
- Thành phần:
  - Tên con vật ở trên giữa
  - Thanh thời gian: thanh chạy + số đếm ngược (1:00 → 0:00). Trạng thái cảnh báo 10 giây cuối: ô số đổi nền đen chữ trắng
  - Khung vẽ bo tròn viền đen
  - Hàng công cụ nút tròn: Bút vẽ, Hoàn tác, Tẩy (nút đang chọn tô vàng)
  - Công tắc "Gợi ý": bật thì hiện hình gợi ý con vật màu xám mờ trong khung
  - Nút "Hoàn thành" (vàng) ở góc phải dưới
  - Hết 60 giây thì tự nộp tranh
- Ảnh: `screenshots/v5/04-artboard-hoan-thanh.png`

## Bước 3 – Sau khi bấm Hoàn thành

### 6. Màn kết quả – con vật thường (ta-da + fact)
- Flow: ngay sau khi bấm "Hoàn thành" hoặc hết giờ
- Thành phần:
  - Animation: tranh vừa vẽ thu nhỏ từ khung vẽ vào khung vuông bo tròn ở trên giữa
  - Hiệu ứng ta-da phía sau khung: nét line đen tỏa ra, dấu + và chấm nhỏ, nhịp nhẹ sau đó
  - Tên con vật
  - Card fact ở dưới giữa (15 fact đúng brief)
  - Nút "Tiếp tục" → lần đầu (chưa đăng nhập) sang Đăng nhập, các lần sau về Bản đồ
- Ảnh: `screenshots/v5/05a-result-capybara.png` (lần đầu), `screenshots/v5/11-result-voi-tada.png` (voi)

### 7. Màn kết quả – Sư tử (tưởng niệm Mimi)
- Flow: như màn 6 nhưng chỉ khi vẽ Sư tử
- Thành phần:
  - Nền đen toàn màn (cả thanh trạng thái), nét vẽ của người dùng đổi thành trắng
  - Khung tranh viền trắng, không có ta-da
  - Hoa trắng 5 cánh rơi liên tục
  - Tên "Sư tử", card fact viền trắng
  - Nút "Tiếp tục" (đen viền trắng)
- Ảnh: `screenshots/v5/12-result-sutu-memorial.png`

## Bước 4 – Đăng nhập (chỉ lần đầu)

### 8. Đăng nhập để lưu tranh
- Flow: sau màn kết quả của bức vẽ đầu tiên
- Thành phần:
  - Badge "Giả lập · không OAuth", tiêu đề "Lưu bức vẽ", mô tả
  - Card "Đăng nhập giả lập" với nút "Đăng nhập với Google"
- Ảnh: `screenshots/v5/06-login.png`

## Bước 5 – Bản đồ và đi tới chuồng tiếp theo

### 9. Bản đồ cá nhân
- Flow: sau đăng nhập, và mỗi lần vẽ xong về lại đây
- Thành phần:
  - Thanh trên gọn: "Bản đồ của bạn" + pill đếm "x / 15"
  - Chip "Gợi ý gần nhất" (chuồng chưa vẽ gần nhất + khoảng cách)
  - Bản đồ art v4: kéo, phóng to; chuồng đã vẽ hiện tranh người dùng có chuyển động, chuồng chưa vẽ là ô viền nét đứt
  - Chấm vị trí người dùng màu xanh
  - Nút zoom tròn "−", "+", "⌂"; dòng credit OSM
  - 2 nút tròn ở 2 góc dưới: "Danh sách con vật" (vàng) và "Hoàn thành hành trình" (mờ/không bấm được khi chưa có tranh nào)
- Ảnh: `screenshots/v5/07-map.png` (1 tranh), `screenshots/v5/13-map-after-3.png` (3 tranh)

### 10. Sheet "Danh sách con vật"
- Flow: bấm nút "Danh sách con vật" trên bản đồ
- Thành phần:
  - Bottom sheet có nền tối phía sau, tiêu đề + nút đóng ✕, mô tả
  - 15 dòng con vật: ô thumbnail (chưa vẽ: emoji xám; đã vẽ: tranh của người dùng), tên, trạng thái "Đã vẽ"/"Chưa vẽ", khoảng cách hoặc "Đang ở đây"
  - Dòng đã vẽ tô vàng nhạt. Bấm 1 dòng thì mở chỉ đường (không mở bảng vẽ)
- Ảnh: `screenshots/v5/08-animal-list.png`

### 11. Sheet chỉ đường
- Flow: sau khi chọn con vật trong danh sách
- Thành phần:
  - Tuyến đường xanh trên bản đồ + ghim đích, các chuồng khác mờ đi
  - Sheet dưới: tên con vật, nút ✕, "x phút · y m", link "Chi tiết chỉ đường ▾" (mở danh sách bước rẽ)
  - Nút "Bắt đầu" (đen) và "Quét NFC" (lối tắt)
  - Trạng thái đang đi: banner hướng dẫn trên cùng, chấm vị trí chạy dọc tuyến
- Ảnh: `screenshots/v5/09-directions-voi.png`

### 12. Sheet đã tới nơi
- Flow: khi tới chuồng
- Thành phần: tên con vật, "Đã tới nơi · Quét NFC để vẽ", nút lớn "Đã tới nơi – quét NFC" → mở Bảng vẽ (màn 5, không còn onboarding) → Màn kết quả (6 hoặc 7) → về Bản đồ
- Ảnh: `screenshots/v5/10-arrival-nfc.png`

## Bước 6 – Hoàn thành hành trình (Tour Wrapped)

### 13. Quãng đường (kiểu Strava)
- Flow: bấm "Hoàn thành hành trình" trên bản đồ
- Thành phần: tiêu đề, 3 ô số liệu (Quãng đường, Bước chân, Chuồng), bản đồ có animation đường đi màu cam qua các chuồng, thanh số liệu chạy theo (giờ, km, bước), nút "Phát lại" và "Xem bộ sưu tập tranh"
- Ảnh: `screenshots/v5/14-wrapped-strava.png`

### 14. Bộ sưu tập (carousel rồi tới lưới)
- Flow: sau màn Quãng đường
- Thành phần:
  - Tiêu đề "Bộ sưu tập", phụ đề "Từng nét vẽ của bạn"
  - Trạng thái carousel: từng tranh hiện lớn giữa màn khoảng 2 giây, có tên con vật, số "n / N", chấm tiến độ, tranh chuyển động giống trên map, trượt sang con tiếp theo
  - Nút nhỏ "Bỏ qua" để vào thẳng lưới
  - Chuyển cảnh: các tranh thu nhỏ bay vào ô của mình trong lưới
  - Trạng thái lưới: 3 cột kèm tên, hàng cuối căn giữa, nằm ngay dưới tiêu đề
  - Ô "chưa kịp vẽ" (lưu mà không có nét): hình gợi ý mờ trong khung nét đứt
  - Nút "Nhận danh hiệu" chỉ hiện sau khi lưới xuất hiện
- Ảnh: `screenshots/v5/collection-carousel/03-mid-voi.png` (carousel), `05-fly-into-grid.png` (chuyển cảnh), `06-final-grid.png` (lưới)

### 15. Danh hiệu
- Flow: sau Bộ sưu tập
- Thành phần: vòng nguyệt quế + tên danh hiệu (Vị thần tốc độ / Đứa con của mẹ hoàn hảo / Vị thần chăm chỉ), mô tả, pháo hoa (đã chuyển sang xám), nút "Tải ảnh / video"
- Ảnh: `screenshots/v5/16-wrapped-titles.png`

### 16. Xem trước & tải
- Flow: bước cuối
- Thành phần:
  - 2 hàng nút chọn: "Lưới" / "Trên map" và "Ảnh" / "Video"
  - Khung xem trước ảnh "Summit Your Drawing – Thảo Cầm Viên · Wrapped"
  - Dòng trạng thái "Đang tạo xem trước…" (loading) rồi "Xem trước: …"
  - Nút "Tải về", "Chia sẻ" (chỉ hiện trên điện thoại hỗ trợ), "Về bản đồ"
  - Popup tiến độ "Đang tạo video…" có thanh % khi tải video
- Ảnh: `screenshots/v5/17-export-preview.png`

## Ghi chú
- Trạng thái trống: bản đồ lúc chưa vẽ con nào thì nút "Hoàn thành hành trình" bị khóa. Ngoài popup tạo video và dòng "Đang tạo xem trước…" thì demo không có màn loading riêng.
- Nút "Tiếp tục" ở màn kết quả là chữ IT tự đặt (brief không ghi), Thư có thể đổi.
