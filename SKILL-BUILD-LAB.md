---
name: build-lab
description: Dựng một bài lab K4 hoàn chỉnh từ repo skeleton-lab. Dùng khi coach cần tạo repo đề bài mới, điền checkpoint, rubric, luật làm bài, hướng dẫn nộp bài và template báo cáo cho bài cá nhân hoặc bài nhóm.
---

# Skill: Dựng bài lab từ skeleton-lab

Skill này hướng dẫn coach (hoặc AI agent như Claude, Codex) biến repo `skeleton-lab` thành một repo đề bài hoàn chỉnh mà học viên mở ra là biết phải làm gì, nộp gì và được chấm thế nào.

Nguyên tắc chung:

- **Giữ đúng khung.** Không đổi tên, không dời các file `.md` ở root. Học viên đã quen vị trí này.
- **Không để lại chỗ trống.** Mọi dấu `...` trong template phải được thay bằng nội dung thật.
- **Viết cho học viên.** Câu ngắn, tiếng Việt, mỗi mục trả lời một câu hỏi của học viên.
- **Chấm được.** Mỗi tiêu chí trong rubric phải chỉ ra được bằng chứng cụ thể (file, output, ảnh chụp).

## Bước 1. Thu thập thông tin trước khi viết

Hỏi coach (hoặc tự lấy từ tài liệu bài giảng) đủ các thông tin sau. Thiếu mục nào thì hỏi lại, **không tự bịa**.

| Thông tin | Ví dụ |
|---|---|
| Tên bài | `GraphRAG` |
| Level và ngày học | `L3A`, `Day19` |
| Loại bài | Cá nhân hoặc Nhóm |
| Mục tiêu học tập (2–4 ý) | Hiểu cách dựng knowledge graph từ văn bản… |
| Thời lượng làm bài | 4 giờ |
| Công cụ, thư viện, dữ liệu dùng trong bài | Python 3.11, LangChain, file `data/docs.json` |
| Công cụ AI được dùng và giới hạn | Được dùng ChatGPT để tra cứu, không được sinh toàn bộ code |
| Deadline và chính sách nộp muộn | 23:59 ngày học, trễ trừ 10%/ngày |
| Bonus (nếu có) | Tối đa 10 điểm, ghi riêng |

## Bước 2. Tạo repo đề bài

1. Tạo repo mới từ `skeleton-lab` (dùng "Use this template" hoặc copy toàn bộ file).
2. Đặt tên repo theo mẫu trong `SUBMISSION.md`:

   ```text
   K4-L3A-TenBai
   ```

   Thay `L3A` bằng level đúng: `L2`, `L2A`, `L2B`, `L3`, `L3A` hoặc `L3B`.

3. Xóa phần không dùng để repo gọn:
   - **Bài cá nhân:** xóa thư mục `report/team/` và `team/`.
   - **Bài nhóm:** xóa thư mục `report/individual/`.
   - Xóa luôn file `SKILL-BUILD-LAB.md` này khỏi repo đề bài. File này dành cho coach, học viên không cần.

## Bước 3. Điền từng file

Làm theo đúng thứ tự dưới đây. File sau dựa vào nội dung file trước.

### 3.1 `CHECKPOINTS.md` — các bước học viên phải làm

Chia bài thành 3–5 checkpoint, mỗi checkpoint là một mốc học viên tự kiểm tra được. Mỗi checkpoint điền đủ 5 dòng:

- **Mục tiêu:** học viên đạt được gì sau checkpoint này.
- **Cần làm:** các việc cụ thể, ghi rõ file nào trong `src/` cần sửa.
- **Sản phẩm:** thứ phải có khi xong (file, output, ảnh chụp, số liệu).
- **Cần hiểu:** khái niệm học viên phải giải thích được trong báo cáo.
- **Tự kiểm tra:** lệnh chạy hoặc kết quả mong đợi để học viên biết mình làm đúng.

Đặt tên checkpoint có nghĩa, ví dụ `CP1 — Đọc và làm sạch dữ liệu`, không để `CP1 — ...`.

### 3.2 `RUBRIC.md` — cách chấm điểm

- Mỗi checkpoint ứng với ít nhất một tiêu chí (`C1`, `C2`, …). Có thể thêm tiêu chí cho báo cáo.
- Cột **Bằng chứng** ghi rõ người chấm nhìn vào đâu: tên file, output, mục nào trong báo cáo.
- Cột **Ghi chú** ghi điều kiện được điểm và lỗi bị trừ điểm.
- Tổng điểm chính phải **đúng 100**.
- Bonus ghi riêng, tối đa 10 điểm, không cộng vào điểm chính.

Kiểm tra nhanh: đưa rubric cho một người không biết bài, họ phải chấm được chỉ bằng cách nhìn bằng chứng.

### 3.3 `RULES.md` — luật làm bài

Thay các câu hướng dẫn bằng nội dung thật của bài:

- **AI và công cụ:** liệt kê công cụ AI được dùng, được dùng vào việc gì, và phần học viên phải tự giải thích được.
- **Liêm chính:** giữ nguyên các dòng có sẵn. Bài nhóm thì giữ yêu cầu khai đóng góp trong `team/TEAM.md`.
- **Secret và API key:** nếu bài cần API key, thêm file `.env.example` vào repo và ghi tên biến cần có.
- **Nộp muộn:** ghi chính sách cụ thể (ví dụ: trễ trừ 10%/ngày, quá 3 ngày không nhận).

### 3.4 `SUBMISSION.md` — cách nộp bài

