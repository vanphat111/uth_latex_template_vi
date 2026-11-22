# UTH LaTeX Template (Bản Tiếng Việt) 🎓

Template báo cáo tiểu luận, đồ án môn học chuẩn định dạng dành cho sinh viên **Trường Đại học Giao thông Vận tải TP.HCM (UTH)**.

Được thiết kế theo cấu trúc mô-đun chuẩn, tối ưu hóa cho **Overleaf**, biên dịch cục bộ (TeX Live / VS Code / Makefile), và đặc biệt **tương thích hoàn hảo với các AI Assistant** (Cursor, ChatGPT, Claude, Gemini...).

---

## 📁 Cấu trúc Thư mục Dự án

```text
uth_latex_template_vi/
├── main.tex                    # File biên dịch chính (chỉ chứa khung \input)
├── preamble.tex                # Khai báo gói, font 13pt Times, thông tin đề tài
├── refs.bib                    # Cơ sở dữ liệu tài liệu tham khảo (BibTeX)
├── AI_GUIDELINES.md            # Nguyên tắc & prompt chuẩn cho AI Assistant
├── README.md                   # Hướng dẫn sử dụng & cấu trúc dự án
├── Makefile                    # Tự động hóa build PDF trên Linux/macOS
├── .gitignore                  # Bỏ qua các file tạm/rác do LaTeX sinh ra
│
├── frontmatter/                # Phần đầu báo cáo (đánh số trang La Mã i, ii...)
│   ├── titlepage.tex           # Trang bìa chuẩn viền đôi TikZ
│   ├── declaration.tex         # Lời cam đoan
│   ├── acknowledgments.tex     # Lời cảm ơn
│   └── abbreviations.tex       # Bảng danh mục từ viết tắt
│
├── chapters/                   # Nội dung chính (đánh số Ả Rập 1, 2, 3...)
│   ├── 01_introduction.tex     # Chương 1: Mở đầu, bối cảnh, mục tiêu
│   ├── 02_theoretical_background.tex  # Chương 2: Cơ sở lý thuyết & công thức
│   ├── 03_methodology.tex      # Chương 3: Phương pháp & kiến trúc hệ thống
│   ├── 04_implementation_results.tex  # Chương 4: Hiện thực mã nguồn & thử nghiệm
│   └── 05_conclusion.tex       # Chương 5: Kết luận & hướng phát triển
│
├── appendices/                 # Phụ lục báo cáo (A, B, C...)
│   └── appendix_a.tex          # Phụ lục A: Mã nguồn, link repo, cấu hình phụ
│
├── figures/                    # Thư mục chứa hình ảnh & đồ thị
│   └── uth_logo.png            # Logo trường UTH
│
├── tables/                     # Thư mục chứa bảng biểu phức tạp (tùy chọn)
└── code/                       # Thư mục chứa mã nguồn đính kèm (tùy chọn)
```

---

## 🤖 Hướng dẫn Dành cho AI Assistant (ChatGPT, Claude, Cursor...)

Nếu bạn dùng các công cụ lập trình AI (như **Cursor**, **GitHub Copilot**, **ChatGPT**, **Claude**) để hỗ trợ viết báo cáo, hãy cấp file [AI_GUIDELINES.md](AI_GUIDELINES.md) làm context hoặc system prompt:

### Các nguyên tắc cốt lõi AI cần tuân thủ:
1. **Kiến trúc mô-đun:** Không bao giờ viết thẳng nội dung vào `main.tex`. Mọi chương phải nằm trong thư mục `chapters/`. Không khai báo lại `\documentclass` hay `\begin{document}` trong các file con.
2. **Metadata đề tài:** Mọi thay đổi tên đề tài, tên sinh viên, giảng viên... phải sửa tại các biến macro trong `preamble.tex`, không sửa cứng trong file bìa `frontmatter/titlepage.tex`.
3. **Quy chuẩn Bảng biểu (`table`):**
   - Vị trí `[H]`.
   - `\caption{...}` **ở trên** bảng.
   - Luôn kèm `\source{...}` ngay dưới `\end{tabular}`.
4. **Quy chuẩn Hình ảnh (`figure`):**
   - Vị trí `[H]`. Ảnh để trong `figures/` (không ghi tiền tố `figures/` trong `\includegraphics`).
   - `\caption{...}` **ở dưới** ảnh.
   - Luôn kèm `\source{...}` ngay dưới `\caption{...}`.
5. **Trích dẫn khoa học:** Mọi trích dẫn phải khai báo trong `refs.bib` và gọi bằng `\cite{key}` (chuẩn IEEE `[1]`, `[2]`). Tuyệt đối không gõ tay số trích dẫn.

👉 *Xem chi tiết đầy đủ các quy tắc tại [AI_GUIDELINES.md](AI_GUIDELINES.md).*

---

## 🚀 Hướng dẫn Sử dụng

### 1. Dùng trên Overleaf (Khuyên dùng)
1. Tải toàn bộ repository về dưới dạng file `.zip` (hoặc nhấn **Code** $\rightarrow$ **Download ZIP** trên GitHub).
2. Đăng nhập [Overleaf](https://www.overleaf.com/).
3. Chọn **New Project** $\rightarrow$ **Upload Project** và tải file `.zip` lên.
4. Chọn compiler mặc định là **pdfLaTeX** và nhấn **Recompile**.

### 2. Dùng trên máy tính cục bộ
Yêu cầu hệ thống đã cài đặt TeX Live:

```bash
# Biên dịch tạo file main.pdf
make

# Dọn dẹp file tạm (.aux, .log, .toc...)
make clean

# Chế độ tự động re-compile khi lưu file (cần latexmk)
make watch
```

---

## ⚙️ Hướng dẫn Tùy biến Thông tin

Tất cả thông tin đồ án được quản lý tập trung tại cuối file `preamble.tex`. Bạn chỉ cần mở file này và chỉnh sửa các dòng sau:

```latex
\newcommand{\UnivName}{TRƯỜNG ĐẠI HỌC GIAO THÔNG VẬN TẢI TP.HCM}
\newcommand{\InstituteName}{VIỆN CÔNG NGHỆ THÔNG TIN VÀ ĐIỆN - ĐIỆN TỬ}
\newcommand{\ReportType}{BÁO CÁO TIỂU LUẬN / ĐỒ ÁN}
\newcommand{\ProjectTitle}{TÊN ĐỀ TÀI CỦA BẠN VIẾT HOA TẠI ĐÂY}
\newcommand{\CourseName}{Tên Môn Học}
\newcommand{\ClassCode}{Mã Lớp Học Phần}
\newcommand{\InstructorName}{TS. Nguyễn Văn A}
\newcommand{\StudentName}{Họ Và Tên Sinh Viên}
\newcommand{\StudentID}{1234567890}
\newcommand{\LocationDate}{TP. Hồ Chí Minh, Tháng ... Năm 2026}
```
*Trang bìa, lời cam đoan và lời cảm ơn sẽ tự động đồng bộ theo các thông tin này!*

---

## 📄 Bản quyền
Phát hành theo giấy phép [MIT License](LICENSE).
