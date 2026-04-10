🚀 Predictive Maintenance Using Unsupervised Anomaly Detection
📌 Business Problem

Manufacturing industries face significant challenges due to unexpected machine failures, leading to costly downtime, operational inefficiencies, and revenue loss. A major limitation is that failure data is scarce and highly imbalanced, making it difficult to train traditional supervised machine learning models.

Therefore, there is a need for an intelligent system that can detect abnormal machine behavior at an early stage without relying on labeled data, enabling proactive maintenance and reducing operational risks.

🎯 Project Objectives
Detect abnormal machine behavior using sensor data
Apply unsupervised learning techniques
Compare performance of multiple models
Enable predictive maintenance to minimize downtime
📊 Dataset Description
Dataset: AI4I 2020 Predictive Maintenance Dataset
Source: https://www.kaggle.com/datasets/stephanmatzka/predictive-maintenance-dataset-ai4i-2020
Size: ~10,000 records
🔑 Key Features:
Air Temperature
Process Temperature
Rotational Speed
Torque
Tool Wear

The dataset contains both normal operating conditions and machine failure cases, making it suitable for anomaly detection.

📈 Data Visualization Insight
🔍 Axes Representation:
X-axis: Rotational Speed (RPM) — speed of machine rotation
Y-axis: Torque (Nm) — force produced by the machine
🎨 Color Representation:
🔵 Blue → Normal operation
🔴 Red → Anomaly / Failure
📊 Observed Pattern:
A clear inverse relationship exists:
Low speed → High torque
High speed → Low torque
⚠️ Anomaly Behavior:
Anomalies appear:
At extreme conditions (very high/low speed and torque)
Outside the dense normal cluster
Occasionally within normal regions
🧠 Interpretation:
The model learns the normal operating curve
Deviations from this curve are flagged as anomalies
Performance is stronger at extreme values but weaker in dense regions
🧹 Data Preprocessing
Handled missing values using imputation/removal
Encoded categorical variables into numerical format
Applied StandardScaler for feature normalization
Selected relevant features to improve performance
⚙️ Methodology
🌲 Isolation Forest
Randomly partitions data to isolate anomalies
Anomalies are detected faster than normal points
Works well with high-dimensional data
Does not rely on distance metrics
⭕ One-Class SVM
Learns a boundary around normal data
Points outside the boundary are classified as anomalies
Sensitive to parameter tuning
Provides stable performance
🔵 DBSCAN
Density-based clustering algorithm
Identifies anomalies as low-density points
No need to define number of clusters
Effective for irregular data patterns
🧠 Model Implementation

The models were implemented using Python and Scikit-learn.

Steps:
Data preprocessing
Model training
Anomaly detection
Performance evaluation
📏 Evaluation Metrics
Accuracy
Precision
Recall
F1-score

⚠️ Due to class imbalance, accuracy is not a reliable metric.
Greater emphasis is placed on precision, recall, and F1-score.

📊 Results & Analysis
🔍 Model Comparison
Isolation Forest
Balanced precision and recall
Effective anomaly detection
Suitable for complex datasets
One-Class SVM
Stable and consistent performance
Sensitive to parameter tuning
DBSCAN
High precision
Low recall (misses many anomalies)
🏆 Best Model: Isolation Forest
✅ Why Isolation Forest?
Provides the best balance between precision and recall
Effectively detects anomalies
Suitable for real-world predictive maintenance systems
🔑 Key Insights
Accuracy is misleading due to imbalanced data
Recall is critical in failure detection problems
DBSCAN is precise but misses many anomalies
One-Class SVM requires careful tuning
Isolation Forest performs best overall
Unsupervised learning works well without labeled data
🏁 Final Conclusion

This project demonstrates that unsupervised learning techniques can effectively detect machine anomalies using sensor data without requiring labeled data. Among the models evaluated, Isolation Forest achieved the best overall performance, maintaining a strong balance between precision and recall.

While DBSCAN achieved high precision, it failed to detect many anomalies due to low recall. One-Class SVM showed moderate and stable performance. Therefore, Isolation Forest is the most suitable model for predictive maintenance, as it enables early detection of failures and helps reduce downtime and operational costs.

🔮 Future Scope
Hyperparameter tuning for improved performance
Real-time anomaly detection systems
Integration with IoT-based monitoring
Exploration of deep learning approaches
