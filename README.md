# AQI-PDF-Estimation-Model
# Learn Probability Density Functions using Roll-Number-Parameterized Non-Linear Model

## 📌 Project Overview
This assignment focuses on estimating the parameters of a specific Probability Density Function (PDF) using **NO₂ air quality data**. The raw data is first transformed using a non-linear equation parameterized by my University Roll Number, and then fitted to a Gaussian distribution model.

* **Student Roll Number:** 102303183

---

## 📂 Dataset
The dataset used is the **India Air Quality Data**, specifically focusing on the `NO2` (Nitrogen Dioxide) concentration values.

* **Source:** [Kaggle - India Air Quality Data](https://www.kaggle.com/datasets/shrutibhargava94/india-air-quality-data)
* **Feature Selected:** `no2` column
* **Preprocessing:** Rows with missing values were removed, and data was converted to numeric format to ensure valid input for transformation.

---

## ⚙️ Methodology

### 1. Non-Linear Transformation
Each valid NO₂ reading ($x$) was transformed into a new variable ($z$) using the following roll-number-based equation:

$$z = x + a_r \sin(b_r x)$$

Where the constants $a_r$ and $b_r$ are derived from my roll number (**102303183**) as follows:

| Constant | Formula | Calculation | Final Value |
| :--- | :--- | :--- | :--- |
| **$a_r$** | $0.05 \times (r \pmod 7)$ | $0.05 \times (102303183 \pmod 7)$ | **0.1** |
| **$b_r$** | $0.3 \times ((r \pmod 5) + 1)$ | $0.3 \times (3 + 1)$ | **1.2** |

### 2. Parameter Estimation
The transformed data ($z$) was modeled using the target Probability Density Function:

$$\hat{p}(z) = c \cdot e^{-\lambda(z-\mu)^{2}}$$

Using `scipy.optimize.curve_fit`, the parameters were estimated to minimize the residual sum of squares between the histogram density and the model.

---

## 📊 Results
The final estimated parameters for the assignment are:

| Parameter | Symbol | Estimated Value |
| :--- | :---: | :--- |
| **Mean** | $\mu$ | [CODE SE AAYI MU VALUE] |
| **Lambda** | $\lambda$ | [CODE SE AAYI LAMBDA VALUE] |
| **Constant** | $c$ | [CODE SE AAYI C VALUE] |

### Visualization
The graph below shows the histogram of the transformed data ($z$) overlaid with the predicted Probability Density Function curve.

![Probability Density Function Fit](Result.png)


---

## 🚀 How to Run
1. **Prepare Data:** Ensure `data.csv` is in the same directory as the script.
2. **Install dependencies:**
   ```bash
   pip install pandas numpy scipy matplotlib
