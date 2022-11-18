# Proyecto_final_IA
Over a wine dataset and several ML models is selected the best one.

# Informe final Proyecto final de IA
 _Sebastian De Valdenebro_



### Introducción
El presente proyecto tiene la intención de implementar una solución a una problemática encontrada a traves de un dataset dentro del sitio web Kaggle.com, haciendo uso de los conocimientos adquiridos en el curso durante todo el semestre, la problemática encontrada es la siguiente: " El vino es un producto muy deseado por la mayoría de la población, sin embargo encontrar un buen vino dentro de la gran variedad existente hoy en día, para cada consumidor es un dilema". Por esto se propone implementar un modelo de aprendizaje de máquina de tipo supervisado el cuál clasificará de la mejór manera los vinos en relación a su calidad, dadas las siguientes características: " 'fixed acidity', 'volatile acidity', 'citric acid', 'residual sugar','chlorides', 'free sulfur dioxide', 'total sulfur dioxide', 'density','pH', 'sulphates', 'alcohol' "

### Desarrollo
El primer paso fue la selección del datset, este proceso se realizo con el asesoramiento del profesor con el fin de que este fuera el adecuado para el desarrollo del proyecto, acto seguido se definió el problema y de que manera se podría abordar haciendo uso del Machine learning y de las herramientas aprendidas en el transcurso del semestre.

El segundo paso que se llevó a cabo fue el pre procesamiento del dataset, en ese momento importó el dataset en Colab y se visualizó por primera vez, se hizo uso de las funciones ".isnull.sum" y ".isna.sum" con el fin de encontrar algún valor null o NAN dentro de nuestro dataset para arreglarlo con cualquiera de los métodos aprendidos, sinembargo en este dataset no se presento ningún elemento de este tipo, a demás ningun dato era del tipo categorico por lo que se procedió a separar el dataset en conjunto X y conjunto Y.

Antes de proseguir se decidió hacer una matriz de correlación con el objetivo de visualizar como las carácterísticas del dataset estaban correlacionadas con la etiqueta("quality").

Acto siguente se separó el dataset en conjunto de características (X) de prueba y entrenamiento y conjunto de etiquetas (y) de prueba y entrenamiento, despues de una revisión preliminar en una clase del progreso del proyecto, el profesor sugirió tomar solo el 15% de los datos del dataset como conjunto de prueba debido al tamaño del dataset (1600 filas por 12 columnas). Después de haber definido estos parámetros se procedió a normalizar el conjunto de características de prueba y de entrenamiento haciendo uso de la función ("StandardScaler").

Dados los resutltados preliminares revisados mediante la matriz de correlación se penso que sería posible hacer uso de PCA y aplicar reducción dimensional para obtener un mejor desempeño del dataset, de esta manera se procedió a hacer reducción de una columna, dejando a los demás conjuntos representando un peso total del 99% del dataset, esto parecia tener sentido y se encontraba dentro de los valores permitidos discutidos en clase, sinembargo al momento de implementar este conjunto reducido en un modelo de regresión logistica, se encontraron resultados desfavorecedores en el desempeño del modelo en comparació con los encontrados haciendo uso del dataset completo, al discutir este fenomeno con el profesor, se encontró que esto se debía al dataset y el hecho de que no todas los posibles valores que podía tomar la etiqueta estaban definidos en el, por consiguiente se descartó el uso de PCA en futuras pruebas con los demás modelos a implementar.

Selección de los modelos a entrenar para determinar cual tiene mejór métrica de evaluación:
Las métricas seleccionadas para trabajar fueron: Coeficiente de correlación de Mathews (la mas relevante), F1 - Score.

Modelos: Logistic Regression, SVM, ANN, Random Forest Classifier, Decision tree y KNN.

Con el fin de hacer el proceso de optimización de cada modelo algo automátizado, se procedió a hacer uso de una función llamada "GridSearchCV" en la cual a demas de iterar los hiperparametros definidos para cada modelo, realiza una cross-Validation de 5 folds, los hiperparametros iterados con esta función por cada modelo fueron los siguientes:

Logistic Regresion: penalty, solver.
SVM: kernel, C, degree. 
ANN:learning_rate, solver, alpha, hidden_layers_sizes, random_state, activation, max_iter.
Random Forest:n_estimators, max_features, max_depth, criterion.
Decision tree: max_depth.
KNN:N_neighbours , weights, n_jobs.

Para cada modelo se realizó a parte una cross validation con el fin de observar como sería su desempeño con todo el dataset.

### Resultado
Despues de realizar las pruebas y observar los indicadores de cada modelo, se seleccionaron los mejores de cada modelo y se compararon sus resultados mediante gráficos para hacer el entendimiento de estos mucho más cómodo, los resultados se muestran a continuación:
![image](https://user-images.githubusercontent.com/104800190/202602833-6187c9d3-04fe-46dc-a47f-4773c2dfd343.png)
<img width="361" alt="image" src="https://user-images.githubusercontent.com/104800190/202602918-d9c4e0a7-cbda-47f9-a7ff-78e2e7b06a4a.png">
<img width="360" alt="image" src="https://user-images.githubusercontent.com/104800190/202602959-8b5382fd-13ef-41ee-8adf-b60856cb8179.png">

Como se puede apreciar, el modelo con mejor desempeño en todas las metricas es el de decision tree, por lo que este fue el modelo seleccionado, a continuación se muestran los resultados del modelo con todo el dataset:

<img width="253" alt="image" src="https://user-images.githubusercontent.com/104800190/202603229-146dacfd-742a-4161-bdca-08ab69e7f58e.png">
<img width="329" alt="image" src="https://user-images.githubusercontent.com/104800190/202603483-e3779e81-2c4a-4774-b23b-7705f3b2c96a.png">
<img width="329" alt="image" src="https://user-images.githubusercontent.com/104800190/202603533-0cbb08e5-c395-4c79-bace-a9cb5d8a4661.png">


### Colclusiones

Se ha demostrado que el mejor desempeño para este dataset es el del modelo Random Forest, las herramientas vistas en este curso fueron fundamentales para la correcta realización de este proyecto y afrontar sus dificultades, se recomienda para el futuro visualizar el rango de la etiqueta como malo, bueno y excelente, esto podría mejorar los scores y facilitarle el trabajo a los modelos empleados.

### GitHub
https://github.com/SDV244/Proyecto_final_IA
### Link Video
https://youtu.be/3DO3CEeZtgo
