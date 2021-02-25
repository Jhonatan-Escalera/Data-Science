# Análisis Multivariado
***
## Overview
Las características físicas de nosotros como personas: la altura, el peso, la edad, el sexo, el lugar donde hemos nacido, el lugar donde vivimos actualmente, que son variables entre las personas, nos definen como individuos dentro de toda la población.

Pensemos en las propiedades de una imagen: su color,su brillo,su contraste. Son características que la definen y la hacen única. Estos son dos ejemplos sencillos de lo que serían datos multivariantes; es decir, observaciones sobre las que se miden varias variables.

El análisis multivariante es entonces todo el conjunto de métodos, que veremos en este curso, y que nos permitirán explorar y describir las características de nuestros datos en función del conjunto de variables.

Por ejemplo, podremos resumir el conjunto de variables en unas pocas nuevas variables construidas como transformaciones de las variables originales, pero con la mínima pérdida de información para poder trabajar con ellos de una forma más eficiente.

También encontrar grupos entre los datos, si existen. Clasificar nuevas observaciones en grupos que ya han sido definidos. Estas técnicas para describir, resumir y condensar información, clasificar datos, relacionar variables, se conocen a veces como técnicas de exploración de datos.

Sin embargo, estas herramientas no permiten directamente obtener conclusiones generales respecto al proceso o sistema que genera los datos. Para ello necesitamos otro tipo de métodos para crear conocimiento respecto al problema mediante un modelo estadístico y la construcción de un modelo estadístico requiere del concepto de probabilidad. Las herramientas básicas para la construcción de modelos requieren estimar los parámetros del modelo a partir de los datos disponibles, contrastar hipótesis respecto a su estructura para lo cual es necesario conocer los fundamentos de la inferencia multivariante.

Así que los métodos van a estar agrupados en estos dos tipos de análisis: el análisis univariante, el más simple, que es cuando tenemos n observaciones (el tamaño muestral) pero de una sola variable. Por ejemplo, si nuestra variable es la altura de 100 estudiantes, la altura sería la variable aleatoria que estamos midiendo sobre esos 100 estudiantes, y 100 es el tamaño de nuestra muestra. Otra variable aleatoria podría ser el nivel de llenado de 50 botellas o por ejemplo la ciudad de nacimiento de los 1000 participantes de una encuesta.

Pero cuando hablamos de datos multivariantes vamos a tener **n** observaciones, pero más de una variable aleatoria a la vez, es decir, que sobre mis observaciones vamos a estar midiendo más de una sola variable, más de una característica. Y esas variables aleatorias van a ser características que se pueden medir simultáneamente sobre los **n** elementos.

Por ejemplo, las características que se miden sobre las personas cuando se les hace una encuesta, que se les preguntan varias cosas a la misma persona: altura, peso, edad, lugar de residencia, etc. Todas esas son características que van a ser medidas sobre cada uno de los elementos de mi muestra.

Entonces el aspecto de nuestros datos, en el caso multivariante, vamos a tener **n** filas en nuestra matriz de datos y vamos a tener **p** columnas, que van a ser las **p** variables.

## Notación

Esta matriz de datos se puede denotar de la siguiente manera: ![](https://render.githubusercontent.com/render/math?math=%5Cboldsymbol%7BX%3D%5Bx_1%2Cx_2%2C...%2Cx_p%5D%7D&mode=display) donde ![](https://render.githubusercontent.com/render/math?math=%5Cboldsymbol%7Bx_i%7D%5Cin%5Cmathbb%7BR%7D%5En&mode=inline)

## Tipos de variables

Vamos a ver que existen dos tipos de variables que se pueden mezclar en nuestros datos cuando tenemos varias variables. Podemos encontrarnos variables cuantitativas, que son datos numéricos, por ejemplo, cuando nos preguntan la edad, la altura, los ingresos que tenemos. O variables cualitativas, que son atributos o categorías, como por ejemplo si nos preguntan el sexo o el color de ojos o la ciudad donde hemos nacido, todas esas variables toman valores que son categorías o atributos, no son números.

Ahora respecto a las variables cuantitativas, pueden ser continuas o discretas.

Las continuas van a ser valores reales dentro de un intervalo. Es decir, es muy raro que se repitan, por ejemplo, en el peso de las personas puede haber varias coincidencias, pero no muchas coincidencias y siempre van a estar definidas dentro de un intervalo de manera continua.

Sin embargo, las variables discretas son valores numerables o contables. Por ejemplo, el número de hermanos. Se puede tener cero hermanos, un hermano, dos hermanos, etc. Son valores que llegan hasta un límite y además son contables, numerables, es decir, nadie va a tener 1,5 hermanos.

Por tanto, vamos a asumir que estamos observando **p** variables aleatorias, cada una de ellas es una variable univariante, y se miden en un conjunto de elementos que son nuestra muestra. Luego, ese conjunto de variables aleatorias forma una variable aleatoria multivariante.
