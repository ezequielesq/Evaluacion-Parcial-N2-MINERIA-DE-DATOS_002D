# README — Predicción de Lluvia en Australia

## Minería de Datos — BIY7121 | Evaluación Parcial N°2

Este proyecto aplica las **tres primeras fases de la metodología CRISP-DM** al dataset de observaciones meteorológicas diarias de Australia, con el objetivo de preparar los datos para la predicción de lluvia mediante modelos de Machine Learning.

---

## Dataset

- **weatherAUS.csv**
  - 142.193 observaciones meteorológicas diarias
  - 49 estaciones distribuidas en Australia
  - Período: Noviembre 2007 — Junio 2017
  - Variable objetivo: `RainTomorrow` (Sí / No)

---

## Estructura del Notebook

### Fase 1 — Business Understanding
- Contexto del negocio y clima australiano
- Definición del problema de predicción
- Objetivos del proyecto
- Descripción del dataset

### Fase 2 — Data Understanding
- Estadísticas descriptivas
- Análisis de valores nulos
- Distribución de variables numéricas
- Análisis de outliers (Boxplots + IQR)
- Matriz de correlación
- Análisis geográfico de lluvia por ubicación

### Fase 3 — Data Preparation

| Paso | Acción |
|---|---|
| 0 | Eliminación de `RISK_MM` (data leakage) |
| 0.1 | Eliminación de variables redundantes (`Temp3pm`, `Temp9am`, `Pressure3pm`) |
| 1 | Extracción de `Mes` y `Estacion` desde `Date` |
| 2 | Corrección de valores inválidos en `Cloud9am` y `Cloud3pm` |
| 3 | Imputación de nulos numéricos (mediana) |
| 4 | Imputación de nulos categóricos (moda) |
| 5 | Tratamiento de outliers (Winsorización IQR) |
| 6 | Encoding de variables categóricas (Label + One Hot) |
| 7 | Escalado de variables numéricas (StandardScaler) |
| 8 | Train/Test Split estratificado 80/20 |
| 9 | Preparación dataset no supervisado |

---

## Resultado Final

| Subconjunto | Registros | Variables |
|---|---|---|
| X_train | 113.754 | 116 |
| X_test | 28.439 | 116 |
| y_train | 113.754 | — |
| y_test | 28.439 | — |

---

## Requisitos

```bash
pip install pandas numpy matplotlib seaborn scikit-learn
```

---

## Hallazgos Principales

- `Humidity3pm` y `Sunshine` son las variables más predictivas (correlación ±0,45)
- Portland llueve el **36,55%** de los días vs Woomera con solo **6,76%**
- El **invierno** presenta la mayor probabilidad de lluvia (26,12%)
- Desbalance de clases: **77,6% No llueve** vs **22,4% Sí llueve**
