Lấy danh sách tất cả GitHub pull requests từ tham số đầu vào: $ARGUMENTS

1. **Phân tích input** từ `$ARGUMENTS`:
   - Nếu có repo (vd: `owner/repo`): chạy `gh pr list --repo <owner>/<repo> --limit 100 --json number,title,state,labels,assignees,reviewDecision,createdAt`
   - Nếu có filter state (vd: `merged`, `closed`): thêm `--state <state>`
   - Nếu không có tham số: chạy `gh pr list --limit 100 --json number,title,state,labels,assignees,reviewDecision,createdAt` trong repo hiện tại (mặc định lấy open PRs)

2. **Hiển thị danh sách** theo định dạng bảng:

```
## Pull Requests (<n> PRs)

| # | Title | State | Review | Assignees |
|---|-------|-------|--------|-----------|
| #1 | ... | open | approved | @alice |
| #2 | ... | open | changes requested | |
```

3. **Hỏi người dùng** muốn làm gì tiếp:
   > "Bạn muốn:
   > 1. Đọc chi tiết PR nào đó (nhập số)
   > 2. Thoát"

   - Nếu chọn **1**: fetch PR đó và hiển thị theo định dạng của lệnh `/pr`
   - Nếu chọn **2**: dừng lại
