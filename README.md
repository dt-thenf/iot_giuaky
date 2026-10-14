# Tổng hợp kiến thức IoT (LuaLaTeX, tiếng Việt)

Bộ tài liệu phục vụ học phần **Cơ sở và thiết kế hệ thống IoT**. Đầu vào hiện tại chỉ có một bài giảng `Chapter 1_An overview of IoT.pdf`; nội dung này được tổ chức lại thành **ba chương tự quản lý**, không phải ba chương gốc của giảng viên.

| Chương | Tệp nguồn | Chủ đề chính | Trang bài giảng nguồn (trang PDF) |
|---|---|---|---|
| 1 | `chapters/chuong_01.tex` | Khái niệm, nguồn gốc, smart object, smart environment, M2M/IIoT | 3, 5–22 |
| 2 | `chapters/chuong_02.tex` | Nút IoT, gateway, cloud, service, UI, kiến trúc 3–7 lớp | 23–41 |
| 3 | `chapters/chuong_03.tex` | Các miền ứng dụng, case study, cơ hội và thách thức | 42–49 |

## Biên dịch

Cần TeX Live có `lualatex`, `fontspec`, `babel`, `tikz`, `tcolorbox`, font Noto Serif/Noto Sans. Ở thư mục gốc:

```bash
latexmk -lualatex -interaction=nonstopmode -halt-on-error -outdir=build main.tex
```

PDF kết quả: `build/main.pdf`. Có ba wrapper biên dịch độc lập:

```bash
latexmk -lualatex -interaction=nonstopmode -halt-on-error -outdir=build chapters/standalone_01.tex
latexmk -lualatex -interaction=nonstopmode -halt-on-error -outdir=build chapters/standalone_02.tex
latexmk -lualatex -interaction=nonstopmode -halt-on-error -outdir=build chapters/standalone_03.tex
```

Các bản PDF đã biên dịch (nếu có) trong `pdf/`. Toàn bộ hình kiến trúc hiện viết trực tiếp bằng TikZ trong từng tệp chương, vì thế chỉnh sửa được bằng mã nguồn.

## Bổ sung ba chương sau

1. Tạo `chapters/chuong_04.tex`, `chapters/chuong_05.tex`, `chapters/chuong_06.tex` từ nguồn mới, giữ quy ước `\chapter{...}`.
2. Thêm `\input{chapters/chuong_04}` ... vào `main.tex` trước `\backmatter`.
3. Nếu cần PDF độc lập, nhân bản `chapters/standalone_03.tex`, đổi tên, đổi `\setcounter{chapter}{3}` và `\input`.
4. Chỉnh bảng phạm vi nguồn ở README; chạy lại `latexmk`.

## Phân biệt nguồn

- Nguồn chính: 50 slide PDF của TS. Nguyễn Đắc Cử, `Chapter 1: An overview of IoT`.
- Tham khảo tăng cường: Q. F. Hassan (2018); McEwen & Cassimally (2014); James, Seth & Mukhopadhyay (2022).
- Mục đóng khung *Kiến thức mở rộng* được biên soạn thêm, không phải trích nguyên văn từ slide.
- Hình vẽ TikZ tự biên soạn, không sử dụng hình bản quyền trong bốn tệp PDF nguồn.