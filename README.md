# 🎓 Segmentación de Estudiantes por Rendimiento Académico

![Python](https://img.shields.io/badge/Python-3.8+-blue?logo=python&logoColor=white)
![Scikit-learn](https://img.shields.io/badge/Scikit--learn-Latest-F7931E?logo=scikitlearn&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-Latest-150458?logo=pandas&logoColor=white)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-F37626?logo=jupyter&logoColor=white)
![Accuracy](https://img.shields.io/badge/Accuracy-100%25-brightgreen)
![Clústers](https://img.shields.io/badge/Clústers%20K--Means-2-blueviolet)
![License](https://img.shields.io/badge/Licencia-MIT-lightgrey)

Proyecto de **análisis de datos y Machine Learning** orientado a la **segmentación de estudiantes universitarios** según su avance académico y rendimiento (GPA), con foco en la Facultad de Ciencias de la Salud. El objetivo es proporcionar a las áreas académicas e institucionales inteligencia accionable para diseñar intervenciones diferenciadas de apoyo estudiantil.

---

## 📌 Contexto Institucional

Las instituciones de educación superior enfrentan el reto permanente de identificar a tiempo a los estudiantes en riesgo académico y a quienes están próximos a graduarse, para orientar recursos de manera eficiente. Este proyecto responde a esa necesidad mediante:

- **Identificación de perfiles estudiantiles** basados en avance de malla y GPA
- **Segmentación automática** para distinguir estudiantes en etapas iniciales vs. avanzadas
- **Apoyo a la toma de decisiones** en tutorías, retención y planificación curricular
- **Visualización de insights** que comunican hallazgos a equipos académicos y directivos

---

## 🎯 Alcance del Proyecto

- Importación, unión y limpieza de dos datasets institucionales (`estudiantes.csv` + `carreras.csv`)
- Detección y manejo de valores faltantes y outliers
- Análisis exploratorio con visualizaciones por carrera, género y rendimiento
- Determinación del número óptimo de clústers mediante **Silhouette Score** y **Dendrograma**
- Modelo de **K-Means** para segmentación + validación con **Regresión Logística**
- Interpretación y comunicación de los segmentos identificados

---

## Visualización de Malla vs GPA por carrera (Facultad de Ciencias de la Salud)

<img width="810" height="403" alt="image" src="https://github.com/user-attachments/assets/367fcc60-7a75-44cd-aeaf-0eb2bb01d740" />


## 🧪 Modelos y Resultados
<img width="638" height="401" alt="image" src="https://github.com/user-attachments/assets/02c9f30f-4904-4810-8f57-d960674b77c7" />

<img width="758" height="409" alt="image" src="https://github.com/user-attachments/assets/05573e37-7c0a-4dcd-88ac-8e5250890ab8" />

### Segmentación — K-Means (2 clústers)

El número óptimo de clústers fue determinado mediante análisis del Silhouette Score y dendrograma jerárquico, resultando en **2 segmentos diferenciados**:

<img width="596" height="406" alt="image" src="https://github.com/user-attachments/assets/a952e0db-53e2-4827-b3e8-dfd11401c306" />


| Segmento | Avance de Malla (%) | GPA Promedio | Perfil |
|:--------:|:-------------------:|:------------:|--------|
| **Clúster 0** | ~24.4% | 85.4 | Estudiantes en etapa inicial — recién incorporados o con bajo avance curricular |
| **Clúster 1** | ~76.7% | 84.8 | Estudiantes avanzados — próximos a completar su programa académico |

> Ambos segmentos presentan un GPA comparable (~85 pts.), lo que indica que el **avance en la malla** — no el rendimiento académico — es el principal diferenciador entre grupos.

### Clasificación — Regresión Logística (validación)

| Métrica | Resultado |
|---------|:---------:|
| ✅ Accuracy | **100%** |
| 🎯 Precision | **1.00** |
| 🔍 Recall | **1.00** |
| ⚖️ F1-Score | **1.00** |

> La exactitud perfecta confirma que los dos segmentos están **linealmente separables** en el espacio avance de malla / GPA, validando la calidad de la segmentación.

---

## 🔍 Insights Clave

**Avance de malla como variable determinante:** La diferencia de ~52 puntos porcentuales entre clústers posiciona el avance curricular como el indicador más discriminante entre perfiles estudiantiles — por encima del GPA.

**GPA homogéneo entre segmentos:** El rendimiento académico promedio es consistente entre grupos (~85 pts.), sugiriendo que los estudiantes mantienen buen desempeño en notas independientemente de su etapa en la carrera.

**Outliers detectados:** Se identificaron **9 casos atípicos** en las variables `avance_malla` y `gpa` dentro de la Facultad de Ciencias de la Salud, que requieren seguimiento individualizado.

---

## 📂 Datasets

El análisis integra dos fuentes de datos institucionales unidas por el campo `id`:

### `estudiantes.csv`

| Variable | Tipo | Descripción |
|----------|------|-------------|
| `id` | Identificador | Código único del estudiante |
| `genero` | Categórica | M / F |
| `edad` | Numérica | Edad del estudiante |
| `periodo_inicio` | Fecha | Periodo académico de ingreso |
| `avance_malla` | Numérica | % de materias aprobadas sobre el total |
| `gpa` | Numérica | Promedio de notas (escala 0–100) |

### `carreras.csv`

| Variable | Tipo | Descripción |
|----------|------|-------------|
| `id` | Identificador | Código único del estudiante |
| `carrera` | Categórica | Nombre de la carrera |
| `facultad` | Categórica | Facultad a la que pertenece |
| `campus` | Categórica | Campus donde recibe clases |

**Dataset combinado:** `data` → **6,723 registros** × 11 variables

**Registros analizados — Facultad de Ciencias de la Salud:**
```
Total registros:   ~2,235 estudiantes
Valores faltantes: 84 registros en GPA → imputados con la media
Outliers:          9 casos atípicos detectados
```

---

## 🛠️ Stack Tecnológico

- **Python 3.8+**
- **Pandas / NumPy** — importación, limpieza y transformación de datos
- **Scikit-learn** — KMeans, LogisticRegression, SimpleImputer, métricas
- **SciPy** — clustering jerárquico y dendrograma
- **Matplotlib / Seaborn** — visualizaciones EDA y resultados
- **Jupyter Notebook** — entorno de análisis interactivo

---

## ⚙️ Instalación y Uso

**1. Clonar el repositorio**
```bash
git clone https://github.com/davallejo/segmentacion-estudiantes.git
cd segmentacion-estudiantes
```

**2. Instalar dependencias**
```bash
pip install -r requirements.txt
```

**3. Colocar los datasets en la raíz del proyecto**
```
segmentacion-estudiantes/
├── estudiantes.csv
├── carreras.csv
└── ...
```

**4. Ejecutar el notebook**
```bash
jupyter notebook analisis_estudiantes.ipynb
```

**5. Predecir el segmento de un nuevo estudiante**
```python
import joblib
import numpy as np

model = joblib.load("logistic_model.pkl")

# Nuevo estudiante: avance_malla=45%, GPA=87
nuevo_estudiante = np.array([[45.0, 87.0]])
cluster = model.predict(nuevo_estudiante)

print(f"Segmento asignado: Clúster {cluster[0]}")
# Clúster 0 → Etapa inicial | Clúster 1 → Etapa avanzada
```

---

## 📁 Estructura del Proyecto

```
segmentacion-estudiantes/
├── data/
│   ├── estudiantes.csv             # Dataset de estudiantes
│   ├── carreras.csv                # Dataset de carreras
│   └── data_merged.csv             # Dataset combinado procesado
├── notebooks/
│   └── analisis_estudiantes.ipynb  # Análisis completo
├── models/
│   ├── kmeans_model.pkl            # Modelo K-Means entrenado
│   └── logistic_model.pkl          # Modelo clasificador entrenado
├── outputs/
│   └── visualizaciones/            # Gráficos exportados
├── requirements.txt
└── README.md
```

---

## 💡 Implicaciones para la Gestión Académica

Los segmentos identificados habilitan acciones concretas para los equipos institucionales:

**Para Bienestar Estudiantil:** El Clúster 0 (etapa inicial, ~24% de avance) es el grupo prioritario para programas de mentoría, tutorías de adaptación universitaria y seguimiento temprano de riesgo de deserción.

**Para Dirección Académica:** El Clúster 1 (avance ~77%) representa candidatos próximos a graduarse. Son el grupo objetivo para talleres de inserción laboral, prácticas profesionales y acompañamiento en trabajos de titulación.

**Para Planificación Curricular:** La homogeneidad del GPA entre clústers sugiere que los planes de estudio mantienen consistencia en exigencia académica a lo largo de la carrera, lo cual es un indicador positivo de diseño curricular.

**Para Registro y Admisiones:** Los 9 outliers detectados merecen análisis individual — pueden representar casos de convalidación, cambio de carrera o situaciones académicas excepcionales.

---

## 🗺️ Roadmap

- [ ] Incorporar variables adicionales: género, campus y periodo de inicio para enriquecer la segmentación
- [ ] Extender el análisis a todas las facultades para comparación institucional
- [ ] Dashboard interactivo con Streamlit para consulta por carrera y campus
- [ ] Modelo predictivo de riesgo de deserción basado en los perfiles identificados
- [ ] Automatización del pipeline con actualización periódica de datos

---

## 📄 Licencia

Este proyecto está bajo la Licencia MIT. Consulta el archivo [LICENSE](LICENSE) para más detalles.

---

## 👤 Autor

**Diego Vallejo**

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Diego%20Vallejo-0A66C2?logo=linkedin&logoColor=white)](https://www.linkedin.com/in/ing-diego-vallejo)
[![GitHub](https://img.shields.io/badge/GitHub-davallejo-181717?logo=github&logoColor=white)](https://github.com/davallejo)
[![Portfolio](https://img.shields.io/badge/Portfolio-davallejo.github.io-4A90D9?logo=githubpages&logoColor=white)](https://davallejo.github.io/)

---

> *Análisis académico orientado a resultados — transformando datos estudiantiles en estrategias de retención, acompañamiento y mejora continua institucional.*
