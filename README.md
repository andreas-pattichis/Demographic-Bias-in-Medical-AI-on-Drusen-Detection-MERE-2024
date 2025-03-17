# Investigating Demographic Bias in Medical AI on Drusen Detection

## Research Overview

This repository contains research investigating demographic biases in OpenAI's GPT-4 model when detecting Drusen in fundus images. Drusen are yellow deposits beneath the retina that are a key marker for age-related macular degeneration (AMD). The study analyzes how the model's performance varies across different demographic groups, specifically focusing on:

1. **Age-related bias**: Comparing performance across young (<30), middle-aged (30-60), and older (>60) adults
2. **Sex-related bias**: Evaluating performance differences between male and female patients

## Key Findings

- **Performance variation by age**: 
  - Older adults had higher recall rates (70.37%) compared to young adults (45.00%)
  - False Positive Rate (FPR) increased with age (26.67% in young vs. 47.83% in older adults)
  - The model showed a clear tendency to over-predict Drusen in older populations

- **Performance variation by sex**:
  - Female patients had significantly higher recall rates (77.42%) compared to males (53.33%)
  - Female patients also had higher false positive rates (47.37% vs. 30.00%)
  - Model showed higher selection rates for females (66% vs. 44% for males)

- **Overall performance**: While GPT-4 showed reasonable diagnostic capability (accuracy ranging from 60-68%), the observed biases could lead to disparities in healthcare outcomes if not addressed.

## Dataset

The study used the Brazilian Multilabel Ophthalmological Dataset (BRSET), consisting of:
- 16,266 color fundus photographs from 8,524 Brazilian patients
- Comprehensive demographic and clinical information
- Multiple ophthalmic conditions, with Drusen being the second most common

## Methodology

The research employed a structured approach to detect and quantify bias:

1. **Data preprocessing**: Filtered for adequate images and confirmed no missing demographic data
2. **Stratified sampling**: Selected 50 images per demographic subgroup with balanced Drusen distribution
3. **API implementation**: Used OpenAI's GPT-4 API with standardized prompts designed for binary classification
4. **Evaluation metrics**: Calculated accuracy, precision, recall, F1 score, false positive/negative rates, demographic parity, and calibration for each subgroup

## Implications for Healthcare Equity

The observed biases have significant implications:

- **Underdiagnosis risk**: Young adults and males are more likely to have their Drusen missed
- **Overdiagnosis risk**: Older adults and females face higher false positive rates
- **Healthcare disparities**: These biases could reinforce existing inequities in medical diagnostics
- **Resource allocation**: Biased models may result in inefficient distribution of healthcare resources

## Limitations and Future Directions

Key limitations of this study include:

- **Sample size**: Limited to 50 images per demographic group due to financial constraints
- **Model selection**: GPT-4 is not specifically trained for medical image analysis
- **Dataset bias**: The BRSET dataset may contain inherent biases related to the Brazilian population
- **Single condition focus**: Analysis focused only on Drusen detection

Future research should:

1. Expand dataset diversity and size to improve statistical robustness
2. Evaluate specialized ophthalmic AI models alongside general-purpose models
3. Implement bias mitigation strategies such as adversarial training
4. Conduct regular fairness audits across multiple demographic variables
5. Explore the intersection of multiple demographic factors (e.g., age and sex combined)

## Ethical Considerations

This research underscores the critical importance of evaluating AI systems for demographic biases before clinical deployment. Failure to address these biases could exacerbate existing healthcare disparities and undermine the potential benefits of AI in medicine.

## Technical Implementation

The study used:
- OpenAI's GPT-4 API for image classification
- Standardized prompts to ensure consistency
- Python data analysis libraries for metric calculation and statistical analysis
- Stratified sampling techniques to ensure balanced representation

## Conclusion

This research reveals important demographic biases in GPT-4's drusen detection capabilities that favor older adults and female patients. These findings highlight the need for comprehensive bias testing and mitigation strategies before deploying AI systems in clinical settings. Ensuring equitable performance across all demographic groups is essential to realizing AI's potential for improving healthcare outcomes.
