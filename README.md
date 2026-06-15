# Analiza Danych Ubezpieczeniowych & Dashboard BI

## Opis projektu
Projekt analityczny obejmujący pełen cykl życia danych: od ekstrakcji i transformacji (ETL), przez budowę wielowymiarowej kostki OLAP, aż po wizualizację kluczowych wskaźników efektywności (KPI) w Power BI. Celem było stworzenie narzędzia wspierającego decyzje menedżerskie dotyczące rentowności polis.

## Technologie i narzędzia
* Wizualizacja: Power BI, DAX
* Hurtownie danych: Architektura OLAP, procesy ETL, Power Query
* Język zapytań: SQL

## Architektura i proces
* Czyszczenie danych (ETL): Pobranie surowych danych i przygotowanie ich do analizy.
* Modelowanie OLAP: Zaprojektowanie struktury wymiarów i miar kluczowych dla biznesu.
* Wizualizacja: Utworzenie interaktywnego dashboardu dla kadry zarządzającej.

## Podgląd Dashboardu

### 1. Wpływ demografii i historii medycznej na koszty ubezpieczenia
Zestawienie pokazujące korelację wieku z rosnącymi kosztami oraz rozkład opłat w zależności od przebytych chorób i regionu zamieszkania.

<img width="1152" height="647" alt="Zrzut ekranu 2026-05-19 130518" src="https://github.com/user-attachments/assets/bfe1d928-64fe-4a1c-9dd6-cf0e544ceb33" />

### 2. Zależność kosztów leczenia od BMI i nałogu tytoniowego
Szczegółowa analiza (wykres punktowy) udowadniająca drastyczny wzrost kosztów leczenia u osób palących, połączona ze szczegółową macierzą kosztów dla poszczególnych zawodów.

<img width="1154" height="647" alt="Zrzut ekranu 2026-05-19 123906" src="https://github.com/user-attachments/assets/ef00da80-25e4-44e8-97a8-05015ae4b766" />

### 3. Główne wskaźniki KPI i rozkład regionalny
Widok podsumowujący z najważniejszymi metrykami biznesowymi (całkowita liczba pacjentów, średni koszt leczenia), mapą drzewa dla regionów oraz wpływem chorób współistniejących na wysokość opłat.

<img width="1150" height="649" alt="Zrzut ekranu 2026-05-19 122527" src="https://github.com/user-attachments/assets/369c7222-e89f-46a0-a628-3d1962fa9c79" />


## Architektura Danych i Proces ETL (SSIS)

Projekt to nie tylko wizualizacja, ale pełen proces zasilania hurtowni danych, zrealizowany przy pomocy narzędzi klasy Enterprise.

### 1. Modelowanie Danych (Schemat Gwiazdy)
Zaprojektowałam strukturę hurtowni danych w klasycznym modelu gwiazdy. Centralną osią jest tabela faktów (`Fact_Insurance`), otoczona tabelami wymiarów (m.in. `Dim_Patient`, `Dim_Medical`, `Dim_Coverage`), co zapewnia optymalizację pod kątem zapytań analitycznych.

<img width="509" height="440" alt="Zrzut ekranu 2026-05-05 141004" src="https://github.com/user-attachments/assets/1b1388cc-837d-4c30-bd12-62de3f3cae0b" />

### 2. Architektura procesu ETL (Control Flow)
Zbudowałam zautomatyzowany rurociąg danych (pipeline). Zachowałam rygorystyczną kolejność ładowania (najpierw wymiary, na końcu tabela faktów), z obsługą błędów i weryfikacją wykonania zadań.

<img width="856" height="260" alt="Zrzut ekranu 2026-04-29 141652" src="https://github.com/user-attachments/assets/c04ea484-c470-4af9-a476-59d39b4a1b86" />


### 3. Transformacja i zasilanie milionami rekordów (Data Flow)
Proces zasilania tabeli faktów sprawnie przetwarza zbiory rzędu 1 000 000 rekordów. Wykorzystałam m.in. transformacje typu `Lookup` do poprawnego mapowania kluczy biznesowych na klucze zastępcze (Surrogate Keys) w hurtowni.

<img width="568" height="468" alt="Zrzut ekranu 2026-05-04 230212" src="https://github.com/user-attachments/assets/294b3039-f255-4823-8255-a7de56bca83b" />


---

## Zaawansowana Analityka i Data Mining

Projekt został rozszerzony o wykorzystanie algorytmów uczenia maszynowego do przewidywania kosztów leczenia. 

### Porównanie modeli predykcyjnych
Zestawienie predykcji stworzonych za pomocą Drzew Decyzyjnych, Klastrowania oraz Sieci Neuronowych z rzeczywistymi kosztami, w podziale na wiek pacjenta.

<img width="1154" height="650" alt="Zrzut ekranu 2026-05-19 133022" src="https://github.com/user-attachments/assets/2e64a243-750e-4f76-89f5-36cb83b528b5" />






