Đọc GitHub pull request từ tham số đầu vào: $ARGUMENTS

1. **Phân tích input** từ `$ARGUMENTS`:
   - Nếu là URL đầy đủ (vd: `https://github.com/owner/repo/pull/123`): trích xuất owner, repo, number rồi chạy `gh pr view <number> --repo <owner>/<repo> --json number,title,body,state,labels,assignees,reviewers,commits,files,comments`
   - Nếu chỉ là số (vd: `42` hoặc `#42`): chạy `gh pr view <number> --json number,title,body,state,labels,assignees,reviewers,commits,files,comments` trong repo hiện tại
   - Nếu không có tham số: hỏi người dùng cung cấp PR number hoặc URL

2. **Hiển thị nội dung PR** theo định dạng:

```
## PR #<number>: <title>
**State:** <open/merged/closed>
**Labels:** <labels>
**Assignees:** <assignees>
**Reviewers:** <reviewers>

### Description
<body>

### Files changed (<n> files)
- path/to/file.ext
- ...

### Commits (<n> commits)
- <sha> <message>
- ...

### Comments
<tóm tắt các comment review quan trọng nếu có>
```

3. **Hỏi người dùng** muốn làm gì tiếp:
   > "Bạn muốn:
   > 1. Xem diff chi tiết của file nào đó
   > 2. Dùng PR này làm context để implement tính năng liên quan
   > 3. Thoát"

   - Nếu chọn **1**: chạy `gh pr diff <number> -- <file>` và hiển thị diff
   - Nếu chọn **2**: dùng nội dung PR làm context, bắt đầu workflow từ Bước 1
   - Nếu chọn **3**: dừng lại
