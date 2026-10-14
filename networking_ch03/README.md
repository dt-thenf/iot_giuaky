# IoT giữa kỳ — Tài liệu LuaLaTeX tiếng Việt

Tài liệu ôn tập học phần **Cơ sở và thiết kế hệ thống IoT**. Hiện đã biên soạn **Chương 3 — Networking Technologies in IoT** từ slide 81 trang của TS. Nguyễn Đắc Cử và ba giáo trình IoT tham khảo. Chương 1, 2 và 4–6 chưa có nguồn bài giảng nên **không tự viết nội dung thay thế**.

## Cấu trúc

```text
main.tex                       # bản tổng hợp; gọi từng chương theo thứ tự
preamble.tex                   # kiểu chữ Unicode, TikZ, bảng, layout chung
chapters/ch01/README.md        # chờ bài giảng chương 1
chapters/ch02/README.md        # chờ bài giảng chương 2
chapters/ch03/chapter.tex      # chương 3: gọi 5 phần kiến thức
chapters/ch03/01_communication.tex
chapters/ch03/02_connectivity.tex
chapters/ch03/03_networks.tex
chapters/ch03/04_data_protocols.tex
chapters/ch03/05_revision.tex
chapters/ch04..ch06/README.md  # dành chỗ mở rộng
Makefile
.github/workflows/latex.yml
```

## Biên dịch PDF

Cài TeX Live có `lualatex`, `latexmk`, các gói `fontspec`, `babel`, `tikz`, `tcolorbox`, `hyperref`, `booktabs` và font Unicode `Noto Serif`, `DejaVu Sans`.

```bash
make pdf
# hoặc
latexmk -lualatex -interaction=nonstopmode -halt-on-error main.tex
```

Kết quả `main.pdf`. Trên GitHub, workflow `Build LuaLaTeX PDF` biên dịch và lưu **artifact `iot-gk-pdf`** để tải từ trang Actions. Để thêm các chương khác, đặt nội dung vào `chapters/chNN/chapter.tex`, rồi thêm `\input{chapters/chNN/chapter}` trong `main.tex` đúng thứ tự. Không copy trực tiếp nguồn PDF bản quyền vào repository.

## Tài liệu chính và giới hạn

Nội dung chương 3 bám sát thứ tự: Communications → Identification/Connectivity/Security/Routing → Types of IoT Networks → HTTP/CoAP/MQTT/WebSocket/AMQP/XMPP. Sơ đồ được vẽ độc lập bằng TikZ, kèm các lưu ý kiểm chứng với những thông số hoặc khẳng định đơn giản hóa từ slide.