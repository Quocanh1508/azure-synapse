# 🚀 Lab Bộ môn Phân tích dữ liệu lớn (BDAN): Triển khai End-to-End Data Pipeline với Azure Synapse Analytics

**Trường:** Đại học Công nghệ Kỹ thuật TP.HCM (HCMUTE)
**Môn học:** Phân tích Dữ liệu Lớn
**Nhóm thực hiện:** Nhóm 8

---

## 📑 1. Giới thiệu Dự án
Dự án này thực hành xây dựng một hệ thống phân tích dữ liệu toàn diện (End-to-End Data Analytics Solution) sử dụng nền tảng điện toán đám mây **Microsoft Azure Synapse Analytics**. 

Mục tiêu của dự án là thiết lập hạ tầng lưu trữ, tự động hóa quá trình thu thập dữ liệu (ETL/ELT), xử lý, phân tích khối lượng dữ liệu lớn và trực quan hóa kết quả kinh doanh.

## 🗄️ 2. Tập dữ liệu (Datasets)
Dự án sử dụng bộ dữ liệu công cộng chuẩn từ **NYC Taxi & Limousine Commission (TLC)**, bao gồm:
1. **Yellow Taxi Trip Records:** Hàng triệu bản ghi chi tiết về các chuyến đi của taxi vàng tại New York (Được lấy từ Azure Open Datasets).
2. **Taxi Zone Lookup:** File danh sách phân vùng địa lý (`taxi_zone_lookup.csv`) được tự động hóa kéo về từ nguồn HTTP của chính quyền NYC thông qua Synapse Pipeline.

## 🏗️ 3. Kiến trúc Hệ thống (Architecture)
Hệ thống được thiết kế theo luồng kiến trúc dữ liệu hiện đại trên Azure:
* **Storage (Lưu trữ):** Azure Data Lake Storage Gen2 (`dlhcmute` -> thư mục `data`).
* **Ingestion (Thu thập):** Sử dụng **Synapse Pipelines (Copy Data tool)** để tự động hóa việc kéo dữ liệu từ Web/HTTP thẳng vào Data Lake.
* **Exploration (Khám phá):** Sử dụng **Serverless SQL Pool** để truy vấn trực tiếp dữ liệu thô (file CSV, Parquet) nhằm thống kê nhanh.
* **Transformation (Xử lý):** Sử dụng **Apache Spark Pool (PySpark)** để làm sạch dữ liệu (Data Cleaning), kết nối (JOIN) bảng lịch sử chuyến đi với bảng phân vùng địa lý.
* **Visualization (Trực quan hóa):** Tích hợp Power BI để xây dựng Dashboard báo cáo nghiệp vụ.
* **CI/CD & Version Control:** Tích hợp với **GitHub** (`main` branch) để kiểm soát phiên bản mã nguồn liên tục.

## ⚙️ 4. Hướng dẫn sử dụng / Khôi phục môi trường
*Mã nguồn trong kho lưu trữ này được liên kết trực tiếp với Azure Synapse Workspace
1. Đảm bảo bạn có quyền truy cập vào Synapse Workspace (`hcmutebigdata01`).
2. Clone repository này về hoặc xem trực tiếp cấu trúc thư mục `/pipeline`, `/dataset`, `/sqlscript` đã được Synapse tự động đồng bộ.
3. Chạy Pipeline `Get_Taxi_Zone_Data` để load dữ liệu lookup.
4. Chạy các file `.sql` trong thư mục SQL Scripts để xem kết quả phân tích.
