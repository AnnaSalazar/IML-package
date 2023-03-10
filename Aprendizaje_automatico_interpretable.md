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

**Individuo/instancia**: una fila del conjunto de datos. Un individuo consiste en las variables explicativas $x^{(i)}$ y, si es conocida, su variable respuesta u objetivo $y_i$.

**Variables explicativas (Features)**: las entradas utilizadas para la predicción/clasificación. Una variable es una columna del conjunto de datos. Se supone que las variables sn interpretables, es decir, que es fácil entender lo que significan. La matriz de las variables se denomina $X$ y $x^{(i)}$ para un único individuo. El vector de una única variable para todos los individuos es $x_j$, y el valor para una variable $j$ y un individuo $i$ es $x^{(i)}_j$.

**Target/objetivo**: la información que la máquina aprende a predecir: $y$ o $y_i$, para un único individuo.

**Tarea de aprendizaje automático**: La combinación de un conjunto de datos con variables explicativas y objetivo. Dependiendo del objetivo la tarea puede ser, por ejemplo, clasificación, regresión, análisis de supervivencia, agrupación o detección de valores atípicos.

**Predicción**: aquello que el modelo de aprendizaje automático *adivina* sobre cuál debería ser el valor objetivo basándose en las variables explicativas. Se denomina $\hat{f}(x^{(i)})$ o $\hat{y}$.

# Interpretabilidad

Es difícil definir (matemáticamente) la interpretabilidad. Una definición (no matemática) podría ser: el grado en que un humano puede entender la causa de una decisión, Miller (2017). Cuanto mayor sea la interpretabilidad de un modelo de parendizaje automático, más fácil será para alguien comprender por qué se han tomado ciertas decisiones o se han hecho xiertas predicciones.

Un modelo es más interpretable que otro si sus decisiones son más fáciles de comprender para un ser humano que las decisiones del otro modelo.

El aprendizaje automático interpretable es un término general útil que abarca la "extracción de conocimientos relevantes de un modelo de aprendizaje automático sobre las relaciones contenidas en los datos o aprendidas por el modelo".

## La importancia de la interpretabilidad

Si un modelo de aprendizaje automático funciona bien, ¿por qué no nos limitamos a confiar en él e ignoramos por qué ha tomado una determinada decisión? $\rightarrow$ El problema es que una sola métrica, como la precisión de la clasificación, es una descripción incompleta de la mayoría de las tareas del mundo real. (Doshi-Velez y Kim 2017)

Cuando se trata de un modelo predictivo, ¿únicamente queremos saber el valor que se predice? ¿O queremos saber por qué se hizo la predicción y, posiblemente, pagar la interpretabilidad con una caída del rendimiento predictivo? En algunos casos, no importa por qué se tomó una decisión, basta con saber que el rendimiento predictivo en un conjunto de datos fue bueno. Pero en otros casos, saber el "por qué" puede ayudar a conocer mejor el problema, los datos y la razón por la que un moelo puede fallar. La necesidad de interpretabilidad surge de una incompletitud en la formalización del problema, lo que significa que para ciertos problemas o tareas no basta con obtener la predicción, sino que el modelo también debe explicar como se llego a ella, porque una predicción correcta solo resuelve parcialmente su problema original.

**La curiosidad humana y el aprendizaje**

Los seres humanos tenemos un modelo mental de nuestro entorno hasta que se actualiza cuando ocurre algo inesperado. Esta actualización se realiza buscando una explicación para este suceso inesperado. Cuando se utilizan modelos opacos de aprendizaje automático en la investigación, los hallazgos científicos quedan completamente ocultos si el modelo sólo ofrece predicciones sin explicaciones. Para facilitar el aprendizaje y satisfacer la curiosidad de por qué las máquinas crean determinadas predicciones o comportamientos, la interpretabilidad y las explicaciones son cruciales.

