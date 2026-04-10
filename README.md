# UML_PROJRCT
NAME: Firdaus Khan
Business Problem
Manufacturing industries face frequent challenges due to unexpected machine failures, which result in costly downtime and operational inefficiencies. Additionally, failure data is scarce and imbalanced, making it difficult to train supervised models effectively.
There is a need for a system that can detect abnormal machine behavior early, without relying on labeled data, to reduce downtime and improve operational efficiency.

Project Objective
•	Detect abnormal machine behavior using sensor data
•	Apply unsupervised learning techniques
•	Compare model performance
•	Enable predictive maintenance to reduce downtime

Dataset Description
Dataset link : https://www.kaggle.com/datasets/stephanmatzka/predictive-maintenance-dataset-ai4i-2020 
The dataset used in this project is the AI4I 2020 Predictive Maintenance dataset. It contains machine sensor readings that help in identifying potential failures.
Key features include:
•	Air Temperature
•	Process Temperature
•	Rotational Speed
•	Torque
•	Tool Wear
The dataset consists of approximately 10,000 records and includes both normal and failure conditions.
 
🔍 What the axes represent
•	X-axis: Rotational speed (rpm) → how fast the machine is spinning 
•	Y-axis: Torque (Nm) → how much force the machine is producing
🎨 What the colors mean
•	🔵 Blue (0) → Normal operation 
•	🔴 Red (1) → Detected anomaly / failure 
📊 What the shape tells you
You can see a clear downward curve:
•	At low speed → high torque 
•	At high speed → low torque 
This is expected physical behavior (inverse relationship between speed and torque in many systems).
⚠️ Where anomalies appear
Look at the red points (failures):
1. Along the edges of the curve
•	At very high speeds + very low torque 
•	At very low speeds + very high torque 
👉 These are extreme operating conditions, which often indicate abnormal behavior.
2. Slightly outside the main blue cluster
•	Red points that sit away from the dense blue region 
👉 These are likely:
•	Sensor noise 
•	Early-stage faults 
•	Rare but valid conditions
3. Some overlap with blue points
•	A few red points are inside the normal cluster 
👉 This means:
•	Your model is not perfectly separating anomalies 
•	There are: 
o	False positives (normal labeled as anomaly) 
o	False negatives (anomalies hidden in blue)
🧠 Key interpretation
•	The model is learning the normal pattern (curve) 
•	Anything that deviates from this curve is flagged as anomaly 
•	But: 
o	It struggles in dense regions 
o	It performs better at extreme values 


Data Preprocessing
Data preprocessing is an important step to ensure model performance and accuracy.
•	Missing values were identified and handled through appropriate techniques such as imputation or removal.
•	Categorical variables (such as machine type) were encoded into numerical format.
•	Feature scaling was applied using StandardScaler to normalize the data. This step is critical for models like One-Class SVM and DBSCAN.
•	Relevant features were selected to improve model efficiency and performance.
________________________________________


Methodology
Three unsupervised learning models were used in this project:
1) Isolation Forest
Isolation Forest detects anomalies by randomly splitting the data. Anomalies are isolated faster compared to normal points. It works efficiently with high-dimensional data and does not rely on distance metrics.

2) One-Class SVM
One-Class SVM creates a boundary around normal data points in a high-dimensional space. Any data point outside this boundary is considered an anomaly.

3) DBSCAN
DBSCAN is a density-based clustering algorithm that groups closely packed points together. Points in low-density regions are classified as anomalies.
________________________________________

Model Implementation
The models were implemented using Python and machine learning libraries such as Scikit-learn.
Steps followed:
•	Data preprocessing
•	Model training
•	Anomaly prediction
•	Performance evaluation

Evaluation Metrics
The models were evaluated using the following metrics:
•	Accuracy
•	Precision
•	Recall
•	F1-score
Due to class imbalance, accuracy alone is not a reliable metric. Greater emphasis is placed on precision, recall, and F1-score.
Results and Analysis
Isolation Forest
•	Works by randomly splitting data points 
•	Anomalies are isolated faster than normal points 
•	Does not depend on distance → works well with complex data 
•	Gives a good balance between precision and recall
One-Class SVM
•	Creates a boundary around normal data 
•	Points outside the boundary are anomalies 
•	Performs well but sensitive to parameter tuning 
•	Gives moderate and stable performance
DBSCAN
•	Groups data based on density 
•	Points in low-density areas are anomalies 
•	No need to specify number of clusters 
•	Gives high precision but very low recall 
Comparison
•	Isolation Forest → Balanced performance 
•	One-Class SVM → Consistent but slightly lower 
•	DBSCAN → High precision but misses many anomalies 
🏆 Best Model
👉 Isolation Forest is the best model
Why?
•	Balanced precision and recall 
•	Detects anomalies effectively 
•	Suitable for real-world predictive maintenance 


Final Conclusion
This project demonstrates that unsupervised learning techniques can successfully detect machine anomalies using sensor data without requiring labeled data. Among the models tested, Isolation Forest provided the best overall performance by maintaining a balance between precision and recall. While DBSCAN achieved high precision, it failed to detect many anomalies, and One-Class SVM showed moderate performance. Therefore, Isolation Forest is the most suitable model for predictive maintenance, as it helps in early detection of failures and reduces operational downtime and costs.

