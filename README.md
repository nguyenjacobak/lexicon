# lexicon
# Phân tích Cảm xúc Tiếng Việt dựa trên Từ điển (Lexicon-Based Sentiment Analysis)

[cite_start]Dự án này áp dụng phương pháp dựa trên từ điển cảm xúc (Lexicon-Based Approach) để chấm điểm và phân loại cảm xúc cho các câu đánh giá trong tập dữ liệu **VSA - Food Reviews**[cite: 5].

## 📖 Giới thiệu

[cite_start]Phân tích cảm xúc là bài toán quan trọng trong NLP[cite: 4]. Nghiên cứu này thực hiện qua 02 giai đoạn:
1.  [cite_start]Sử dụng từ điển cảm xúc có sẵn **VietSentiWordNet**[cite: 7].
2.  [cite_start]Tự xây dựng từ điển mở rộng (**20.500 từ**) sử dụng Mô hình ngôn ngữ lớn (LLM - Gemini)[cite: 8, 62].

## 📂 Cấu trúc Dữ liệu

### 1. Từ điển cảm xúc
* [cite_start]**VietSentiWordNet** (`VietSentiWordnet_Ver1.3.5.txt`)[cite: 12]:
    * Quy mô: ~1000 từ.
    * [cite_start]Gồm 2 điểm: `PosScore` và `NegScore`[cite: 13].
    * [cite_start]Công thức: `Polarity = PosScore - NegScore`[cite: 14].
* **Từ điển mở rộng** (Custom Lexicon):
    * [cite_start]Được tạo tự động bằng cách cào định nghĩa từ web và dùng Gemini chấm điểm trong khoảng $[-1, 1]$[cite: 61, 62, 63].

### 2. Từ chỉ mức độ (Intensifiers)
[cite_start]File `tu_muc_do.txt` chứa các từ và hệ số nhân tương ứng[cite: 21, 22]. Ví dụ:
```text
rất: 1.5
cực kỳ: 2.0
hơi: 0.8
