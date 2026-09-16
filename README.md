# Análisis de la satisfacción del cliente a partir de reseñas

Trabajo Fin de Máster · Máster en Data Science, Big Data & Business Analytics · UCM

Estudio de los factores que explican la satisfacción del cliente en distintas
industrias, a partir de 200.000 reseñas en español del *Multilingual Amazon
Reviews Corpus*, y herramienta de diagnóstico que aplica el modelo entrenado
a cualquier conjunto de reseñas.

## Contenido del repositorio

| Archivo | Descripción |
|---|---|
| `TFM_notebook.ipynb` | Análisis completo: carga, exploración, análisis de aspectos por industria, modelado, evaluación e interpretabilidad |
| `TFM_notebook.html` | El mismo notebook ejecutado, en formato HTML (anexo de código) |
| `herramienta.html` | Herramienta de diagnóstico. Se abre en el navegador |
| `modelo_web.json` | Vocabulario, pesos IDF y coeficientes del modelo, exportados para la herramienta |
| `modelo.pkl` / `vectorizador.pkl` | Modelo y vectorizador serializados (scikit-learn) |
| `ficha_modelo.json` | Metadatos del entrenamiento: fecha, parámetros y métricas |
| `muestra_resenas.csv` | Muestra de 3.000 reseñas para probar la herramienta |

## Resultados

| Métrica | Valor |
|---|---|
| Exactitud (test) | 0,861 |
| F1 (test) | 0,832 |
| AUC | 0,932 |
| Reseñas de entrenamiento | 160.000 |
| Reseñas de test | 40.000 |

## La herramienta

Abre `herramienta.html`, carga un CSV de reseñas y devuelve el porcentaje de
clientes satisfechos, los aspectos que concentran la satisfacción y el descontento,
y la comparación entre industrias.

No necesita servidor ni instalación: la predicción se ejecuta en el propio
navegador a partir de `modelo_web.json`, que contiene el vocabulario y los
coeficientes del modelo entrenado en el notebook. El apartado *Verificación del
modelo* de la propia página comprueba que las puntuaciones coinciden con las que
produce scikit-learn en Python sobre una muestra de control.

## Reproducibilidad

Semilla fija (`SEMILLA = 42`) en la partición de datos y en todos los muestreos.
Los datos proceden del *Multilingual Amazon Reviews Corpus* (Keung et al., EMNLP 2020),
de acceso público para uso de investigación y anonimizado en origen.

## Datos

El corpus no se incluye en este repositorio. Puede descargarse desde su fuente
original; el notebook espera el archivo `train.jsonl.gz` en la carpeta de trabajo.
