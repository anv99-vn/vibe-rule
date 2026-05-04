Tạo git tag mới và push lên origin từ tham số đầu vào: $ARGUMENTS

Thực hiện theo các bước sau:

1. **Phân tích input** từ `$ARGUMENTS`:
   - Nếu có version (vd: `v1.0.1` hoặc `1.0.1`): dùng version đó (thêm prefix `v` nếu chưa có)
   - Nếu không có tham số: tự động tính version tiếp theo (xem bước 2)

2. **Tính version tự động** (chỉ khi không có tham số):
   - Chạy: `git tag --sort=-version:refname | head -1`
   - Nếu không có tag nào: dùng `v1.0.0`
   - Nếu có tag (vd: `v1.2.3`): tăng patch lên 1 → `v1.2.4`
   - Logic tăng patch: tách `MAJOR.MINOR.PATCH`, tăng PATCH thêm 1

3. **Tạo annotated tag**:
   - Chạy: `git tag -a <version> -m "Release <version>"`

4. **Push tag lên origin**:
   - Chạy: `git push origin <version>`

5. **Báo cáo kết quả**:
```
✅ Đã tạo và push tag <version> lên origin
```

Nếu có lỗi (vd: tag đã tồn tại, không có remote origin), hiển thị thông báo lỗi rõ ràng và dừng lại.
