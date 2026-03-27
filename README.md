# Proyecto-SecurityDS
Michelle Mejía 22596 y  Silvia Illescas 22376

## 1. Descripción del proyecto

Este proyecto tiene como objetivo desarrollar un sistema capaz de detectar si un audio corresponde a voz humana real o voz sintética generada mediante modelos de síntesis de voz (Text-to-Speech). El problema se enmarca dentro del área de **seguridad informática**, específicamente en la detección de **deepfakes de audio**, los cuales pueden utilizarse en ataques de ingeniería social, fraude o suplantación de identidad.

Para abordar este problema, se utilizan técnicas de **Machine Learning** y **Deep Learning**, comparando el desempeño de un modelo tradicional (**Random Forest**) con un modelo basado en redes neuronales profundas (**Convolutional Neural Network - CNN**).

El dataset utilizado es **Fake-or-Real (FoR)**, el cual contiene miles de grabaciones de voz humana y voz generada por sistemas modernos de síntesis de voz.

---

## 2. Objetivo

Desarrollar un modelo de clasificación capaz de distinguir entre voz real y voz sintética mediante el análisis de características acústicas extraídas de señales de audio.

---

## 3. Dataset

Se utiliza el dataset **Fake-or-Real (FoR)**, el cual contiene aproximadamente **195,000 muestras de audio** clasificadas en:

* voz real
* voz sintética generada mediante modelos TTS como WaveNet y Deep Voice 3

El dataset incluye múltiples versiones:

* for-original → archivos originales
* for-norm → audios normalizados y balanceados
* for-2sec → audios truncados a 2 segundos
* for-rerec → audios regrabados para simular escenarios reales

Para este proyecto se utiliza la versión:

**for-norm**

porque presenta datos balanceados y normalizados, lo que facilita el entrenamiento de modelos.

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
* tensorflow / keras
* glob
* os

---

## 5. Estructura del proyecto

```
project/

│
├── dataset/
│
├── notebooks/
│   ├── 01_EDA.ipynb
│   ├── 02_preprocessing.ipynb
│   ├── 03_random_forest.ipynb
│   ├── 04_CNN.ipynb
│
├── src/
│   ├── feature_extraction.py
│   ├── model_rf.py
│   ├── model_cnn.py
│
├── results/
│   ├── confusion_matrix.png
│   ├── accuracy_results.txt
│
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

El objetivo del EDA es identificar patrones que permitan diferenciar voz real de voz sintética.

---

### 6.2 Preprocesamiento

Los archivos de audio se convierten en representaciones numéricas que puedan ser utilizadas por los modelos de aprendizaje automático.

Se utilizan técnicas como:

* normalización de audio
* conversión a espectrogramas Mel
* extracción de características acústicas

Características utilizadas:

* MFCC (Mel Frequency Cepstral Coefficients)
* espectrograma Mel
* zero crossing rate
* energía de la señal
* chroma features

---

### 6.3 Modelo Random Forest

Random Forest es un algoritmo de aprendizaje supervisado basado en múltiples árboles de decisión.

Cada árbol realiza una predicción y el resultado final se obtiene mediante votación.

Ventajas:

* buen desempeño en datasets estructurados
* robusto al overfitting
* fácil interpretación

El modelo se entrena utilizando las características acústicas extraídas del audio.

---

### 6.4 Modelo CNN

Las redes neuronales convolucionales (CNN) permiten analizar patrones en imágenes.

En este proyecto, los audios se convierten en espectrogramas, los cuales pueden interpretarse como imágenes que representan la frecuencia en función del tiempo.

La CNN permite detectar patrones característicos de voz sintética, tales como:

* irregularidades en frecuencias
* patrones repetitivos
* falta de variabilidad natural

Arquitectura general:

* capa convolucional
* función de activación ReLU
* capa de pooling
* capas densas
* función de activación sigmoid

---

### 6.5 Evaluación del modelo

Para evaluar el desempeño de los modelos se utilizan métricas de clasificación:

* accuracy
* precision
* recall
* F1-score
* matriz de confusión

Estas métricas permiten comparar cuál modelo detecta mejor la voz sintética.

---

## 7. Análisis exploratorio de datos (EDA)

Durante el análisis exploratorio se evaluaron las siguientes características:

### distribución de clases

Se verificó que el dataset contiene una cantidad balanceada de audios reales y sintéticos.

Esto es importante para evitar sesgos en el modelo.

---

### duración de audios

Se analizó la duración de las muestras de audio para verificar si existen diferencias entre voz real y sintética.

---

### visualización de señales

Se graficaron las ondas de audio para observar patrones en la amplitud.

---

### espectrogramas

Se generaron espectrogramas Mel para visualizar la distribución de frecuencias.

Estos espectrogramas sirven como entrada para la CNN.

---

## 8. Pasos para ejecutar el proyecto

### 1. instalar dependencias

```
pip install numpy pandas matplotlib librosa scikit-learn tensorflow
```

---

### 2. descargar dataset

descargar el dataset Fake-or-Real y ubicarlo en la carpeta:

```
dataset/
```

---

### 3. ejecutar análisis exploratorio

ejecutar:

```
01_EDA.ipynb
```

---

### 4. ejecutar preprocesamiento

```
02_preprocessing.ipynb
```

---

### 5. entrenar modelo Random Forest

```
03_random_forest.ipynb
```

---

### 6. entrenar modelo CNN

```
04_CNN.ipynb
```

---

## 9. Resultados esperados

Se espera que el modelo CNN obtenga mejor desempeño que Random Forest, debido a su capacidad de detectar patrones complejos en espectrogramas.

---

## 10. Aplicaciones

Este proyecto puede aplicarse en:

* detección de fraude
* autenticación biométrica
* prevención de ataques de ingeniería social
* sistemas de verificación de identidad
* análisis forense digital


