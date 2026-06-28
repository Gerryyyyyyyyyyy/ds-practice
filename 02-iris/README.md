# Flower Image Classification

## Ziel

In diesem Projekt möchte ich ein Deep-Learning-Modell trainieren, das verschiedene Blumenarten anhand von Bildern klassifizieren kann.

Das Modell soll ein Bild einer Blume analysieren und vorhersagen, zu welcher der folgenden fünf Klassen es gehört:

* Daisy
* Dandelion
* Rose
* Sunflower
* Tulip

## Datensatz

Der Datensatz besteht aus Bildern von fünf verschiedenen Blumenarten.
Die Bilder sind in separaten Ordnern nach ihrer jeweiligen Klasse gespeichert:

* `daisy`
* `dandelion`
* `rose`
* `sunflower`
* `tulip`

Jedes Bild wird mit OpenCV geladen, auf eine einheitliche Größe von `100 x 100` Pixeln skaliert und anschließend als NumPy-Array gespeichert.

## Vorgehen

1. Notwendige Bibliotheken importieren
2. Bildordner einlesen
3. Anzahl der Bilder pro Blumenklasse ausgeben
4. Bilder laden und Labels zuweisen
5. Bilder auf `100 x 100` Pixel skalieren
6. Labels mit LabelEncoder in numerische Werte umwandeln
7. Labels mit One-Hot-Encoding vorbereiten
8. Pixelwerte normalisieren
9. Daten in Trainings- und Testdaten aufteilen
10. CNN-Modell erstellen
11. Modell trainieren
12. Training Loss und Accuracy visualisieren
13. Modell mit Testdaten bewerten
14. Classification Report erstellen
15. ROC- und AUC-Kurven darstellen
16. Ergebnis dokumentieren

## Verwendete Technologien

* Python
* NumPy
* pandas
* matplotlib
* seaborn
* OpenCV
* tqdm
* scikit-learn
* Keras
* TensorFlow
* Jupyter Notebook

## Datenvorbereitung

Zuerst wurden leere Listen für die Bilddaten und Labels erstellt.
Danach wurden die Bilddateien aus den jeweiligen Ordnern geladen.

Für jede Blumenklasse wurde eine Funktion verwendet, die jedem Bild das passende Label zuweist.
Die Bilder wurden mit OpenCV eingelesen und auf eine feste Größe von `100 x 100` Pixeln gebracht.

Die Bilddaten wurden anschließend in NumPy-Arrays umgewandelt.
Damit das neuronale Netz besser lernen kann, wurden die Pixelwerte normalisiert. Ursprünglich liegen Bildpixel im Bereich von `0` bis `255`. Durch die Division durch `255.0` wurden sie auf Werte zwischen `0` und `1` skaliert.

Die Labels wurden mit dem `LabelEncoder` in Zahlen umgewandelt.
Danach wurden sie mit `to_categorical` in One-Hot-Encoding umgewandelt, da das Modell fünf Klassen vorhersagen soll.

## Modell

Für die Klassifikation wurde ein Convolutional Neural Network, also ein CNN, verwendet.

Das Modell besteht aus mehreren Schichten:

* Conv2D-Layer zur Erkennung von Bildmerkmalen
* MaxPool2D-Layer zur Reduktion der Bildgröße
* Dropout-Layer zur Verringerung von Overfitting
* Flatten-Layer zur Umwandlung der Feature Maps in einen Vektor
* Dense-Layer zur Klassifikation
* Softmax-Ausgabeschicht für die fünf Blumenklassen

Die erste Convolution-Schicht verarbeitet Bilder mit der Form:

```python
(100, 100, 3)
```

Dabei steht `100 x 100` für die Bildgröße und `3` für die RGB-Farbkanäle.

Die letzte Schicht besitzt fünf Neuronen, da es fünf mögliche Blumenklassen gibt.
Als Aktivierungsfunktion in der Ausgabeschicht wurde `softmax` verwendet, damit das Modell Wahrscheinlichkeiten für jede Klasse ausgibt.

