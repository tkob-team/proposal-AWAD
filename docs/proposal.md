# LeeTKOB — Proposal

Nhóm: Lê Tấn Hiệp, Tống Dương Thái Hoà, Nguyễn Phúc Hoàng. Repo: https://github.com/tkob-team/proposal-AWAD

## 1. Người dùng và vấn đề
**TA chấm lab C++.** Đề có yêu cầu ngoài output ("tự cài merge sort"), nhưng máy chấm chỉ so output: gọi `std::sort` vẫn qua hết test. Hết hạn, TA đọc code từng bài, chấm tay cả bài lỗi biên dịch (khoảng 80 bài/tuần, 3–4 giờ).

## 2. Tính năng LLM và cái giá khi sai
**Soát ràng buộc, đề xuất trừ điểm**: một bước cố định trong quy trình chấm, không phải chatbot hay agent. Chấm cả lớp sau hạn → **luật cứng** bắt vi phạm chắc chắn (cấm hàm, đệ quy) → **LLM** xét phần cần hiểu code (đúng thuật toán, mảng phụ; rubric bài lỗi biên dịch), trả JSON `đạt / vi phạm / không chắc` kèm dòng code làm bằng chứng → kiểm tra schema, dòng trích → tính điểm theo mức TA đặt → **TA duyệt theo nhóm rồi mới công bố**. Đề phải qua lời giải mẫu trước khi phát hành.
**Sai thì sao:** trừ oan có thể làm sinh viên rớt môn hoặc mất học bổng; hiểu sai một ràng buộc là cả lớp bị trừ. **Eval:** bộ dev, bộ giữ kín, red-team; ngưỡng **0 trừ oan**, recall vi phạm ≥ 90%, "không chắc" ≤ 20%. **Dữ liệu gửi ra:** đề và code đã bỏ comment, MSSV, tên.

## 3. Phạm vi
**Làm:** 55 tính năng có mã (36 Must, 12 Should, 7 Could) trong 9 nhóm, từ tài khoản, lớp, đề tới chấm theo hạn, duyệt điểm, khiếu nại, vận hành (mục 3.1 [`proposal-detail.md`](./proposal-detail.md)). **Không làm:** chấm hoặc báo biên dịch khi nộp; ngôn ngữ thứ hai; LLM quyết mức trừ hay viết nhận xét; phát hiện đạo văn; API/MCP cho agent ngoài; Classroom add-on.

## 4. Kế hoạch
| Hạn | R1 Lớp, điểm (Node) | R2 Chấm bài, hạ tầng (Java) | R3 Tính năng LLM (Python) |
|---|---|---|---|
| 11/11 PA#2 | Đăng nhập, lớp, CSV, đề, nộp bài; test phân quyền | Sandbox, job chấm theo hạn; CI gate; test không chấm trùng | Hợp đồng JSON, checker giả; thử 2 mô hình; harness eval |
| 25/11 PA#3 | Tính điểm, công bố, sinh viên xem dòng bị trừ | Kiểm tra đề bằng lời giải mẫu; nối checker | Luật cứng + LLM + kiểm tra đầu ra; rubric; hàng chờ duyệt |
| 02/12 PA#4 | Khiếu nại, nhật ký duyệt; test công bố 2 lần | Timeout, hạn mức chi phí; test thoát sandbox | Giữ kín + red-team đạt ngưỡng; gate eval; báo cáo |
| 16/12 PA#5 | Nhận xét, xuất CSV; thống kê (cắt trước) | URL công khai, load test, dashboard | Eval trên bản triển khai, chi phí thật |
| 30/12 bản cuối | Test E2E luồng TA và sinh viên | Triển khai bản cuối theo runbook | Kịch bản demo, video |

**06/01/2027:** vấn đáp cả ba người. R1–R3 là vai trò, mỗi nhóm tự gán cho 3 thành viên. Milestone tuần ở bản chi tiết mục 5, mỗi mã tính năng một GitHub Issue.

## 5. Rủi ro
**Mô hình trừ oan / "không chắc" nhiều** → tuần này chạy 5 bài × 4 lời giải trên 2 mô hình; trừ oan hoặc "không chắc" > 40% thì R3 chỉ làm checker tới PA#2, R1, R2 dùng checker giả. **Hạ tầng chấm bài** → sandbox + hàng đợi ở W1; dự phòng Judge0, isolate. **TA duyệt mù** → không có nút "duyệt tất cả" cho đề xuất LLM.

## 6. Công nghệ và chi phí
React, NestJS, Spring Boot, Python (tree-sitter); PostgreSQL, MongoDB, Redis, RabbitMQ, Garage; Docker, GitHub Actions; Vercel + máy ảo. Gemini 3.1 Flash-Lite (dự phòng Groq); khoảng 5.000 lần gọi ≈ 6 USD, hạn mức 10 USD.
