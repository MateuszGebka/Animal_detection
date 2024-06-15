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
   * projekt.ipynb
   * Gradio.ipynb
 * README.md

## Środowisko

Program wykonany w Jupyter Notebook wraz z Anaconda Navigator,
gdzie w oknie dialogowym Anaconda Prompt instalowane były wszystkie 
paczki.

W pliku requirements.txt zawarte są wymagane biblioteki/
paczki do zainstalowania w Anaconda Prompt.

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

Przykład trenowania modelu:
![img.png](img.png)


## Ocena

Do oceny modelu na zbiorze testowym użyjemy klasy ModelEvaluator.

Ładujemy model z pliku, przygotowujemy dane testowe by były takie
jak treningowe (rozmiar i ilość) i wykonujemy funkcję
evaluate, która zwraca accuracy i loss naszego modelu.

Przykład oceny na zbiorze testowym
![img_2.png](img_2.png)

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

Przykład klasyfikacji nowego zdjęcia w Gradio:
![img_4.png](img_4.png)
![img_5.png](img_5.png)

Przykład klasyfikacji nowego zdjęcia w noteboku:
![img_3.png](img_3.png)

## Gotowy model

Plik ,,mod.h5" zawiera wyuczony już przeze mnie model,
którego można użyć do klasyfikacji nowych zdjęć.