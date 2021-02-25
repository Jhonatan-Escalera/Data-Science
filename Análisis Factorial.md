# Análisis de factorial

El análisis factorial tiene por objetivo explicar un conjunto de variables observadas por un pequeño número de variables latentes, o no observadas, que llamaremos factores.

Por ejemplo, supongamos que hemos tomado veinte medidas físicas del cuerpo de una persona: estatura, longitud del tronco y de las extremidades, anchura de hombros, peso, etc. Es intuitivo que todas estas medidas no son independientes entre sí, y que conocidas algunas de ellas podemos saber con poco error las restantes porque las dimensiones del cuerpo humano dependen de ciertos factores, y si estos fuesen conocidos podríamos prever con poco error los valores de las variables observadas.

El análisis factorial está relacionado con los componentes principales. Sin embargo, una diferencia es que componentes principales es un herramienta descriptiva, mientras que el análisis factorial presupone un modelo estadístico formal de generación de la muestra dada.

## El modelo factorial

Sea ![](https://render.githubusercontent.com/render/math?math=X%3D%28X_1%2CX_2%2C...%2CX_p%29&mode=inline) nuestra variable multivariante. El modelo de análisis factorial establece que **X** puede representarse de la siguiente manera:

![](https://render.githubusercontent.com/render/math?math=X%3D%5Cvec%7B%5Cmu%7D%2B%5CLambda%20f%2BU&mode=display)

donde:
* _f_ es una variable aleatoria multivariante de dimensión m (m<p). Este f es llamado vector de variables latentes o vector de factores no observados. Como no podemos observar los factores f, se supone sin perder generalidad que su vector de medias es 0, las correlaciones entre sus variables son 0 y las varianzas de cada componente es 1.

* Lambda es una matriz de p filas y m columnas, donde sus elementos son constantes que desconocemos. Contiene los coeficientes que describen cómo es que f afecta al vector aleatorio original X. Se le conoce como matriz de carga.

* U es una variable aleatoria multivariante con vector de medias 0 y matriz de covarianzas diagonal. Se trata de las perturbaciones no observadas (por ejemplo, el error que cometemos cuando usamos instrumentos no calibrados). Recoge el efecto de de todas las variables distintas de los factores que influyen sobre X.

De esta manera, **estamos diciendo que cada dato de nuestra tabla es el resultado de la media de la característica a la que corresponde ese dato, junto con los factores escondidos que relacionan las características y perturbaciones que no podemos observar.**

## Varimax

La interpretación de los factores se facilita si los que afectan a algunas variables no lo hacen a otras y al revés. Este objetivo conduce al criterio de maximizar la varianza de los coeficientes que definen los efectos de cada factor sobre las variables observadas.

Bajo este criterio, se selecciona la llamada matriz de varimax H, que es una matriz ortogonal, la cual tiene la propiedad de que si Lambda es la matriz de carga, entonces Lambda = Lambda H^ es una matriz de carga que hace que haya factores con correlaciones altas con un número pequeño de variables y correlaciones nulas en el resto, quedando así redistribuida la varianza de los factores.

> En R, se utiliza la función `varimax`para calcularla.
