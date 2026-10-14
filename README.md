# Cơ sở và thiết kế hệ thống IoT — tài liệu LuaLaTeX theo chương gốc

**Quy tắc:** một bài giảng `Chapter N` của giảng viên tương ứng đúng **một chương N** trong tài liệu. Các tệp con được tách để quản lý **mục kiến thức**, không được đặt thành chương mới.

Hiện repo đã có hai bài giảng: **Chapter 1 — An overview of IoT** (50 trang) và **Chapter 2 — IoT Hardware** (79 trang). Tài liệu của TS. Nguyễn Đắc Cử, Khoa Điện – Điện tử, Trường Đại học Phenikaa.

## Cấu trúc

```text
main.tex                            # Ghép toàn bộ: Chương 1 + Chương 2
preamble.tex                        # Kiểu chữ, tiếng Việt, TikZ
hardware_macros.tex                 # Macro kỹ thuật cho chương phần cứng
hardware_only.tex                   # PDF riêng Chương 2 có bìa
chapters/
  chuong_01.tex                     # Chương 1: Tổng quan về IoT
  chuong_01/
    01_lich_su_khai_niem.tex        # Các mục 1.x: lịch sử, khái niệm, M2M/IIoT
    02_kien_truc_iot.tex            # Các mục 1.x: thành phần, mô hình 3–7 lớp
    03_ung_dung_thach_thuc.tex       # Các mục 1.x: ứng dụng, cơ hội, thách thức
  chuong_02.tex                     # Chương 2: Phần cứng IoT
  chuong_02/
    01_cam_bien.tex                 # Các mục 2.x: sensors
    02_co_cau_chap_hanh.tex         # Các mục 2.x: actuators
    03_vi_dieu_khien.tex            # Các mục 2.x: MCU, Arduino, ESP, Raspberry Pi
  standalone_01.tex                 # Biên dịch riêng Chương 1
  standalone_02.tex                 # Biên dịch riêng Chương 2
pdf/                                 # PDF do GitHub Actions tạo tự động
```

## Tài liệu và phạm vi

| Chương gốc | Nội dung được giữ trong cùng chương |
|---|---|
| 1 – Tổng quan về IoT | Khái niệm IoT; lịch sử; Smart Object/Smart Environment; M2M, IIoT, Industry 4.0; Things/Gateway/Cloud/Services/UI; kiến trúc IoT 3–7 lớp; ứng dụng, cơ hội và thách thức |
| 2 – IoT Hardware | Cảm biến; cơ cấu chấp hành; vi điều khiển/vi xử lý, ATmega, Arduino, ESP8266/ESP32, Intel Edison, Raspberry Pi; ví dụ thiết kế |

Các phần mở rộng kiến thức, hình vẽ TikZ, ví dụ và câu hỏi ôn tập được biên soạn bổ trợ, không phải trích nguyên văn từ slide. Sách đối chiếu: Hassan (2018), McEwen & Cassimally (2014), James, Seth & Mukhopadhyay (2022).

## PDF

- `pdf/iot_tong_hop_2_chuong.pdf`: Chương 1 + Chương 2.
- `pdf/chuong_01.pdf`: riêng Chương 1.
- `pdf/chuong_02.pdf`: riêng Chương 2.
- `pdf/iot_hardware_chuong_02.pdf`: Chương 2, bản chuyên đề phần cứng có bìa.

**Các bản cũ `iot_tong_hop_6_chuong.pdf`, `iot_hardware_3_chuong.pdf`, `chuong_03.pdf` đến `chuong_06.pdf` bị đánh số sai và được xóa khi biên dịch lại.**

## Biên dịch bằng LuaLaTeX

Cài đặt `latexmk`, LuaLaTeX, `fontspec`, `babel`, `tikz`, `tcolorbox`, `listings`, phông Noto Serif, Noto Sans, DejaVu Sans Mono.

```bash
latexmk -lualatex -interaction=nonstopmode -halt-on-error -outdir=build main.tex
latexmk -lualatex -interaction=nonstopmode -halt-on-error -outdir=build chapters/standalone_01.tex
latexmk -lualatex -interaction=nonstopmode -halt-on-error -outdir=build chapters/standalone_02.tex
latexmk -lualatex -interaction=nonstopmode -halt-on-error -outdir=build hardware_only.tex
```

Workflow `.github/workflows/build-pdf.yml` thực hiện các lệnh trên khi cập nhật mã nguồn ở nhánh `main`, rồi commit PDF đã biên dịch.

## Thêm Chương 3 và các chương sau

Tạo `chapters/chuong_03.tex`, chỉ đặt **một** `\chapter{...}` tương ứng bài giảng gốc. Các mục nhỏ lưu ở `chapters/chuong_03/*.tex`, được nạp bằng `\input`. Thêm một dòng `\input{chapters/chuong_03}` vào `main.tex`, cập nhật GitHub Actions và README. Tuyệt đối không đổi `\section` thành `\chapter` chỉ vì chia tệp.
