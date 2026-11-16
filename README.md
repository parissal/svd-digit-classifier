# Handwritten Digit Classification with the SVD

Classifying handwritten digits from the US Postal Service dataset with one SVD basis per digit class. Each test digit is projected onto the first *k* left singular vectors of every class and assigned to the class with the smallest relative residual. No training beyond ten SVDs is needed.

## What's inside

`svd_digit_classifier.ipynb` covers:

- **Choosing k:** test accuracy for k = 1 to 20 basis vectors
- **Per-class difficulty:** which digits are hardest, with examples of misclassified digits
- **Per-class k:** using a different number of basis vectors for each class, based on its singular values
- **Two-stage algorithm:** classifying with a single singular vector first, and running the full algorithm only when that is inconclusive

## Key results

- Accuracy rises from 80.2% with k = 1 to **94.2% with k = 18** (2007 test digits).
- The easiest digits are 0 (98.9%) and 1 (98.1%). The hardest are 5 (88.1%), 2 (89.9%) and 3 (90.4%).
- Choosing k per class by a 90%-energy rule gives 90.9%, lower than a single k = 18 for all classes.
- The two-stage algorithm keeps the full 94.2% accuracy up to θ = 0.75 while skipping the full computation for about 28% of the digits. At θ = 0.9 it skips it for 61%, at 93.0% accuracy.

## Running it

```bash
pip install -r requirements.txt
jupyter notebook svd_digit_classifier.ipynb
```

The data is not included in this repository. Download `azip.mat`, `dzip.mat`, `testzip.mat` and `dtest.mat` from [Lars Eldén's course page](https://users.mai.liu.se/larel04/matrix-methods/computer-assignments/character-recogn.html) and put them in the same folder as the notebook. They are a subset of the USPS digit database (1707 training and 2007 test images, 16×16 pixels).

## About this project

This was originally written as an assignment for a course at the Athens University of Economics and Business (AUEB), based on the digit classification assignment from Lars Eldén's *Matrix Methods in Data Mining and Pattern Recognition*. The original explanations and comments were written in Greek. The English version here was translated with the help of an AI tool and then reviewed by me. The code, experiments and analysis are my own.
