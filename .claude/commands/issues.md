Lấy danh sách tất cả GitHub issues từ tham số đầu vào: $ARGUMENTS

1. **Phân tích input** từ `$ARGUMENTS`:
   - Nếu có repo (vd: `owner/repo`): chạy `gh issue list --repo <owner>/<repo> --limit 100 --json number,title,labels,state,createdAt,assignees`
   - Nếu không có tham số: chạy `gh issue list --limit 100 --json number,title,labels,state,createdAt,assignees` trong repo hiện tại

2. **Hiển thị danh sách** theo định dạng bảng:

```
## Issues (<n> issues)

| # | Title | Labels | Assignees |
|---|-------|--------|-----------|
| #1 | ... | bug, ui | @alice |
| #2 | ... | feature | |
```

3. **Hỏi người dùng** muốn làm gì tiếp:
   > "Bạn muốn:
   > 1. Đọc chi tiết issue nào đó (nhập số)
   > 2. Implement một issue (nhập số)
   > 3. Thoát"

   - Nếu chọn **1**: chạy `/issue <number>` để xem chi tiết
   - Nếu chọn **2**: fetch issue đó rồi bắt đầu workflow từ Bước 2 (dùng issue làm spec)
   - Nếu chọn **3**: dừng lại
