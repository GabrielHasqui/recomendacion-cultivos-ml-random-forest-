# Recomendación de cultivos con Random Forest

Proyecto de machine learning orientado a recomendar el cultivo más adecuado a partir de variables de suelo y clima: nitrógeno, fósforo, potasio, temperatura, humedad, pH y lluvia.

**Desarrollador:** Gabri

## Objetivo

Entrenar y evaluar un modelo `RandomForestClassifier` que reciba variables de suelo y clima para recomendar uno de los 22 cultivos disponibles en el dataset `Crop_recommendation.csv`.

## Dataset

Este proyecto utiliza el dataset **Crop Recommendation Dataset**, publicado en Kaggle por **Atharva Ingle**.

- Fuente: [Crop Recommendation Dataset - Kaggle](https://www.kaggle.com/datasets/atharvaingle/crop-recommendation-dataset)
- Autor: Atharva Ingle

El dataset fue construido a partir de datos de lluvia, clima y fertilizantes. Su propósito es facilitar el desarrollo de modelos predictivos para recomendar cultivos según condiciones de suelo y clima.

El archivo `dataset/Crop_recommendation.csv` se incluye en el repositorio para permitir la ejecución local del notebook sin depender de Google Drive ni descargas externas.

El dataset contiene 2200 registros, 8 columnas y 22 cultivos balanceados con 100 registros por clase. No presenta valores nulos ni registros duplicados.

Columnas:

- `N`: proporción de nitrógeno en el suelo
- `P`: proporción de fósforo en el suelo
- `K`: proporción de potasio en el suelo
- `temperature`: temperatura en grados Celsius
- `humidity`: humedad relativa en porcentaje
- `ph`: valor de pH del suelo
- `rainfall`: lluvia en milímetros
- `label`: cultivo recomendado

Cultivos incluidos:

```text
apple, banana, blackgram, chickpea, coconut, coffee, cotton, grapes,
jute, kidneybeans, lentil, maize, mango, mothbeans, mungbean, muskmelon,
orange, papaya, pigeonpeas, pomegranate, rice, watermelon
```

## Tecnologías usadas

- Python
- Pandas
- Scikit-learn
- Matplotlib
- Seaborn
- Jupyter Notebook

## Metodología

El desarrollo del modelo se realizó mediante las siguientes etapas:

1. Carga del dataset.
2. Revisión inicial de la estructura de datos.
3. Validación de valores nulos.
4. Separación de variables predictoras y variable objetivo.
5. División del dataset en entrenamiento y prueba: 80% para entrenamiento, 20% para prueba, `random_state=42` y estratificación por clase.
6. Entrenamiento del modelo Random Forest.
7. Evaluación mediante accuracy, reporte de clasificación y matriz de confusión.
8. Validación del modelo con un nuevo ejemplo de entrada.

## Ejecución

1. Crear un entorno virtual:

```bash
python -m venv .venv
```

2. Activar el entorno virtual en Windows:

```bash
.venv\Scripts\activate
```

3. Instalar dependencias:

```bash
pip install -r requirements.txt
```

Librerías principales incluidas en `requirements.txt`:

- `pandas==2.2.3`
- `scikit-learn==1.6.1`
- `matplotlib==3.10.0`
- `seaborn==0.13.2`
- `jupyter==1.1.1`

4. Abrir el notebook:

```bash
jupyter notebook Modelo_Recomendacion_Cultivos_RandomForest.ipynb
```

## Resultado del modelo

Con una división de 80% entrenamiento y 20% prueba, usando `random_state=42` y estratificación por clase, el modelo obtiene el siguiente resultado sobre el conjunto de prueba:

```text
Accuracy: 0.9955
```

El accuracy es una métrica válida en este caso porque el dataset está perfectamente balanceado, con 100 registros por cada cultivo, lo que evita que el rendimiento del modelo se vea favorecido por clases mayoritarias.

## Modelo utilizado

```python
RandomForestClassifier(n_estimators=100, random_state=42)
```

## Ejemplo de predicción

Para una muestra de entrada con valores de nitrógeno, fósforo, potasio, temperatura, humedad, pH y lluvia, el modelo genera una recomendación de cultivo:

```text
Entrada: N=91, P=21, K=26, temperatura=26.33377983, humedad=57.36469955, ph=7.261313694, lluvia=191.6549412
Cultivo recomendado: coffee
```
