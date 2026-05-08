# Mô tả bộ dữ liệu và bài toán

## Bộ dữ liệu

- [Global AI Adoption & Workforce Impact Dataset](https://www.kaggle.com/datasets/mohankrishnathalla/global-ai-adoption-and-workforce-impact-dataset?resource=download)
- Định dạng: CSV
- Kích thước: 38.5 MB (windows)

`Mô tả`: Bộ dữ liệu này thu thập các chỉ số cấp công ty, bao gồm giai đoạn áp dụng AI, đầu tư vào AI, tỷ lệ tự động hóa, thay đổi lực lượng lao động, thực tiễn quản trị và các chỉ số hiệu suất kinh doanh. Nó cũng bao gồm các chỉ số cấp quốc gia vĩ mô ảnh hưởng đến quá trình chuyển đổi số và mô hình áp dụng AI.

`Đặc tính (file chính ai_company_adoption.csv)`:
- Có 43 trường dữ liệu trong đó: 2 trường id, 12 trường category, 27 trường numeric và 2 trường chore.

`Mở rộng`: Bên cạnh file chính, bộ dữ liệu còn bao gồm 2 file phụ: ai_industry_summary.csv (7 trường numeric) và country_ai_index.csv (5 trường numeric, 1 trường category), bổ sung đặc trưng thông tin tổng quan về ngành công nghiệp và chỉ số AI quốc gia.

## Bài toán

Thực hiện bài toán `hồi quy` với đầu ra dự kiến là `revenue_growth_percent` (tỉ lệ tăng doanh thu) hoặc `customer_satisfaction` (mức độ hài lòng của khách hàng).

# Đánh giá mức độ phù hợp của đề tài với bộ môn Học Máy

- Thỏa mãn các yêu cầu về dữ liệu của thầy: đầu vào có ít nhất 15 thuộc tính bao gồm cả dạng số và dạng lựa chọn (category), 300 mẫu – đầu ra có dạng giá trị số (đại lượng liên tục - numeric)

Điểm hay:
- `Trường numeric`: Phần lớn các trường numeric đều có xu hướng tuân theo phân phối chuẩn, điều này có thể giúp cho việc áp dụng các thuật toán hồi quy tuyến tính hoặc các mô hình dựa trên giả định phân phối chuẩn trở nên hiệu quả hơn.
- `Trường category`: Đa dạng các loại category và cần mã hóa theo nhiều cách khác nhau (có thể là điểm cộng 🤔) như trường `quater`[¹] (Q1/Q2/Q3/Q4) do Q4 gần Q1 hơn Q3 gần Q1 lên phải label kiểu [(0,0)/(0,1)/(1,1)/(1,0)], trường `industry` (Education/Finance/Healthcare/...) cần dùng one-hot-encoding, trường `company_size` (Startup/SME/Enterprise/...) phân chia cấp độ thì cần label theo Ordinal Encoding (1/2/3/...).

[¹] `quater`: Quý trong năm, vì thế Q1 (tháng 1-3) gần Q4 (tháng 10-12) hơn là Q3 (tháng 7-9) nên cần mã hóa theo kiểu vòng tròn để phản ánh mối quan hệ này.