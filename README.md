# Dự báo nhu cầu taxi tại New York (Taxi Demand Forecasting NYC)

## Tổng quan dự án

Dự án này tập trung vào việc dự báo nhu cầu taxi tại thành phố New York dựa trên dữ liệu lịch sử các chuyến đi. Việc dự đoán chính xác nhu cầu giúp tối ưu hóa hệ thống vận tải, giảm thời gian chờ của hành khách và cải thiện hiệu quả phân bổ tài xế.

Dự án được xây dựng theo quy trình khoa học dữ liệu hoàn chỉnh (end-to-end), bao gồm: tiền xử lý dữ liệu, phân tích khám phá (EDA), xây dựng đặc trưng, huấn luyện mô hình và đánh giá kết quả.

## Mục tiêu

* Phân tích dữ liệu taxi để hiểu các xu hướng nhu cầu
* Xác định các yếu tố thời gian (giờ, ngày, tuần) ảnh hưởng đến nhu cầu
* Xây dựng các mô hình dự báo nhu cầu taxi
* Đánh giá và so sánh hiệu năng các mô hình

## Dữ liệu

Dữ liệu bao gồm các chuyến taxi tại New York với các thông tin như:

* Thời gian đón khách (pickup datetime)
* Thời gian trả khách (dropoff datetime)
* Thông tin vị trí
* Các đặc trưng liên quan đến chuyến đi

Các bước xử lý dữ liệu:

* Làm sạch dữ liệu và xử lý giá trị thiếu
* Chuyển đổi dữ liệu thời gian
* Tổng hợp số lượng chuyến theo từng khoảng thời gian (ví dụ: theo giờ)

## Phân tích dữ liệu (EDA)

Phân tích dữ liệu giúp khám phá các đặc điểm quan trọng:

* Sự thay đổi nhu cầu theo giờ trong ngày
* Xu hướng theo ngày trong tuần
* Các khung giờ cao điểm (peak hours)
* Phân bố nhu cầu taxi

## Xây dựng đặc trưng (Feature Engineering)

Các đặc trưng được xây dựng nhằm cải thiện hiệu quả mô hình:

* Đặc trưng thời gian: giờ, ngày, ngày trong tuần
* Lag features: nhu cầu tại các thời điểm trước đó
* Rolling statistics: trung bình trượt

## Mô hình (Modeling)
Dự án sử dụng kết hợp cả phương pháp chuỗi thời gian truyền thống và mô hình machine learning:
### 1. SARIMAX
Mô hình SARIMAX được sử dụng để nắm bắt xu hướng và tính mùa vụ trong dữ liệu chuỗi thời gian.
Phù hợp với:
* Dữ liệu có tính chu kỳ (theo ngày/tuần)
* Dữ liệu có tự tương quan
### 2. Prophet
Prophet là mô hình dự báo chuỗi thời gian mạnh mẽ do Facebook phát triển.
Ưu điểm:
* Xử lý tốt dữ liệu thiếu
* Tự động phát hiện xu hướng
* Nắm bắt nhiều mùa vụ khác nhau
### 3. Random Forest Regressor
Mô hình học máy dạng ensemble dựa trên nhiều cây quyết định.
Ưu điểm:
* Giảm overfitting
* Nắm bắt quan hệ phi tuyến
* Ổn định và dễ triển khai

### 4. XGBoost Regressor
XGBoost là mô hình boosting mạnh mẽ cho bài toán hồi quy.
Ưu điểm:
* Độ chính xác cao
* Xử lý dữ liệu lớn hiệu quả
* Có cơ chế regularization chống overfitting

### So sánh mô hình
Các mô hình được đánh giá và so sánh dựa trên các chỉ số:
* MAE (Mean Absolute Error)
* MSE (Mean Squared Error)
Việc so sánh giúp lựa chọn mô hình phù hợp nhất cho bài toán dự báo nhu cầu taxi.

## Đánh giá kết quả
Kết quả cho thấy:
* Nhu cầu taxi có tính chu kỳ rõ ràng theo thời gian
* Các mô hình học máy (đặc biệt như XGBoost) có khả năng nắm bắt tốt các pattern phức tạp
* Các mô hình chuỗi thời gian (SARIMAX, Prophet) hoạt động tốt với dữ liệu có tính mùa vụ
* 
## Công nghệ sử dụng

* Python
* Pandas, NumPy
* Matplotlib, Seaborn
* Scikit-learn
* XGBoost
* Statsmodels (SARIMAX)
* Prophet
* Jupyter Notebook

## Insight chính
* Nhu cầu taxi tăng mạnh vào giờ cao điểm (giờ đi làm và tan ca)
* Có sự khác biệt rõ giữa ngày trong tuần và cuối tuần
* Thông tin lịch sử đóng vai trò quan trọng trong dự báo

## Kết luận
Dự án chứng minh rằng việc kết hợp giữa phân tích dữ liệu và mô hình dự báo có thể giải quyết hiệu quả bài toán thực tế trong lĩnh vực giao thông đô thị. Kết quả có thể được áp dụng để tối ưu hóa dịch vụ gọi xe và quản lý vận tải.

