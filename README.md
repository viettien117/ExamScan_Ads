# ExamScan_Ads

Cơ sở dữ liệu quảng cáo dùng chung cho ứng dụng **ExamScan** (Windows + Android).

Cả app Windows và app Android đều tải dữ liệu từ repo này, nên chỉ cần
cập nhật ở đây là quảng cáo thay đổi trên cả hai nền tảng — không phải
build lại app.

## Nội dung

- **`ads.db`** — bảng quảng cáo, dạng văn bản. Mỗi dòng là một bản ghi:

  ```
  id|brand_name|image_path|click_url|duration_ms|expiry_date
  ```

  - Dòng bắt đầu bằng `#` là chú thích, bỏ qua.
  - `image_path` — đường dẫn ảnh tương đối (trong thư mục `AdImages`).
  - `duration_ms` — thời gian hiển thị mỗi quảng cáo (mili giây).
  - `expiry_date` — `YYYY-MM-DD`; để trống = hiển thị mãi.
  - Ký tự đặc biệt được escape: `\` → `\\`, `|` → `\|`.

- **`AdImages/`** — thư mục chứa ảnh quảng cáo.

## URL truy cập (raw)

```
https://raw.githubusercontent.com/viettien117/ExamScan_Ads/main/ads.db
https://raw.githubusercontent.com/viettien117/ExamScan_Ads/main/AdImages/<tên ảnh>
```

## Cách cập nhật quảng cáo

1. Sửa `ads.db` (thêm/sửa/xoá dòng), thêm ảnh vào `AdImages/` nếu cần.
2. Commit và push lên nhánh `main`.
3. App sẽ tự tải bản mới ở lần mở kế tiếp.
