# Transformer (EN→VI) — Tiny From-Scratch Project

Mục tiêu: xây một mô hình Transformer nhỏ (2 encoder layers, 2 decoder layers) trên tập dữ liệu song ngữ Anh–Việt (một vài bài báo xã hội), phục vụ **dịch máy**. Dự án tối giản, toàn bộ pipeline *chuẩn bị dữ liệu → xử lý → tokenize/embedding → kiến trúc → huấn luyện → metrics → checkpoint* nằm **trong 1 notebook duy nhất**.

# Tạo môi trường
```bash
python -m venv env
source env/bin/activate  # Linux/Mac
.\env\Scripts\activate   # Windows
pip install -r requirements.txt
```

## Cấu trúc
```
Transformer/
├── README.md
├── requirements.txt
├── .gitignore
├── notebooks/
│   ├── 01_train_transformer_en2vi.ipynb   # Toàn bộ pipeline huấn luyện + xuất checkpoint + metrics
│   └── 02_demo_translate.ipynb            # Nạp checkpoint và thử dịch tương tác
├── data/
│   ├── raw/                               # Đặt/copy dữ liệu song ngữ gốc (ví dụ: article_en_vi.txt)
│   └── processed/                         # Dữ liệu đã chuẩn hoá/token hoá (nếu cần lưu)
├── models/
│   └── checkpoints/                       # Nơi lưu *.pt
├── reports/
│   └── metrics/                           # Lưu JSON/CSV metrics, figure
└── outputs/
    └── translations/                      # Kết quả dịch mẫu (txt/csv)
```

## Cách dùng nhanh
1. Mở `notebooks/01_train_transformer_en2vi.ipynb` → chạy từ trên xuống để huấn luyện và xuất checkpoint.
2. Sau khi có checkpoint, mở `notebooks/02_demo_translate.ipynb` để thử dịch tương tác.

> Lưu ý: Dự án *from scratch* sử dụng PyTorch cho mô hình; tokenization sẽ tối giản (whitespace/subword nho nhỏ) để phù hợp dữ liệu nhỏ.