Estrechamente relacionado con el aprendizaje está el deseo humano de encontrar sentido al mundo. Queremos armonizar contradicciones o incoherencias entre elementos de nuestras estructuras de conocimiento. Cuanto más afecta la decisión de una máquina a la vida de una persona, más importante es que la máquina explique su comportamiento. Por ejemplo, si un modelo de aprendizaje rechaza una solicitud de préstamo, esto puede ser completamente inesperado para los solicitantes, que sólo podrán conciliar esta incoherencia entre expectativas y realidad mediante algún tipo de explicación. En realidad, las explicaciones no tienen que explicar completamente la situación, pero deben abordar una causa principal.

Muchas disciplinas científicas están pasando de los métodos cualitativos a los cuantitativos, y también hacia el aprendizaje automático. El objetivo de la ciencia es adquirir conocimientos, pero muchos problemas se resuelven con grandes cantidades de datos y modelos de aprendizaje automático de caja negra. El propio modelo se convierte en la fuente de conocimiento en lugar de los datos, y la interpretabilidad permite extraer este conocimiento adicional captado por el modelo.

Por defecto, los modelos de aprendizaje automático adquieren sesgos de los datos de entrenamiento. Esto puede convertir los modelos en "racistas" que discriminen a los grupos infrarrepresentados. La interpretabilidad es una herramienta de depuración útil para detectar sesgos en los modelos de aprendizaje automático. Si se detectan estos sesgos, se pueden añadir nuevas restricciones en el modelo para evitarlos y, con ello, optimizar el modelo.

El proceso de integración de máquinas y algoritmos en nuestra vida cotidiana requiere interpretabilidad para aumentar la aceptación social. La gente atribuye a los objetos creencias, deseos, intenciones, etc. Una máquina o algoritmo que explique sus predicciones tendrá más aceptación. La explicaciones sirven para gestionar las interacciones sociales. Al crear un significado compartido de algo, el emisor influye en las acciones, emociones y creencias del receptor. Para que una máquina interactúe con nosotros, puede necesitar moldear nuestras emociones y creencias. La máquinas tienen que "persuadirnos" para alcanzar su objetivo. Curiosamente, puede haber un desajuste entre lo que la máquina explica (crear confianza) y el objetivo del receptor (entender la predicción o el comportamiento).

Los modelos de aprendizaje automático sólo pueden depurarse y auditarse cuando pueden interpretarse. Incluso en entornos de bajo riesgo, como las recomendaciones de películas, la capacidad de interpretación es valiosa en la fase de investigación y desarrollo, así como después de la implantación. La interpretación de una predicción errónea ayuda a comprender la causa del error. Aporta una orientación sobre cómo arreglar el problema.

Si puede asegurarse que el modleo puede explicar las decisiones, también puede comprobar los siguientes rasgos más fácilmente:
- Imparcialidad: garantizar que las predicciones no discriminan implícita o explícitamente a los grupos infrarrepresentados. 
- Privacidad: asegurar la protección de la información sensible contenida en los datos.
- Fiabilidad o robustez: comprobar que los pequeños cambios en los datos de entrada no provoquen grandes cambios en la predicción.
- Causalidad: cerciorarse de que sólo se detectan las relaciones causales.
- Confianza: a los humanos les resulta más fácil confiar en un sistema que explica sus decisiones que en una caja negra.


**¿Cuándo no necesitamos la interpretabilidad?**

La interpretabilidad no es necesaria si el modelo no tiene un impacto significativo. En cuanto el modelo tiene un impacto significativo, ya sea financiero o social, la interpretabilidad adquiere relevancia.

Tampoco es necesaria cuando el modelo está bien estudiado. Algunas aplicaciones han sido lo suficientemente bien estudiadas como para que haya suficiente experiencia práctica con el mdelo y sus problemas se hayan resuelto con el tiempo.

La interpretabilidad puede permitir que personas o programas manipulen el sistema. Los problmas con usuarios que engañan a un sistema se derivan de un desajuste entre los bjetivos dl creador y el usuario de un modelo. Solo se puede engañar al sistema si las entradas son aproximaciones a una característica causal, pero no causan realmente el resultado. Siempre que sea posible, deben evitarse las características indirectas, ya que hacen que los modelos sean manipulables.

