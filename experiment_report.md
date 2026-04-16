# Experiment Report: Data Quality Impact on AI Agent

**Student ID:** 2A202600218  
**Name:** Nguyễn Tiến Đạt  
**Date:** 15/04/2026  

---

## Experiment Results

| Scenario                          | Agent Response                                                   | Accuracy (1-10) | Notes                                             |
| --------------------------------- | ---------------------------------------------------------------- | --------------- | ------------------------------------------------- |
| Clean Data (`processed_data.csv`) | Based on my data, the best choice is Laptop at $1200.            | 9/10            | Clean data leads to reliable results              |
| Garbage Data (`garbage_data.csv`) | Based on my data, the best choice is Nuclear Reactor at $999999. | 2/10            | Noisy data leads to unrealistic results           |

---

## Analysis

When using garbage data, the quality of input data significantly decreases, which leads to incorrect decisions by the AI agent.

- **Outliers:** Extremely large values (e.g., Nuclear Reactor price) distort decision-making.
- **Wrong data types:** Incorrect formats (string instead of numeric) can break calculations.
- **Missing values:** Missing `price` or `category` reduces data reliability.
- **Duplicate records:** Can bias the model toward certain values.
- **Lack of validation:** Without proper filtering, bad data flows into the system.

As a result, the agent selects unrealistic options instead of reasonable ones.

---

## Insights

- Data quality is critical for reliable AI systems.
- Poor quality data can lead to incorrect and misleading outputs.
- Validation is essential in ETL pipelines to filter bad data.
- Logging improves observability and helps detect issues early.
- AI systems depend heavily on the quality of input data.

---

## Conclusion

**Quality Data > Quality Prompt**

Even with a well-designed prompt, poor data quality will still produce bad results.

- Clean Data → Accurate and meaningful output  
- Garbage Data → Incorrect and misleading output  

This demonstrates the principle:

> Garbage In → Garbage Out

Therefore, building a strong ETL pipeline with proper validation and data cleaning is essential for trustworthy AI systems.