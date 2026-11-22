# 🤖 HƯỚNG DẪN DÀNH CHO AI ASSISTANT (AI PROMPT / SYSTEM RULES)

Tài liệu này quy định các nguyên tắc nghiêm ngặt mà các trợ lý AI (ChatGPT, Claude, Gemini, Cursor, Copilot...) **BẮT BUỘC** phải tuân thủ khi sinh mã nguồn, viết nội dung hoặc chỉnh sửa tài liệu trong dự án LaTeX này.

---

## 1. 📌 Nguyên tắc Kiến trúc Cốt lõi

1. **Không viết nội dung vào `main.tex`:**
   - File `main.tex` chỉ đóng vai trò khung xương kết nối bằng các lệnh `\input{...}`.
   - Toàn bộ nội dung từng chương phải được viết riêng biệt trong thư mục `chapters/`.
2. **Không khai báo lại Preamble trong các file con:**
   - Các file trong `chapters/`, `frontmatter/`, `appendices/` **tuyệt đối không** chứa `\documentclass`, `\usepackage`, `\begin{document}`, hay `\end{document}`.
3. **Cấu hình thông tin qua Macro:**
   - Khi cần đổi tên đề tài, tác giả, giảng viên, môn học... chỉ chỉnh sửa các biến macro trong `preamble.tex` (`\ProjectTitle`, `\StudentName`, `\InstructorName`...). Không sửa cứng (hardcode) trên trang bìa `frontmatter/titlepage.tex`.

---

## 2. ✍️ Quy chuẩn Soạn thảo Văn bản (Typography)

1. **Giãn đoạn và Thụt đầu dòng:**
   - Dự án đã cấu hình chuẩn: không thụt đầu dòng (`\parindent = 0cm`) và giãn giữa các đoạn văn 6pt (`\parskip = 6pt`).
   - **Cấm:** Không dùng các lệnh xuống dòng cưỡng bức liên tiếp như `\\ \\` hoặc `\vspace` bừa bãi giữa các đoạn văn thường. Chỉ cần cách nhau 1 dòng trống trong mã nguồn `.tex`.
2. **Tiêu đề phân cấp (Headings):**
   - Cấp 1 (Chương): `\chapter{TÊN CHƯƠNG}` (Tự động in hoa, căn giữa, font 14pt).
   - Cấp 2 (Mục lớn): `\section{Tên Mục}` (Font 13pt, đậm, căn trái).
   - Cấp 3 (Tiểu mục): `\subsection{Tên Tiểu Mục}` (Font 13pt, nghiêng đậm).
   - Cấp 4 (Mục con): `\subsubsection{Tên Mục Con}` (Font 13pt, đậm, đánh số a, b, c...).
   - **Lưu ý:** Không tự ý dùng lệnh định dạng thủ công (như `\textbf{\large ...}`) để giả lập tiêu đề.

---

## 3. 📊 Quy chuẩn Bảng biểu (Tables)

Mọi bảng biểu tạo mới phải tuân theo cấu trúc mẫu:

```latex
\begin{table}[H]
    \caption{Tên bảng biểu mô tả ngắn gọn và rõ ràng}
    \label{tab:ten_nhan_duy_nhat}
    \centering
    \begin{tabular}{|l|p{6cm}|c|}
        \hline
        \textbf{Cột 1} & \textbf{Cột 2 (Văn bản dài)} & \textbf{Cột 3} \\ \hline
        Dữ liệu 1 & Nội dung mô tả chi tiết tự xuống dòng & 100 \\ \hline
    \end{tabular}
    \source{Ghi rõ nguồn tài liệu hoặc "Tác giả tổng hợp"}
\end{table}
```

* **Quy tắc:**
  - Tiêu đề bảng (`\caption`) **bắt buộc đặt ở trên** bảng.
  - Sử dụng định vị `[H]` (từ gói `float`) để cố định vị trí.
  - Sau `\end{tabular}` **bắt buộc** có lệnh `\source{...}` để chú thích nguồn gốc số liệu.
  - Trong bài viết, tham chiếu đến bảng bằng: `Bảng~\ref{tab:ten_nhan_duy_nhat}`.

---

## 4. 🖼️ Quy chuẩn Hình ảnh & Đồ thị (Figures)

```latex
\begin{figure}[H]
    \centering
    \includegraphics[width=0.8\textwidth]{ten_file_anh.png}
    \caption{Tên hình ảnh mô tả nội dung}
    \label{fig:ten_nhan_duy_nhat}
    \source{Ghi rõ nguồn hoặc "Tác giả tự thiết kế"}
\end{figure}
```

* **Quy tắc:**
  - File ảnh phải được đặt trong thư mục `figures/`.
  - Trong lệnh `\includegraphics`, **không ghi tiền tố** `figures/` vì `\graphicspath{{figures/}}` đã được định cấu hình.
  - Tiêu đề hình (`\caption`) **bắt buộc đặt ở dưới** ảnh.
  - Sau `\caption` **bắt buộc** có lệnh `\source{...}`.
  - Tham chiếu đến hình bằng: `Hình~\ref{fig:ten_nhan_duy_nhat}`.

---

## 5. 🧮 Quy chuẩn Công thức Toán học (Math)

- Công thức nội dòng (inline): `$E = mc^2$`.
- Công thức một dòng có đánh số:
  ```latex
  \begin{equation}
      y = f(x) = ax^2 + bx + c
      \label{eq:ham_bac_hai}
  \end{equation}
  ```
- Công thức nhiều dòng canh lề: Dùng môi trường `aligned` bên trong `equation`:
  ```latex
  \begin{equation}
  \begin{aligned}
      A &= B + C \\
        &= D + E + F
  \end{aligned}
  \label{eq:bien_doi}
  \end{equation}
  ```
- Tham chiếu công thức: Sử dụng `Phương trình~\eqref{eq:ham_bac_hai}`.

---

## 6. 💻 Quy chuẩn Chèn Mã Nguồn (Code Listings)

Khi trình bày thuật toán hoặc mã lệnh, sử dụng gói `listings`:

```latex
\begin{lstlisting}[language=Python, caption={Thuật toán xử lý dữ liệu}, label={lst:thuat_toan_mau}]
def hello_world():
    print("UTH LaTeX Template")
\end{lstlisting}
```
- Tham chiếu mã nguồn: `Đoạn mã~\ref{lst:thuat_toan_mau}`.

---

## 7. 📚 Quy chuẩn Trích dẫn Tài liệu (Citations)

1. Mọi tài liệu trích dẫn phải được khai báo chuẩn BibTeX trong file `refs.bib`.
2. Trích dẫn trong bài viết bằng lệnh: `\cite{khoa_trich_dan}` (sẽ hiển thị dạng số `[1]`, `[2]` theo chuẩn IEEE).
3. **Cấm tuyệt đối:** Không tự gõ tay số `[1]` hoặc tự tạo môi trường `thebibliography` thủ công ở cuối chương.
