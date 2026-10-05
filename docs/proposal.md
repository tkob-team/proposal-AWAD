# <Tên sản phẩm> — Proposal (PA#1)

<Tên sản phẩm> giúp <ai> <làm gì>.

Thành viên: A — Lê Tấn Hiệp (23120255); B — <Họ tên> (<MSSV>); C — <Họ tên> (<MSSV>)
Repo: <link repo>

<!--
Giới hạn: bản PDF tối đa 2 trang A4. Tổng khoảng 660 chữ + bảng kế hoạch.
Giữ đúng 6 mục, đúng thứ tự, đánh số 1–6 để SELF_ASSESSMENT trỏ vào ("proposal.pdf, mục 2").
Các khối ghi chú như thế này không hiện khi render — xóa trước khi xuất PDF.
Xuất PDF: cỡ chữ 11pt, lề khoảng 2 cm; mở PDF ra đếm trang trước khi tự chấm.
-->

## 1. Người dùng và vấn đề

<!-- ~120 chữ. Một người cụ thể (vai trò, nơi làm, tình huống, quy mô) — không phải một nghề.
Vấn đề trong MỘT câu. Hiện họ đang làm cách nào, tốn gì. Có ít nhất một con số thật. -->

## 2. Tính năng LLM và cái giá khi sai

<!-- ~220 chữ.
- Đầu vào → mô hình làm gì → đầu ra (có cấu trúc). Ai dùng đầu ra, rồi làm gì với nó.
- Sai thì: ai bị ảnh hưởng, BAO NHIÊU (đồng, giờ, số người), CÓ ĐẢO NGƯỢC được không.
- Làm sao biết nó sai: ít nhất 2 ca khó cụ thể.
- Một mệnh đề: người duyệt đặt ở bước nào (bước không đảo ngược).
- Một câu: dữ liệu nào gửi ra mô hình, và vì sao chấp nhận được. -->

## 3. Phạm vi

<!-- ~100 chữ. Mỗi dòng "Làm" phải xuất hiện trong kế hoạch mục 4; không gì trong mục 4 nằm ở "Không làm". -->

**Làm trong học kỳ**

- 

**Chủ động không làm**

- <việc> — <lý do ngắn>

## 4. Kế hoạch 6 mốc

| Mốc | Ngày mục tiêu | Việc chính | Phụ trách |
|---|---|---|---|
| PA#1 | 07/10/2026 | Proposal, repo, AI-LOG | A |
| PA#2 | 11/11/2026 | Spec tính năng cốt lõi; khung app, đăng nhập, CSDL, CI | B |
| PA#3 | 25/11/2026 | Tính năng LLM có hàng rào; eval v1 | C |
| PA#4 | 02/12/2026 | Eval đầy đủ; CI gate chặn merge khi dưới ngưỡng | A |
| PA#5 | 09/12/2026 | Triển khai; theo dõi chi phí và dữ liệu gửi ra | B |
| PA#6 | 06/01/2027 nộp, 08/01/2027 vấn đáp | Bản cuối; ôn vấn đáp | C |

Ngày PA#2–PA#6 là ngày mục tiêu nội bộ, suy theo nhịp 2 tuần của PA#1; sẽ cập nhật khi hạn chính thức được công bố.

<!-- Mỗi ô "Việc chính" tối đa ~12 chữ. Mỗi mốc đúng MỘT người phụ trách; không ghi "cả nhóm".
Nội dung PA#2–PA#5 là bản nháp, sửa theo đề tài đã chọn. -->

## 5. Rủi ro

<!-- ~130 chữ. Đúng HAI rủi ro riêng của dự án này (không phải "thiếu thời gian").
Mỗi rủi ro: vì sao có thể làm hỏng dự án → biện pháp bắt đầu được trong tuần này → ai, hạn ngày nào. -->

1. **<Rủi ro 1>** — <vì sao>. Biện pháp: <việc cụ thể>, <A/B/C>, trước <ngày>.
2. **<Rủi ro 2>** — <vì sao>. Biện pháp: <việc cụ thể>, <A/B/C>, trước <ngày>.

## 6. Lựa chọn công nghệ

<!-- ~90 chữ. Mỗi dòng: chọn gì — vì sao với dự án NÀY. Bắt buộc có mô hình + chi phí ước tính cả học kỳ. -->

- **React, Node, Docker, GitHub Actions** — stack của môn; <một lý do gắn với dự án>
- **Cơ sở dữ liệu:** <...> — <lý do>
- **Triển khai:** <...> — <lý do>
- **Mô hình:** <nhà cung cấp, tên mô hình> — <lý do>; ước tính <số> lần gọi cả học kỳ ≈ <số> USD
- **Trợ lý code AI:** <Copilot / Claude Code / Cursor, chỉ một> — <lý do>
