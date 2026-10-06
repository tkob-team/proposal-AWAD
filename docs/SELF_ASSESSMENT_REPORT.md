# Self-assessment — PA#1

Người nộp:
- 23120255 — Lê Tấn Hiệp (A)
- 23120262 — Tống Dương Thái Hoà (B)
- 23120264 — Nguyễn Phúc Hoàng (C)

Tổng điểm tự đánh giá: 100 / 100

Tình trạng bài nộp: zip gồm `proposal.pdf` (2 trang, có link repo), `proposal.md`, `AI-LOG.md` và file này. Repo: https://github.com/tkob-team/proposal-AWAD

| Tiêu chí | Tối đa | Tự chấm | Bằng chứng |
|---|---|---|---|
| Problem and users | 20 | 20 | proposal.pdf, mục 1 — người dùng là TA lớp lab C++ trong một tình huống cụ thể (tối trước hạn công bố điểm lab "Sắp xếp"); vấn đề trong một câu (bài Accepted vẫn vi phạm ràng buộc đề); cách làm hiện tại lấy từ lớp dạy kèm thật của thành viên A (2 lớp, 20 học viên, 10–20 bài/tuần: đọc code, trừ theo đề, viết nhận xét, xử lý khiếu nại). |
| The LLM feature, and the cost of it being wrong | 25 | 25 | proposal.pdf, mục 2 — một tính năng (soát ràng buộc đề, đề xuất trừ điểm) theo quy trình luật cứng → LLM trả JSON có dòng code làm bằng chứng → kiểm tra đầu ra → TA duyệt trước khi công bố điểm. Cái giá khi sai nêu đủ ai (sinh viên, TA), bao nhiêu (mất điểm theo mức đề, có thể học lại hoặc mất học bổng, tới 80 khiếu nại), có đảo ngược được không (trước/sau công bố). Eval có ngưỡng 0 trừ oan, ca khó, lỗi đã biết; có câu về dữ liệu gửi ra mô hình. |
| Scope: in and out | 15 | 15 | proposal.pdf, mục 3 — 4 dòng "làm" và 4 dòng "không làm" kèm lý do. Mọi dòng "làm" đều có trong kế hoạch mục 4 (PA#2–PA#5), không dòng "không làm" nào xuất hiện trong kế hoạch. |
| Plan and ownership | 20 | 20 | proposal.pdf, mục 4 — bảng 6 mốc, mỗi mốc có việc chính, một người phụ trách (A/B/C, đối chiếu họ tên ở đầu trang) và ngày; có ghi chú ngày theo nhịp lịch học phần của PA#1. |
| Risks | 10 | 10 | proposal.pdf, mục 5 — hai rủi ro riêng của dự án (hạ tầng chấm bài và ghép ba service; mô hình trừ oan hoặc trả "không chắc" quá nhiều), mỗi rủi ro có biện pháp bắt đầu trong tuần này, người phụ trách và hạn 14/10. |
| Technology choices | 10 | 10 | proposal.pdf, mục 6 — mỗi lựa chọn có một dòng lý do gắn với dự án (React, Docker, GitHub Actions; ba service Node/Java/Python; PostgreSQL, MongoDB, Redis, RabbitMQ, MinIO; nơi triển khai). Mô hình mặc định Gemini 2.5 Flash-Lite, dự phòng Azure for Students/gpt-5-mini, chi phí ước tính 0–6 USD cả học kỳ; trợ lý code chính là Claude Code. |
| **Tổng** | **100** | **100** | Đúng với tên file zip `23120255-23120262-23120264_100.zip` |

## Những gì nhóm chưa làm được

- Quy mô của người dùng mục tiêu (TA lớp lab, khoảng 80 bài/tuần) vẫn là ước tính; bằng chứng thực tế hiện đến từ lớp dạy kèm của thành viên A. Nhóm sẽ xác minh với một TA trước PA#2, như đã ghi ở proposal mục 1.
- Ngày PA#2–PA#6 là mục tiêu nội bộ suy theo nhịp của PA#1, chưa phải hạn chính thức.

## Những gì nhóm sẽ làm khác đi

Xác định người dùng thật trước khi brainstorm đề tài. Lần này nhóm chọn đề tài rồi mới tìm người dùng, nên phải dựa vào lớp dạy kèm của một thành viên thay vì hỏi được một TA bên ngoài nhóm.
