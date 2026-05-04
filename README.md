# Proyecto-SecurityDS

Michelle Mejía 22596 y Silvia Illescas 22376

---

## 1. Descripción del proyecto

Este proyecto tiene como objetivo desarrollar un sistema capaz de detectar si un audio corresponde a voz humana real o voz sintética generada mediante modelos de síntesis de voz (Text-to-Speech).

El problema se enmarca dentro del área de **seguridad informática**, específicamente en la detección de **deepfakes de audio**, los cuales pueden utilizarse en ataques de ingeniería social, fraude o suplantación de identidad.

Para abordar este problema, se utilizan técnicas de **Machine Learning**, comparando el desempeño de distintos modelos a partir de características acústicas extraídas del audio.

---

## 2. Objetivo

Desarrollar un modelo de clasificación capaz de distinguir entre voz real y voz sintética mediante el análisis de características acústicas extraídas de señales de audio.

---

## 3. Dataset

Se utiliza el dataset **Fake-or-Real (FoR)**, el cual contiene aproximadamente **195,000 muestras de audio** clasificadas en:

* voz real
* voz sintética generada mediante modelos TTS como WaveNet y Deep Voice 3

El dataset incluye múltiples versiones:

* `for-original` → archivos originales
* `for-norm` → audios normalizados y balanceados
* `for-2sec` → audios truncados a 2 segundos
* `for-rerec` → audios regrabados para simular escenarios reales

Para este proyecto se utiliza la versión:

**for-norm**, ya que presenta datos balanceados y normalizados.

---

## 4. Tecnologías utilizadas

Lenguaje:

* Python 3

Librerías principales:

* numpy
* pandas
* matplotlib
* librosa
* scikit-learn
* glob
* os

---

## 5. Estructura del proyecto

```
project/

├── dataset/
├── notebooks/
│   ├── 01_EDA.ipynb
│   ├── 02_Gen_y_Sel.ipynb
│   ├── 03_Modelos_y_Evaluacion.ipynb
├── README.md
```

---

## 6. Metodología

El proyecto se desarrolla en las siguientes etapas:

### 6.1 Análisis exploratorio de datos (EDA)

Se realiza un análisis inicial del dataset para comprender sus características principales:

* distribución de clases
* duración de audios
* frecuencia de muestreo
* visualización de señales de audio
* generación de espectrogramas

---

### 6.2 Generación y selección de características

Los archivos de audio se transforman en representaciones numéricas mediante:

* MFCC (Mel Frequency Cepstral Coefficients)
* espectrogramas Mel
* zero crossing rate
* energía de la señal
* chroma features

Estas características permiten representar el audio de forma adecuada para los modelos de Machine Learning.

---

### 6.3 Modelado

Se implementan modelos de clasificación supervisada:

* Logistic Regression
* Random Forest

Además, se aplica **GridSearchCV** para optimizar hiperparámetros y mejorar el desempeño de los modelos.

---

### 6.4 Evaluación del modelo

Para evaluar el desempeño se utilizan métricas de clasificación:

* Accuracy
* Precision
* Recall
* F1-score
* Curva ROC
* Matriz de confusión

Estas métricas permiten analizar la capacidad del modelo para distinguir entre audios reales y sintéticos.

---

## 7. Evaluación de modelos

En el notebook `03_Modelos_y_Evaluacion.ipynb` se realiza:

* Implementación de modelos
* Refinamiento mediante búsqueda de hiperparámetros
* Evaluación completa de métricas
* Generación de curva ROC
* Análisis de matriz de confusión

---

## 8. Interpretación de resultados

Los resultados obtenidos permiten evaluar el desempeño de los modelos en el contexto del problema.

El modelo Random Forest presenta un buen balance entre **precision y recall**, lo cual es importante en problemas de detección, ya que permite identificar correctamente casos positivos sin generar demasiados falsos positivos.

La curva ROC y su valor AUC indican que el modelo tiene una adecuada capacidad de discriminación entre clases.

En el contexto de seguridad informática, esto sugiere que el modelo puede ser utilizado como una herramienta de apoyo para la detección de deepfakes de audio.

---

## 9. Flujo del proyecto

1. `01_EDA.ipynb` → análisis exploratorio de datos
2. `02_Gen_y_Sel.ipynb` → extracción y selección de características
3. `03_Modelos_y_Evaluacion.ipynb` → entrenamiento, refinamiento y evaluación

---

## 10. Pasos para ejecutar el proyecto

### 1. Instalar dependencias

```
pip install numpy pandas matplotlib librosa scikit-learn
```

---

### 2. Descargar dataset

Descargar el dataset Fake-or-Real (FoR) y ubicarlo en:

```
dataset/
```

---

### 3. Ejecutar notebooks

```
01_EDA.ipynb
02_Gen_y_Sel.ipynb
03_Modelos_y_Evaluacion.ipynb
```

---

## 11. Nota importante

El dataset original no se incluye en el repositorio debido a su tamaño.

Para ejecutar completamente el proyecto, es necesario descargar el dataset y colocarlo en la carpeta `dataset/`.

Los archivos de características (`features_train`, `features_val`, `features_test`) deben generarse ejecutando el notebook `02_Gen_y_Sel.ipynb`.

---

## 12. Aplicaciones

Este proyecto puede aplicarse en:

* detección de fraude
* autenticación biométrica
* prevención de ataques de ingeniería social
* sistemas de verificación de identidad
* análisis forense digital

---
