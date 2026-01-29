# 📑 Report-LaTeX Template

Dự án này là bộ khung viết báo cáo bằng **LaTeX**.  
Hỗ trợ: **XeLaTeX + Biber**.

---

## 1️⃣ Yêu cầu hệ thống

- **Windows:** [MiKTeX](https://miktex.org/download) + [TeXstudio](https://www.texstudio.org/)  
- **Linux / macOS:** [TeX Live](https://tug.org/texlive/) + TeXstudio  
- Đảm bảo có:  
  - `xelatex`  
  - `biber`  

> Lưu ý: Nếu dùng MiKTeX, hãy bật tùy chọn *Install missing packages on-the-fly*.

---

## 2️⃣ Cấu trúc thư mục

```

report-latex/
├─ main.tex              # File chính
├─ cover.tex             # Trang bìa (đã thiết kế sẵn)
├─ preamble/             # Cấu hình (packages.tex, commands.tex)
├─ sections/             # Nội dung các chương
├─ refs/references.bib   # Tài liệu tham khảo (BibTeX)
├─ figures/              # Hình ảnh
├─ tables/               # Bảng
└─ misc/                 # Phụ lục, thuật ngữ

````

---

## 3️⃣ Cách build report

### Cách 1: Dùng TeXstudio (dễ nhất)
1. Mở `main.tex` trong TeXstudio.  
2. Chọn `Tools → Commands → XeLaTeX`.  
3. Chọn `Tools → Bibliography → Biber`.  
4. Chạy lại `XeLaTeX` **2 lần**.  
➡ File `main.pdf` sẽ được sinh ra.

### Cách 2: Dùng dòng lệnh
Trong thư mục `report-latex`:

```bash
xelatex main.tex
biber main
xelatex main.tex
xelatex main.tex
````

### Cách 3: File build.bat (Windows 1-click)

Tạo file `build.bat`:

```bat
@echo off
xelatex -interaction=nonstopmode main.tex
biber main
xelatex -interaction=nonstopmode main.tex
xelatex -interaction=nonstopmode main.tex
pause
```

Double-click `build.bat` → xuất PDF tự động.

---

## 4️⃣ Thêm tài liệu tham khảo

* Mở `refs/references.bib`, thêm entry:

```bibtex
@book{goodfellow2016deep,
  title     = {Deep Learning},
  author    = {Goodfellow, Ian and Bengio, Yoshua and Courville, Aaron},
  year      = {2016},
  publisher = {MIT Press}
}
```

* Trong nội dung (ví dụ `sections/01-introduction.tex`):

```tex
Theo \cite{goodfellow2016deep}, học sâu được ứng dụng rộng rãi...
```

* Biên dịch lại (XeLaTeX → Biber → XeLaTeX ×2).

---

## 5️⃣ Lỗi thường gặp

* ❌ `latexmk.pl not found` hoặc `perl not found`:
  → Không cần `latexmk`. Hãy dùng chuỗi lệnh `xelatex → biber → xelatex`.

* ❌ `Undefined control sequence \vietnamese`:
  → Do file phụ cũ khi dùng `polyglossia`. Xóa các file `.aux, .bbl, .log, .toc, …` rồi biên dịch lại.

* ❌ `Empty bibliography`:
  → File `references.bib` rỗng hoặc chưa có `\cite{...}` trong nội dung.

---

## 6️⃣ Trang bìa (Cover)

* Trang bìa được định nghĩa trong `cover.tex`.
* Thông tin (trường, đề tài, GVHD, nhóm, thành viên) có thể chỉnh trực tiếp trong file này.
* Logo: để trong thư mục `figures/` (ví dụ: `figures/fpt-logo.png`).

---

✅ Sau khi hoàn tất, bạn sẽ có file **`main.pdf`** với đầy đủ trang bìa, mục lục, nội dung, hình/bảng, tài liệu tham khảo.
