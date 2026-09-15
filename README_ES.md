# Predicción de Entregas Tardías con Machine Learning

**Español** | [English](README.md)

Proyecto de Machine Learning enfocado en identificar órdenes de producción con riesgo de entrega tardía utilizando datos operativos y modelos lineales interpretables de clasificación.

Desarrollado con **Python, Pandas, NumPy, Scikit-learn, Matplotlib y Seaborn**.

> Este proyecto fue desarrollado como un caso académico de Machine Learning en el programa de Ciencia de Datos de la Universidad de La Sabana. Se presenta como proyecto de portafolio para demostrar habilidades en preprocesamiento, análisis exploratorio, Feature Engineering, clasificación, comparación e interpretación de modelos.

## Problema de negocio

Las entregas tardías pueden afectar la satisfacción del cliente, la planeación de producción y la eficiencia operativa. El objetivo del proyecto es analizar variables operativas asociadas con los retrasos y construir un flujo de clasificación que permita identificar órdenes con mayor riesgo de entrega tardía.

La variable objetivo es `entrega_tardia`:

- `0`: orden entregada a tiempo
- `1`: orden entregada tarde

## Dataset

El caso académico original utiliza:

- Un dataset etiquetado con **1.800 órdenes de producción** y 22 columnas incluyendo la variable objetivo.
- Un dataset sin variable objetivo con **600 órdenes** y 21 variables predictoras para generar las predicciones finales.

La distribución de la variable objetivo en los datos etiquetados es:

- **1.146 órdenes a tiempo (63,7%)**
- **654 órdenes tardías (36,3%)**

Debido al desbalance moderado entre clases, el análisis considera Recall, F1-score y Balanced Accuracy además de Accuracy.

> Los CSV originales no se encuentran actualmente incluidos en este repositorio público. El repositorio contiene el notebook del proyecto y su documentación.

## Flujo del proyecto

El análisis incluye:

1. Carga e inspección estructural de los datos
2. Análisis de calidad
3. Tratamiento de valores faltantes
4. Análisis de duplicados y valores atípicos
5. Análisis Exploratorio de Datos
6. Codificación de variables categóricas y escalamiento
7. Entrenamiento de modelos baseline
8. Feature Engineering
9. Reentrenamiento y comparación de modelos
10. Análisis mediante matrices de confusión
11. Interpretación de coeficientes de Regresión Logística
12. Selección del modelo final
13. Predicción de las 600 órdenes sin etiqueta

## Feature Engineering

Se crearon seis variables operativas para representar relaciones que no estaban directamente disponibles en las variables originales:

- `carga_por_operario`
- `presion_cola_capacidad`
- `lote_por_operario`
- `indice_inestabilidad`
- `riesgo_externo`
- `degradacion_equipo`

Estas variables combinan información relacionada con carga de trabajo, capacidad de producción, disponibilidad de personal, inestabilidad operativa, riesgo externo y condición de los equipos.

Un resultado importante del experimento es que **Feature Engineering no mejoró todos los modelos ni todas las métricas**. Por esta razón, las nuevas variables se interpretan como una alternativa experimental de modelado y no como una mejora automática del desempeño.

## Modelos evaluados

Se compararon tres métodos lineales de clasificación:

- Regresión Logística
- Perceptrón
- Adaline

Cada modelo fue analizado con las variables baseline y después de Feature Engineering.

## Métricas reportadas por el experimento

El notebook reporta las siguientes métricas para los modelos baseline:

| Modelo | Accuracy | Recall | F1-score | Balanced Accuracy |
|---|---:|---:|---:|---:|
| Regresión Logística | 69,39% | 69,27% | 62,18% | 69,36% |
| Perceptrón | 66,50% | 48,01% | 51,02% | 62,53% |
| Adaline | 72,67% | 59,17% | 61,14% | 69,77% |

Después de Feature Engineering:

