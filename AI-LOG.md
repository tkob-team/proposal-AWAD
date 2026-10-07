# AI-LOG

One entry per task where an assistant did part of the work. The letter in each
heading (A, B, C) is the team member who did the task — see the member line in the proposal.

## 2026-10-05 — đọc đề, phân tích rubric, chuẩn bị chọn đề tài (Tấn Hiệp)
Tool: Claude (claude.ai).
Asked for: viết lại đề PA#1 bằng tiếng Việt, tìm chỗ lệch giữa slide/Classroom/rubric, gợi ý đề tài và khung proposal cho nhóm.
Kept: phân tích chỗ lệch về spec và AI-LOG; khung 6 mục theo rubric.
Changed: lịch quy đổi — AI lấy tuần 1 là 21/09, sửa lại thành 14/09 theo lịch thật và đặt hạn theo buổi học thứ Năm; ngày nộp bản cuối/vấn đáp do nhóm tự chọn (06/01, 08/01).
Rejected: file Excel chấm đề tài và phân công — quá dài, nhóm sẽ không đọc; thay bằng quy trình 4 bước trong tài liệu.
By hand: thông tin lịch học, hạn PA#1, quyết định làm sản phẩm mới thay vì smart-restaurant.

## 2026-10-06 — mở rộng ý tưởng đề tài và đánh giá các đề tài trong sheet (Tấn Hiệp)
Tool: Claude (claude.ai).
Asked for: mở rộng 4 ý tưởng của A (TMĐT, video, học theo JD, ghi calo món Việt) thành các cột của sheet; chấm thử các đề tài nhóm đề xuất theo tiêu chí và khối lượng.
Kept: cách diễn đạt "sai thì ai thiệt, bao nhiêu" và ca khó cho từng ý tưởng; bảng so sánh khối lượng với đồ án năm trước.
Changed: AI đề xuất "1 luồng chính xoay quanh LLM" — nhóm sửa thành app có 3–4 luồng riêng, LLM nằm ở một điểm quyết định; tăng mức CRUD lên khoảng 50–60% đồ án năm trước.
Rejected: AI xếp EventComms là lựa chọn số 1 — nhóm vote chọn LeetCode-Lite vì muốn thực hành bài toán backend thực tế, có nhiều người dùng.
By hand: 4 ý tưởng gốc, mô tả hạn chế và vấn đề của idea học tập và ghi calo; vote chọn đề tài trong buổi họp 06/10.

## 2026-10-06 — brainstorm ý tưởng đồ án Web Nâng cao (Phúc Hoàng)
Tool: Claude (chat, có kèm các file yêu cầu môn học).
Asked for: gợi ý ý tưởng đồ án sao cho hợp mong muốn của mình, đủ kỹ năng cho phỏng vấn fresher backend (dùng luôn đồ án làm dự án cá nhân), đúng yêu cầu của thầy (clone một sản phẩm phổ biến, không cần mới, kèm một tính năng LLM).
Kept: tiêu chí "phần clone tự nó đã nhiều kỹ năng backend (đồng thời, hàng đợi, lưu file, realtime), LLM chỉ gắn vào đúng một chỗ có rủi ro". Giữ bảng 6 ý tưởng (LeetCode/VNOJ, CGV/Galaxy, Viblo, Google Drive, Stack Overflow, Messenger/Zalo) và bảng xếp hạng làm cơ sở so sánh; chọn đi tiếp hướng LeetCode/VNOJ (hạng 1).
Changed: không sửa nội dung từng ý tưởng; từ danh sách này chuyển sang bước sau là yêu cầu gom về một dự án duy nhất, tối đa hóa số bài toán backend.
Rejected: Google Drive, vì muốn bật cảnh báo phải gửi file nhạy cảm (CCCD, bảng điểm) cho mô hình. Messenger/Zalo, vì không có bước duyệt tự nhiên và tin nhắn riêng tư là dữ liệu nhạy cảm. Viblo và Stack Overflow, vì phần clone chủ yếu là CRUD nên backend mỏng. CGV/Galaxy, vì concurrency tốt nhưng xếp sau LeetCode cả về điểm môn lẫn giá trị phỏng vấn.
By hand: viết yêu cầu và tiêu chí chọn đề tài; đánh giá hướng đi mới "ổn hơn" so với các lần gợi ý trước; quyết định chọn hướng chấm code.