## Taxonomía de los métodos de interpretabilidad

Los métodos de interpretabilidad del aprendizaje automático pueden clasificarse según varios criterios.

1. ¿Intrínseca o post hoc?

Este criterio distingue si la interpretabilidad se consigue restringiendo la complejidad del modelo (intrínseca) o aplicando métodos que analizan el modelo después del entrenamiento (post hoc).

- **Intrínseca**: Se refiere a modelos que se consideran interpretables debido a su estructura simple, como los árboles de decisión cortos o los modelos lineales dispersos.
- **Post hoc**: Se refiere a la aplicación de métodos de interpretación tras el entrenamiento del modelo.

*Nota*: Los métodos post hoc también pueden aplicarse en modelos intrínsecamente interpretables. Por ejemplo, la permutación de la importancia de los rasgos puede calcularse para árboles de decisión.

2. Resultado del método de interpretación

Los distintos métodos de interpretación pueden diferenciarse a grandes rasgos en función de sus resultados.

- Estadísticos de resumen de las variables: muchos métodos de interpretación proporcionan estadísticos para cada atributo. Algunos devuelven un único resultado, como la importancia de la variable, mientras que otros dan resultados más complejos, como las fuerzas de interacción entre variables por pares.
- Visualización del resumen de las variables: La mayoría de los resúmenes estadísticos de las variables también pueden visualizarse. Por ejemplo, los gráficos de independencia parcial, que son curvas que muestran una característica y el resultado medio previsto.
- Datos internos del modelo (por ejemplo, los pesos): la interpretación de modelos intrínsecos entra en esta categoría. En los modleos lineales, por ejemplo, los límites entre los datos internos del modelo y los estadísticos de resumen de las variables son difusos, ya que los pesos son a la vez datos internos del modelo y estadísticos de resumen de las variables.
- Punto de datos: esta categoría incluye todos los métodos que devuelven puntos de datos (ya existentes o de nueva creación) para hacer interpretable un modelo. Uno de los métodos se denomina *explicaciones contrafactuales*. Para explicar la predicción de una instancia de datos, el método encuentra un punto de dats similar cambiando algunas variables para las que el resultado predicho cambia de forma relevante. Para ser útiles, los métodos de interpretación que producen nuevos puntos de datos requieren que los propios puntos de datos puedan interpretarse (funciona bien para imágenes y texto, pero es menos útil para datos tabulares con cientos de variables).
- Modelos intrínsecamente interpretables: una solución para interpretar los modelos de caja negra es aproximarlos con un modelo interpretable. El modelo interpretable en si se entiende observando los parámetros interns del modelo o los estadísticos de resumen de las variables.

3. ¿Modelo específico o agnóstico?

La herramientas de interpretación específicas de un modelo se limitan a clases cncretas de modelos, mientras que las herramientas agnósticas al modelo pueden utilizarse en cualquier modelo de aprendizaje automático, y se aplican después de haber entrenado el modelo (post hoc). Por definición, estos métodos no pueden acceder a la información interna del modleo, como los pesos o la información estructural.

4. ¿Local o global?

¿El método de interpretación explica una predicción individual o todo el comportamiento del modelo? ¿O tiene un alcance intermedio?

## Alcance de la interpretabilidad

Un algoritmo entrena un modelo que produce predicciones. Cada paso puede evaluarse en términos de transparencia o interpretabilidad.

### Transparencia del algoritmo

La transparencia del algoritmo se refiere a cómo aprende un modelo a partir de los datos y qué tipo de relaciones puede aprender. En el caso de la redes convolucionales para interpretar imágenes, se puede explicar que el algoritmo aprende detectores de bordes y filtros en las capas más bajas. Así se entiende cómo funciona el algoritmo, pero no el modelo concreto que se aprende al final ni como se hacen las predicciones individuales. La transparencia del algoritmo solo requiere el conocimiento del algoritmo y no de los adtos o del modelo aprendido.

