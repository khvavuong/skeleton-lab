# Skeleton lab — quy ước Kn + TEAM + SUBMISSION deadline

## Goal

- Cập nhật skeleton theo quy ước tên `Kn` (khóa) + `L{level}` (lớp).
- Sửa warning audit #2 (`TEAM.md` root) và #4 (`SUBMISSION` đủ cấu trúc/đặt tên/checklist).
- Deadline: lab sáng `23h59 GMT+7` ngày lab; lab tối/chiều `11h59 GMT+7` ngày hôm sau.
- **Không** đụng path-example (audit #7) hay ép SUBMISSION liệt kê `report/` kiểu AP10 (#8) — user bỏ qua.
- Outcome: `run_audit.sh --compact` không còn FILE02 / DOC01-SUBMISSION / POL03 / POL04 / POL06.

## Out of scope

- Đổi tên repo `skeleton-lab` → `Kn-…` (giữ skeleton).
- Không sửa CHECKPOINTS/RUBRIC placeholder nội dung bài.
- Không thêm deliverable `report/` bắt buộc vào checklist chỉ để xóa AP10.
- Không commit/push/PR trong AGY — Cursor làm PR sau.

## Worktree / branch

- Base: `main`
- Slug: `skeleton-k4-convention-update`
- Stop: thiếu file trong `files` → `blocked`

## Context (verbatim)

### TEAM hiện ở `team/TEAM.md` (phải chuyển root)

```markdown
# Team

## Thông tin nhóm

- Tên nhóm:
- Repo nhóm: `K4-L3-DAYxx-TenNhom-TenBai`
```

Quy ước audit: `TEAM.md` **ở root**. Di chuyển `team/TEAM.md` → `TEAM.md`. Xóa thư mục `team/` nếu trống (hoặc chỉ còn rác). Cập nhật mọi doc trỏ `team/TEAM.md` → `TEAM.md`. Trong `TEAM.md` dùng mẫu `Kn-L3-DAYxx-TenNhom-TenBai` (ghi chú `n` = số khóa; ví dụ khóa 4 → `K4`).

### SUBMISSION.md hiện thiếu cấu trúc + deadline

File hiện tại chỉ có loại bài, tên repo `K4-…`, tên file báo cáo, deadline placeholder, checklist trống.

Viết lại `SUBMISSION.md` gồm tối thiểu:

1. **Loại bài** — Cá nhân | Nhóm.
2. **Biến tên:** `Kn` = khóa; `L2/L2A/L2B/L3/L3A/L3B` = level/lớp. Ví dụ khóa hiện tại dùng `K4`.
3. **Tên repo đề bài / nộp** (giữ pattern hiện có, prefix `Kn-` thay vì cứng “chỉ K4”; ví dụ vẫn được viết `K4-…` kèm câu “thay K4 bằng Kn theo khóa”).
4. **Cấu trúc / deliverable phải nộp** (đặt tên + cấu trúc — đủ keyword DOC01):
   - Cá nhân: đổi tên `report/individual/MSSV_HoTen.md`; code trong `src/` nếu có.
   - Nhóm: `TEAM.md` (root) + `report/team/group_report.md` + mỗi thành viên `report/team/MSSV_HoTen.md`.
   - Mỗi cá nhân tự nộp link repo LMS (đã có — giữ).
5. **Deadline (GMT+7)** — bắt buộc cả hai dòng:
   - Lab **sáng**: nộp trước **23h59 GMT+7** ngày lab.
   - Lab **tối** (hoặc chiều): nộp trước **11h59 GMT+7** ngày hôm sau.
   - Coach có thể gia hạn ≤48h.
6. **Checklist** — bullet cụ thể (không để trống): chọn loại bài, đổi tên repo, điền TEAM nếu nhóm, đổi tên file báo cáo, không commit secret, nộp link LMS.

### README.md

- Dòng cấu trúc: `TEAM.md` ở root (không nói nằm trong `report/team/`).
- Giữ ví dụ path `report/individual/20241234_…` (user bỏ qua #7).
- Có thể sửa typo `dêx` → `dễ` nếu đụng dòng đó.

### RULES.md

- Nếu nhắc `TEAM.md`, đảm bảo path root (không `team/TEAM.md`).

## Steps

1. `git mv team/TEAM.md TEAM.md` (hoặc tương đương); xóa `team/` nếu trống.
2. Cập nhật `TEAM.md`: mẫu repo `Kn-L3-DAYxx-TenNhom-TenBai` + ghi chú khóa.
3. Viết lại `SUBMISSION.md` theo Context ở trên (đủ cấu trúc / đặt tên / deadline sáng+tối GMT+7 / checklist).
4. Sửa `README.md` (và `RULES.md` nếu cần) cho nhất quán `TEAM.md` root + `Kn`.
5. Không thêm AP10-style “SUBMISSION phải liệt kê report/” nếu chỉ để silence audit #8.

## Worklog plan

- Title: Worklog — skeleton Kn + TEAM + deadline
- WHY: Chuẩn hóa skeleton theo khóa biến thiên và deadline sáng/tối GMT+7
- Notion sync: no

```files
TEAM.md
team/TEAM.md
SUBMISSION.md
README.md
RULES.md
docs/plans/skeleton-k4-convention-update.md
```

```checks
test ! -f team/TEAM.md
test -f TEAM.md
rg -q "23h59" SUBMISSION.md
rg -q "11h59" SUBMISSION.md
rg -q "GMT\\+7|GMT\\+7|gmt\\+7" SUBMISSION.md -i
rg -q "cấu trúc|deliverable|phải nộp|đặt tên|naming" SUBMISSION.md -i
rg -q "Kn|số khóa|thay K4" SUBMISSION.md
~/.cursor/skills/k4-lab-repo-audit/scripts/run_audit.sh --compact .
```
