# Introducción

La interpretabilidad de un modelo es una característica necesaria para la mayoría de los algoritos de aprendizaje automático. Este tipo de algoritmos se denominan, generalmente, de *caja negra*. Esto se refiere a un sistema del que solo podemos observar las entradas y salidas, pero no su funcionamiento interno. La habilidad de la **interpretabilidad** puede ayudar a los usarios a explicar por qué el modelo hace estas predicciones.

## ¿Qué es el aprendizaje automático?

El aprendizaje automático es un conjunto de métodos que los ordenadores utilizan para hacer y mejorar predicciones o comportamientos basados en datos.

Existen dos tipos de aprendizaje automático: supervisado y no supervisado.

**Aprendizaje automático supervisado**: abarca los problemas de predicción en los que tenemos un conjunto de datos para el que ya conocemos el resultado de interés y queremos aprender a predecir el resultado para nuevos datos.

**Aprendizaje automático no supervisado**: tareas de agrupación en las que no tenemos un resultado específico de interés, sino que queremos encontrar agrupaciones de puntos de datos.

El objetivo del aprendizaje supervisado es aprendre un modelo predictivo que relacione las características de los datos con un resultado. Dependiendo del tipo de resultado de estudio se hablará de tarea de regresión (si el resultado es numérico) o de clasificación (si el resultado es categórico).

El algoritmo de aprendizaje automático aprende un modelo estimando parámetros (como pesos) o estructuras de aprendizaje (cmo árboles).

Pasos para resolver un problema de aprendizaje supervisado:

1. Recogida de datos (cuantos más, mejor). Los datos deben contener el resultado que se quiere predecir e información adicional a partir de la cual realizar la predicción.
2. Introducir esta información en un modelo de aprendizaje automático.
3. Utilizar el modelo con nuevos datos. Integrar el modelo en un producto o proceso.

La máquinas superna a los humanos en muchas tareas, como jugar al ajedrez o predecir el tiempo. Incluso si la máquina es tan buena como un humano o un poco peor en una tarea, sigue habiendo grandes ventajas en términos de velocidad, reproducibilidad y escalabilidad. Replicar un modleo de aprendizaje automático en otra máquina es rápido y barato, mientras que el entrenamiento de un humano puede llevar décadas y es costoso.

Por otro lado, una gran desventaja de usar el aprendizaje automático es que la información sobre los datos y la tarea que resuelve la máquina queda oculta en modleos cada vez más complejos. Por ejemplo, se necesitan millones de números para describir una red neuronal profunda, y no hay forma de entender el modelo en su totalidad. Asimismo, los modelos con mejores resultados suelen ser mezclas de varios modelos (*conjuntos*) que no pueden interpretarse. Si nos centramos sólamente en el rendimiento, obtendreos automáticamente modelos cada vez más opacos. 

## Terminología

**Algoritmo**: conjunto de reglas que sigue una máquina para alcanzar un objetivo concreto.

**Aprendizaje automático**: conjunto de métodos que permiten a los ordenadores aprender de los datos para hacer y mejorar predicciones. El aprendizaje automático supone un cambio de paradigma, se pasa de la *programación normal*, en la que tdas las instrucciones deben darse explícitamente al ordenador, a la *programación indirecta*, que tiene lugar mediante el suministro de datos.

**Algoritmo de aprendizaje automático**: el programa utilizado para aprender un modelo de aprendizaje automático a partir de datos.

**Modelo de aprendizaje automático**: el programa aprendido que asigna entradas a las predicciones. Puede ser un conjunto de pesos para un modelo lineal o para un ared neuronal. Otros nombres podrían ser *clasificador* o *modelo de regresión*. En las fórmulas, el modelo de aprendizaje automático entrenado se denomina $\hat{f}$ o bien $\hat{f}(x)$.

**Modelo de caja negra**: es un sistema que no revela sus mecanismos internos. En el aprendizaje automático, *caja negra* describe los modelos que no pueden entenderse observando sus parámetros (por ejemplo, una reD neuronal). Lo contrario de una caja negra lo denminaremos *modelo interpretable*.

Nota: Los métodos agnósticos de models interpretables tratan los modelos de aprendizaje autmático como cajas negras, aunque no lo sean.

**Aprendizaje automático interpretable**: se refiere a los métodos y modelos que hacen que el comportamiento y las predicciones de los sistemas de aprendizaje automático sean comprensibles para los humanos.

**Conjunto de datos (Dataset)**: tabla con los datos a partir de los cuales aprende la máquina. Contiene las variables y el objetivo a predecir. Cuando se utiliza para inducir un modelo, el conjunto de datos de denomina *datos de entrenamiento*.

**Individuo/instancia**: 

**Variables/características**:

**Target/objetivo**:

**Tarea de aprendizaje automático**:

**Predicción**:

# Interpretabilidad