### Interpretabilidad global y holística del modelo

Se puede decir que un modleo es interpretable cuando se puede comprender todo el modelo a la vez. Para explicar el resultado global del modelo se necesita: el modelo entrenado, el conocimiento del algoritmo y los datos. Este nivel de interpretabilidad consiste en comprender cómo toma decisiones el modelo, basándose en una visión holística de sus variables y de cada uno de los componentes aprendidos, como pesos, otros parámetros y estructuras.

La interpretabilidad global del modelo ayuda a comprender la distribución del resultado deseado en función de sus características. Es muy difícil de conseguir en la práctica, ya que cualquier modelo que supere un puñado de parámetros o ponderaciones es poco probable que quepa en la memoria a corto plazo del ser humano medio.

### Interpretabilidad global del modelo a nivel modular

Un modelo Naive Bayes con muchos cientos de características sería demasiado grande para que un humano lo guarde en su memoria de trabajo, pero en cambio, un humano puede enterder una sola ponderación. Aunque la interpretabilidad global de un modelo suele estar fuera de nuestro alcance, hay muchas posibilidades de entender al menos alguns modelos a nivel modeluar (de parámetros). En el caso de los modelos lineales, las partes interpretables son las ponderaciones, en el caso de los árboles serían las divisiones y las predicciones de los nodos hoja.

Los modelos lineales, por ejemplo, parece como si pudieran interpretarse perfectamente a nivel modular, pero la interpretación de un solo peso está enlazada con todos los demás, ya que viene dada bajo la condición de que las demás variables de entrada se mantengan con el mismo valor, cosa que no ocurre en muchas aplicaciones reales. Aun así, las ponderaciones de un modelo lineal pueden interpretarse mejor que, por ejemplo, las de una red neuronal profunda.

### Interpretabilidad local de una única predicción

Es posible acercarse a un cas concreto y examinar lo que el modelo predice para esa entrada y explicar el por qué. Localmente, la predicción podría depender sólo lineal o monotónicamente de algunas variables, en lugar de tener una dependencia compleja entre ellas. Por tanto, las explicaciones locales puedes ser más precisas que las globales.

### Interpretabilidad local de un grupo de predicciones

La predicciones del modelo para varias instancias pueden explicarse con métodos globales de interpretación del modelo (a nivel modular) o con explicaciones de instancias individuales.

1. Los métodos globales pueden aplicarse tomando el grupo de instancias, tratándolas como si el grupo fuera el conjunto de datos completo y utilizando los métodos globales en este subconjunto. 
2. Los métodos de explicación individual pueden utilizarse en cada instancia y luego enumerarse o agregarse para todo el grupo.


## Evaluación de la interpretabilidad

No existe un conseso real sobre qué es la interpretabilidad en el aprendizaje automático. Tampoco está claro como medirla.

Doshi-Velez y Kim (2017) proponen 3 niveles principales para la evaluación de la interpretabilidad:

1. Evaluación a nivel de aplicación real

Poner la explicación en el producto y que lo pruebe el usuario final. Esto requiere una buena configuración experimental y una comprensión de cómo evaluar la calidad. Un buen punto de referencia para ello es siempre cómo de bueno sería un humano explicando la misma decisión.

2. Evaluación a nivel humano

La diferencia diferencia es que estos experimentos no se realizan con los expertos del dominio, sino con particulares. Esto hace que los experimentos sean más baratos y sea más fácil encontrar probadores.

3. Evaluación a nivel de función

Funciona mejor cuando la clase de modelo utilizada ya ha sido evaluada por otra persona en una evaluación a nivel humano. Por ejemplo, una evaluación a nivel de función de un árbol de decisión puede basarse en la profundidad del árbol. Los árboles más cortos obtendrían una mejor puntación de explicabilidad. Tendría sentido añadir esta restricción de que rendimiento predictivo del árbol siga siendo bueno y no disminuya demasiado en comparación con un árbol grande.


