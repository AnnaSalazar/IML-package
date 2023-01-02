# Paquete `iml` (Interpretable Machine Learning)

Los modelos de aprendizaje automático suelen dar muy buenos resultados en las predicciones, pero no son interpretables. Se denominan **modelos de caja negra**, ya que es difícil acceder a su funcionamiento interno, es decir, su estructura, lógica y componentes internos son imposibles de dilucidar.

El paquete `iml` proporciona herramientas para analizar este tipo de modelos. Principalmente, permite responder a las siguientes cuestiones:
- ¿Cuáles son las variables más importantes?
- ¿Cómo influye una variable en las predicciones?
- ¿De qué forma afectaron los valores de las variables de un punto de datos a su predicción?
- ¿Se puede aproximar el modelo de caja negra subyacente con un árbol de decisión?

## Importancia de las variables

Se puede medir la importancia de cada variable en las predicciones con `Featurelmp()`. La medida de importancia de la variable funciona modificando cada variable y midiendo cuánto disminuye el rendimiento. Para esta tarea de regresión se mide la pérdida de rendimiento con el error medio absoluto (MAE), aunque también se podría usar el error cuadrático medio (MSE).

Una vez se crea un nuevo objeto con `Featurelmp()`, la importancia se calcula automáticamente (`$results`). Podemos graficar este nuevo objeto con la función `plot()` o mirar los resultados en un dataframe.

## Influencia de las variables en las predicciones

Además de saber qué variables son importantes, nos interesa saber cómo influyen estas en el resultado predicho. La función `FeatureEffect()` implementa gráficos de efectos locales acumulados, gráficos de dependencia parcial y curvas de expectativas condicionales individuales.

- Efectos locales acumulados (ALE) para una variable

Este gráfico muestra cómo cambia localmente la predicción cuando se varía una variable. La marcas en el eje de las x indican la distribución de la variable, mostrando lo relevante que es una región para la interpretación (pocos puntos o ninguno indican que no se debe sobreinterpretar dicha región).

Función: 

```
obj <- FeatureEffect$new(predictor, feature = "[variable]")
obj$plot()
```

Si se quiere calcular las curvas de dependencia parcial de otra variable, solo se debe reajustar la variable:

```
obj$set.feature("[nueva_variable]")
obj$plot()
```

## Medida de las interacciones

También se puede medir la intensidad con la que las variables interactúan entre si. La medida de la interacción se refiere a la parte de la varianza de la función que se explica por la interacción. Esta puede tomar valores entre 0 (ninguna interacción) y 1 (el 100% de la varianza de la función es debida a las interacciones).

Para cada variable, se mide en qué medida interactúan con cualquier otra variable:

```
interaccion <- Interaction$new(predictor)
plot(interaccion)
```

También se puede especificar una variable y medir todas sus interacciones bidireccionales con todas las demás variables:

```
interaccion2 <- Interaction$new(predictor, feature = "[variable]")
plot(interaccion2)
```

También se pueden trazar los efectos de todas las variables a la vez:

```
efectos <- FeatureEffects$new(predictor)
plot(efectos)
```

## Modelo alternativo

Otra forma de hacer que los modelos sean más interpretables es sustituir la caja negra por un modelo más sencillo: un árbol de decisión. Se toman las predicciones del modelo de caja negra y se entrena un árbol de decisión con las variables originales y el resultado predicho. El gráfico muestra los nodos terminales del árbol ajustado.

El parámetro de profundidad máxima controla la profuncidad a la que puede crecer el árbol y, por tanto, su interpretabilidad.

```
arbol <- TreeSurrogate$new(predictor, maxdepth = 2)
plot(arbol)
```

Se puede usar el árbol para hacer predicciones:

```
arbol$predict(datos)
```

## Explicar las predicciones individuales con un modelo local

Un modelo sustitutivo local puede mejorar la comprensión del comportamiento global del modelo. También se puede ajustar un modelo localmente para comprender mejor una predicción individual.

El modelo local ajustado por `LocalModel()` es un modelo de regresión lineal y los puntos de los datos se ponderan en función de su proximidad al punto de datos cuya predicción queremos explicar.

```
lime.explain <- LocalModel$new(predictor, x.interest = X[1,])
lime.explain$results
plot(lime.explain)

lime.explain$explain(X[2,])
plot(lime.explain)
```


## Explicar las predicciones individuales mediante la teoría de juegos

Una alternativa para explicar las predicciones individuales es un método de la teoría de juegos de coalición denominado *valor de Shapley*. Supongamos que, para un punto de datos, los valores de los rasgos juegan juntos a un juego en el que obtienen la predicción como pago. El valor de shapley nos dice cómo distribuir equitativamente el pago entre los valores de los rasgos.

```
shapley <- Shapley$new(predictor, x.interest = X[1,])
shapley$plot()
```


Podemos reutilizar el objeto para explicar otros punto de datos:

```
shapley$explain(x.interest = X[2,])
shapley$plot()
```


Los resultados se pueden extraer en forma de data frame de la siguiente forma:

```
resultados <- shapley$results
```



# Anexo 

```
set.seed(123)
library(iml)
library(randomForest)

rf <- randomForest([variable_respuesta] ~ ., data = [datos], ntree = 50)

X <- [datos][which(names([datos]) != "[variable_respuesta]")]
predictor <- Predictor$new(rf, data = X, y = [datos]$[variable_respuesta])
```


