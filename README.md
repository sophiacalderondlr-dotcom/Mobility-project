# 🚦 Movilidad urbana y productividad económica en ciudades de Latinoamérica

Análisis de datos que explora **si existe una relación entre la congestión vehicular y el PIB per cápita** en las principales ciudades latinoamericanas durante 2024, combinando datos reales de **TomTom Traffic Index** y **OECD Cities**.

---

## 📌 Descripción del proyecto

Como analista de datos, el objetivo es evaluar cómo la movilidad urbana se relaciona con la productividad económica para apoyar una pregunta de negocio: **¿en qué ciudades conviene invertir en infraestructura de transporte?**

La hipótesis de partida es que *a mayor congestión, menor productividad económica*. El proyecto limpia, combina y visualiza los datos para contrastarla.

## 🎯 Pregunta de investigación

> ¿Las ciudades con más congestión vehicular tienen un menor PIB per cápita?

## 📊 Fuentes de datos

| Dataset | Fuente | Contenido principal |
|---|---|---|
| `tomtom_traffic.csv` | TomTom Traffic Index | Índice de tráfico, minutos de retraso, longitud y cantidad de congestiones, tiempos de viaje por cada 10 km |
| `oecd_city_economy.csv` | OECD Cities | PIB per cápita, tasa de desempleo, contaminación PM2.5 y población por ciudad |

> Los archivos CSV originales no se incluyen en este repositorio. El notebook los lee desde `/datasets/`.

## 🔄 Flujo de trabajo

1. **Carga y exploración:** lectura de ambos CSV y revisión de estructura, tipos de datos y valores.
2. **Limpieza y preparación:**
   - Estandarización de nombres de columnas a `snake_case`.
   - Conversión de columnas de fecha a `datetime`.
   - Limpieza de separadores y símbolos (`.`, `,`, `%`) para convertir PIB per cápita, desempleo, población y PM2.5 a valores numéricos.
   - Conversión de la población de millones a unidades absolutas.
3. **Filtrado por año:** extracción del año y selección de registros de **2024**.
4. **Agregación de movilidad:** promedio de las métricas de tráfico por ciudad, país y año.
5. **Unión de datasets:** `INNER JOIN` por `city` y `year`, para conservar solo ciudades presentes en ambas fuentes.
6. **Visualización:** boxplot, histograma y gráficos de barras para comparar congestión (`jams_delay`) y PIB per cápita (`city_dgp_capita`).
7. **Exportación:** generación del dataset limpio `ladb_mobility_economy_2024_clean.csv`.

## 🔍 Principales hallazgos

- El análisis cubre **15 ciudades de 7 países** en 2024.
- **Ciudad de México** es la ciudad con mayor retraso promedio por congestión (`jams_delay`).
- **No se observa una relación clara y consistente** entre PIB per cápita y congestión: algunas ciudades con mayor PIB también tienen alta congestión, pero no es la norma.
- Los datos **no respaldan** de forma clara la hipótesis de que mayor congestión implica menor productividad económica; por ejemplo, Bogotá combina congestión baja con un PIB per cápita bajo.

> ⚠️ Estos resultados son exploratorios y descriptivos. No se calculó un coeficiente de correlación ni se probó causalidad.

## 🛠️ Tecnologías

- Python 3
- pandas
- NumPy
- Matplotlib
- Seaborn
- Jupyter Notebook

## 📁 Estructura del repositorio

```
.
├── S5_ladb_mobility_economy_project.ipynb   # Notebook con todo el análisis
├── ladb_mobility_economy_2024_clean.csv     # Dataset final limpio (salida del notebook)
└── README.md
```

## ▶️ Cómo ejecutarlo

1. Clona el repositorio:
   ```bash
   git clone https://github.com/<tu-usuario>/<tu-repositorio>.git
   cd <tu-repositorio>
   ```
2. Instala las dependencias:
   ```bash
   pip install pandas numpy matplotlib seaborn jupyter
   ```
3. Coloca los archivos `tomtom_traffic.csv` y `oecd_city_economy.csv` en la carpeta `/datasets/` (o ajusta las rutas en la primera celda del notebook).
4. Abre y ejecuta el notebook:
   ```bash
   jupyter notebook S5_ladb_mobility_economy_project.ipynb
   ```

## 🚀 Posibles mejoras

- Calcular correlaciones (Pearson/Spearman) entre congestión y PIB per cápita.
- Incorporar otras variables ya disponibles, como desempleo, PM2.5 y población.
- Ampliar el análisis a varios años para observar tendencias.
- Normalizar la congestión por población o tamaño de la ciudad.

## 👤 Autor

**Sophia Elizabeth Calderon** · [GitHub](https://github.com/<tu-usuario>) · [LinkedIn](www.linkedin.com</in/sophia-elizabet-calderon-de-los-rios>)
