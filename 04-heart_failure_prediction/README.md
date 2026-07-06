# Heart Failure Prediction

## Ziel

In diesem Projekt möchte ich vorhersagen, ob bei einem Patienten mit Herzinsuffizienz ein `DEATH_EVENT` auftritt.

Dafür werden mehrere Machine-Learning-Modelle trainiert und miteinander verglichen. Neben der reinen Accuracy werden auch Precision, Recall, F1-Score, ROC AUC und Average Precision betrachtet.

Zusätzlich wird mit Cross Validation untersucht, wie stabil die Modelle auf unbekannten Daten funktionieren.

## Datensatz

Verwendet wird der Datensatz:

`heart_failure_clinical_records_dataset.csv.xls`

Der Datensatz enthält klinische Informationen von Patienten mit Herzinsuffizienz.

Die Zielvariable ist `DEATH_EVENT`.

Dabei gilt:

* `0 = kein Death Event`
* `1 = Death Event`

## Spaltenbeschreibung

| Spalte                     | Beschreibung                                              |
| -------------------------- | --------------------------------------------------------- |
| `age`                      | Alter des Patienten                                       |
| `anaemia`                  | Gibt an, ob eine Anämie vorliegt                          |
| `creatinine_phosphokinase` | CPK-Enzymwert im Blut                                     |
| `diabetes`                 | Gibt an, ob Diabetes vorliegt                             |
| `ejection_fraction`        | Anteil des ausgeworfenen Blutes bei einer Herzkontraktion |
| `high_blood_pressure`      | Gibt an, ob Bluthochdruck vorliegt                        |
| `platelets`                | Anzahl der Blutplättchen                                  |
| `serum_creatinine`         | Kreatininwert im Blut                                     |
| `serum_sodium`             | Natriumwert im Blut                                       |
| `sex`                      | Geschlecht des Patienten                                  |
| `smoking`                  | Gibt an, ob der Patient raucht                            |
| `time`                     | Dauer des Follow-ups                                      |
| `DEATH_EVENT`              | Zielvariable                                              |

## Vorgehen

1. Daten laden und verstehen
2. Fehlende Werte überprüfen
3. Zielvariable analysieren
4. Korrelationsmatrix erstellen
5. Potenzielle Ausreißer untersuchen
6. Trainings- und Testdaten aufteilen
7. Feature Scaling mit einer Pipeline durchführen
8. Stratified 5-Fold Cross Validation anwenden
9. Mehrere Modelle trainieren und vergleichen
10. Generalization Gap analysieren
11. Bestes Modell auswählen
12. Finales Modell auf den Testdaten bewerten
13. Confusion Matrix analysieren
14. ROC- und Precision-Recall-Kurve untersuchen

## Verwendete Modelle

Im Projekt werden vier Modelle miteinander verglichen:

* Support Vector Machine
* K-Nearest Neighbors
* Logistic Regression
* XGBoost

Alle Modelle werden mit denselben Cross-Validation-Folds bewertet.

Dadurch können die Ergebnisse besser miteinander verglichen werden.

## Cross Validation

Für die Modellbewertung wird eine Stratified 5-Fold Cross Validation verwendet.

Der Trainingsdatensatz wird dabei in fünf Teile aufgeteilt. Jeder Teil wird einmal als Validation-Datensatz verwendet.

Durch die stratifizierte Aufteilung bleibt die Klassenverteilung möglichst ähnlich.

Für jedes Modell werden unter anderem folgende Metriken berechnet:

* Accuracy
* Precision
* Recall
* F1-Score
* ROC AUC
* Average Precision

Zusätzlich werden Training-F1 und Validation-F1 miteinander verglichen.

## Generalization Gap

Der Generalization Gap beschreibt den Unterschied zwischen Training-F1 und Validation-F1.

Die Ergebnisse waren:

