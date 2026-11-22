# UTH LaTeX Template (Bản Tiếng Việt) 🎓

Template báo cáo tiểu luận, đồ án môn học chuẩn định dạng dành cho sinh viên **Trường Đại học Giao thông Vận tải TP.HCM (UTH)**.

Được thiết kế theo cấu trúc mô-đun chuẩn, tối ưu hóa cho **Overleaf** và biên dịch cục bộ (TeX Live / VS Code / Makefile).

---

## 📁 Cấu trúc Thư mục Dự án

```text
uth_latex_template_vi/
├── main.tex                    # File biên dịch chính (chỉ chứa khung \input)
├── preamble.tex                # Khai báo gói, font 13pt Times, thông tin đề tài
├── refs.bib                    # Cơ sở dữ liệu tài liệu tham khảo (BibTeX)
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

## 💡 Quy ước Soạn thảo Nhanh

* **Thêm hình ảnh:** Đặt ảnh vào thư mục `figures/` (ví dụ `figures/my_chart.png`). Trong bài chỉ cần gọi `\includegraphics[width=...]{my_chart.png}` (đường dẫn `figures/` đã được cấu hình tự động).
* **Trích dẫn nguồn ảnh/bảng:** Sử dụng lệnh `\source{Tên nguồn}` ngay dưới caption.
* **Trích dẫn tài liệu:** Thêm entry vào `refs.bib` và dùng `\cite{key}` trong văn bản.
* **Chèn code:** Dùng môi trường `\begin{lstlisting}[language=Python] ... \end{lstlisting}`.

---

## 📄 Bản quyền
Phát hành theo giấy phép [MIT License](LICENSE).
