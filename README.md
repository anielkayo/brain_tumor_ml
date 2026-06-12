# Klasyfikacja guzów mózgu na podstawie obrazów MRI

## Opis projektu

Celem projektu było stworzenie modelu klasyfikującego obrazy MRI mózgu do jednej z dwóch klas:

- tumor - obecność guza
- no_tumor - brak guza

W projekcie porównano kilka klasycznych algorytmów uczenia maszynowego oraz zbadano wpływ ekstrakcji cech HOG na skuteczność klasyfikacji.

## Dataset
Brain Tumor MRI Dataset, Kaggle, Masoud Nickparvar

## Cele projektu

- przygotowanie danych
- ekstrakcja cech HOG
- porównanie modeli klasyfikacyjnych
- porównanie HOG i surowych pikseli
- strojenie hiperparametrów
- ocena końcowa na zbiorze testowym

## Hipotezy

H1: Zastosowanie cech HOG poprawia skuteczność klasyfikacji względem surowych pikseli.

H2: Modele liniowe (Logistic Regression i Linear SVM) dobrze radzą sobie z klasyfikacją obrazów MRI po zastosowaniu HOG.


## Przygotowanie danych

Każdy obraz został:

- przekonwertowany do skali szarości,
- przeskalowany do stałego rozmiaru,
- znormalizowany,
- zamieniony na wektor cech.

## Ekstrakcja cech

### HOG

Histogram of Oriented Gradients (HOG) opisuje obraz za pomocą informacji o krawędziach, konturach i zmianach jasności.

Schemat:

Obraz MRI
-> preprocessing
-> HOG
-> wektor cech
-> model klasyfikacyjny

### Surowe piksele

Dla porównania wykorzystano również bezpośrednie wartości pikseli bez ekstrakcji cech.

## Standaryzacja

W modelach liniowych zastosowano StandardScaler, który sprowadza cechy do podobnej skali i poprawia działanie modeli Logistic Regression oraz SVM.

## Modele

- Dummy Classifier
- Logistic Regression
- Linear SVM
- RBF SVM
- Random Forest

## Strojenie hiperparametrów

Do optymalizacji parametrów wykorzystano GridSearchCV.

Linear SVM:
- C = [0.01, 0.1, 1.0, 10.0]

RBF SVM:
- C = [0.1, 1.0, 10.0]
- gamma = ["scale", 0.001, 0.01, 0.1]

Metryka optymalizacji:
- recall

## Wyniki

Logistic Regression + HOG:
- Accuracy: 98.21%

Linear SVM + HOG:
- Accuracy: 97.50%

RBF SVM + HOG:
- Accuracy: 97.68%

Random Forest + HOG:
- Accuracy: 96.52%

Logistic Regression + raw pixels:
- Accuracy: 96.07%

## Wnioski

1. Najlepsze wyniki uzyskał model Logistic Regression wykorzystujący cechy HOG.

2. HOG poprawił skuteczność klasyfikacji względem wykorzystania surowych pikseli.

3. Recall dla klasy tumor osiągnął bardzo wysoką wartość, co oznacza skuteczne wykrywanie przypadków guza.

4. Modele liniowe okazały się wystarczające do rozwiązania badanego problemu.

5. Klasyczne metody uczenia maszynowego w połączeniu z HOG pozwalają skutecznie klasyfikować obrazy MRI mózgu.

## Technologie

- Python
- NumPy
- Pandas
- Matplotlib
- OpenCV
- Scikit-learn
- Jupyter Notebook