## 2026-10-06 — chốt đề tài và thiết kế tính năng LLM (Phúc Hoàng)
Tool: Claude (chat, cùng cuộc hội thoại với entry trên).
Asked for: một dự án duy nhất giải quyết càng nhiều vấn đề backend càng tốt, mà vẫn đúng yêu cầu của thầy.
Kept: đề tài LeetCode-lite (nền tảng chấm code cho lớp lập trình). Tính năng LLM: mô hình chỉ sinh *input* test (JSON gồm input, loại ca biên, lý do), *output lấy bằng cách chạy lời giải mẫu trong sandbox*, luật cứng loại input vi phạm ràng buộc, trợ giảng duyệt (human gate) trước khi xuất bản. Cách đo lỗi bằng máy: khoảng 20 bài, mỗi bài có 3–5 lời giải sai đã biết, chỉ số bắt được ≥ 90% lời giải sai và 0 test vi phạm ràng buộc. Giữ bảng bài toán backend (sandbox, hàng đợi, idempotency, rate limit, realtime, bảng xếp hạng, phiên bản test, MinIO, JWT/RBAC, phân trang, pipeline LLM, log/metric, CI gate), phần phạm vi làm/không làm, 6 mốc PA#1–PA#6 và stack Spring Boot (hoặc NestJS), PostgreSQL, Redis, RabbitMQ, MinIO, Docker, React.
Changed: coi các con số AI đưa ra (80 sinh viên, 3 bài lab/tuần, chi phí dưới 10 USD/học kỳ) là giả định, sẽ hỏi trợ giảng thật để kiểm chứng. Tên mô hình và giá token (gpt-5-mini, Gemini Flash) phải kiểm tra lại trên trang chính thức trước khi ghi vào proposal. Danh sách backend quá nhiều cho nhóm 3 người, nên hai mục sandbox và hàng đợi là bắt buộc, còn bảng xếp hạng realtime và load test có thể cắt nếu chậm tiến độ.
Rejected: lấy nguyên danh sách backend rồi cam kết làm hết; dùng số liệu và giá chưa kiểm chứng làm căn cứ trong proposal. Các mục AI đặt vào phần "Không làm" (ngôn ngữ thứ ba, phát hiện đạo văn, IDE online, diễn đàn, Elo, tích hợp hệ thống trường) cũng được loại khỏi phạm vi.
By hand: quyết định chốt đề tài này; các việc kiểm chứng sẽ tự làm: khảo sát một trợ giảng thật, dựng thử container chạy C++ không mạng có giới hạn thời gian (nếu không ổn thì chuyển sang Judge0), gom 5 bài kèm lời giải sai trước ngày 14/10 và thử mô hình bằng tay, hỏi thầy có cho dùng Spring Boot không.

## 2026-10-07 — phát triển tính năng LLM và viết proposal (Tấn Hiệp)
Tool: Claude (claude.ai).
Asked for: đổi tính năng LLM của LeetCode-Lite (C đề xuất) từ sinh test sang "soát ràng buộc đề, đề xuất trừ điểm"; viết toàn bộ proposal từ các ý đã chốt trong họp; chấm thử theo rubric.
Kept: quy trình luật cứng → LLM trả JSON có bằng chứng → kiểm tra đầu ra → TA duyệt trước khi công bố điểm; ngưỡng eval 0 trừ oan; hai rủi ro.
Changed: mục 1 viết lại theo lớp dạy kèm thật của A (AI ban đầu dùng số giả định 80 bài/tuần làm số chính); mục 2 thêm hậu quả học lại/mất học bổng (AI đánh giá điểm số là cái giá "nhẹ"); câu xác minh đổi từ "một TA" sang người đang dạy lập trình; thêm Codex vào trợ lý code.
Rejected: đề xuất bỏ Java và MongoDB để gọn stack — nhóm giữ microservice Node/Java/Python và mỗi service một CSDL.
By hand: chọn đề tài và hướng A trong họp, chọn stack và phân công, số liệu lớp dạy kèm, tên sản phẩm LeeTKOB.

## 2026-10-07 — nghiên cứu và đề xuất đề tài mới cho PA#1 (Thái Hoà)
Tool: ChatGPT (GPT-5.6 Sol) + Superpowers brainstorming + web research.

Asked for: Nghiên cứu các ý tưởng đề tài mới cho PA#1, bám rubric của môn; ưu tiên đề tài là một web app rõ ràng, có workflow, dữ liệu, vai trò người dùng và một tính năng LLM cốt lõi có thể đánh giá được.

