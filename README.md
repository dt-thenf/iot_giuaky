# Tổng hợp kiến thức IoT (LuaLaTeX, tiếng Việt)

Bộ tài liệu phục vụ học phần **Cơ sở và thiết kế hệ thống IoT**. Hiện có **hai bài giảng**: `Chapter 1: An overview of IoT` (50 trang) và `Chapter 2: IoT Hardware` (79 trang). Mỗi bài giảng được biên soạn thành **ba chương độc lập**, tổng cộng **sáu chương**. Số chương trong repo là quy ước tự quản lý, không phải số chương gốc của giảng viên.

| Chương | Tệp nguồn | Chủ đề chính | Trang bài giảng nguồn (trang PDF) |
|---|---|---|---|
| 1 | `chapters/chuong_01.tex` | Khái niệm, nguồn gốc, smart object, smart environment, M2M/IIoT | 3, 5–22 |
| 2 | `chapters/chuong_02.tex` | Nút IoT, gateway, cloud, service, UI, kiến trúc 3–7 lớp | 23–41 |
| 3 | `chapters/chuong_03.tex` | Các miền ứng dụng, case study, cơ hội và thách thức | 42–49 (Chapter 1) |
| 4 | `chapters/chuong_04.tex` | Cảm biến: phân loại, analog/digital, ADC, bus, node IoT | 3–12, 16–17 (Chapter 2) |
| 5 | `chapters/chuong_05.tex` | Cơ cấu chấp hành: sensor vs actuator, motor/LED, PWM, driver | 13–15 (Chapter 2) |
| 6 | `chapters/chuong_06.tex` | MCU/SBC: ATmega, Arduino, ESP8266/ESP32, Edison, Edge, Raspberry Pi | 18–78 (Chapter 2) |

## Tài liệu PDF và biên dịch

- `pdf/iot_tong_hop_6_chuong.pdf`: bản ghép sáu chương từ cả hai bài giảng (tạo bởi GitHub Actions).
- `pdf/iot_hardware_3_chuong.pdf`: tài liệu riêng cho ba chương phần cứng, với trang bìa và mục lục riêng.
- `pdf/chuong_01.pdf` ... `pdf/chuong_06.pdf`: bản PDF độc lập từng chương.

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

Để biên dịch riêng phần cứng: `latexmk -lualatex -interaction=nonstopmode -halt-on-error -outdir=build hardware_only.tex`. Có sáu wrapper biên dịch độc lập `chapters/standalone_01.tex` ... `chapters/standalone_06.tex`.

Các bản PDF đã biên dịch (nếu có) trong `pdf/`. Toàn bộ hình kiến trúc hiện viết trực tiếp bằng TikZ trong từng tệp chương, vì thế chỉnh sửa được bằng mã nguồn.

## Bổ sung chương tiếp theo

1. Tạo `chapters/chuong_07.tex`, `chapters/chuong_08.tex`, `chapters/chuong_09.tex` từ nguồn mới, giữ quy ước `\chapter{...}`.
2. Thêm `\input{chapters/chuong_07}` ... vào `main.tex` trước `\backmatter`.
3. Nếu cần PDF độc lập, nhân bản `chapters/standalone_06.tex`, đổi tên, đổi `\setcounter{chapter}{6}` và `\input`.
4. Chỉnh bảng phạm vi nguồn ở README; chạy lại `latexmk`.

## Phân biệt nguồn

- Nguồn chính: 50 trang của `Chapter 1: An overview of IoT` và 79 trang của `Chapter 2: IoT Hardware`, TS. Nguyễn Đắc Cử, Đại học Phenikaa.
- Tham khảo tăng cường: Q. F. Hassan (2018); McEwen & Cassimally (2014); James, Seth & Mukhopadhyay (2022).
- Mục đóng khung *Kiến thức mở rộng* được biên soạn thêm, không phải trích nguyên văn từ slide.
- Hình vẽ TikZ tự biên soạn, không sử dụng hình bản quyền trong các tệp PDF nguồn.