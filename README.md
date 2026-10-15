Archivo: train.csv (1.460 registros, 81 columnas).
Objetivo supervisado: SalePrice (valor continuo).
Identificador: Id (se excluye de las variables predictoras).
Segmentación: se realiza sin usar SalePrice como variable de agrupación; el precio se utiliza después para describir los segmentos.
Limitación: son datos históricos de viviendas; no constituyen tasaciones actuales ni resultados generalizables sin nueva validación.
machine-learning-viviendas/

├── README.md                  # Instrucciones y metodología
├── requirements.txt           # Dependencias y versiones
├── Untitled9.ipynb            # Notebook principal
├── data/
│   └── train.csv              # Opcional: solo si está permitido redistribuirlo
├── resultados/                # Se genera al ejecutar el notebook
│   ├── eda.png
│   ├── modelo_rf_optimizado.joblib
│   ├── versiones.txt
│   └── README.md
└── .gitignore                 # Exclusiones de Git

Abrir Untitled9.ipynb en Google Colab.
En el panel Archivos de Colab, subir el archivo CSV y verificar que su ruta sea /content/train.csv.
Ejecutar las celdas en orden, desde la instalación de dependencias hasta los gráficos finales.
Consultar los resultados en la carpeta /content/resultados/. Descargarla antes de cerrar el entorno, porque el almacenamiento temporal de Colab puede eliminarse al reiniciar la sesión.
Para este proyecto debe prevalecer la ruta real /content/train.csv indicada aquí. Conviene corregir ese texto dentro de la celda 14 si se vuelve a ejecutar.

import sys, numpy, pandas, scipy, sklearn, matplotlib, seaborn, joblib
print('Python:', sys.version)
for paquete in (numpy, pandas, scipy, sklearn, matplotlib, seaborn, joblib):
    print(paquete.__name__, paquete.__version__)

EDA: descripción de SalePrice, detección de valores faltantes y análisis de valores extremos.
Separación de datos: entrenamiento 80 % y prueba 20 %, con random_state=42.
Preprocesamiento: imputación numérica por mediana, imputación categórica, One-Hot Encoding y escalamiento cuando corresponde. Para modelos supervisados se ajusta dentro de pipelines con los datos de entrenamiento.
Modelos supervisados: Lasso, Ridge, Elastic Net, regresión lineal, MLP y Random Forest.
Reducción de dimensionalidad: PCA, comparando resultados con y sin transformación.
Segmentación: K-Means y DBSCAN.
Evaluación: MAE, RMSE y R² para regresión; Silhouette, Calinski-Harabasz y Davies-Bouldin para clustering.
Optimización: búsqueda de hiperparámetros de Random Forest mediante validación cruzada.
Comunicación: gráficos de EDA, comparación de modelos, perfiles de segmentos y precio real versus estimado.

Mantener la semilla 42 donde corresponda.
Guardar el CSV original sin modificaciones y documentar su procedencia.
Registrar versiones de Python y librerías.
Usar Git para guardar cambios con mensajes descriptivos.
Registrar los hiperparámetros y métricas de cada experimento.
No utilizar los datos de prueba para seleccionar hiperparámetros.
Evitar publicar credenciales, datos personales o conjuntos sin permiso de redistribución.

