Análisis No Supervisado – K-Means Clustering

Integrantes: Eduardo Molina, Diego Martínez

 Docente: Matías Arriola
 
 Sección: 001D

1. Descripción de la técnica utilizada y justificación de su elección
La técnica empleada en este análisis es K-Means Clustering, un algoritmo de aprendizaje no supervisado cuyo objetivo es agrupar observaciones según su similitud, particionando el conjunto de datos en k clusters. El algoritmo busca minimizar la distancia intra-cluster y maximizar la separación entre clusters.
Justificación de la elección

K-Means es un método eficiente y ampliamente utilizado para tareas de segmentación de clientes.


Permite identificar patrones y subpoblaciones dentro del dataset sin necesidad de utilizar etiquetas durante el entrenamiento.


Es adecuado para datasets con un número moderado de variables numéricas, como los datos crediticios utilizados en este proyecto.


Facilita la interpretación de perfiles de riesgo, al agrupar clientes con características socioeconómicas y comportamientos similares.


Su simplicidad lo convierte en un primer enfoque apropiado para explorar la estructura latente del dataset antes de aplicar modelos más complejos.


Importante: La variable TARGET no se utiliza para entrenar el modelo K-Means. Esta se emplea únicamente de forma posterior para interpretar el nivel de riesgo asociado a cada cluster, evitando así data leakage.

2. Instrucciones de ejecución del código
Requisitos
Python 3.x


Librerías necesarias:


pip install pandas numpy scikit-learn matplotlib seaborn

Ejecución
Abrir el notebook EVA3.ipynb en un entorno compatible (Jupyter Notebook, JupyterLab, VSCode o Google Colab).


Verificar que los archivos de datos estén disponibles en la ruta configurada en el notebook.


Ejecutar todas las celdas en orden.


El notebook incluye:
Importación de librerías.


Carga y preparación del dataset.


División explícita del conjunto de datos en train / validation / test, con el fin de prevenir data leakage.


Estandarización de variables numéricas.


Selección del número óptimo de clusters mediante el método del codo (y métricas complementarias).


Entrenamiento del modelo K-Means utilizando solo el conjunto de entrenamiento.

Análisis de perfiles por cluster.

Visualización de clusters en dos dimensiones mediante PCA.


3. Análisis e interpretación de resultados
Los resultados del clustering muestran diferencias claras entre los grupos formados, especialmente en variables relacionadas con ingresos, edad, estabilidad laboral y comportamiento crediticio.
Se identifican clusters con características asociadas a mayor riesgo crediticio, evidenciado por una mayor proporción de clientes con TARGET = 1.


Otros clusters agrupan clientes con mejores condiciones socioeconómicas y una menor tasa de TARGET positivo, lo que sugiere un perfil de menor riesgo.


La visualización mediante PCA permite observar una separación razonable entre los clusters, lo que indica que el algoritmo logró capturar una estructura diferenciable en los datos.


En conjunto, el modelo permite segmentar la población de clientes en perfiles con comportamientos distintos, aportando valor analítico al entendimiento del riesgo.

4. Discusión sobre la aplicabilidad al proyecto final supervisado
El método de clustering sí puede incorporarse al proyecto final de scoring crediticio, pero como complemento y no como reemplazo del modelo supervisado.
Razones a favor
El identificador de cluster (cluster_id) puede incorporarse como una variable adicional en el modelo supervisado.


Permite identificar segmentos específicos de riesgo, útiles para políticas crediticias diferenciadas.


Aporta valor en la etapa de exploración y entendimiento del dataset.


Limitaciones y consideraciones
K-Means asume clusters de forma aproximadamente esférica, lo que puede no representar completamente la estructura real de los datos.


Es sensible a outliers y a la escala de las variables, por lo que requiere un preprocesamiento adecuado.


Para su uso en producción, se recomienda validar la estabilidad de los clusters, por ejemplo mediante métricas como Silhouette Score o Davies-Bouldin, y compararlo con otros métodos de clustering.


Validación recomendada
Para evaluar su aporte real, se sugiere entrenar el modelo supervisado:
con y sin la variable cluster_id,


comparando métricas como AUC, recall y estabilidad en validación y prueba.


Si no se observa mejora, el clustering puede mantenerse como herramienta de segmentación y análisis, sin incorporarse directamente al modelo productivo.

Conclusión
El uso de K-Means Clustering permite identificar perfiles diferenciados de clientes y aporta información valiosa para el análisis del riesgo crediticio. Su aplicación es recomendable como herramienta complementaria, apoyando el modelo supervisado y enriqueciendo el entendimiento del comportamiento de los clientes, sin sustituir el enfoque principal de scoring
