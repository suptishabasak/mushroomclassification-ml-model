# 🍄 Mushroom Classification: Edible or Poisonous?

## Project Overview
This project uses machine learning to classify mushrooms as **edible or poisonous** based on their physical characteristics. It compares two classification algorithms: Decision Tree and K-Nearest Neighbors (KNN).

> ⚠️ This is an educational machine learning project and must **not** be used to determine whether a real mushroom is safe to eat.

## Dataset
- **Dataset:** UCI Mushroom Dataset
- **Source:** [UCI Machine Learning Repository – Mushroom Dataset](https://archive.ics.uci.edu/dataset/73/mushroom)
- **Records:** 8,124 mushrooms (4,208 edible, 3,916 poisonous)
- **Features:** 22 categorical mushroom characteristics (117 columns after one-hot encoding)
- **Target:** `class` — edible (`e`) or poisonous (`p`)

## Technologies Used
- Python
- Jupyter Notebook
- Pandas and NumPy
- Matplotlib
- Scikit-learn

## Setup Instructions

1. Install Python and Jupyter Notebook.
2. Install the required libraries:

   ```bash
   pip install pandas numpy matplotlib scikit-learn notebook
   ```

3. Clone or download this repository.
4. Open `mushroom_classification.ipynb` in Jupyter Notebook.
5. Run all cells in order. The notebook downloads the dataset automatically if a local `mushrooms.csv` file is not available (an internet connection is needed in that case).

## Methodology
1. Load the dataset and inspect missing values. Missing values are written as `?`, so `isnull()` alone does not find them.
2. Replace unknown stalk-root values (`?`, 2,480 rows) with an `unknown` category.
3. Encode categorical features using one-hot encoding.
4. Split the dataset into training and testing sets using an 80:20 stratified split (6,499 train, 1,625 test, `random_state=42`).
5. Train and evaluate:
   - **Decision Tree:** maximum depth of 5.
   - **K-Nearest Neighbors:** 5 neighbors, with additional values of `k` compared.
6. Evaluate performance using accuracy, confusion matrices, precision, recall, and F1-score.

## Results
Both models were evaluated on the same 1,625 test mushrooms.

| Model | Test Accuracy | Poisonous Recall | Poisonous Mushrooms Missed |
|---|---|---|---|
| Decision Tree (max depth = 5) | 99.88% | 0.9974 | about 2 of 783 |
| KNN (k = 5) | 100.00% | 1.0000 | 0 of 783 |

Comparing values of `k` for KNN: `k` = 1, 3, 5, 7 and 9 all reached 100% accuracy, while `k` = 11 dropped slightly to 99.88%.

The most dangerous error is a poisonous mushroom classified as edible. The Decision Tree made about 2 of these errors and never labeled an edible mushroom as poisonous. KNN made none on this test set.

## Conclusion
Both models performed almost perfectly. KNN (k = 5) got every test mushroom right, and the Decision Tree was wrong on about 2 of 1,625. The Decision Tree is easier to explain, since you can see exactly which questions it asks, while KNN is slower at prediction time and depends on the choice of `k`.

These near-perfect scores mostly show that this dataset is easy: features such as `odor`, `spore-print-color` and `gill-size` separate the classes very clearly. High accuracy on this dataset does not establish that either model is safe for real-world mushroom identification.

## Project Files
- `mushroom_classification.ipynb` — data preparation, model training, evaluation, and conclusions.
- `README.md` — project overview, dataset information, setup instructions, and results.