- Mục **Loại bài:** giữ một lựa chọn (`Cá nhân` hoặc `Nhóm`), xóa lựa chọn kia.
- Mục **Tên repo:** giữ mẫu tên của loại bài đã chọn, thay `DAYxx` và `TenBai` bằng giá trị thật, ví dụ `K4-L3-DAY19-HoVaTen-MSSV-GraphRAG`.
- Mục **Deadline:** ghi ngày giờ cụ thể.
- Mục **Checklist:** viết danh sách học viên tự tick trước khi nộp, ví dụ:

  ```markdown
  - [ ] Repo đặt đúng tên
  - [ ] Code chạy được theo hướng dẫn trong `src/README.md`
  - [ ] Có đủ sản phẩm của CP1, CP2, CP3
  - [ ] Báo cáo đã đổi tên thành `MSSV_HoTen.md` và điền đủ các mục
  - [ ] Không commit file `.env` hay API key
  - [ ] Đã nộp link repo trên LMS
  ```

### 3.5 `src/` — code khởi đầu

- Đặt code khởi đầu (starter code) và dữ liệu vào `src/`.
- Điền đủ 5 dòng trong `src/README.md`: file bắt đầu chạy, lệnh chạy, input, output, file học viên được sửa.
- Chỗ học viên cần viết code đánh dấu rõ bằng `TODO`, kèm số checkpoint, ví dụ `# TODO CP2: viết hàm tính điểm`.
- Nếu bài cần thư viện, thêm `requirements.txt` (hoặc file tương đương) vào `src/`.

### 3.6 `docs/` — tài liệu thêm

Nếu bài có tài liệu dài (lý thuyết, hướng dẫn cài đặt, slide), đặt vào `docs/` và dẫn link từ `README.md` hoặc `CHECKPOINTS.md`. Bài ngắn thì để nguyên `docs/README.md`.

### 3.7 `report/` và `team/` — template báo cáo

Giữ nguyên các template. Chỉ sửa khi bài cần thêm mục riêng, ví dụ thêm mục "So sánh kết quả hai phương pháp" vào phần **Kết quả**.

- **Bài cá nhân:** học viên dùng `report/individual/MSSV_HoTen.md`.
- **Bài nhóm:** nhóm điền `team/TEAM.md` và `report/team/group_report.md`; mỗi thành viên thêm một file `report/team/MSSV_HoTen.md`.

### 3.8 `README.md` — trang đầu của repo

Viết lại `README.md` cho học viên đọc (bỏ phần hướng dẫn dành cho coach). Nên có:

1. Tên bài và một đoạn giới thiệu 2–3 câu.
2. Mục tiêu học tập.
3. Loại bài, thời lượng, deadline.
4. Thứ tự đọc: `RULES.md` → `CHECKPOINTS.md` → `src/README.md` → `RUBRIC.md` → `SUBMISSION.md`.
5. Cấu trúc thư mục (chỉ liệt kê thư mục còn giữ lại).
6. Tên file báo cáo cần đổi, ví dụ `report/individual/20241234_NguyenVanAn.md`.

## Bước 4. Tự kiểm tra trước khi giao

Chạy hết danh sách này. Chỉ giao khi tất cả đều đạt.

- [ ] Tên repo đúng mẫu `K4-<Level>-TenBai`.
- [ ] Đủ 6 file ở root: `README.md`, `CHECKPOINTS.md`, `RUBRIC.md`, `RULES.md`, `SUBMISSION.md`, `.gitignore`.
- [ ] Không còn dấu `...` hay câu hướng dẫn dành cho coach. Kiểm tra bằng lệnh:

  ```bash
  grep -rn --include='*.md' --exclude-dir=report --exclude-dir=team '\.\.\.' .
  ```

  Lệnh không in gì là đạt. Lệnh bỏ qua `report/` và `team/` vì dấu `...` trong template báo cáo là chỗ để học viên tự điền.
- [ ] Đã xóa phần không dùng (`report/team/` + `team/` cho bài cá nhân, `report/individual/` cho bài nhóm) và file `SKILL-BUILD-LAB.md`.
- [ ] Mỗi checkpoint có tiêu chí tương ứng trong rubric; tổng điểm chính đúng 100; bonus ghi riêng.
- [ ] Code trong `src/` chạy được theo đúng lệnh ghi trong `src/README.md` trên một máy sạch.
- [ ] Không có API key, password hay file `.env` trong repo.
- [ ] Nhờ một người chưa biết bài đọc `README.md` trong 5 phút: họ nói lại được bài yêu cầu làm gì và nộp gì.

## Bước 5. Giao bài

1. Push repo đề bài lên GitHub.
2. Gửi link repo cho người duyệt (PM hoặc lead) kèm tóm tắt: tên bài, loại bài, số checkpoint, deadline.
3. Sau khi được duyệt mới công bố cho học viên.

## Lỗi hay gặp

| Lỗi | Cách tránh |
|---|---|
| Rubric chấm thứ checkpoint không yêu cầu làm | Đối chiếu từng dòng rubric với cột **Sản phẩm** của checkpoint |
| Tổng điểm khác 100 vì cộng cả bonus | Bonus để ở bảng hoặc dòng riêng |
| Học viên không biết sửa file nào | Ghi tên file trong **Cần làm** và trong `src/README.md` |
| Báo cáo bị đặt tên sai nên khó chấm tự động | Nhắc quy tắc `MSSV_HoTen.md` ở `README.md`, `SUBMISSION.md` và checklist |
| Bài nhóm thiếu đóng góp cá nhân | Giữ `team/TEAM.md` và yêu cầu mỗi người một file báo cáo |
