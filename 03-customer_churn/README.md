# Customer Churn Prediction

## Ziel

In diesem Projekt möchte ich vorhersagen, ob Kunden einer Marketing-Agentur abwandern werden, also ob sie den Service nicht mehr weiter nutzen.

Dafür wird eine logistische Regression verwendet, die von Grund auf selbst implementiert wurde. Das Modell soll anschließend das Churn-Risiko für neue Kunden vorhersagen.

## Datensatz

Es werden zwei CSV-Dateien verwendet:

### customer_churn.csv

Dieser Datensatz enthält historische Kundendaten mit bekannten Churn-Werten.

Enthaltene Informationen sind unter anderem:

## Spaltenbeschreibung

| Spalte            | Beschreibung                                                           |
| ----------------- | ---------------------------------------------------------------------- |
| `Name`            | Name des letzten Kontakts beim Unternehmen                             |
| `Age`             | Alter des Kunden                                                       |
| `Total_Purchase`  | Gesamtanzahl der gekauften Werbeanzeigen                               |
| `Account_Manager` | Gibt an, ob ein Account Manager zugewiesen wurde: `0 = Nein`, `1 = Ja` |
| `Years`           | Anzahl der Jahre, die der Kunde bereits Kunde ist                      |
| `Num_Sites`       | Anzahl der Webseiten, die den Service nutzen                           |
| `Onboard_date`    | Datum, an dem der letzte Kontakt onboarded wurde                       |
| `Location`        | Adresse des Hauptsitzes des Kunden                                     |
| `Company`         | Name des Kundenunternehmens                                            |

### new_customers.csv

Dieser Datensatz enthält neue Kundendaten ohne Churn-Label.

Das trainierte Modell wird verwendet, um für diese neuen Kunden vorherzusagen, ob ein erhöhtes Risiko für Churn besteht.

## Vorgehen

1. Daten laden
2. Daten verstehen
3. Relevante Features auswählen
4. Daten bereinigen und vorbereiten
5. Daten visualisieren
6. Trainings- und Testdaten aufteilen
7. Features skalieren
8. Sigmoid-Funktion selbst implementieren
9. Kostenfunktion selbst implementieren
10. Gradient Descent selbst implementieren
11. Logistische Regression trainieren
12. Modell bewerten
13. Churn-Risiko für neue Kunden vorhersagen
14. Ergebnisse dokumentieren

## Modell

Für die Vorhersage wird eine logistische Regression verwendet.

Die wichtigsten Bestandteile wurden manuell implementiert:

* Sigmoid-Funktion
* Kostenfunktion
* Gradient Descent
* Training der Modellparameter
* Vorhersagefunktion

Dadurch soll besser verstanden werden, wie logistische Regression intern funktioniert.

## Verwendete Technologien

* Python
* pandas
* numpy
* matplotlib
* seaborn
* scikit-learn

  * train_test_split
  * StandardScaler
* Jupyter Notebook
* Eigene Implementierung der logistischen Regression

## Ergebnis

Das Modell erreicht auf den Testdaten eine Accuracy von **88.88 %**.  
Das bedeutet, dass ungefähr **89 von 100 Kunden** korrekt als `Churn` oder `kein Churn` vorhergesagt wurden.

## Was ich gelernt habe

In diesem Projekt habe ich gelernt, wie logistische Regression grundsätzlich funktioniert und wie man sie ohne fertiges Modell aus `scikit-learn` selbst implementieren kann.

Besonders wichtig waren dabei folgende Punkte:

* wie man Daten mit `pandas` lädt und vorbereitet
* warum nicht-numerische Spalten vor dem Training entfernt werden müssen
* wie man Daten in Trainings- und Testdaten aufteilt
* warum Feature Scaling wichtig ist
* wie die Sigmoid-Funktion Wahrscheinlichkeiten zwischen 0 und 1 berechnet
* wie eine Kostenfunktion den Fehler des Modells misst
* wie Gradient Descent die Modellparameter Schritt für Schritt verbessert
* warum eine Intercept-Spalte für den Bias-Term benötigt wird
* wie Wahrscheinlichkeiten mit einem Schwellenwert von 0.5 in Klassen umgewandelt werden
* wie man die Accuracy eines Modells berechnet
* wie ein trainiertes Modell auf neue Kundendaten angewendet werden kann

Durch das Projekt habe ich ein besseres Verständnis dafür bekommen, was bei einer logistischen Regression intern passiert.


