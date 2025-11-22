# Big Data Project — Analiza sentymentu i przetwarzanie tekstu (Databricks + Spark)

Projekt wykonany w środowisku **Databricks Community Edition** z użyciem **Apache Spark (PySpark)**.  
Celem było zbudowanie pipeline’u do przetwarzania tekstów w języku polskim, ekstrakcji cech (TF‑IDF), 
klastrowania dokumentów oraz wyznaczania emocji na podstawie słownika.

Repozytorium zawiera:
- `notebook/projekt_databricks.html` — eksport notebooka z Databricks z całym kodem i wynikami,
- `docs/index.html` — to samo co wyżej, ale w formie strony pod GitHub Pages,
- `data/slownik.xlsx` — słownik emocji używany w analizie,
- `README.md` — opis projektu,
- `requirements.txt` — lista najważniejszych bibliotek.

---

## 🔗 Podgląd projektu online (bez instalacji)

Możesz otworzyć cały projekt z wykresami w przeglądarce:

👉 **GitHub Pages:** `https://TWOJ-LOGIN.github.io/big_data_project/`

Po włączeniu Pages w ustawieniach repo link zacznie działać.  
Nie potrzebujesz Pythona ani Databricks — to zwykła strona HTML.

---

## 1. Problem / cel
1. Wczytanie i przygotowanie korpusu krótkich tekstów.
2. Tokenizacja i czyszczenie tekstu (stop‑words, normalizacja).
3. Budowa wektorów TF‑IDF.
4. Klastrowanie dokumentów metodą **K‑Means**.
5. Analiza emocji/sentymentu na podstawie słownika (`slownik.xlsx`).
6. Wizualizacja wyników.

---

## 2. Dane
- Teksty wejściowe są zdefiniowane w notebooku jako przykładowy zbiór zdań/opisów.
- Słownik emocji w pliku `data/slownik.xlsx` zawiera (m.in.) kolumny:
  - `word`
  - `mean Happiness`
  - `mean Anger`
  - `mean Sadness`
  - `mean Fear`
  - `mean Disgust`

Na etapie notebooka słownik jest ładowany do Sparka i rozgłaszany (broadcast).

---

## 3. Technologia
- **Databricks CE**
- **Apache Spark / PySpark**
- Spark MLlib:
  - `Tokenizer`
  - `StopWordsRemover`
  - `HashingTF`
  - `IDF`
  - `KMeans`
  - `ClusteringEvaluator`
- Dodatkowo:
  - `numpy`
  - `matplotlib`
  - (opcjonalnie) `pandas`

---

## 4. Pipeline (high‑level)
1. **SparkSession**  
2. **DataFrame** z tekstami
3. **Tokenizer** → lista słów
4. **StopWordsRemover** → czyszczenie
5. **HashingTF + IDF** → macierz TF‑IDF
6. **KMeans (k=5)** → przypisanie klastra
7. **Mapowanie emocji**
   - przypisanie wartości emocji ze słownika,
   - agregacja na poziomie tekstu.
8. **Ewaluacja + wizualizacje**  

---

## 5. Wyniki
W notebooku znajdują się:
- przypisania tekstów do klastrów,
- metryki jakości klastrowania (Silhouette),
- agregacje emocji,
- wykresy.

Szczegóły: `notebook/projekt_databricks.html` lub wersja online przez Pages.

---

## 6. Struktura repo
```
big_data_project/
├── notebook/
│   └── projekt_databricks.html
├── docs/
│   └── index.html
├── data/
│   └── slownik.xlsx
├── requirements.txt
└── README.md
```

---

## Autor
Projekt wykonany przez: **<TU WPISZ SWOJE IMIĘ I NAZWISKO>**