| Modelo | Accuracy | Recall | F1-score | Balanced Accuracy |
|---|---:|---:|---:|---:|
| Regresión Logística | 69,56% | 68,35% | 62,00% | 69,30% |
| Perceptrón | 57,67% | 59,48% | 50,52% | 58,06% |
| Adaline | 73,11% | 59,79% | 61,77% | 70,25% |

### Limitación de la evaluación

Estos valores corresponden a **métricas calculadas sobre los datos de entrenamiento en el notebook actual**, no a resultados de validación hold-out ni a desempeño sobre un conjunto de prueba etiquetado no visto.

Son útiles para documentar el experimento académico, pero no deben interpretarse como una estimación del desempeño de generalización del modelo.

Una versión metodológicamente más fuerte utilizaría una partición estratificada entrenamiento/validación o validación cruzada, ajustaría el preprocesamiento únicamente con los folds de entrenamiento, seleccionaría el modelo utilizando datos de validación y finalmente reentrenaría el pipeline seleccionado con todos los datos etiquetados antes de predecir las 600 órdenes sin etiqueta.

## Comparación del Feature Engineering

Para Regresión Logística, las métricas de entrenamiento cambiaron ligeramente después de Feature Engineering:

| Métrica | Baseline | Feature Engineering |
|---|---:|---:|
| Accuracy | 69,39% | 69,56% |
| Recall | 69,27% | 68,35% |
| F1-score | 62,18% | 62,00% |
| Balanced Accuracy | 69,36% | 69,30% |

Este resultado deja una lección importante: crear más variables no garantiza mejores resultados. El impacto del Feature Engineering debe evaluarse empíricamente.

## Modelo final del experimento académico

El notebook selecciona **Regresión Logística con Feature Engineering** considerando el equilibrio buscado entre Recall, F1-score, estabilidad e interpretabilidad.

Esto no significa que sea el modelo con el valor más alto en todas las métricas. Por ejemplo, Adaline registra mayor Accuracy y Balanced Accuracy de entrenamiento dentro del experimento reportado.

La Regresión Logística también permite analizar directamente sus coeficientes para estudiar cómo las variables operativas contribuyen a la decisión de clasificación.

## Predicciones sobre órdenes sin etiqueta

Después de seleccionar el modelo, el flujo académico genera predicciones para **600 órdenes sin variable objetivo conocida**:

- **330 predichas a tiempo**
- **270 predichas como tardías**
- **45,0% de tasa predicha de entrega tardía**

Estas cifras son predicciones sobre registros sin etiquetas conocidas y no representan una evaluación de Accuracy.

## Tecnologías

`Python` · `Pandas` · `NumPy` · `Scikit-learn` · `Matplotlib` · `Seaborn` · `Jupyter Notebook`

## Estructura actual del repositorio

```text
late-delivery-prediction/
├── README.md
├── README_ES.md
└── Proyecto_corte2_corregido.ipynb
```

Esta estructura representa el repositorio tal como existe actualmente. En futuras mejoras del portafolio se puede estandarizar el nombre del notebook y añadir documentación del entorno y las dependencias.

## Explorar el proyecto

Clona el repositorio:

```bash
git clone https://github.com/david1727x/late-delivery-prediction.git
cd late-delivery-prediction
```

Abre el notebook con Jupyter:

```bash
jupyter notebook Proyecto_corte2_corregido.ipynb
```

Los datasets académicos originales son necesarios para reproducir la ejecución completa y no están incluidos actualmente en el repositorio público.

## Habilidades demostradas

`Machine Learning` · `Python` · `Análisis de Datos` · `Preprocesamiento de Datos` · `Feature Engineering` · `Regresión Logística` · `Clasificación` · `Interpretación de Modelos` · `Visualización de Datos`

## Autor

**David Santiago Cifuentes Grimaldo**  
Estudiante de Ciencia de Datos  
Universidad de La Sabana
