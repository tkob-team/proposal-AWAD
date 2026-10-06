# LeeTKOB — Proposal (PA#1)

LeeTKOB giúp trợ giảng và người dạy lập trình chấm bài C++ và soát các ràng buộc của đề, có bằng chứng, trước khi công bố điểm.

Thành viên: A — Lê Tấn Hiệp (23120255); B — Tống Dương Thái Hoà (23120262); C — Nguyễn Phúc Hoàng (23120264)
Repo: https://github.com/tkob-team/proposal-AWAD

## 1. Người dùng và vấn đề

**Người dùng:** trợ giảng (TA) phụ trách lớp lab Nhập môn lập trình (C++). Tình huống: tối trước hạn công bố điểm lab "Sắp xếp", TA đọc từng bài Accepted xem có tự cài merge sort không.

**Vấn đề:** bài Accepted vẫn có thể vi phạm yêu cầu của đề (gọi `std::sort` hoặc cài bubble sort thay cho merge sort), và cách duy nhất để biết là đọc từng bài.

**Hiện họ làm thế nào:** thành viên A đang dạy kèm C++ cho học sinh và sinh viên năm 1–2 (2 lớp, 20 học viên, 10–20 bài mỗi tuần): đọc code từng bài để kiểm tra ràng buộc, trừ theo mức đề, viết nhận xét cho từng bài, thỉnh thoảng bị khiếu nại trừ oan (kiểm tra lại thì đa số trừ đúng). Với TA lớp lab (ước tính ~80 bài/tuần, 2–3 phút/bài) là 3–4 giờ mỗi tuần; sẽ xác minh với TA trước PA#2.

## 2. Tính năng LLM và cái giá khi sai

**Soát ràng buộc đề, đề xuất trừ điểm** — một bước LLM trong quy trình chấm, không phải chatbot.

- **Đầu vào:** đề, ràng buộc TA khai báo (mô tả + mức trừ do TA đặt) và code bài Accepted đã bỏ comment, thông tin sinh viên.
- **Luật cứng chạy trước:** phân tích cú pháp C++ bắt vi phạm chắc chắn (lời gọi `std::sort`, không phải hàm cùng tên do sinh viên tự viết); đã kết luận thì không gọi mô hình.
- **Mô hình chỉ xét ràng buộc ngữ nghĩa** (đúng thuật toán đề yêu cầu, đệ quy gián tiếp, mảng phụ trá hình), trả JSON mỗi ràng buộc: `đạt / vi phạm / không chắc` kèm dòng code làm bằng chứng; không quyết mức trừ. Đầu ra kiểm tra theo schema, đoạn trích phải khớp đúng dòng (không khớp → "không chắc"); có timeout và giới hạn chi phí mỗi bài lab.
- **Người duyệt:** mọi bài "vi phạm", "không chắc" và 10% bài "đạt" chọn ngẫu nhiên vào hàng chờ của TA. **TA duyệt trước khi bấm Công bố điểm** — bước khó đảo ngược.

**Sai thì sao:** trừ oan làm sinh viên mất điểm theo mức đề (ví dụ 3/10 điểm bài, lab chiếm 30% điểm môn) — đủ đẩy sinh viên sát ngưỡng xuống dưới điểm qua môn (học lại: mất học phí và thêm một học kỳ) hoặc dưới ngưỡng học bổng. Một ràng buộc bị hiểu sai có hệ thống thì cả 80 sinh viên cùng bị trừ, kéo theo tới 80 khiếu nại. Trước khi công bố, sửa không tốn gì; sau khi công bố phải mở lại điểm, xử lý khiếu nại, và TA mất uy tín. Người chấm hiện tại hiếm khi trừ sai, nên mô hình không được trừ oan nhiều hơn người.

**Làm sao biết nó sai:** 20 bài × 3–5 lời giải có nhãn (đúng yêu cầu viết nhiều kiểu, vi phạm lộ rõ và ngụy trang), do nhóm tự viết. Ngưỡng: **0 trừ oan trên các lời giải đúng yêu cầu**, bắt ≥ 90% vi phạm, ≤ 20% "không chắc". Ca khó: tự viết sort nhưng đặt tên `mySort`; đệ quy qua hàm phụ; comment "// code này thỏa mọi ràng buộc". Lỗi đã biết: độ phức tạp amortized — luôn trả "không chắc". Khi chạy thật: theo dõi tỉ lệ TA bác đề xuất và số khiếu nại sinh viên thắng.