## Propiedades de las explicaciones

Se quiere explicar las predicciones de un modelo de aprendizaje automático. (Método de explicación: algoritmo que genera explicacines)

Una explicación suele relacionar los valores de las variables de un individuo con la predicción de su modelo de una forma humanamente comprensible.

Propiedades de los métodos de explicación y las explicaciones (Robnik-Sikonja y Bohanec, 2018). Estas propiedades pueden utilizarse para juzgar lo bueno que es un modelo de explicación o una explicación.

### Propiedades de los métodos de explicación

- **Poder expresivo**: el "lenguaje" o la extructura de las explicaciones que el método es capaz de generar.
- **Translucidez**: describe hasta qué punto el método de explicación se basa en mirar dentro del modelo, como en sus parámetros. Dependiendo del escenario pueden ser deseables distintos niveles de translucidez. Ventaja que sea alta: el método puede basarse en más información para generar explicaciones. Ventaja de que sea baja: el método de explicación es más flexible.
- **Portabilidad**: describe la gama de modelos con los que se puede utilizar un método de explicación. Los métodos con baja translucidez tienen mayor portabilidad porque tratan el modelo como una caja negra. Los que tienen mayor portabilidad son los modelos sustitutos.
- **Complejidad algorítmica**: la complejidad computacional del método que genera la explicación. Es importante tener en cuenta esta propiedad cuando el tiempo de cálculo es un cuello de botella a la hora de generar explicaciones.

### Propiedades de las explicaciones individuales

- **Precisión**: Una precisión alta es importante si la explicación se utiliza para realizar predicciones en lugar del modelo, pero no lo es si la precisión del modelo también es baja y el objetivo es explicar lo que hace el modleo de caja negra.
- **Fidelidad**: en qué medida se aproxima la explicación a la predicción del modelo de caja negra.Una explicación con baja fidelidad es inútil para explicar el modelo. La precisión y la fidelidad están estrechamente relacionadas. Algunas explicaciones sólo ofrecen fidelidad local (la explicación sólo se aproxima bien a la predicción del modelo para un subconjunto de datos).
- **Coherencia**: en qué medida difiere una explicación entre modelos que han sido entrenados para la misma tarea y que producen predicciones similares. Si las explicaciones son muy parecidas, seran muy coherentes.

*Nota*: Efecto Rashomon = los modelos podrían utilizar características diferentes, pero obtener predicciones similares. En este caso una alta coherencia no es deseable, porque las explicaciones tienen que ser muy diferentes.

- **Estabilidad**: mientras que la coherencia compara explicaciones entre modelos, la estabilidad lo hace entre instancias similares para un modelo fijo. Una alta estabilidad significa que ligeras variaciones en las variables de un caso no cambian sustancialmente la explicación (a menos que estas ligeras variaciones también cambien en gran medida la predicción). La falta de estabilidad puede deberse a una varianza elevada en el método de explicación.
- **Comprensibilidad**: en qué medida entienden los humanos las predicciones. Entre las medidas para medir la comprensibilidad se incluyen medir el tamaño de la explicación o probar hasta qué punto las personas pueden predecir el comportamiento del modelo a partir de las explicaciones. También debe tenerse en cuenta la comprensibilidad de las variables usadas en la explicación (una transformación compleja de las variables puede resultar menos comprensible que las variables originales).
- **Certeza**: medida de confianza para las predicciones del modelo.
- **Grado de importancia**: en qué medida refleja la explicación la importancia de las características o partes de la explicación-
- **Novedad**: ¿refleja la explicación si un dato que hay que explicar procede de una región "nueva" alejada de la distribución de los datos de entrenamiento? Cuanto mayor sea la novedad, más probable es que el modelo tenga poca certeza debido a la falta de datos.
- **Representatividad**: Cuantas instancias (individuos) cubre una explicación.

## Explicacines Human-friendly

La explicaciones son interacciones sociales entre entre el emisor y el receptor y, por tanto, el contexto social influye mucho en el contenido real de la explicación.

