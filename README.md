# LeeTKOB

Hệ thống chấm bài C++ sau hạn nộp, có tính năng LLM **soát ràng buộc của đề và đề xuất trừ điểm** kèm dòng code làm bằng chứng. TA duyệt rồi mới công bố điểm; LLM không quyết mức trừ.

Đồ án môn **CSC13114 — Phát triển ứng dụng web nâng cao (học phần tốt nghiệp)**.

## Thành viên

| | Họ tên | MSSV |
|---|---|---|
| A | Lê Tấn Hiệp | 23120255 |
| B | Tống Dương Thái Hoà | 23120262 |
| C | Nguyễn Phúc Hoàng | 23120264 |

Chữ A, B, C dùng trong `AI-LOG.md` để ghi ai làm việc nào.

## Trạng thái

- **PA#1 — Đề xuất và kế hoạch:** đã nộp ngày 07/10/2026. Đề tài được thầy chọn làm project chung cho cả lớp, mỗi nhóm 3 người cùng làm.
- **23/10/2026:** viết lại proposal theo góp ý của thầy: bản 1 trang, bản chi tiết có danh mục tính năng theo mã và milestone hằng tuần.
- **Tiếp theo:** PA#2 (harness và quality gate), hạn 11/11/2026.

## Tài liệu

- [Proposal 1 trang](docs/proposal.md) ([PDF](docs/proposal.pdf))
- [Proposal chi tiết](docs/proposal-detail.md): người dùng, tính năng LLM và eval, danh mục 55 tính năng, kiến trúc, kế hoạch theo milestone, rủi ro, công nghệ và chi phí
- [AI-LOG](AI-LOG.md): cách nhóm dùng AI ở từng việc, theo template của môn học

## Quy ước

- Không commit `.env`, API key hay dữ liệu thật của người dùng. Biến môi trường cần có được liệt kê trong `.env.example`.
- Mỗi việc có AI tham gia: người làm tự thêm một mục vào `AI-LOG.md`, ghi ngay khi làm.
- Mỗi mã tính năng (ví dụ `C8`) là một GitHub Issue, gắn nhãn nhóm, mức ưu tiên, vai trò và milestone (proposal chi tiết, mục 5.5).
- Không push thẳng lên `main`: mỗi PR cần một người review và CI xanh mới được merge.
