# Ngày 1 — Bài Tập & Phản Ánh
## Nền Tảng LLM API | Phiếu Thực Hành

**Thời lượng:** 1:30 giờ  
**Cấu trúc:** Lập trình cốt lõi (60 phút) → Bài tập mở rộng (30 phút)

---

## Phần 1 — Lập Trình Cốt Lõi (0:00–1:00)

Chạy các ví dụ trong Google Colab tại: https://colab.research.google.com/drive/172zCiXpLr1FEXMRCAbmZoqTrKiSkUERm?usp=sharing

Triển khai tất cả TODO trong `template.py`. Chạy `pytest tests/` để kiểm tra tiến độ.

**Điểm kiểm tra:** Sau khi hoàn thành 4 nhiệm vụ, chạy:
```bash
python template.py
```
Bạn sẽ thấy output so sánh phản hồi của GPT-4o và GPT-4o-mini.

---

## Phần 2 — Bài Tập Mở Rộng (1:00–1:30)

### Bài tập 2.1 — Độ Nhạy Của Temperature
Gọi `call_openai` với các giá trị temperature 0.0, 0.5, 1.0 và 1.5 sử dụng prompt **"Hãy kể cho tôi một sự thật thú vị về Việt Nam."**

> **Temperature 0.0 (latency: 3.03s):**
> Một sự thật thú vị về Việt Nam là đất nước này có một trong những hệ thống hang động lớn nhất thế giới, đó là hang Sơn Đoòng. Nằm trong Vườn quốc gia Phong Nha-Kẻ Bàng ở tỉnh Quảng Bình, hang Sơn Đoòng được phát hiện vào năm 1991 và chính thức được công nhận là hang động lớn nhất thế giới vào năm 2009. Hang có chiều dài hơn 5 km, cao 200 m và rộng 150 m, đủ lớn để chứa cả một tòa nhà chọc trời 40 tầng. Bên trong hang có cả một hệ sinh thái riêng với rừng cây, sông ngầm và các loài động thực vật độc đáo.

> **Temperature 0.5 (latency: 3.05s):**
> Một sự thật thú vị về Việt Nam là đất nước này có một trong những hệ thống hang động lớn nhất thế giới, đó là hang Sơn Đoòng. Hang động này nằm trong Vườn quốc gia Phong Nha-Kẻ Bàng ở tỉnh Quảng Bình. Được phát hiện vào năm 1991 bởi một người dân địa phương và chính thức được khám phá vào năm 2009 bởi một nhóm thám hiểm người Anh, hang Sơn Đoòng có chiều dài hơn 5 km, cao 200 mét và rộng 150 mét. Hang động này thậm chí còn có hệ sinh thái riêng với rừng nhiệt đới, sông ngầm và các loài động thực vật độc đáo. Sơn Đoòng được coi là hang động lớn nhất thế giới và là một điểm đến hấp dẫn cho những người yêu thích phiêu lưu và khám phá thiên nhiên.

> **Temperature 1.0 (latency: 3.31s):**
> Một sự thật thú vị về Việt Nam là đất nước này có Hang Sơn Đoòng, hang động lớn nhất thế giới. Hang Sơn Đoòng nằm trong Vườn quốc gia Phong Nha-Kẻ Bàng, thuộc tỉnh Quảng Bình. Hang động này được phát hiện vào năm 1991 bởi một người dân địa phương tên là Hồ Khanh, nhưng mãi đến năm 2009 mới được công bố rộng rãi sau khi các nhà thám hiểm người Anh khám phá. Hang Sơn Đoòng có kích thước khổng lồ với những phần trần hang cao tới 200 mét và rộng đến 150 mét. Đặc biệt, bên trong hang có cả một hệ sinh thái riêng biệt với rừng rậm, sông ngầm và cả những đám mây nội tại, tạo nên một cảnh quan vô cùng kỳ vĩ và độc đáo.

> **Temperature 1.5 (latency: 3.78s):**
> Một sự thật thú vị về Việt Nam là quốc gia này là quê hương của hang Sơn Đoòng, hang động tự nhiên lớn nhất thế giới. Hang Sơn Đoòng nằm trong Vườn quốc gia Phong Nha-Kẻ Bàng ở tỉnh Quảng Bình. Hang này có chiều dài khoảng 9 km, cao tới 200 mét và rộng khoảng 150 mét, đủ lớn để chứa một tòa nhà chọc trời 40 tầng. Bên trong hang, có hệ sinh thái riêng biệt, với rừng nhiệt đới và sông ngầm, tạo nên một cảnh quan tuyệt đẹp và huyền bí mà rất ít nơi trên thế giới có được. Hang Sơn Đoòng chỉ mới được phát hiện vào năm 1991 bởi một người dân địa phương và được thám hiểm chính thức bởi các nhà khoa học vào năm 2009.

