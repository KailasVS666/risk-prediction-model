Student Performance Risk Prediction Model
This project analyzes student performance data to build and evaluate machine learning models that predict whether a student is "at risk" of failing a course. The primary goal is to create an early-warning system that can help educators identify struggling students before their grades suffer, enabling timely intervention.

Methodology
The project uses a Gradient Boosting Classifier to predict student risk. The definition of an "at-risk" student is a final grade (G3) of ≤ 9 out of 20. The project explores two distinct models to serve different purposes:

Early-Warning Model: This model uses only non-academic features like demographics, family background, and lifestyle to predict risk. The key insight is that this model can identify at-risk students before their first and second-period grades (G1 and G2) are available.

End-of-Course Model: This model includes all features, including G1 and G2 grades. It serves as a highly accurate benchmark to show the predictive power of early academic performance.

The model was trained and evaluated using a comprehensive pipeline that includes:

Data preprocessing with scaling for numeric features and one-hot encoding for categorical features.

Hyperparameter tuning with GridSearchCV to find the best model configuration.

Optimization for the F2-score to prioritize recall, which is crucial for an early-warning system where missing an at-risk student (a false negative) is more costly than a false alarm (a false positive).

Fine-tuning of the classification threshold to find a practical balance between precision and recall, reducing alert fatigue for real-world application.

Key Findings
The two models performed as expected, highlighting a critical trade-off between timing and accuracy:

The End-of-Course Model showed very high predictive power (high ROC-AUC and F2-score) because it was trained on G1 and G2 grades, which are strong indicators of final performance. However, this model's predictions come too late for effective intervention.

The Early-Warning Model had lower predictive power but is far more valuable for real-world use. It successfully identifies patterns in non-academic data that are correlated with a student being at risk. By adjusting the prediction threshold, the model was tuned to prioritize a good balance between catching most at-risk students (high recall) and avoiding an excessive number of false alarms (acceptable precision).

Repository Structure
student-performance-model.ipynb: The main Google Colab notebook containing all the code for data analysis, model training, evaluation, and visualization.

student-mat.csv: The dataset used for the primary analysis of math course performance.

student-por.csv: The dataset for the Portuguese language course, included for project completeness and potential future analysis.

student.txt: A description of all the attributes in the datasets.

student-merge.R: An R script that shows how to merge the two datasets and identifies the number of shared students.

.gitignore: A file to ensure that large .joblib model files and other non-essential files are not uploaded to the repository.

How to Run the Project
Clone the repository: git clone https://github.com/KailasVS666/risk-prediction-model.git

Open in Google Colab: Upload the student-performance-model.ipynb file to your Google Colab environment.

Upload Datasets: Upload the CSV and text files to your Colab session.

Run All Cells: Execute all the cells in the notebook to recreate the entire analysis from start to finish.

Dataset
This dataset is publicly available from the UCI Machine Learning Repository.

P. Cortez and A. Silva. "Using Data Mining to Predict Secondary School Student Performance." In Proceedings of the 5th European Conference on Data Mining, Pisa, Italy, 2008.

