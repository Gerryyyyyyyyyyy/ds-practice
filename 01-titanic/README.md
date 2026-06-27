# Titanic Survival Prediction

## Ziel

In diesem Projekt möchte ich vorhersagen, ob eine Person auf der Titanic überlebt hätte.

## Datensatz

Der Datensatz enthält Informationen wie:

- Alter
- Geschlecht
- Ticketklasse
- Anzahl Geschwister/Ehepartner
- Anzahl Eltern/Kinder
- Fahrpreis
- Überlebt oder nicht überlebt

## Vorgehen

1. Daten laden
2. Daten verstehen
3. Fehlende Werte behandeln
4. Daten visualisieren
5. Features vorbereiten
6. Modell trainieren
7. Modell bewerten
8. Ergebnis dokumentieren

## Verwendete Technologien

- Python
- pandas
- matplotlib
- seaborn
- scikit-learn
- Jupyter Notebook

## Ergebnis
In diesem Projekt wurde der Titanic-Datensatz Schritt für Schritt analysiert, bereinigt und für ein Machine-Learning-Modell vorbereitet.

Im ersten Notebook wurde zunächst eine explorative Datenanalyse durchgeführt. Dabei wurden fehlende Werte, Verteilungen und Zusammenhänge zwischen den Merkmalen untersucht. Besonders auffällig war, dass Geschlecht, Passagierklasse, Fahrpreis, Alter und Familiengröße einen erkennbaren Einfluss auf die Überlebenswahrscheinlichkeit hatten. Frauen, Kinder, Passagiere der ersten Klasse und Personen mit höheren Ticketpreisen hatten im Datensatz tendenziell bessere Überlebenschancen.

Im zweiten Notebook wurden die Daten bereinigt und neue Features erstellt. Die Spalte Cabin wurde entfernt, aber vorher wurde daraus das neue Merkmal HasCabin erstellt. Fehlende Werte bei Age wurden mit Medianwerten ersetzt, fehlende Werte bei Embarked mit dem häufigsten Wert gefüllt. Zusätzlich wurden neue Merkmale wie FamilySize, IsAlone, AgeGroup und FareBin erstellt. Kategoriale Variablen wurden anschließend in numerische Werte umgewandelt, damit sie für Machine Learning genutzt werden können. Der bereinigte Datensatz wurde danach als titanic_cleaned.csv gespeichert.

Im dritten Notebook wurden mehrere Machine-Learning-Modelle trainiert und verglichen. Dazu gehörten Logistic Regression, Decision Tree, Random Forest, K-Nearest Neighbors, Support Vector Machine, Gradient Boosting und Naive Bayes. Die Modelle wurden mit Accuracy, Precision, Recall, F1-Score, Confusion Matrices, ROC-Kurven und Cross-Validation bewertet.

Am besten schnitten vor allem Ensemble-Methoden wie Random Forest und Gradient Boosting ab. Das Random-Forest-Modell wurde zusätzlich mit GridSearchCV optimiert, um bessere Hyperparameter zu finden. Die wichtigsten Merkmale für das finale Modell waren unter anderem Geschlecht, Ticketpreis, Passagierklasse sowie selbst erstellte Features wie FamilySize, HasCabin und Title.

Das finale Modell kann auf Basis der vorbereiteten Passagierdaten vorhersagen, ob ein Passagier überlebt hätte oder nicht. Die genaue Modellleistung ist im Modellvergleich des dritten Notebooks dargestellt.

## Was ich gelernt habe

In diesem Projekt habe ich meine grundlegenden Basis Informationen vertiefen können.

Ich habe vertieft, wie wichtig die explorative Datenanalyse ist, um Muster und Zusammenhänge im Datensatz zu erkennen. Beim Titanic-Datensatz wurde deutlich, dass bestimmte Merkmale wie Geschlecht, Klasse, Alter, Fahrpreis und Familiengröße stark mit der Überlebenswahrscheinlichkeit zusammenhängen.

Außerdem habe ich vertieft, wie man mit fehlenden Werten umgeht und warum Feature Engineering eine wichtige Rolle spielt. Durch neue Merkmale wie HasCabin, FamilySize, IsAlone, AgeGroup und FareBin konnten zusätzliche Informationen aus den vorhandenen Daten gewonnen werden.

Beim Modelltraining habe ich verstanden, dass verschiedene Modelle unterschiedlich mit Daten umgehen. Einige Modelle wie Logistic Regression, KNN und SVM benötigen skalierte Daten, während baumbasierte Modelle wie Decision Tree, Random Forest und Gradient Boosting auch ohne Skalierung gut funktionieren.

Zusätzlich habe ich gelernt, dass Accuracy allein nicht ausreicht, um ein Modell sinnvoll zu bewerten. Precision, Recall, F1-Score, Confusion Matrices, ROC-Kurven und Cross-Validation helfen dabei, die Leistung eines Modells besser einzuschätzen.

Besonders hilfreich war das Hyperparameter-Tuning mit GridSearchCV. Dadurch habe ich gesehen, wie ein Modell gezielt verbessert werden kann, anstatt nur die Standardeinstellungen zu verwenden.

Insgesamt habe ich vertieft/gelernt, wie aus Rohdaten durch Analyse, Bereinigung, Feature Engineering und Modellvergleich ein vollständiges Machine-Learning-Projekt entsteht.