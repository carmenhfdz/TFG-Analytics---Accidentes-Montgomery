# Análisis y predicción de lesiones en accidentes de tráfico — Condado de Montgomery

Trabajo de Fin de Grado (TFG) — Grado en Administración y Dirección de Empresas + Business Analytics
Autora: Carmen Humanes Fernández
Universidad Pontificia Comillas (ICADE)

## Descripción del proyecto

Este repositorio contiene el código desarrollado para el TFG, centrado en el análisis de la
siniestralidad vial en el condado de Montgomery (Maryland, EE. UU.) a partir de datos abiertos.

El objetivo principal es construir un modelo capaz de predecir la **presencia o ausencia de
lesiones** en las personas implicadas en un accidente (clasificación binaria: con lesión / sin
lesión), así como identificar qué factores se asocian en mayor medida a la aparición de lesiones.

El trabajo sigue la metodología *ETL (Extract, Transform, Load)* y combina análisis exploratorio,
modelización predictiva, interpretabilidad mediante SHAP y visualización de resultados.

## Datos

- *Fuente:* Crash Reporting – Drivers Data, publicado por el gobierno del condado de Montgomery
  a través del portal de datos abiertos de EE. UU. (Data.gov).
- *Nivel de los datos:* cada registro corresponde a un conductor implicado en un accidente, por lo
  que un mismo accidente puede aparecer en varias filas.
- *Nota:* se trata de datos preliminares procedentes de informes policiales, que presentaban
  numerosas inconsistencias y valores faltantes y requirieron un proceso de limpieza exhaustivo.

> El dataset original no se incluye en el repositorio por su tamaño. Puede descargarse directamente
> desde la fuente oficial (Data.gov).

## Contenido del repositorio

- TFG ANALYTICS-final.ipynb — Notebook principal con todo el proceso: limpieza, transformación,
  análisis exploratorio, modelización e interpretabilidad.
- README.md — Este archivo.

## Flujo de trabajo

1. *Extract:* carga y corrección de los problemas estructurales del fichero CSV original.
2. *Transform:* tratamiento de valores nulos, limpieza y agrupación de variables (mayoritariamente
   categóricas) y creación de nuevas variables mediante feature engineering.
3. *Load:* preparación del conjunto de datos final para el análisis y exportación para su uso en
   Tableau.
4. *Análisis exploratorio (EDA):* estudio de los patrones de siniestralidad y de la relación de las
   distintas variables con la presencia de lesiones.
5. *Modelización:* entrenamiento y comparación de varios modelos de clasificación, abordando el
   fuerte desbalanceo de la variable objetivo.
6. *Interpretabilidad:* análisis SHAP para explorar qué variables influyen más en las predicciones
   del modelo.

## Modelos y técnicas

- Regresión logística (modelo de referencia)
- Random Forest
- Random Forest + SMOTE (sobremuestreo)
- Balanced Random Forest
- Ajuste del umbral de decisión
- Distinción entre un conjunto de variables *predictivo* (información disponible antes del
  accidente) y otro *explicativo* (incluye variables conocidas tras el siniestro)

## Resultados principales

La capacidad predictiva del modelo es *moderada y limitada*: la información disponible antes del
accidente no captura por completo los factores que determinan que se produzcan lesiones. El análisis
SHAP muestra que las variables más asociadas a las lesiones son las que describen la dinámica del
propio accidente (tipo de colisión, tipo de vehículo, movimiento del vehículo), que solo se conocen
una vez ocurrido el siniestro.

Más allá del rendimiento del modelo, el principal valor del trabajo reside en el proceso: el manejo
de datos reales e imperfectos, la elección de métricas adecuadas en un problema desbalanceado y la
evaluación crítica de distintas técnicas y de las limitaciones del problema.

## Tecnologías utilizadas

- *Python* (pandas, NumPy)
- *scikit-learn* e *imbalanced-learn* (modelización y tratamiento del desbalanceo)
- *SHAP* (interpretabilidad)
- *Matplotlib, **Seaborn* y *WordCloud* (visualización)
- *Tableau* (panel de visualización final)


## Licencia y uso

Repositorio con fines exclusivamente académicos, como parte de un Trabajo de Fin de Grado.