Kept: Cách đánh giá đề tài theo các tiêu chí: người dùng cụ thể, vấn đề thực tế, hậu quả khi LLM sai, khả năng tạo bộ eval có đáp án, human gate ở bước có hậu quả, phạm vi CRUD phù hợp và khả năng hỏi người dùng thật. Giữ các hướng đề tài mới có workflow nghiệp vụ rõ như quản lý mua hàng, quản lý sản xuất/vendor cho agency-event, quản lý thay đổi đơn hàng, quản lý campaign khuyến mãi, quản lý thực tập và đối soát nhập kho.

Changed: Loại bỏ hướng chỉ tối ưu lại 5 đề tài gợi ý có sẵn trong tài liệu vì yêu cầu là tìm ý tưởng mới. Chuyển từ các “checker/tool” nhỏ sang cách đặt đề tài ở cấp hệ thống web lớn hơn, trong đó LLM chỉ đảm nhiệm một bước semantic quan trọng như trích xuất yêu cầu, đối chiếu tài liệu hoặc phát hiện mismatch.

Rejected: Các ý tưởng quá giống chatbot hỏi đáp, chỉ upload một file rồi trả kết quả, hoặc không có workflow/approval rõ ràng; các ý tưởng khó định lượng hậu quả khi sai hoặc khó tạo ground-truth để eval.

By hand: Tự quyết định tiêu chí “web lớn rõ ràng” cần thể hiện qua dashboard, nhiều thực thể dữ liệu, trạng thái xử lý, lịch sử, approval và role; tự chọn các đề tài phù hợp nhất để đưa vào sheet vote của nhóm.

## 2026-10-07 — điền bảng đề tài để nhóm vote (Thái Hoà)
Tool: ChatGPT (GPT-5.6 Sol).

Asked for: Điền các đề tài mới vào đúng bảng chung của nhóm với các cột: Người đề xuất, Tên đề tài, Người dùng, Vấn đề, Cách làm hiện tại, Tính năng LLM, Hậu quả khi sai, Cách biết sai, Khả năng hỏi người dùng thật và Số phiếu.

Kept: Sáu đề tài mới gồm:
1. Hệ thống quản lý mua hàng và phê duyệt báo giá nhà cung cấp.
2. Hệ thống quản lý yêu cầu sản xuất và phê duyệt vendor cho Agency/Event.
3. Hệ thống quản lý ngoại lệ và thay đổi đơn hàng thương mại điện tử.
4. Hệ thống quản lý chiến dịch khuyến mãi và kiểm duyệt cấu hình trước khi publish.
5. Cổng quản lý thực tập doanh nghiệp và kiểm tra điều kiện thực tập.
6. Hệ thống quản lý nhập kho và đối soát đơn mua hàng – hàng thực nhận.

Changed: Viết lại tên và mô tả theo hướng một web system hoàn chỉnh thay vì một tính năng LLM đơn lẻ. Mỗi đề tài đều bổ sung workflow, dữ liệu, approval và điểm human gate để phù hợp với yêu cầu của đồ án.

Rejected: Không dùng lại 5 đề tài gợi ý AI đã có trong file 02; không tiếp tục các đề tài Listing Policy Gate và Shipping Claim Copilot vì mục tiêu của bước này là mở rộng candidate set bằng ý tưởng mới.

By hand: Chưa chốt số phiếu, người đề xuất thật và số liệu thiệt hại thực tế; các số tiền trong bảng chỉ là giả định brainstorm và cần thay bằng dữ liệu từ người dùng thật trước khi viết proposal.

---

## LLM feature in our product: dữ liệu rời khỏi hệ thống (rule 6)

- **Gửi ra mô hình:** chỉ đề bài, ràng buộc và lời giải mẫu do trợ giảng nhập. Không có dữ liệu cá nhân, bài nộp của sinh viên, thông tin đăng nhập hay API key.
- **Vì sao chấp nhận được:** đây là nội dung trợ giảng tự soạn, không thuộc về sinh viên, và trợ giảng biết rõ nội dung nào được gửi đi.
- **Mô hình không quyết định kết quả cuối:** output lấy từ việc chạy lời giải mẫu trong sandbox, input bị luật cứng kiểm tra theo ràng buộc, trợ giảng duyệt trước khi xuất bản.
- **Kiểm soát rủi ro:** validate theo JSON schema, timeout, retry có giới hạn, trần chi phí cho mỗi trợ giảng, chống prompt injection (ví dụ đề bài chèn câu "bỏ qua ràng buộc").
