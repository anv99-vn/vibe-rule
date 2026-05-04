# Vibe Coding Workflow

Khi nhận yêu cầu implement tính năng, sửa bug, hoặc viết code mới — LUÔN thực hiện đúng 6 bước sau theo thứ tự. Không được bỏ qua hoặc gộp bước. Không được bắt đầu code khi chưa qua bước 4.

---

## Bước 1 — Thu thập yêu cầu

Đầu tiên hỏi người dùng có GitHub issue để đọc spec không:

> "Bạn có link GitHub issue hoặc issue number không? (hoặc nhập yêu cầu trực tiếp)"

**Nếu có issue:**
- Nếu là URL đầy đủ: dùng `gh issue view <number> --repo <owner/repo> --json title,body,labels,comments`
- Nếu chỉ có số: dùng `gh issue view <number> --json title,body,labels,comments` (trong repo hiện tại)
- Hiển thị title và nội dung issue cho người dùng xem
- Dùng nội dung issue làm base cho yêu cầu, sau đó hỏi bổ sung nếu thiếu thông tin:
  - Có điểm nào trong issue chưa rõ không?
  - Có ràng buộc kỹ thuật nào ngoài issue không?
  - Có edge case cần bổ sung không?

**Nếu không có issue**, hỏi trực tiếp:
- Mục tiêu cụ thể là gì?
- Input / output mong muốn?
- Ràng buộc kỹ thuật (ngôn ngữ, framework, thư viện)?
- Edge case hoặc điều kiện đặc biệt cần xử lý?

Chỉ tiếp tục khi đã có đủ thông tin.

---

## Bước 2 — Xác định context cần đọc

Hỏi người dùng muốn cung cấp context theo cách nào:

> "Để hiểu codebase, tôi có thể:
> 1. Đọc toàn bộ project
> 2. Đọc một số file/thư mục cụ thể (bạn chỉ định)
> 3. Không cần đọc thêm file nào
>
> Bạn chọn cách nào?"

- Nếu chọn **1**: quét cấu trúc thư mục trước, sau đó đọc các file liên quan theo nhóm. Thông báo các file sẽ đọc trước khi đọc.
- Nếu chọn **2**: chỉ đọc đúng các file/thư mục người dùng liệt kê. Không tự ý đọc thêm.
- Nếu chọn **3**: bỏ qua bước này, tiếp tục bước 3.

Sau khi đọc xong, tóm tắt ngắn những gì đã nắm được từ codebase.

---

## Bước 3 — Tóm tắt & Xác nhận

Tóm tắt lại toàn bộ yêu cầu đã hiểu theo dạng bullet point rõ ràng. Kết thúc bằng câu hỏi:

> "Bạn xác nhận tôi có thể tiếp tục không?"

Chỉ tiếp tục khi người dùng xác nhận (y / đúng / ok / tiếp tục).

---

## Bước 4 — Kế hoạch cấu trúc code

Liệt kê toàn bộ file sẽ được tạo mới hoặc sửa đổi, theo định dạng:

```
📁 path/to/file.ext  [TẠO MỚI / SỬA ĐỔI]
   → Tác dụng: ...
```

Kết thúc bằng câu hỏi:

> "Bạn đồng ý với cấu trúc này không?"

Chỉ bắt đầu code sau khi được xác nhận.

---

## Bước 5 — Implement

Viết code theo đúng kế hoạch đã xác nhận ở bước 4. Không tự ý thêm file hoặc thay đổi scope ngoài những gì đã thống nhất.

---

## Bước 6 — Tự kiểm tra & Báo cáo

Sau khi implement xong, tự đánh giá lại theo checklist:

- [ ] Tất cả file trong kế hoạch bước 4 đã được xử lý?
- [ ] Có file nào bị sửa ngoài scope đã xác nhận không?
- [ ] Các edge case trong yêu cầu đã được xử lý đủ chưa?

Báo cáo kết quả ngắn gọn cho người dùng theo định dạng:

```
✅ Hoàn thành: ...
⚠️  Lưu ý: ... (nếu có deviation hoặc edge case chưa xử lý)
```

---

## Giới hạn file đọc

Nếu project có file `.vibe-allowed`, chỉ được đọc các file/thư mục được liệt kê trong đó. Nếu cần đọc file ngoài danh sách, hỏi người dùng trước.

## Giới hạn token

Ưu tiên giải pháp ngắn gọn, tránh đọc file thừa. Chỉ đọc file khi thực sự cần thiết cho tác vụ hiện tại.
