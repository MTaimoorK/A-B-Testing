# _A/B Testing Project_

## Author: Muhammad Taimoor Khan

## Introduction

This project conducts A/B Testing for an e-commerce company, comparing the conversion rates of the old and new landing pages. Two approaches, Frequentist and Bayesian, are utilized to analyze the results.

## Table of Contents

- [Dependencies](#dependencies)
- [Data Collection](#data-collection)
- [Frequentist Approach](#experiment-frequentist-approach)
- [Bayesian Approach](#experiment-bayesian-approach)
- [Conclusion](#conclusion)
- [Advantages of Bayesian over Frequentist](#advantages-of-bayesian-over-frequentist)

## Dependencies
```python
# Importing Dependencies
import pandas as pd
import numpy as np
import datetime
from scipy.stats import chi2_contingency, beta
from IPython.display import Image
```

### Data Collection
```python
df = pd.read_csv('./data/ab_data.csv')
print("Dataset has been read.")
df.head(5)
# ... (additional data exploration and preprocessing)
```

### Experiment: Frequentist Approach
```python
# Get Stats
NUM_WEEKS = 4
experiment_data = df[df['week'] <= NUM_WEEKS]
control = experiment_data[experiment_data['group'] == 'control']
treatment = experiment_data[experiment_data['group'] == 'treatment']

# ... (additional calculations)

# Chi-Squared Test
# ... (creating contingency table and conducting chi-squared test)
print(f"{round(p_value * 100, 2)}% probability that a more extreme chi-square than {round(chi, 3)} would have occurred by chance.")
print(f"(We CANNOT say this) We are {round(p_value * 100, 2)}% sure that our lift = {lift}%")
Image(filename='./assets/b_v_f.png')
```

### Experiment: Bayesian Approach
```python
# ... (prior distribution modeling and calculations)

# Update Prior parameters with experiment conversion rates
posterior_control = beta(prior_alpha + control_converted, prior_beta + control_unconverted)
posterior_treatment = beta(prior_alpha + treatment_converted, prior_beta + treatment_unconverted)

# ... (additional calculations)
print(f"Probability that treatment > control: {probability * 100}%")
print(f"Control Posterior: Mean: {control_mu}, Variance: {control_var}")
print(f"Treatment Posterior: Mean: {treatment_mu}, Variance: {treatment_var}")
```

### Conclusion
As per the results of A/B tests, we recommend the company to keep the old page and eliminate the need for running the experiment longer, considering the current relatively long duration of 21 days. However, if we analyze the different aspects of time and evaluate their impact on the difference between the conversion rates of old and new pages, and if the influence exists, then it would be recommended to run the experiment longer to make their final decision.

### Advantages of Bayesian over Frequentist
- Results are more interpretable than the ones we got from the frequentist approach.
- We can interpret results at any point during the experiment. Don't need to wait for an arbitrary "statsig."

## Contributing

🎉 **Feel Free to Contribute!** 🎉

We welcome contributions from the community! Whether you want to report a bug, suggest an improvement, or add a new feature, your input is highly valued.

### How to Contribute

1. Fork the repository.
2. Create a new branch for your feature or bug fix (`git checkout -b feature/your-feature`).
3. Make your changes and commit them (`git commit -am 'Add your feature'`).
4. Push to the branch (`git push origin feature/your-feature`).
5. Open a Pull Request.

### What You Can Contribute

- Reporting bugs
- Discussing new features or improvements
- Writing or improving documentation
- Adding new tests or enhancing existing ones
- Providing feedback on the project

### Code of Conduct

Please note that this project adheres to the [Contributor Covenant Code of Conduct](CODE_OF_CONDUCT.md). By participating, you are expected to uphold this code.

Thank you for considering contributing to our project! 🚀

