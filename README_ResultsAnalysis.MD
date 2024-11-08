# Analysis of Results

In this analysis, we evaluate the performance of the GPT-4o model on classifying fundus images from the BRSET dataset for the presence of Drusen (1 if present, 0 if absent). We conducted two experiments to assess potential biases in the model's performance across different demographic groups:

- **Experiment 1 (Age Groups):** Young, Middle-aged, and Older adults.
- **Experiment 2 (Sex Groups):** Male and Female patients.

## Explanation of the Analysis

1. **Data Overview:**
   - Summarized the dataset distribution for both experiments, including the number of images and Drusen cases in each group.

2. **Metric Calculation:**
   - Calculated performance metrics for each group using standard classification metrics:
     - **Overall Metrics:** Accuracy, Precision, Recall, False Positive Rate (FPR), False Negative Rate (FNR), Demographic Parity, Calibration, False Discovery Rate (FDR), False Omission Rate (FOR).
     - **Class-specific Metrics:** Precision, Recall, and F1 Score for Drusen presence (positive class) and absence (negative class).

3. **Bias Analysis Techniques:**
   - Applied fairness metrics to identify potential biases:
     - **Demographic Parity:** Examined selection rates across groups.
     - **Equalized Odds:** Compared TPR and FPR across groups.
     - **Equal Opportunity:** Focused on TPR similarities.

4. **Interpretation:**
   - Analyzed the metrics to detect disparities in model performance.
   - Identified significant differences indicating potential biases.

5. **Considerations:**
   - Acknowledged the limitations due to small sample sizes (50 samples per group).
   - Emphasized that findings are indicative and require further investigation with larger datasets.
   - Highlighted the importance of early bias detection, especially as AI models like GPT-4o may be increasingly used in medical diagnostics.

6. **Recommendations:**
   - [to be added]

---

## Dataset Overview

### Age Experiment:

- **Total Images per Group:**
  - **Young:** 50 images
  - **Middle-aged:** 50 images
  - **Older:** 50 images

- **Drusen Presence per Group:**
  - **Young:** 20 images with Drusen
  - **Middle-aged:** 25 images with Drusen
  - **Older:** 27 images with Drusen

### Sex Experiment:

- **Total Images per Group:**
  - **Male:** 50 images
  - **Female:** 50 images

- **Drusen Presence per Group:**
  - **Male:** 30 images with Drusen
  - **Female:** 31 images with Drusen

## Understanding Drusen and Age

Drusen are small, yellowish deposits that form under the retina, commonly associated with aging, and are more prevalent in individuals over 60. In younger people, Drusen tend to be smaller and less numerous, making them less apparent and potentially more challenging to detect during eye examinations.

## Performance Metrics Interpretation

We interpret key metrics for each experiment to understand the model's performance and potential biases.

### Experiment 1: Age Groups

**Age Experiment Metrics:**

| **Metric**                 | **Young** | **Middle-aged** | **Older** |
|----------------------------|-----------|-----------------|-----------|
| **Overall Accuracy**       | 0.62      | 0.64            | 0.62      |
| **Overall FPR**            | 0.2667    | 0.3600          | 0.4783    |
| **Overall FNR**            | 0.5500    | 0.3600          | 0.2963    |
| **Demographic Parity**     | 0.34      | 0.50            | 0.60      |
| **Calibration**            | 0.4865    | 0.6400          | 0.6667    |
| **Overall Precision**      | 0.5294    | 0.6400          | 0.6333    |
| **Overall Recall**         | 0.4500    | 0.6400          | 0.7037    |
| **Overall FDR**            | 0.4706    | 0.3600          | 0.3667    |
| **Overall FOR**            | 0.3333    | 0.3600          | 0.4000    |
| **Presence Precision**     | 0.5294    | 0.6400          | 0.6333    |
| **Presence Recall**        | 0.4500    | 0.6400          | 0.7037    |
| **Presence F1**            | 0.4865    | 0.6400          | 0.6667    |
| **Absence Precision**      | 0.6667    | 0.6400          | 0.6000    |
| **Absence Recall**         | 0.7333    | 0.6400          | 0.5217    |
| **Absence F1**             | 0.6984    | 0.6400          | 0.5581    |

**Bias Analysis:**

1. **Demographic Parity (Selection Rate):**
   - **Selection Rates:**
     - **Young:** 34%
     - **Middle-aged:** 50%
     - **Older:** 60%
   - The model predicts Drusen presence more frequently in older adults, indicating a potential bias favoring older individuals.

2. **Equalized Odds:**
   - **True Positive Rate (Recall):**
     - **Young:** 45%
     - **Middle-aged:** 64%
     - **Older:** 70.37%
   - **False Positive Rate (FPR):**
     - **Young:** 26.67%
     - **Middle-aged:** 36%
     - **Older:** 47.83%
   - Significant differences in TPR and FPR across age groups violate the Equalized Odds criterion, suggesting bias.

3. **Equal Opportunity:**
   - The TPR increases with age, showing the model is better at detecting Drusen in older individuals, indicating bias.

