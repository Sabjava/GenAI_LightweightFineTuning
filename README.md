**Project Report: Lightweight Fine-Tuning of GPT-2 Using LoRA**
 Udacity GenAI nanodegree project


### **Overview**
This project focuses on lightweight fine-tuning of the GPT-2 model using the LoRA (Low-Rank Adaptation) technique. The Rotten Tomatoes dataset was used for fine-tuning, and the Hugging Face Trainer was employed for evaluation.

### **Objectives**
- To efficiently fine-tune a pre-trained GPT-2 model for sentiment analysis using LoRA.
- To evaluate the model’s performance in terms of accuracy, F1 score, precision, recall, and loss.

### **Dataset**
- **Name**: Rotten Tomatoes
- **Source**: Hugging Face Datasets
- **Description**: A binary sentiment analysis dataset consisting of positive and negative movie reviews.

### **Model**
- **Base Model**: GPT-2
- **Fine-Tuning Method**: LoRA with parameter-efficient updates.

### **Training and Evaluation Configuration**
- **Learning Rate**: Varies across experiments (2e-5, 1e-5, 5e-6)
- **Batch Sizes**:
  - Train: 16 or 32
  - Eval: 32 or 64
- **Epochs**: 4 or 8
- **Evaluation Metrics**:
  - Accuracy
  - F1 Score
  - Precision
  - Recall
  - Loss

### **Results Summary**

| Model Variant            | Eval Loss | Accuracy (%) | F1 Score | Precision | Recall | Runtime (s) | Samples/sec | Steps/sec |
|--------------------------|-----------|--------------|----------|-----------|--------|-------------|-------------|-----------|
| **Foundation (GPT-2)**  | 1.8753    | 50.00        | 0.3333   | 0.2500    | 0.5000 | 3.7163      | 286.846     | 4.574     |
| **Training 1**          | 0.6314    | 69.51        | 0.6943   | 0.6972    | 0.6951 | 3.9093      | 272.685     | 4.349     |
| **Training 2**          | 0.6245    | 66.51        | 0.6651   | 0.6652    | 0.6651 | 3.6257      | 294.016     | 9.378     |
| **Training 3**          | 0.6719    | 60.23        | 0.6022   | 0.6023    | 0.6023 | 3.5796      | 297.797     | 9.498     |

### **Key Observations**
1. **Foundation Model Performance**:
   - The baseline model’s performance is poor, with accuracy and F1 score at 50% and 0.33, respectively, indicating random predictions.
2. **Training 1 (LoRA Rank: 4, Learning Rate: 2e-5)**:
   - Achieved the best overall performance with 69.51% accuracy and an F1 score of 0.694.
   - The model showed significant improvement compared to the baseline, benefiting from optimal learning rate and parameter tuning.
3. **Training 2 (LoRA Rank: 4, Learning Rate: 1e-5)**:
   - Delivered slightly lower performance than Training 1 but still outperformed the foundation model with 66.51% accuracy and an F1 score of 0.665.
   - The smaller learning rate allowed more stable training but at the cost of slightly reduced performance.
4. **Training 3 (LoRA Rank: 8, Learning Rate: 5e-6)**:
   - The increased LoRA rank and smaller learning rate led to suboptimal performance (60.23% accuracy, F1 score 0.602).
   - Indicates over-regularization or insufficient learning due to very small learning rate.

### **Conclusions and Recommendations**
1. **Performance Gains**:
   - LoRA significantly improved GPT-2’s performance, with Training 1 achieving the highest accuracy (69.51%) and F1 score (0.694).
   - All fine-tuned models outperformed the foundation model by a large margin.

2. **Optimal Hyperparameters**:
   - The best results were observed with a LoRA rank of 4 and a learning rate of 2e-5.
   - Overly small learning rates (e.g., 5e-6 in Training 3) hindered performance.

3. **Future Improvements**:
   - Experiment with intermediate LoRA ranks (e.g., 6) to balance capacity and regularization.
   - Use learning rate schedulers (e.g., cosine decay) for dynamic adjustments.
   - Perform additional evaluations with cross-validation for more robust conclusions.

4. **Application Potential**:
   - Lightweight fine-tuning with LoRA demonstrates practical applicability in resource-constrained environments while maintaining strong performance gains.