**Bạn nhận thấy quy luật gì qua bốn phản hồi?** (2–3 câu)
> Khi temperature tăng từ 0.0 lên 1.5, câu trả lời trở nên đa dạng hơn về cách diễn đạt và cấu trúc câu, mặc dù nội dung chính vẫn tương tự. Ở temperature 0.0 và 0.5, phản hồi gần như giống nhau và rất cấu trúc; ở 1.0 và 1.5, ngôn ngữ sáng tạo hơn, thêm chi tiết mới (như tên người phát hiện, "đám mây nội tại") nhưng đôi khi kém chính xác hơn (ví dụ chiều dài hang thay đổi từ 5km lên 9km).

**Bạn sẽ đặt temperature bao nhiêu cho chatbot hỗ trợ khách hàng, và tại sao?**
> Tôi sẽ đặt temperature khoảng 0.0–0.3. Chatbot hỗ trợ khách hàng cần trả lời chính xác, nhất quán và đáng tin cậy. Temperature thấp giúp giảm thiểu sự "bịa đặt" (hallucination) và đảm bảo thông tin trả lời luôn đúng, tránh gây nhầm lẫn cho khách hàng.

---

### Bài tập 2.2 — Đánh Đổi Chi Phí
Xem xét kịch bản: 10.000 người dùng hoạt động mỗi ngày, mỗi người thực hiện 3 lần gọi API, mỗi lần trung bình ~350 token.

**Ước tính xem GPT-4o đắt hơn GPT-4o-mini bao nhiêu lần cho workload này:**
> Tổng token/ngày = 10,000 × 3 × 350 = 10,500,000 tokens. Chi phí GPT-4o = 10,500,000 / 1,000 × $0.010 = **$105/ngày**. Chi phí GPT-4o-mini = 10,500,000 / 1,000 × $0.0006 = **$6.3/ngày**. GPT-4o đắt hơn GPT-4o-mini khoảng **16.67 lần** ($105 / $6.3 ≈ 16.67).

**Mô tả một trường hợp mà chi phí cao hơn của GPT-4o là xứng đáng, và một trường hợp GPT-4o-mini là lựa chọn tốt hơn:**
> **GPT-4o xứng đáng:** Các tác vụ yêu cầu suy luận phức tạp như phân tích hợp đồng pháp lý, chẩn đoán y tế, hay giải toán nâng cao — nơi chất lượng câu trả lời quan trọng hơn chi phí và sai sót có thể gây hậu quả nghiêm trọng. **GPT-4o-mini phù hợp hơn:** Các tác vụ đơn giản, lặp lại nhiều như phân loại email, trả lời FAQ, tóm tắt nội dung ngắn, hay chatbot hỗ trợ cơ bản — nơi khối lượng lớn và chi phí là ưu tiên hàng đầu.

---

### Bài tập 2.3 — Trải Nghiệm Người Dùng với Streaming
**Streaming quan trọng nhất trong trường hợp nào, và khi nào thì non-streaming lại phù hợp hơn?** (1 đoạn văn)
> Streaming quan trọng nhất trong các ứng dụng chatbot tương tác trực tiếp với người dùng, nơi thời gian chờ đợi ảnh hưởng lớn đến trải nghiệm — người dùng thấy từng token xuất hiện ngay lập tức thay vì chờ 3–5 giây mới thấy toàn bộ phản hồi, tạo cảm giác phản hồi nhanh và tự nhiên hơn. Ngược lại, non-streaming phù hợp hơn khi cần xử lý hậu kỳ (post-processing) toàn bộ phản hồi trước khi hiển thị, ví dụ: trích xuất JSON có cấu trúc, kiểm duyệt nội dung, hoặc gọi API trong pipeline tự động mà kết quả chỉ được sử dụng bởi hệ thống chứ không hiển thị trực tiếp cho người dùng.


## Danh Sách Kiểm Tra Nộp Bài
- [ ] Tất cả tests pass: `pytest tests/ -v`
- [ ] `call_openai` đã triển khai và kiểm thử
- [ ] `call_openai_mini` đã triển khai và kiểm thử
- [ ] `compare_models` đã triển khai và kiểm thử
- [ ] `streaming_chatbot` đã triển khai và kiểm thử
- [ ] `retry_with_backoff` đã triển khai và kiểm thử
- [ ] `batch_compare` đã triển khai và kiểm thử
- [ ] `format_comparison_table` đã triển khai và kiểm thử
- [ ] `exercises.md` đã điền đầy đủ
- [ ] Sao chép bài làm vào folder `solution` và đặt tên theo quy định 
