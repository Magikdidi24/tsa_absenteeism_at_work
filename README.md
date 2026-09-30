# Absentéisme au travail — analyse de séries temporelles

Projet de Time Series Analysis (EPITA) sur le dataset UCI
[Absenteeism at work](https://archive.ics.uci.edu/dataset/445/absenteeism+at+work) :
740 absences enregistrées chez un transporteur brésilien entre juillet 2007 et juillet 2010.

Deux questions :
1. peut-on **prévoir** le volume mensuel d'heures d'absence ?
2. peut-on **expliquer / classer** la durée d'une absence à partir de ses caractéristiques ?

La série s'avère proche d'un bruit blanc (prévision peu utile), d'où un pivot vers une approche
explicative : effet du jour de la semaine, puis classification de la durée en trois classes.

## Contenu

| Fichier | Contenu |
|---|---|
| `main.ipynb` | Notebook complet : moyennes mobiles, décomposition (additive, multiplicative, STL), stationnarité, ACF/PACF, AR/MA/ARMA + diagnostic Box-Jenkins, classification |
| `rapport.tex` / `rapport.pdf` | Rapport |
| `slides.tex` / `slides.pdf` | Slides de soutenance |
| `oral.tex` / `oral.pdf` | Support de l'oral |
| `figs/` | Figures générées par le notebook |
| `note.txt` | Notes d'analyse |

## Lancer

```sh
pip install ucimlrepo pandas matplotlib scipy statsmodels scikit-learn
jupyter notebook main.ipynb
```

Les données sont téléchargées directement depuis UCI (`fetch_ucirepo(id=445)`).