**Interpretation:**

- **Age Bias Toward Older Adults:**
  - The model is more effective at detecting Drusen in older adults, likely due to more pronounced features associated with aging.
  - However, higher FPR in older adults suggests a tendency to over-predict Drusen presence, potentially leading to false positives.
- **Underperformance in Younger Adults:**
  - Lower recall indicates the model misses a significant number of actual Drusen cases in young individuals.
  - This could result in underdiagnosis and delayed treatment for younger patients.
- **Implications:**
  - The model's performance reflects clinical realities but also highlights a bias that may disadvantage certain age groups.
  - There is a need to improve detection in younger individuals without increasing false positives in older adults.

### Experiment 2: Sex Groups

**Sex Experiment Metrics:**

| **Metric**                 | **Male** | **Female** |
|----------------------------|----------|------------|
| **Overall Accuracy**       | 0.60     | 0.68       |
| **Overall FPR**            | 0.3000   | 0.4737     |
| **Overall FNR**            | 0.4667   | 0.2258     |
| **Demographic Parity**     | 0.44     | 0.66       |
| **Calibration**            | 0.6154   | 0.7500     |
| **Overall Precision**      | 0.7273   | 0.7273     |
| **Overall Recall**         | 0.5333   | 0.7742     |
| **Overall FDR**            | 0.2727   | 0.2727     |
| **Overall FOR**            | 0.5000   | 0.4118     |
| **Presence Precision**     | 0.7273   | 0.7273     |
| **Presence Recall**        | 0.5333   | 0.7742     |
| **Presence F1**            | 0.6154   | 0.7500     |
| **Absence Precision**      | 0.5000   | 0.5882     |
| **Absence Recall**         | 0.7000   | 0.5263     |
| **Absence F1**             | 0.5833   | 0.5556     |

**Bias Analysis:**

1. **Demographic Parity (Selection Rate):**
   - **Selection Rates:**
     - **Male:** 44%
     - **Female:** 66%
   - The model predicts Drusen presence more frequently in females, indicating potential bias.

2. **Equalized Odds:**
   - **True Positive Rate (Recall):**
     - **Male:** 53.33%
     - **Female:** 77.42%
   - **False Positive Rate (FPR):**
     - **Male:** 30%
     - **Female:** 47.37%
   - Significant differences in TPR and FPR between sexes violate the Equalized Odds criterion.

3. **Equal Opportunity:**
   - Higher TPR in females indicates the model is better at detecting Drusen in female patients, suggesting bias.

**Interpretation:**

- **Sex Bias Favoring Females in Drusen Detection:**
  - The model is more sensitive in detecting Drusen in females (higher recall).
  - However, increased FPR suggests a tendency to over-predict Drusen in females, leading to potential false positives.
- **Underdiagnosis in Males:**
  - Lower recall for Drusen presence indicates the model misses more actual cases in males.
  - This could lead to underdiagnosis and delayed treatment in male patients.
- **Implications:**
  - The disparity in performance could contribute to unequal healthcare outcomes between sexes.
  - Addressing this bias is essential to ensure accurate diagnoses for both male and female patients.

## Overall Analysis and Recommendations

**Summary of Biases Identified:**

- **Age Bias:**
  - The model favors older adults, with higher detection rates and selection rates in this group.
  - Younger adults are at risk of underdiagnosis due to lower detection rates.
- **Sex Bias:**
  - The model favors female patients, with higher detection rates but also higher false positive rates.
  - Male patients may experience underdiagnosis.

**Considerations on Sample Size:**

- **Limited Sample Size:**
  - With only 50 samples per group, the dataset is relatively small.
  - Findings are indicative and should be interpreted with caution.
  - Larger, more diverse datasets are needed to draw definitive conclusions about model bias.

**Importance of Early Bias Detection:**

- **Future Implications:**
  - While GPT-4o may not yet be ready for this diagnostic task, AI models are increasingly being integrated into healthcare.
  - Early identification of potential biases helps in refining models and ensuring they are fair and reliable.
  - Understanding biases in current models can guide the development of future models and prompt evaluation of similar models for comparable biases.

**Future Work:**

- [to be added]

Addressing these biases is crucial to ensure fair and accurate diagnostic support. While the model is not yet ready for clinical deployment and would be used as an additional tool rather than a standalone diagnostic system, identifying these potential biases is important. As AI models become more prevalent in healthcare, early detection and mitigation of biases can improve model development and patient outcomes.

By implementing the suggestions in future work, we can further investigate the model's fairness and reliability, contributing to the validation of results and potentially raising the need for improvement in order for a more equitable healthcare for all patient groups. Additionally, recognizing these biases raises awareness to examine other similar models for potential biases, promoting responsible and ethical AI integration in medical diagnostics.

---

**Note:** Continuous efforts are essential to monitor and mitigate biases in AI models, especially in healthcare, where implications directly affect patient well-being. Collaboration between data scientists and medical professionals is key to developing ethical and effective diagnostic tools. Future studies should utilize larger and more diverse datasets to validate these findings and further refine the model.