## Training

Das Modell wurde mit Trainingsdaten trainiert und mit Testdaten validiert.

Die Daten wurden mit `train_test_split` aufgeteilt:

* 80 % Trainingsdaten
* 20 % Testdaten

Das Modell wurde für 10 Epochen trainiert.

Als Loss-Funktion wurde `categorical_crossentropy` verwendet, da es sich um ein Mehrklassen-Klassifikationsproblem mit One-Hot-Encoded Labels handelt.

Als Optimizer wurde `Adam` verwendet.
Die Genauigkeit wurde mit `accuracy` gemessen.

## Evaluation

Nach dem Training wurde das Modell mit den Testdaten bewertet.

Dazu wurden folgende Methoden verwendet:

* Test Loss
* Test Accuracy
* Classification Report
* Precision
* Recall
* F1-Score
* ROC-Kurve
* AUC-Wert
* Micro-Average ROC-Kurve

Zusätzlich wurden Trainings- und Validierungswerte visualisiert:

* Training Loss
* Validation Loss
* Training Accuracy
* Validation Accuracy

Diese Diagramme helfen dabei zu erkennen, ob das Modell gut lernt oder ob Overfitting auftritt.

## Ergebnis

Das CNN-Modell erreicht auf dem Validierungs-/Testdatensatz eine Accuracy von ca. 67,7% und einen Loss von ca. 1,03. 
Auf den Trainingsdaten erreicht das Modell in der 10. Epoche eine Accuracy von ca. 80,8% und einen Loss von ca. 0,51.

Die Trainingskurven zeigen, dass der Trainingsverlust kontinuierlich sinkt. Gleichzeitig steigt die Validierungsgenauigkeit nur leicht und der Validierungsverlust stagniert ungefähr bei 1,02. 
Das deutet auf moderates Overfitting hin: Das Modell lernt die Trainingsdaten besser als die unbekannten Validierungsdaten.

Trotzdem liegt die Genauigkeit deutlich über zufälligem Raten. Da es fünf Blumenklassen gibt, würde zufälliges Raten ungefähr 20% Accuracy erreichen. Das Modell erkennt also bereits relevante Unterschiede zwischen den Blumenarten, hat aber noch Verbesserungspotenzial.

## Was ich gelernt habe

In diesem Projekt habe ich gelernt, wie man Bilddaten für ein Deep-Learning-Modell vorbereitet.

Ich habe verstanden, wie Bilder mit OpenCV geladen und auf eine einheitliche Größe gebracht werden. Außerdem habe ich gelernt, warum Pixelwerte normalisiert werden müssen, damit ein neuronales Netz stabiler und effizienter lernen kann.

Zusätzlich habe ich vertieft, wie Labels für ein Mehrklassenproblem vorbereitet werden. Mit dem LabelEncoder wurden die Klassennamen zuerst in Zahlen umgewandelt. Danach wurden sie mit One-Hot-Encoding in ein Format gebracht, das zur Softmax-Ausgabe und zur Loss-Funktion `categorical_crossentropy` passt.

Beim Modellaufbau habe ich gelernt, wie ein Convolutional Neural Network aufgebaut ist. Besonders wichtig waren dabei Conv2D-Schichten zur Merkmalsextraktion, MaxPooling-Schichten zur Reduktion der Datenmenge und Dropout-Schichten gegen Overfitting.

Außerdem habe ich gelernt, wie man ein Modell nicht nur mit Accuracy bewertet, sondern auch mit Precision, Recall, F1-Score, ROC-Kurven und AUC-Werten. Dadurch lässt sich die Leistung des Modells genauer beurteilen.

Insgesamt habe ich verstanden, wie aus rohen Bilddaten durch Datenvorbereitung, Label-Encoding, Modelltraining und Evaluation ein vollständiges Deep-Learning-Projekt zur Bildklassifikation entsteht.

