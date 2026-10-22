# may-in-tool-drivers

Driver máy in dùng cho nút **"Cài máy in vào Windows"** trong app Máy In Tool.

Các file driver nằm trong thư mục [`drivers/`](drivers). App đọc danh sách
[`drivers/drivers.json`](drivers/drivers.json), tải đúng file, kiểm tra mã SHA-256 rồi mới cài.

| Máy in | File | Cách cài |
|---|---|---|
| HPRT máy bill (TP80N, TP80NL, TP80N-H…) | `hprt-pos-2.7.3.23.zip` | Tự động: các file gốc lấy ra từ bộ cài HPRT v2.7.3.23 (đã đối chiếu SHA-1 từng file), `.inf` có chữ ký Xiamen Hanin |
| PDIT PD304 (tem) | `pdit-pd304-4barcode-2024.11.14.1.exe` | Tự động: giải nén `.inf` (4BARCODE, có chữ ký số), `pnputil` + `Add-PrinterDriver` |
| Xprinter XP-365B (tem) | `xprinter-365b-seagull-2022.2.exe` | Tự động: `/x` giải nén, `DriverWizard.exe install` (Seagull) |
| KiotViet KV 804 (bill) | `kiotviet-kv804-pos-8.205.exe` | Bán tự động: mở công cụ của hãng để chọn model, app tạo cổng và máy in |

## Thêm hoặc cập nhật driver

1. Thêm file driver mới vào thư mục `drivers/` (mỗi file dưới 100 MB).
2. Thêm/sửa một mục trong `drivers/drivers.json`, với `sha256` và `size` đúng của file.
3. Không cần build lại app: app đọc `drivers.json` mỗi lần mở trang cài.

Các driver là phần mềm miễn phí của từng hãng, chỉ để lại đây để khách hàng cài cho tiện.
