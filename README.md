# Day 10 Lab: Data Pipeline & Data Observability

**Student Email:** 69tiendat@gmail.com
**Name:** Nguyễn Tiến Đạt

---

## Mô tả

Trong bài lab này, tôi xây dựng một **ETL Pipeline (Extract - Transform - Load)** để xử lý dữ liệu từ file JSON sang CSV.

Pipeline bao gồm các bước chính:

* **Extract:** Đọc dữ liệu từ file `raw_data.json`
* **Validate:** Kiểm tra chất lượng dữ liệu và loại bỏ các record không hợp lệ:

  * `price <= 0`
  * `category` bị thiếu hoặc rỗng
* **Transform:** Áp dụng business logic:

  * Tính `discounted_price = price * 0.9`
  * Chuẩn hóa `category` về Title Case
  * Thêm timestamp `processed_at`
* **Load:** Lưu dữ liệu đã xử lý vào file `processed_data.csv`

Ngoài ra, tôi thực hiện **stress test với AI Agent** để đánh giá ảnh hưởng của chất lượng dữ liệu (clean vs garbage data).

---

## Cách chạy (How to Run)

### Prerequisites

Cài đặt thư viện cần thiết:

```bash
pip install pandas pytest
```

---

### Chạy ETL Pipeline

```bash
python solution.py
```

Kết quả:

* Tạo file `processed_data.csv`
* In log số record hợp lệ và bị loại

---

### Chạy Agent Simulation (Stress Test)

#### 1. Với dữ liệu sạch (Clean Data)

```bash
python agent_simulation.py
```

#### 2. Với dữ liệu rác (Garbage Data)

```bash
python generate_garbage.py
python agent_simulation.py
```

#### 3. Quan sát kết quả

* Clean Data → Agent đưa ra lựa chọn hợp lý (Laptop)
* Garbage Data → Agent bị ảnh hưởng bởi outlier (Nuclear Reactor)

---

## Cấu trúc thư mục

```
├── solution.py              # ETL Pipeline script
├── processed_data.csv       # Output của pipeline
├── experiment_report.md     # Báo cáo thí nghiệm
├── raw_data.json            # Dữ liệu đầu vào
├── generate_garbage.py      # Script tạo dữ liệu bẩn
├── agent_simulation.py      # Mô phỏng AI Agent
└── README.md                # File này
```

---

## Kết quả

* **Tổng số records đầu vào:** 5
* **Records hợp lệ:** 3
* **Records bị loại:** 2

### Nhận xét:

* Pipeline hoạt động ổn định, không lỗi
* Validation giúp loại bỏ dữ liệu sai (price <= 0, category rỗng)
* Transform bổ sung đầy đủ thông tin cần thiết cho downstream tasks
* AI Agent hoạt động tốt với clean data nhưng bị ảnh hưởng mạnh bởi garbage data

---

## Kết luận

Bài lab cho thấy tầm quan trọng của **Data Quality** trong hệ thống AI.

> **Garbage In → Garbage Out**

Việc xây dựng ETL Pipeline với bước validation là cần thiết để đảm bảo:

* Độ chính xác của mô hình
* Độ tin cậy của hệ thống AI
* Tránh các kết quả phi thực tế do dữ liệu lỗi

---
