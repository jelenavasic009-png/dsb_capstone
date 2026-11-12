# 🚢 Vignette Sales and Vessel Revenue Analysis (`dsb_capstone`)

> **Data Science Capstone Project** | Exploratory Data Analysis, Feature Engineering & Revenue Trends

[![Python 3.x](https://img.shields.io/badge/Python-3.x-blue.svg)](https://www.python.org/)
[![Pandas](https://img.shields.io/badge/Library-Pandas-orange.svg)](https://pandas.pydata.org/)
[![Status](https://img.shields.io/badge/Status-Completed%20%2F%20Active-success.svg)]()

---

## 📌 Project Overview
The primary objective of this project is to answer a core business question: **How do monthly revenues and the volume of sold vignettes trend over the years, and in what ways do vessel characteristics (such as length) impact financial outcomes?**

By leveraging historical transactional logs (`Baza podataka 5 godina.xlsx`), this project conducts a thorough **Exploratory Data Analysis (EDA)** alongside robust **Feature Engineering** to transform raw operational data into structured, actionable insights for future predictive forecasting models[cite: 2].

---

## 📂 Data Source & Structure
* **Source Dataset:** Internal Excel logs tracking issued vessel vignettes over a 5-year period[cite: 2].
* **Initial Dimensions:** 26,764 rows and 12 initial columns[cite: 2].
* **Key Attributes:** Unique vignette serial numbers, vessel names, registration IDs, physical attributes (vessel length), validity periods, regional branch offices issuing documents, and financial metrics (with and without tax)[cite: 2].

---

## ⚠️ Data Quality & Challenges
Initial data auditing revealed several structural obstacles that required systematic cleaning:
* **Missing Data:** Certain rows lacked critical details, such as vessel names or registration marks (~79 missing vessel IDs), requiring careful imputation[cite: 2].
* **Manual Entry Flaws:** Empty rows at the bottom of spreadsheets and automatically generated summary rows introduced noise that needed removal[cite: 2].
* **Date Formatting:** Raw date entries started as plain text strings (`object` data type) and were converted into proper `pandas datetime` objects for accurate chronological tracking[cite: 2].

---

## 🔄 Step-by-Step EDA & Feature Engineering Pipeline
The analysis is structured sequentially within the Jupyter/Colab notebook (`JelenaVasic_capstone.ipynb`)[cite: 1, 2]:

1. **Data Sourcing & Initial Loading:** Imported raw Excel files into a Pandas DataFrame and verified structural dimensions (`26,764 rows`, `12 columns`)[cite: 2].
2. **Structural Audit & Descriptive Statistics:** Evaluated column types via `info()` and calculated baseline descriptive statistics (mean, min, max, percentiles) using `describe()`[cite: 2].
3. **Data Cleansing:** Identified null values via `isnull().sum()` and filtered out unusable rows lacking critical identifiers to safeguard data integrity[cite: 2].
4. **Categorical Grouping & Business Insights:** Analyzed transaction volumes and gross revenue generation across regional branch offices (such as Tivat, Zelenika, and Bar) using `value_counts()` and `groupby()`[cite: 2].
5. **Datetime Normalization & Temporal Decomposition:** Converted textual dates into formal `datetime64` objects to extract dedicated `Year` and `Month` features for year-over-year and seasonal trend analysis[cite: 2].
6. **Data Visualization:** Generated visual analytical reports using Matplotlib and Seaborn, including office distribution counts, vessel length histograms, and seasonal revenue trend line charts[cite: 1, 2].
7. **Advanced Feature Engineering:** 
   * *Data Imputation:* Filled missing vessel names with 'Unknown Vessel' and missing lengths with the median value[cite: 2].
   * *Categorization:* Classified vignettes into distinct price tiers (`Low Price`, `Medium Price`, `High Price`)[cite: 2].
   * *Time Series Metrics:* Calculated time gaps (`diff`) between consecutive transactions to capture temporal momentum[cite: 2].
   * *Dimensionality Reduction:* Applied `StandardScaler` and Principal Component Analysis (`PCA`) to project numerical vessel and pricing attributes into principal components (`PCA1`, `PCA2`)[cite: 2].
8. **Predictive Modeling (Introductory Preview):** Implemented a foundational Linear Regression model grouped by year and office location to establish a baseline for future inventory demand forecasting[cite: 2].

---

## 🛠️ Technologies & Libraries Used
The project is built within a **Python 3** environment using the following core packages[cite: 2]:

| Library | Primary Purpose |
| :--- | :--- |
| **Pandas & NumPy** | Data loading, cleaning, feature engineering, and aggregation[cite: 2]. |
| **Matplotlib & Seaborn** | Visual exploratory analysis, discovering seasonal trends, and tracking data distributions[cite: 1, 2]. |
| **Scikit-learn** | Preprocessing (`StandardScaler`), feature transformation (`PCA`), and introductory predictive modeling (`Linear Regression`)[cite: 2]. |

---
*For a detailed walkthrough of the code and implementation details, please refer to the [JelenaVasic_capstone.ipynb](https://github.com/jelenavasic009-png/DSB-Unit-02/tree/main) notebook.*

















# 🚢 Analiza prodaje vinjeta i prihoda plovila (`dsb_capstone`)

> **Data Science Capstone projekat** | Exploratory Data Analysis, Feature Engineering & Trendovi prihoda

[![Python 3.x](https://img.shields.io/badge/Python-3.x-blue.svg)](https://www.python.org/)
[![Pandas](https://img.shields.io/badge/Library-Pandas-orange.svg)](https://pandas.pydata.org/)
[![Status](https://img.shields.io/badge/Status-Završeno%20%2F%20Aktivno-success.svg)]()

---

## 📌 Pregled projekta
Primarni cilj ovog projekta jeste da odgovori na ključno poslovno pitanje: **Kako se mjesečni prihodi i obim prodatih vinjeta kreću kroz godine, i na koje načine karakteristike plovila (poput dužine) utiču na finansijske ishode?**

Korišćenjem istorijskih transakcionih evidencija (`Baza podataka 5 godina.xlsx`), ovaj projekat sprovodi temeljnu **Eksploratornu analizu podataka (EDA)** uz robusno **inženjerstvo obeležja (Feature Engineering)**, pretvarajući sirove operativne podatke u struktuirane i upotrebljive uvide za buduće prediktivne modele[cite: 2].

---

## 📂 Izvor podataka i struktura
* **Izvorni skup podataka:** Interni Excel izvještaji koji prate izdate vinjete za plovila tokom perioda od 5 godina[cite: 2].
* **Inicijalne dimenzije:** 26.764 reda i 12 početnih kolona[cite: 2].
* **Ključni atributi:** Jedinstveni serijski brojevi vinjeta, imena plovila, registracione oznake, fizičke karakteristike (dužina plovila), periodi važenja, regionalne ispostave koje su izdale dokumente i finansijske metrike (sa porezom i bez poreza)[cite: 2].

---

## ⚠️ Kvalitet podataka i izazovi
Inicijalna revizija podataka otkrila je nekoliko strukturnih prepreka koje su zahtijevale sistematsko čišćenje:
* **Nedostajući podaci:** Određeni redovi nijesu imali ključne detalje, poput imena plovila ili registracionih oznaka (~79 nedostajućih ID-jeva plovila), što je zahtijevalo pažljivu imputaciju[cite: 2].
* **Greške pri ručnom unosu:** Prazni redovi na dnu tabela i automatski generisani redovi sa zbirnim vrijednostima unijeli su šum koji je trebalo ukloniti[cite: 2].
* **Formatiranje datuma:** Sirovi unosi datuma počinjali su kao obične tekstualne niske (`object` tip podataka) i konvertovani su u odgovarajuće `pandas datetime` objekte radi preciznog hronološkog praćenja[cite: 2].

---

## 🔄 Korak-po-korak EDA i Feature Engineering pipeline
Analiza je struktuirana sekvencijalno unutar Jupyter/Colab sveske (`JelenaVasic_capstone.ipynb`)[cite: 1, 2]:

1. **Učitavanje podataka i inicijalni pregled:** Uvezeni su sirovi Excel fajl u Pandas DataFrame i provjerene strukturne dimenzije (`26.764 reda`, `12 kolona`)[cite: 2].
2. **Strukturna revizija i deskriptivna statistika:** Procenjeni su tipovi kolona pomoću `info()` funkcije i izračunata osnovna deskriptivna statistika (srednja vrijednost, minimum, maksimum, percentili) korišćenjem `describe()`[cite: 2].
3. **Čišćenje podataka:** Identifikovane su nulte vrijednosti pomoću `isnull().sum()` i filtrirani su neupotrebljivi redovi kojima su nedostajali ključni identifikatori radi očuvanja integriteta podataka[cite: 2].
4. **Kategorijsko grupisanje i poslovni uvidi:** Analizirani su obimi transakcija i generisanje bruto prihoda po regionalnim ispostavama (poput Tivta, Zelenike i Bara) korišćenjem `value_counts()` i `groupby()`[cite: 2].
5. **Normalizacija datuma i vremenska dekompozicija:** Tekstualni datumi su konvertovani u formalne `datetime64` objekte radi ekstrakcije namjenskih kolona `Year` i `Month` za analizu trendova iz godine u godinu i sezonskih kretanja[cite: 2].
6. **Vizuelizacija podataka:** Generisani su vizuelni analitički izvještaji pomoću biblioteka Matplotlib i Seaborn, uključujući prikaze distribucije po ispostavama, histogram dužina plovila i linijske grafikone sezonskih trendova prihoda[cite: 1, 2].
7. **Napredno inženjerstvo obeležja (Feature Engineering):** 
   * *Imputacija podataka:* Nedostajuća imena plovila popunjena su sa 'Unknown Vessel', a nedostajuće dužine medijanom[cite: 2].
   * *Kategorizacija:* Vinjete su klasifikovane u jasne cjenovne rangove (`Low Price`, `Medium Price`, `High Price`)[cite: 2].
   * *Metrike vremenskih serija:* Izračunati su vremenski razmaci (`diff`) između uzastopnih transakcija radi hvatanja vremenskog momenta[cite: 2].
   * *Smanjenje dimenzionalnosti:* Primijenjeni su `StandardScaler` i analiza glavnih komponenti (**PCA**) kako bi se numerički atributi plovila i cijena projektovali u glavne komponente (`PCA1`, `PCA2`)[cite: 2].
8. **Prediktivno modelovanje (Uvodni pregled):** Implementiran je osnovni model linearne regresije grupisan po godinama i lokaciji ispostave radi postavljanja osnove za buduće predviđanje potražnje i zaliha[cite: 2].

---

## 🛠️ Korišćene tehnologije i biblioteke
Projekat je razvijen u **Python 3** okruženju uz oslanjanje na sledeće ključne pakete[cite: 2]:

| Biblioteka | Primarna namjena |
| :--- | :--- |
| **Pandas & NumPy** | Učitavanje, čišćenje, inženjerstvo obeležja i agregacija podataka[cite: 2]. |
| **Matplotlib & Seaborn** | Vizuelna eksploratorna analiza, otkrivanje sezonskih trendova i praćenje distribucije podataka[cite: 1, 2]. |
| **Scikit-learn** | Pretprocesiranje (`StandardScaler`), transformacija obeležja (`PCA`) i uvodno prediktivno modelovanje (`Linear Regression`)[cite: 2]. |

---
*Za detaljan pregled koda i implementacije, molimo pogledajte [JelenaVasic_capstone.ipynb](https://github.com/jelenavasic009-png/DSB-Unit-02/tree/main) svesku.*
