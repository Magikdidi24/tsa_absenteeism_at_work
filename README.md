# Absenteeism at work

Project for the Time Series Analysis course at EPITA, done with Maeva Ange Koumo. We used the UCI [Absenteeism at work](https://archive.ics.uci.edu/dataset/445/absenteeism+at+work) dataset: 740 absences recorded at a Brazilian courier company between July 2007 and July 2010.

The first question was whether the monthly hours of absence can be forecast. Summed by month it's only 37 points, and it behaves almost like white noise. ADF and KPSS both say it's stationary, so no differencing. We fit AR, MA and ARMA models on the first 28 months and tested on the last 9. The best was AR(2) with an RMSE of 96.3 hours, and just predicting the training mean already gives 98.5.

So we moved to explaining how long an absence lasts. Absences last 9.2 h on average on Monday and 4.4 h on Thursday (Kruskal-Wallis p = 0.030), and the share of absences over 8 h depends on the day too (chi-squared p = 0.021). Then we classified each absence as up to 4 h, 5 to 8 h, or more than 8 h. Logistic regression got the best macro-F1 in 5-fold CV, 0.61, where always predicting the majority class gives 0.26. The over 8 h class is the hard one: only 63 of the 737 absences left after dropping 3 rows with month 0, and an F1 of 0.35 on the test set.

## Files

- `main.ipynb`: the whole analysis (moving averages, additive, multiplicative and STL decomposition, stationarity tests, ACF/PACF, AR/MA/ARMA with Box-Jenkins residual checks, the day of week tests and the classification)
- `rapport.pdf`: the report
- `slides.pdf`: the slides for the presentation
- `oral.pdf`: our notes for the oral
- `figs/`: the plots used in the report and slides
- `note.txt`: working notes

Everything is in French. The .tex sources are next to the pdfs.

## Running the notebook

```sh
pip install ucimlrepo pandas matplotlib scipy statsmodels scikit-learn jupyter
jupyter notebook main.ipynb
```

The first cell downloads the data from UCI with `fetch_ucirepo(id=445)`.
