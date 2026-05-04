Tải asset từ GitHub release của repo hiện tại từ tham số đầu vào: $ARGUMENTS

Thực hiện theo các bước sau:

1. **Phân tích input** từ `$ARGUMENTS`:
   - Nếu có version (vd: `v1.0.1` hoặc `1.0.1`): dùng version đó (thêm prefix `v` nếu chưa có)
   - Nếu không có tham số: dùng latest release

2. **Lấy thông tin release**:
   - Nếu có version: `gh release view <version> --json tagName,assets`
   - Nếu không có version: `gh release view --json tagName,assets`
   - Nếu không có release nào: hiển thị lỗi và dừng lại

3. **Hiển thị danh sách asset** theo định dạng:
```
## Release <tagName>
Assets:
  1. <tên file> (<size>)
  2. <tên file> (<size>)
  ...
```

4. **Hỏi user chọn asset**:
   > "Bạn muốn tải file nào? (nhập số thứ tự, `all` để tải tất cả, hoặc `cancel` để hủy)"

   - Nếu nhập số: download đúng file đó
   - Nếu nhập `all`: download tất cả asset
   - Nếu nhập `cancel`: dừng lại

5. **Download asset**:
   - Nếu chọn file cụ thể: `gh release download <version> --pattern <tên file>`
   - Nếu chọn all: `gh release download <version>`
   - Nếu không có version: thay `<version>` bằng tagName lấy được ở bước 2
   - File sẽ được tải về thư mục hiện tại

6. **Báo cáo kết quả**:
```
✅ Đã tải: <tên file(s)> từ release <tagName>
📁 Lưu tại: <thư mục hiện tại>
```

Nếu có lỗi (vd: release không tồn tại, không có asset, lỗi network), hiển thị thông báo lỗi rõ ràng và dừng lại.