Cuando se necesitan explicaciones con TODOS los fatores para una predicción o comportamiento concreto, no se requiere una explicación humana, sino una atribución causal completa.

En los sucesivo, el término *explicación* se refiere al proceso social y cognitivo de explicar, pero también al producto de estos procesos. El *explicador* u omisor puede ser un ser humano o una máquina.


### ¿Qué es una buena explicación?

La explicaciones son **contrastables**. Los humanos no solemos preguntarnos por qué se hizo determinada predicción, sino por qué se hizo esta en lugar de otra. De la mayoría de los modelos interpretables se puede extraer una una explicación que implícitamente contrasta la predicción de una instancia con la predicción de una instancia de datos artificial o una media de instancias. La explicaciones contrastivas son más fáciles de entender que las explicaciones completas. La mejor explicación destaca la mayor diferencia entre el objeto de interés y el objeto de referencia.

**¿Qué sigifica para el aprendizaje automático interpretable?**: la creación de explicaciones contrastables depende de la aplicación, en la medida que requiere un punto de referencia para la comparación. Y esto puede depender del punto de datos a explicar, pero también del usuario que recibe la explicación. La solución para la creación automática de explicaciones contrastables también puede consistir en encontrar prototipos o arquetipos de datos.

Las explicaciones se **seleccionan**. La gente no espera explicaciones que abarquen la lista real y completa de causas del suceso, sino que estamos acostumbrados a seleccionar 1 o 2 causas de entre una variedad de causas posibles como LA explicación. El hecho de que un acontecimiento pueda explicarse por varias causas se denomina efecto Rashomon. Los métodos de conjunto, que combinan varios modelos con distintas características (diferentes explicaciones), suelen dar bueos resultados (predicciones más sólidas y presisas), pero tambéi significa que hay más de una explicación selectiva de por qué se hizo determinada predicción.

**Método LIME**: para hacer explicaciones muy cortas (de solo 1 o 3 razones, aunque el mundo sea más complejo).

Las explicaciones son sociales y forman parte de una conversación o interacción entre el que explica y el que recibe la información. Para el aprendizaje automático interpretable, acertar con la parte social del modelo depende totalmente de su aplicación específica.

La explicaciones se centran en lo **anormal**. La gente se centra más en las causas anormales para explicar los acontecimientos. Se trata de causas que tenían una probabilidad pequeña pero que, sin embargo, ocurrieron. La eliminación de estas causas anormales habría cambiado mucho el resultado. Esto, en el ámbito del aprendizaje autoomático se traduce en que si una de las variables de entrada de una predicción es atípica y la característica inflye en la predicción, debe incluirse en la predicción, incluso si otras características "normales" tienen la misma influencia en la predicción que esta.

La explicaciones son veraces (resultan ser ciertas en la realidad), pero este no es el factor más importante para una buena explicación. Por ejemplo, la selectividad (selección de 1 o 2 causas posibles) parece ser más importante que la veracidad, aunque omite parte de la verdad.

Las buenas explicaciones son **coherentes** con las creencias previas del receptor de la explicación. Los seres humans tendems a ignorar la información que no concuerda con nuestras creenias previas (sesgo de confirmación). Esto es difícil de integrar en el aprendizaje automático y probablemente comprometería drásticamente el rendimiento predictivo. Se pueden imponer restricciones de monotonicidad (una característica sólo puede afectar a la predicción en una dirección) o utilizar algo como un modelo lineal que tenga esta propiedad.

Las buenas explicaciones son generales y probables. Una csausa que puede explicar muchos sucesos es muy general y podría considerarse una buena explicación. La generalidad puede medirse fácilmente por el soporte de una característica, que es el número de instancias a las que se aplica la explicación dividido por el número total de instancias.


# Modelos interpretables

## Regresión lineal

## Regresión logística

## GLM, GAM y más

## Árboles de decisión

## Reglas de decisión

## RuleFit

## Otros modelos interpretables

# Métodos agnósticos de modelos










