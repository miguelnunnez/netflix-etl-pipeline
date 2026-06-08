# 🎬 Netflix ETL Pipeline — Arquitectura Medallion

Pipeline de datos end-to-end construido con Python y Pandas que implementa la **arquitectura Medallion** (Bronze → Silver → Gold) sobre el dataset público de Netflix.

---

## 🏗️ Arquitectura

```
[Kaggle CSV]
     │
     ▼
🥉 BRONZE  →  Datos crudos + timestamp de ingesta       (Parquet)
     │
     ▼
🥈 SILVER  →  Limpieza · Validación · Normalización     (Parquet)
     │
     ▼
🥇 GOLD    →  Tablas analíticas listas para negocio     (Parquet / PNG)
```

## 📊 Resultados — Tablas Gold

| Tabla | Descripción |
|---|---|
| `gold_content_per_year` | Títulos agregados al catálogo por año y tipo |
| `gold_top_genres` | Top 15 géneros más frecuentes |
| `gold_type_distribution` | Distribución porcentual Movies vs TV Shows |

## 🛠️ Stack Tecnológico

| Herramienta | Uso |
|---|---|
| Python 3.x | Lenguaje principal |
| Pandas | Transformación y limpieza de datos |
| PyArrow | Serialización en formato Parquet |
| Matplotlib / Seaborn | Visualizaciones |
| Google Colab | Entorno de ejecución |

## 📁 Estructura del Proyecto

```
netflix-etl/
├── notebooks/
│   └── netflix_etl.ipynb       # Pipeline completo
├── data/
│   ├── bronze/
│   │   └── netflix_raw.parquet
│   ├── silver/
│   │   └── netflix_clean.parquet
│   └── gold/
│       ├── gold_content_per_year.parquet
│       ├── gold_top_genres.parquet
│       ├── gold_type_distribution.parquet
│       └── netflix_dashboard.png
└── README.md
```

## 🚀 Cómo ejecutar

1. Abre el notebook en Google Colab:  
   [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/)

2. Descarga el dataset desde [Kaggle — Netflix Shows](https://www.kaggle.com/datasets/shivamb/netflix-shows)

3. Ejecuta las celdas en orden — el notebook te pedirá subir el CSV

## 🔄 Transformaciones aplicadas (Silver)

- Eliminación de registros duplicados por `show_id`
- Campos de texto nulos (`director`, `cast`, `country`) reemplazados con `"Unknown"`
- `rating` nulo imputado con la moda del dataset
- `date_added` convertido a `datetime`
- Extracción de `year_added` y `month_added`
- `release_year` convertido a entero
- Campo `genres_list` generado a partir de `listed_in` (lista de géneros separados)

## ✅ Checklist del entregable

- [x] Extracción desde fuente (CSV Kaggle)
- [x] Bronze Layer — datos crudos con timestamp
- [x] Silver Layer — limpieza y validación completa
- [x] Gold Layer — 3 tablas analíticas
- [x] Visualizaciones (dashboard de 3 gráficos)
- [x] Buenas prácticas: funciones modulares, logging, type hints, docstrings
- [x] README documentado

---

**Autor:** Miguel Angel Núñez Martínez  
**Dataset:** [Netflix Movies and TV Shows](https://www.kaggle.com/datasets/shivamb/netflix-shows) — Kaggle  

