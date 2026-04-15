# Experiment Report: Data Quality Impact on AI Agent

**Student ID:** 2A202600218
**Name:** Nguyễn Tiến Đạt
**Date:** 15/04/2026

---

## 1. Kết quả thí nghiệm

Chạy `agent_simulation.py` với 2 bộ dữ liệu và ghi lại kết quả:

| Scenario                          | Agent Response                                                   | Accuracy (1-10) | Notes                                             |
| --------------------------------- | ---------------------------------------------------------------- | --------------- | ------------------------------------------------- |
| Clean Data (`processed_data.csv`) | Based on my data, the best choice is Laptop at $1200.            | 9/10            | Dữ liệu sạch, giá hợp lý, kết quả đáng tin cậy    |
| Garbage Data (`garbage_data.csv`) | Based on my data, the best choice is Nuclear Reactor at $999999. | 2/10            | Dữ liệu bất thường (outlier), kết quả phi thực tế |

---

## 2. Phân tích & nhận xét

### Tại sao Agent trả lời sai khi dùng Garbage Data?

Khi sử dụng Garbage Data, chất lượng dữ liệu đầu vào bị suy giảm nghiêm trọng, dẫn đến việc AI Agent đưa ra kết quả không chính xác. Một số vấn đề chính bao gồm:

* **Outliers (giá trị ngoại lai):**
  Ví dụ như sản phẩm *"Nuclear Reactor"* với giá $999999 là không thực tế trong ngữ cảnh dữ liệu. Agent không có khả năng tự hiểu đây là dữ liệu sai, nên vẫn sử dụng để đưa ra quyết định.

* **Sai kiểu dữ liệu (Wrong data types):**
  Nếu giá trị `price` bị chuyển thành string hoặc null, quá trình tính toán sẽ bị sai lệch hoặc không chính xác.

* **Thiếu dữ liệu (Null values):**
  Các record thiếu `category` hoặc `price` có thể làm mô hình hiểu sai phân phối dữ liệu.

* **Duplicate IDs (trùng lặp dữ liệu):**
  Khi dữ liệu bị lặp lại, một số giá trị có thể bị "overweight", làm bias kết quả.

* **Thiếu bước validation mạnh:**
  Nếu pipeline không lọc kỹ dữ liệu (ví dụ không loại outlier), Agent sẽ học từ dữ liệu sai.

👉 Kết quả là Agent chọn sản phẩm đắt nhất (outlier) thay vì sản phẩm hợp lý.

---

## 3. Kết luận

### **Quality Data > Quality Prompt?**

👉 **Đồng ý.**

Dữ liệu đầu vào đóng vai trò quan trọng hơn prompt trong nhiều trường hợp. Dù prompt có tốt đến đâu, nếu dữ liệu bị nhiễu, sai lệch hoặc chứa outliers, AI vẫn sẽ đưa ra kết quả sai.

Trong thí nghiệm này:

* Với **Clean Data** → Agent đưa ra lựa chọn hợp lý (Laptop).
* Với **Garbage Data** → Agent bị đánh lừa bởi dữ liệu sai (Nuclear Reactor).

👉 Điều này cho thấy:

> **Garbage In → Garbage Out**

Vì vậy, việc xây dựng một hệ thống ETL với bước **validation và data cleaning** là cực kỳ quan trọng để đảm bảo độ tin cậy của AI system.

---

## 4. Bonus Insight (Optional)

* Data Observability giúp phát hiện sớm các vấn đề dữ liệu.
* Validation là lớp bảo vệ đầu tiên của hệ thống AI.
* AI không “hiểu” dữ liệu sai — nó chỉ “học” từ dữ liệu được cung cấp.

---
