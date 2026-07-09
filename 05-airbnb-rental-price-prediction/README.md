# Airbnb Rental Price Prediction

## Ziel

In diesem Projekt möchte ich den Preis einer Airbnb-Unterkunft anhand verschiedener Merkmale vorhersagen.

Dafür werden zwei Varianten einer linearen Regression verwendet und miteinander verglichen.

Das beste Modell wird anschließend auf bisher unbekannten Testdaten bewertet.

## Datensatz

Verwendet wird der Datensatz:

`airbnb_rental_data.csv`

Der Datensatz enthält Informationen über Airbnb-Unterkünfte, deren Lage, Unterkunftsart, Bewertungen und Verfügbarkeit.

Die Zielvariable ist `price`.

## Spaltenbeschreibung

| Spalte                           | Beschreibung                            |
| -------------------------------- | --------------------------------------- |
| `neighbourhood_group`            | Übergeordnete geografische Region       |
| `neighbourhood`                  | Stadtteil der Unterkunft                |
| `latitude`                       | Breitengrad                             |
| `longitude`                      | Längengrad                              |
| `room_type`                      | Art der Unterkunft                      |
| `price`                          | Preis der Unterkunft                    |
| `minimum_nights`                 | Mindestanzahl an Übernachtungen         |
| `number_of_reviews`              | Anzahl der Bewertungen                  |
| `reviews_per_month`              | Durchschnittliche Bewertungen pro Monat |
| `calculated_host_listings_count` | Anzahl der Unterkünfte des Hosts        |
| `availability_365`               | Verfügbarkeit innerhalb eines Jahres    |

## Vorgehen

1. Daten laden und verstehen
2. Fehlende Werte und Duplikate überprüfen
3. Nicht benötigte Spalten entfernen
4. Preisverteilung analysieren
5. Potenzielle Ausreißer untersuchen
6. Daten visualisieren
7. Trainings-, Validation- und Testdaten erstellen
8. Numerische Features skalieren
9. Kategorische Features mit One-Hot-Encoding umwandeln
10. Standard Linear Regression trainieren
11. Log-Transformed Linear Regression trainieren
12. Modelle auf den Validation-Daten vergleichen
13. Bestes Modell auswählen
14. Finales Modell auf den Testdaten bewerten
15. Vorhersagen und Residuen analysieren

## Modell

Für die Preisvorhersage werden zwei Modelle miteinander verglichen:

* Standard Linear Regression
* Linear Regression mit logarithmischer Target-Transformation

Die Datenvorverarbeitung wird mit Pipelines durchgeführt.

Numerische Features werden mit dem `StandardScaler` skaliert.

Kategorische Features werden mit dem `OneHotEncoder` in numerische Werte umgewandelt.

Die Modelle werden anhand des Validation-RMSE miteinander verglichen.

## Verwendete Technologien

* Python
* pandas
* numpy
* matplotlib
* scikit-learn

  * train_test_split
  * StandardScaler
  * OneHotEncoder
  * SimpleImputer
  * ColumnTransformer
  * Pipeline
  * LinearRegression
  * TransformedTargetRegressor
* Jupyter Notebook

## Ergebnis

Die Standard Linear Regression wurde als bestes Modell ausgewählt.

Auf den Testdaten wurden folgende Ergebnisse erreicht:

| Metrik | Ergebnis |
| ------ | -------: |
| MAE    |    68.71 |
| MSE    | 26312.83 |
| RMSE   |   162.21 |
| R²     |   0.1660 |

Der durchschnittliche absolute Vorhersagefehler beträgt ungefähr **68.71 Preiseinheiten**.

Das R² von **0.1660** zeigt, dass das Modell ungefähr **16.6 % der Variation der Airbnb-Preise erklären kann**.

Der deutlich höhere RMSE zeigt außerdem, dass bei einigen Unterkünften sehr große Vorhersagefehler auftreten.

## Was ich gelernt habe

In diesem Projekt habe ich gelernt, wie ein Regressionsproblem mit Machine Learning umgesetzt und bewertet werden kann.

Besonders wichtig waren dabei folgende Punkte:

* wie man einen Datensatz analysiert und vorbereitet
* wie fehlende Werte und Duplikate behandelt werden
* wie potenzielle Ausreißer mit der IQR-Methode untersucht werden
* warum statistische Ausreißer nicht automatisch entfernt werden sollten
* wie numerische und kategorische Features unterschiedlich verarbeitet werden
* wie One-Hot-Encoding funktioniert
* wie Pipelines eine konsistente Datenvorverarbeitung ermöglichen
* warum Trainings-, Validation- und Testdaten getrennt werden
* wie MAE, MSE, RMSE und R² interpretiert werden
* warum R² keine Accuracy ist
* wie eine logarithmische Target-Transformation funktioniert
* wie mehrere Regressionsmodelle miteinander verglichen werden
* wie Residuen und Vorhersagefehler analysiert werden

Durch das Projekt habe ich ein besseres Verständnis dafür bekommen, wie Regressionsmodelle trainiert und bewertet werden.

Besonders wichtig war die Erkenntnis, dass ein funktionierendes Modell nicht automatisch eine hohe Vorhersageleistung erreicht und dass auch die Modellannahmen und die Struktur der Daten berücksichtigt werden müssen.
