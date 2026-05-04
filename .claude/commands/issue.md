Đọc GitHub issue từ tham số đầu vào: $ARGUMENTS

Thực hiện theo các bước sau:

1. **Phân tích input** từ `$ARGUMENTS`:
   - Nếu là URL đầy đủ (vd: `https://github.com/owner/repo/issues/123`): trích xuất owner, repo, number rồi chạy `gh issue view <number> --repo <owner>/<repo> --json title,body,labels,comments`
   - Nếu chỉ là số (vd: `42` hoặc `#42`): chạy `gh issue view <number> --json title,body,labels,comments` trong repo hiện tại
   - Nếu không có tham số: hỏi người dùng cung cấp issue number hoặc URL

2. **Hiển thị nội dung issue** theo định dạng:
```
## Issue #<number>: <title>
**Labels:** <labels>

<body>

---
**Comments** (<n> comments):
<tóm tắt các comment quan trọng nếu có>
```

3. **Hỏi người dùng** có muốn dùng issue này làm spec để bắt đầu workflow không:
   > "Bạn có muốn bắt đầu implement issue này không? (y/n)"

   - Nếu **y**: tiếp tục từ Bước 2 của Vibe Coding Workflow (Xác định context cần đọc), dùng nội dung issue làm yêu cầu đã thu thập ở Bước 1.
   - Nếu **n**: dừng lại, chờ hướng dẫn tiếp theo từ người dùng.
