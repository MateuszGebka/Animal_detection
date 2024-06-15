# Klasyfikacja zdjęć zwierząt wykorzystując sieci konwolucyjne

Projekt służy pobraniu zestawu danych i nauczeniu konwolucyjnej sieci neuronowej rozpoznawania
zdjęć zwierząt.

## Struktura

 * projekt/
   * dane/ 
     * train/  - zestaw danych treningowych
     * test/  - zestaw danych testowych
     * val/  - zestaw danych walidacyjnych
   * mod.h5
   * notes.ipynb
   * Gradio.ipynb
 * README.md

 
## Przygotowanie danych

Dane muszą być uporządkowane w następujący sposób:

* dane/
   * train/  
     * klasa1/
     * klasa2/
     * klasa3/
     * ...
   * test/
     * klasa1/
     * klasa2/
     * klasa3/
     * ...
   * val/  
     * klasa1/
     * klasa2/
     * klasa3/
     * ...,

gdzie każdy folder ,,klasaX" nosi nazwę zwierzęcia, a wewnątrz znajdują
się jego zdjęcia.

## Trening

Do przygotowania danych, konstrukcji i 
trenowania oraz zapisywania modelu służy klasa ModelTrainer.

- prepare_data:
 
funkcja służy sztucznemu dodaniu danych poprzez przesuwanie,
przybliżanie, obracanie itd. zdjęć.

train i val generatory transportują dane do funkcji .fit()
w odpowiednich rozmiarach i ilości.

- build_model:

konstrukcja sieci konwolucyjnej oraz skompilowanie jej.

- train_model:

inicjujemy moduły wczesnego zatrzymywania oraz 
zmiejszania learning-rate modelu w odpowiednich przypadkach.

history - trening.

- save_model:

zapisanie modelu do pliku.


## Ocena

Do oceny modelu na zbiorze testowym użyjemy klasy ModelEvaluator.

Ładujemy model z pliku, przygotowujemy dane testowe by były takie
jak treningowe (rozmiar i ilość) i wykonujemy funkcję
evaluate, która zwraca accuracy i loss naszego modelu.

## Predykcja

Do klasyfikacji nowych zdjęć użyjemy funkcji ImagePredictor.

Ładujemy model z pliku, przygotowujemy nasze zdjęcie, by
pasowało do modelu, pobieramy nazwy klas i zwracamy
nazwę klasy z największym prawdopodobieństwem według funkcji
predict.

Do predykcji użyjemy przygotowanego już notebooku ,,Gradio",
który postawi prostą stronę web, na której możemy umieszczać
nasze zdjęcia i program pokaże najbardziej prawdopodobne
wyniki.

## Gotowy model

Plik ,,mod.h5" zawiera wyuczony już przeze mnie model,
którego można użyć do klasyfikacji nowych zdjęć.

