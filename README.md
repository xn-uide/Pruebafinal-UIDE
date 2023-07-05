# Pruebafinal-UIDE
El proyecto final de la materia de Tratamiento de datos se basó en:
Redes neuronales convucionales (CNNs) con:

Capa convolucional: Esta es tal vez la capa más importante en visión artificial, y por eso las redes neuronales utilizadas heredan su nombre de ella: CNN por su acrónimo en inglés (convolutional neural network). Una capa de este tipo aplica un filtro o kernel a una región determinada de la imagen, siendo 3x3 o 5x5 píxeles los tamaños más usuales. Esto permite dos cosas:
En primer lugar, extraer características locales de la imagen, al estar relacionando píxeles cercanos. Pero además, según profundizamos en la red se va reduciendo el tamaño de la imagen que circula por ella, con lo cual capas más profundas van a relacionar píxeles que corresponden a secciones más alejadas en la imagen inicial. Esto significa que las primeras capas de la red van a extraer características generales como puede ser encontrar “bordes” en la imagen, mientras que capas más profundas se centran en objetos más grandes, como podría ser identificar los ojos o la nariz si tuviésemos un clasificador de perros y gatos, o encontrar formas circulares como puede tener un 3 o un 9 en el caso del dataset que hemos elegido.
En segundo lugar, estas capas tienen muy pocos parámetros (por ejemplo, en el caso de un filtro de 3x3 pixeles y una imagen RGB tendríamos 3x3x3=27 parámetros por filtro). Esto implica que podemos apilar un gran número de filtros de forma que cada uno extraiga distintas características de nuestras imágenes a un coste computacional muy bajo. Lo que buscaremos según profundicemos en la red es aumentar este número de filtros a la vez que reducimos el tamaño espacial, ya que así podemos extraer más características de la imagen sin incrementar demasiado el tiempo de entrenamiento.

Activation

Las funciones de activación no son específicas de las CNNs sino de cualquier tipo de red neuronal. Normalmente se aplican después de cada capa, y permiten tener elementos no lineales, que es lo que da a las redes neuronales su capacidad predictiva.

Pooling layers

El segundo elemento fundamental de estas redes son las capas de pooling, normalmente se utilizan dos: average pooling y max pooling, lo que hacen estas capas es, para un tamaño dado (por ejemplo, 2x2 píxeles) reducir cada región del input de ese tamaño a un único píxel con el valor medio/máximo. La principal utilidad es la de reducir el tamaño de la imagen según avanzamos en la red, ya que aunque las capas convolucionales ya lo reducen, normalmente queremos hacerlo más rápido y así reducir el número de operaciones.

Capas densas

Las dos capas anteriores son los building blocks de la parte de extracción de características de las imágenes, pero una vez hemos extraído esta información, hace falta otro tipo de capa que pese estas características y clasifique la imagen en nuestras clases. Estas son las capas densas. Las capas densas son las capas típicas de las redes neuronales, conectan todos los elementos del input (un vector) con todos los del output (otro vector), para lo cual necesitaremos “aplanar” la imagen que sale de nuestra última capa convolucional. Estas capas tienen muchos parámetros y permiten extraer mucha información, pero por esto mismo son muy costosas computacionalmente, por lo que conviene no abusar de ellas.

Para ello se necesitan los siguientes pasos:
Preparación del dataset, una vez descargado localmente se procede a apuntar al path especifico de training.
Construimos un modelo en base a las caracteristicas mencionadas en la parte superior.
Se entrena el modelo entre mas epoch mejor entrenado estará, pero este tomará más tiempo.
Se visualizan los datos y se generan imágenes para comprobar que se este entrenando de acuerdo a las categorias del dataset.
Se procede a validar los datos del train con el test para obtener resultados, en cuanto se valida se toma una imagen de muestra que puede estar en otra carpeta y se verifica la precisión del modelo entrenado.
Posteriormente se genera la matriz de confusión y así se puede tener mejores detalles de la eficiencia del modelo ya con datos de test.
