# ✈️ FlightDelays_ETL_Dashboard

> ⚠️ **Remarque :** Le fichier **`flights.csv`** (plus de 100 Mo) **n'est pas inclus** dans ce dépôt GitHub.  
> Merci de le télécharger manuellement depuis [Kaggle](https://www.kaggle.com/datasets/usdot/flight-delays) et de le placer dans le dossier :
> ```
> data/raw/flights.csv
> ```

---

## 📊 Objectif du projet

Ce projet a pour but d’analyser les retards de vols aux États-Unis en 2015 à travers trois étapes majeures :

1. **Processus ETL (Extract, Transform, Load)**  
   Extraction des données brutes, nettoyage et transformation des données pour une exploitation efficace.

2. **Visualisation avec Power BI**  
   Création d’un **dashboard interactif** facilitant l’analyse des retards, compagnies aériennes, et aéroports.

3. **Orchestration avec Apache Airflow**  
   Mise en place d’un pipeline de traitement des données automatique et planifiable.

---

## 📁 Structure du projet

```
FlightDelays_ETL_Dashboard/
│
├── data/
│   ├── raw/                    # Données originales téléchargées depuis Kaggle
│   │   ├── airlines.csv
│   │   ├── airports.csv
│   │   └── flights.csv         ⚠️ Non inclus (à ajouter manuellement)
│   └── processed/              # Données nettoyées et prêtes à l’analyse
│
├── etl/                        # Scripts Python pour ETL
│   ├── extract.py
│   ├── transform.py
│   └── load.py
│
├── dashboards/                 # Fichiers Power BI (.pbix)
│
├── airflow/                    # DAGs Airflow pour l’orchestration
│
├── notebooks/                  # Analyses et explorations initiales
│
├── .gitignore
├── README.md                   # Ce fichier
└── requirements.txt
```

---

## 📦 1. Dataset utilisé

Le dataset provient du **Bureau of Transportation Statistics** (DOT) des États-Unis via [Kaggle](https://www.kaggle.com/datasets/usdot/flight-delays), basé sur l'année **2015**.  
Il contient trois fichiers principaux :

---

### 🔹 1.1 `flights.csv` — Détails des vols

Ce fichier contient environ **5.8 millions** de lignes et **31 colonnes**. Chaque ligne représente un vol.

#### 📅 Informations générales
- `YEAR`, `MONTH`, `DAY`, `DAY_OF_WEEK` : Date du vol.
- `AIRLINE` : Code de la compagnie aérienne.
- `FLIGHT_NUMBER` : Numéro du vol.
- `TAIL_NUMBER` : Immatriculation de l’avion.

#### 🛫 Aéroports
- `ORIGIN_AIRPORT` : Code IATA de départ.
- `DESTINATION_AIRPORT` : Code IATA d’arrivée.

#### 🕒 Heures
- `SCHEDULED_DEPARTURE`, `DEPARTURE_TIME` : Heure prévue vs. réelle de départ.
- `SCHEDULED_ARRIVAL`, `ARRIVAL_TIME` : Heure prévue vs. réelle d’arrivée.

#### ⏱️ Durées et distances
- `SCHEDULED_TIME`, `ELAPSED_TIME`, `AIR_TIME` : Durées diverses.
- `DISTANCE` : Distance en miles.

#### 🚖 Temps au sol
- `TAXI_OUT`, `TAXI_IN` : Temps de roulage au départ et à l’arrivée.
- `WHEELS_OFF`, `WHEELS_ON` : Moments précis de décollage/atterrissage.

#### ⏰ Retards
- `DEPARTURE_DELAY`, `ARRIVAL_DELAY` : Retards principaux.
- `AIRLINE_DELAY`, `WEATHER_DELAY`, `AIR_SYSTEM_DELAY`, `SECURITY_DELAY`, `LATE_AIRCRAFT_DELAY` : Causes détaillées des retards.

#### ❌ Annulations et déroutements
- `CANCELLED`, `CANCELLATION_REASON` : Statut et raison (A/B/C/D).
- `DIVERTED` : Indique un déroutement.

---

### 🔹 1.2 `airlines.csv` — Compagnies aériennes

- `IATA_CODE` : Code IATA (ex. "AA")
- `AIRLINE` : Nom complet de la compagnie

---

### 🔹 1.3 `airports.csv` — Aéroports

- `IATA_CODE` : Code IATA (ex. "JFK")
- `AIRPORT` : Nom complet
- `CITY`, `STATE`, `COUNTRY` : Localisation
- `LATITUDE`, `LONGITUDE` : Coordonnées GPS

---

## 🛠️ Étapes techniques

| Étape       | Description                                  | Fichiers concernés                 |
|-------------|----------------------------------------------|-----------------------------------|
| **ETL**     | Scripts d'extraction, transformation, chargement | `etl/*.py`                       |
| **Analyse** | Exploration avec Pandas, nettoyage            | `notebooks/*.ipynb`               |
| **Dashboard** | Visualisation via Power BI                  | `dashboards/*.pbix`               |
| **Orchestration** | DAGs pour Airflow                     | `airflow/*.py`                    |

---

## ✅ Pré-requis techniques

- Python (>= 3.9)
- Pandas, Numpy
- Power BI Desktop
- Apache Airflow 


## 🧾 Remarque sur les fichiers volumineux

> Le fichier `flights.csv` est trop volumineux pour être hébergé sur GitHub (limite de 100 Mo).  
> Il est volontairement **ignoré via `.gitignore`**.  
> ➕ Une alternative avec **Git LFS** peut être envisagée, mais ce projet propose uniquement un téléchargement manuel.

---