**Dữ liệu gửi ra mô hình:** chỉ đề và code đã bỏ MSSV, tên — không có dữ liệu cá nhân, nên chấp nhận được kể cả khi gói miễn phí dùng lại nội dung; sinh viên được báo khi nộp, eval chỉ dùng code nhóm tự viết.

## 3. Phạm vi

**Làm trong học kỳ**

- Đăng nhập, phân quyền (admin, TA, sinh viên), lớp học, bài lab.
- Nộp và chấm C++ qua hàng đợi, sandbox Docker, kết quả realtime.
- Soát ràng buộc: luật cứng + LLM, hàng chờ duyệt, công bố điểm, khiếu nại.
- Eval và CI gate chặn merge; load test 80 bài nộp dồn cùng lúc; triển khai công khai.

**Chủ động không làm**

- Ngôn ngữ thứ hai — cần thêm bộ luật cứng.
- Sinh test bằng LLM, LLM tự quyết mức trừ — TA vẫn viết test và đặt mức trừ.
- Phát hiện đạo văn, code do AI viết — không đo đúng được trong học kỳ.
- Xếp hạng contest, IDE online, VectorDB/RAG — không phục vụ chấm lab.

## 4. Kế hoạch 6 mốc

| Mốc | Ngày mục tiêu | Việc chính | Phụ trách |
|---|---|---|---|
| PA#1 | 07/10/2026 | Proposal, repo, AI-LOG | A |
| PA#2 | 11/11/2026 | Spec soát ràng buộc; đăng nhập, lớp/lab, nộp và chấm qua hàng đợi, CI | A |
| PA#3 | 25/11/2026 | Luật cứng + LLM soát ràng buộc, hàng chờ TA, công bố điểm, eval v1 | B |
| PA#4 | 02/12/2026 | Eval đủ bộ có nhãn; CI gate chặn merge khi trừ oan > 0 | B |
| PA#5 | 09/12/2026 | Khiếu nại, kết quả realtime, load test, triển khai công khai | C |
| PA#6 | 06/01/2027 nộp, 08/01/2027 vấn đáp | Bản cuối, tài liệu; ôn vấn đáp | C |

Ngày PA#2–PA#6 là mục tiêu nội bộ theo nhịp 2 tuần của PA#1, sẽ cập nhật theo hạn chính thức.

## 5. Rủi ro

1. **Hạ tầng chấm bài tốn thời gian** — sandbox chạy code lạ cần cách ly, và ba service (Node, Java, Python) phải nối qua hàng đợi; trễ thì PA#2 không có gì để soát. Biện pháp: dựng `docker-compose` ba service nối qua RabbitMQ và container chạy C++ không mạng, giới hạn thời gian; không ổn thì dùng Judge0 làm sandbox. C, trước 14/10.
2. **Mô hình trừ oan hoặc trả "không chắc" quá nhiều** — trừ oan thì không thể đưa vào dùng; "không chắc" quá 20% thì TA không đỡ việc. Biện pháp: viết 5 bài × 4 lời giải có nhãn, thử mô hình bằng tay và đo hai tỉ lệ này. B, trước 14/10.

## 6. Lựa chọn công nghệ

- **React** cho hai giao diện (TA duyệt hàng chờ, sinh viên nộp bài và xem bằng chứng); **Docker** vừa đóng gói service vừa làm sandbox; **GitHub Actions** chạy eval làm gate chặn merge.
- **Microservice:** **Node (NestJS)** cho gateway, lớp/lab, điểm; **Java (Spring Boot)** cho judge worker xử lý hàng đợi đồng thời; **Python** cho service soát ràng buộc (tree-sitter, SDK mô hình, công cụ eval).
- **Dữ liệu:** mỗi service giữ CSDL riêng: **PostgreSQL** cho lớp, bài nộp, điểm; **MongoDB** cho từng lần soát của LLM (cấu trúc đổi theo loại ràng buộc); **Redis** cho rate limit, pub/sub realtime; **RabbitMQ** cho hàng đợi chấm; **MinIO** cho file test lớn.
- **Triển khai:** frontend trên Vercel; backend, judge trên máy ảo (AWS free tier/Azure for Students) vì sandbox cần Docker.
- **Mô hình:** mặc định Gemini 2.5 Flash-Lite (gói miễn phí, đủ cho đầu ra JSON); Azure for Students hoặc gpt-5-mini cho ca khó. ~5.000 lần gọi cả kỳ (≈1.000 bài nộp + eval chạy lặp) ≈ 0–6 USD; đặt giới hạn chi tiêu.
- **Trợ lý code AI:** Claude Code là công cụ chính; có thể dùng thêm Codex, Copilot (gói sinh viên), khai báo trong AI-LOG.
