Segmentación de Clientela (Clustering K-Means)
Este repositorio contiene un análisis de segmentación de clientes utilizando el algoritmo de agrupamiento no supervisado K-Means. El objetivo es identificar distintos grupos (clusters) de clientes basándose en sus características demográficas y de comportamiento financiero.

📝 Contenido del Notebook
El notebook está estructurado en las siguientes etapas principales:

1. Importación y Carga de Datos
Bibliotecas: Se importan las bibliotecas esenciales para el análisis: pandas, numpy, matplotlib.pyplot y seaborn para manipulación y visualización de datos, y sklearn para el preprocesamiento y el modelo de clustering.

Carga de Datos: El script está configurado para cargar un archivo Excel (BD_proyecto_DMC(grupal).xlsx) en un entorno de Google Colab.

2. Análisis Exploratorio de Datos (EDA)
Se realiza una revisión inicial de los datos para entender su estructura y distribución:

Resumen Estadístico: Uso de df.describe() para obtener estadísticas descriptivas de las variables numéricas.

Valores Nulos: Identificación de columnas con valores faltantes.

Visualización:

Histogramas para entender la distribución de las variables numéricas.

Gráficos de barras (countplots) para ver la frecuencia de las variables categóricas.

Matriz de correlación (heatmap) para identificar relaciones lineales entre variables.

Boxplots para detectar outliers en las características numéricas.

3. Preprocesamiento de Datos
Para preparar los datos para el modelo K-Means, se aplican varias transformaciones:

Selección de Variables: Se eliminan columnas que no son relevantes para el clustering (ej. "ID_CLIENTE").

Imputación de Nulos: Los valores nulos en las columnas numéricas se rellenan utilizando la media de cada columna.

Normalización: Las variables numéricas se escalan a un rango (generalmente 0 a 1) usando MinMaxScaler de Scikit-learn. Esto es crucial para K-Means, ya que es sensible a la escala de las características.

Codificación Categórica: Las variables categóricas (como "EST_CIVIL" y "F33_GRADO_INS_3") se convierten a formato numérico mediante One-Hot Encoding (pd.get_dummies).

Consolidación: Se crea un DataFrame final (df_procesado) que combina los datos numéricos normalizados y los categóricos codificados.

4. Modelo de Clustering (K-Means)
Determinación de K (Método del Codo): Se calcula la inercia (Suma de los cuadrados dentro de los clusters - WSS) y la varianza explicada para diferentes números de clusters (K=1 a K=8).

Visualización del Codo: Se genera un gráfico que muestra cómo la inercia disminuye y la varianza explicada aumenta a medida que K incrementa. El "codo" de la curva (en este análisis, K=3) se selecciona como el número óptimo de clusters.

Entrenamiento del Modelo: Se instancia y entrena el modelo KMeans final con n_clusters=3.

5. Análisis de Resultados
Asignación de Clusters: Se asigna cada cliente a uno de los 3 clusters identificados.

Interpretación de Clusters: Se genera un resumen comparativo de los clusters. Este resumen muestra:

La moda (valor más frecuente) para las características categóricas originales (ej. Estado Civil, Grado de Instrucción) de cada cluster.

La media de las características numéricas originales (ej. Edad, Ingreso) para cada cluster.

Visualización de Segmentos: Se prepara un resumen gráfico (utilizando un DataFrame "derretido" o melted) para facilitar la visualización de las diferencias entre los segmentos de clientes.