| Modell                 | Train F1 | Validation F1 | F1 Gap |
| ---------------------- | -------: | ------------: | -----: |
| XGBoost                |    0.983 |         0.728 |  0.256 |
| Logistic Regression    |    0.748 |         0.707 |  0.041 |
| Support Vector Machine |    0.760 |         0.681 |  0.079 |
| K-Nearest Neighbors    |    0.705 |         0.491 |  0.214 |

Die Logistic Regression zeigt mit einem F1 Gap von `0.041` die stabilste Generalisierung.

XGBoost erreicht zwar den höchsten Validation-F1, zeigt mit einem F1 Gap von `0.256` jedoch deutliche Anzeichen von Overfitting.

KNN zeigt ebenfalls einen großen Unterschied zwischen Training und Validation.

## Ergebnis

Anhand des höchsten durchschnittlichen Validation-F1 wurde XGBoost als bestes Modell der Cross Validation ausgewählt.

XGBoost erreichte:

* Validation F1: `0.728`
* Validation F1 Standard Deviation: `0.066`

Auf dem finalen Testdatensatz wurden folgende Ergebnisse erreicht:

| Metrik            | Ergebnis |
| ----------------- | -------: |
| Accuracy          |  81.67 % |
| Precision         |  68.18 % |
| Recall            |  78.95 % |
| F1-Score          |  73.17 % |
| ROC AUC           |    0.896 |
| Average Precision |    0.816 |

Die Confusion Matrix zeigt, dass das Modell `15 von 19` tatsächlichen Death Events korrekt erkennt.

Vier Death Events werden nicht erkannt und sieben negative Fälle werden fälschlicherweise als Death Event klassifiziert.

## Vergleich mit Logistic Regression

Die Logistic Regression erreichte auf dem Testdatensatz:

| Metrik            | Ergebnis |
| ----------------- | -------: |
| Accuracy          |  83.33 % |
| Precision         |  71.43 % |
| Recall            |  78.95 % |
| F1-Score          |  75.00 % |
| ROC AUC           |    0.865 |
| Average Precision |    0.760 |

Obwohl XGBoost den höheren Validation-F1 sowie eine höhere ROC AUC und Average Precision erreicht, zeigt die Logistic Regression eine deutlich stabilere Generalisierung.

Die Logistic Regression erreicht außerdem einen höheren Test-F1 und einen wesentlich kleineren Generalization Gap.

Dadurch zeigt sich, dass das Modell mit dem höchsten Cross-Validation-Score nicht automatisch in allen Bereichen das beste Modell sein muss.

## Verwendete Technologien

* Python
* pandas
* numpy
* matplotlib
* seaborn
* scikit-learn
* XGBoost
* Jupyter Notebook

## Was ich gelernt habe

In diesem Projekt habe ich gelernt, wie mehrere Machine-Learning-Modelle systematisch miteinander verglichen werden können.

Besonders wichtig waren dabei folgende Punkte:

* wie klinische Daten analysiert und visualisiert werden
* warum Trainings- und Testdaten vor dem Scaling getrennt werden sollten
* wie Pipelines Data Leakage verhindern können
* wie Stratified Cross Validation funktioniert
* warum ein einzelner Train-Test-Split nicht immer ausreicht
* wie Accuracy, Precision, Recall und F1-Score interpretiert werden
* wie ROC AUC und Average Precision bewertet werden
* wie eine Confusion Matrix interpretiert wird
* wie Overfitting anhand des Generalization Gaps erkannt werden kann
* warum ein hoher Trainingsscore nicht automatisch ein gutes Modell bedeutet
* warum einfachere Modelle teilweise stabiler generalisieren
* wie Classification Thresholds Precision und Recall beeinflussen
* warum Modellstabilität bei kleinen Datensätzen besonders wichtig ist

Durch das Projekt habe ich ein besseres Verständnis dafür bekommen, wie Machine-Learning-Modelle bewertet und miteinander verglichen werden.

Besonders wichtig war die Erkenntnis, dass nicht nur der höchste Score betrachtet werden sollte. Auch Generalisierung, Stabilität und Overfitting spielen eine wichtige Rolle bei der Auswahl eines Modells.
