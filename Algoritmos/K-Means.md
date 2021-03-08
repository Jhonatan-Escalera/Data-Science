## Introducción

Existen muchos algoritmos de **clustering**. En este ejercicio, presentaremos el algoritmo de **K-means**, que se considera uno de los algoritmos de clustering más simples. A pesar de su simplicidad, el K-means es ampliamente utilizado para el clustering en muchas aplicaciones de ciencia de datos, y es especialmente útil si necesitas descubrir rápidamente ideas de **datos no etiquetados**.

Algunas aplicaciones del mundo real de k-means:
- Segmentación de clientes
- <p><a href = "http://www.r-bloggers.com/clustering-search-keywords-using-k-means-clustering/">Entender lo que los visitantes de un sitio web intentan conseguir</a></p>
- Reconocimiento de patrones
- Aprendizaje automático
- Compresión de datos
-----------------

## Tabla de contenidos 

- <p><a href="#ref1">El problema que queremos resolver</a></p>
- <p><a href="#ref2">Enmarcando el problema real a la aplicación del algoritmo k-means</a></p>
- <p><a href="#ref3">El conjunto de datos</a><p>
- <p><a href="#ref4">Una implementación rápida</a><p>
<p></p>
</div>
<br>

***
<a id="ref1"></a>
# El problema a resolver

Imagina que tienes algo de dinero para invertir y decides que quieres montar una pequeña empresa de moda con un amigo (Al fin y al cabo, si vendes ropa, puedes conseguirla a precios más bajos para ti, tu familia y tus amigos). El nombre de tu empresa será _K&M_ </font> y el primer producto de tu empresa serán las camisetas blancas (porque todo el mundo las tiene, y si todo el mundo las tiene, debe comprarlas en algún sitio). Mientras hablaba con los proveedores, dibujaba los modelos de camisetas y discutía sobre su campaña de lanzamiento, surgieron **dos preguntas importantes**: 

- *¿Cuántas tallas de camisetas deberíamos tener*?
- *¿Qué dimensiones debe tener cada talla de camiseta*?

La primera idea que se te ocurre es comprobar la talla de una de las camisetas de la competencia. Pero entonces recuerdas aquella vez que compraste dos camisetas de talla pequeña de dos marcas diferentes para luego darte cuenta de que sólo una de ellas te quedaba bien. Tu amigo sugiere que mida a sus amigos más bajos y más altos, y utilice esas medidas para diseñar las tallas Pequeña y Grande respectivamente. La talla mediana tendría entonces las dimensiones medias entre las tallas grande y pequeña.

Tras una larga discusión entre tu amigo y tú, sin llegar a ninguna conclusión, recuerdas una cosa que tu profesor de la universidad solía decir en la clase: 

<h2 align=center>"Contra los hechos no hay argumentos"</h2>

¡Así que ambos están de acuerdo en adoptar un enfoque basado en datos, y para ello pueden utilizar el algoritmo **K-means**!

***
<a id="ref2"></a>
<a id="ref100"></a>
# Enmarcando el problema real a la aplicación del algoritmo k-means
En lugar de basarse en la información de dos personas o copiar el fallo de otros, ¿por qué no explorar la causa raíz de este problema? Vas a buscar en los <color de la fuente = verde>datos de tus clientes potenciales </font>y ejecutar <color de la fuente = verde>algunos experimentos</font> para decidir <color de la fuente = verde>cuántas tallas de camisetas</font> debes tener, y cuáles deben ser <color de la fuente = verde>las dimensiones de cada talla de camiseta</font>.

***
<a id="ref3"></a>
<a id="ref20"></a>
# El conjunto de datos
Usted ha decidido que <font color = rojo size = 4> *K<font size = 1>&</font>M* </font> iniciará sus operaciones en Hong Kong. Para esta tarea, se utilizará un conjunto de datos abierto (disponible públicamente). <a href = "http://socr.ucla.edu/docs/resources/SOCR_Data/SOCR_Data_Dinov_020108_HeightsWeights.html"> ***HKkids***</a> tiene información sobre el peso y la altura de 25000 niños de Hong Kong, recogida en 1993 para un estudio de crecimiento. Utilizaremos sólo estas dos medidas para simplificar el problema. (¡Pero podríamos haber utilizado un conjunto de datos con todas las medidas de pecho, brazos, cuello, cintura, etc. si quisiéramos!)  

Ahora vamos a empezar a jugar con los datos. Trabajaremos según el siguiente flujo de trabajo:
1. Cargar
- Resumen
- Limpiar
- Visualizar
## Descarga del archivo en la base de datos de este repositorio
`weight-height.csv`

## Abre en R Studio y revisa el contenido
Utiliza los comandos `read.csv y head`
`head(weight.height.csv)`
`str(weight.height.csv)`
`weight.height.csv$Gender <- NULL`
`library(ggplot2)`
`ggplot(weight.height.csv, aes(x = weight.height.csv$'Height', y = weight.height.csv$'Weight')) +`
  `geom_point(shape=1, size = 2, color = "black", alpha = 1/3) +`
  `geom_point(size = 0.1, color = "red4", alpha = 1/3) +`
  `labs (x = "Peso (Kilos)", y ="Altura (Centimetros)" )`

## Calcular la media y la desviación standar, antes de normalizar
`Media_Altura = mean(weight.height.csv$Height)`
`Desviacion_Altura = sd(weight.height.csv$Height)`
`Media_Peso = mean(weight.height.csv$Weight)`
`Desviacion_Peso = sd(weight.height.csv$Weight)`

## Puntajes Z
`weight.height.csv$Height <- (weight.height.csv$Height - Media_Altura) / Desviacion_Altura`
`weight.height.csv$Weight <- (weight.height.csv$Weight - Media_Peso) / Desviacion_Peso`

## "centers" es el numero de clusters
## "iter.max" es el número de iteraciones
`numero_clusters = kmeans (weight.height.csv, centers = 3, iter.max = 10)`

## Usamos color_offset = 4 solo para sea más visual
`color_offset = 4`
## Convertimos los numeros a datos categoricos en orden de color
`weight.height.csv$Cluster <- as.factor(numero_clusters$cluster + color_offset)`
`head(weight.height.csv)`
## Lo visualizamos
`ggplot() +`
  `geom_point(data = weight.height.csv, aes(x = weight.height.csv$Height, y = weight.height.csv$Weight), shape=1, size = 2, color = "black", alpha = 1/2) +`
  `geom_point(data = weight.height.csv, aes(x = weight.height.csv$Height, y = weight.height.csv$Weight), shape=1, size = 0.1, colour = weight.height.csv$Cluster, alpha = 1/2) +`
  `labs (x = "Altura (Centimetros)", y = "Peso (Kilos)")`

## Extrayendo los centroides
`Cluster_centroids <- as.data.frame(numero_clusters$centers)`
## Visualizando los centroides
`ggplot() +`
  `geom_point(data = weight.height.csv, aes(x = weight.height.csv$Height, y = weight.height.csv$Weight), shape=1, size = 2, color = "black", alpha = 1/10) +`
  `geom_point(data = weight.height.csv, aes(x = weight.height.csv$Height, y = weight.height.csv$Weight), shape=1, size = 0.1, colour = weight.height.csv$Cluster, alpha = 1/4) +`
  `geom_point(data = Cluster_centroids, aes(x = Cluster_centroids$Height, y = Cluster_centroids$Weight), shape = 1, size = 3, color = "black") +`
  `geom_point(data = Cluster_centroids, aes(x = Cluster_centroids$Height, y = Cluster_centroids$Weight), shape = 1, size = 5, color = "black") +`
  `geom_point(data = Cluster_centroids, aes(x = Cluster_centroids$Height, y = Cluster_centroids$Weight), shape = 3, size = 10, color = "black") +`
  `labs (x = "Altura (Centimetros", y = "Peso (Kilos)")`

## Revisando la ubicación de cada centroide con el cluster
`Cluster_centroids`

## Deshaciendo la normalización
`tamaño_camiseta <- Cluster_centroids`
`tamaño_camiseta$Height <- (tamaño_camiseta$Height * Desviacion_Altura) + Media_Altura`
`tamaño_camiseta$Weight <- (tamaño_camiseta$Weight * Desviacion_Peso) + Media_Peso`
`tamaño_camiseta`

`small <- which(tamaño_camiseta$Height==min(tamaño_camiseta$Height))`
`tamaño_camiseta[small,]`
`medium <- which(tamaño_camiseta$Height==median(tamaño_camiseta$Height))`
`tamaño_camiseta[medium,]`
`large <- which(tamaño_camiseta$Height==max(tamaño_camiseta$Height))`
`tamaño_camiseta[large,]`

    Height   Weight

1 338.8861 6553.730

2 305.4305 4192.293

3 322.0376 5372.720

![](https://lh3.googleusercontent.com/proxy/UzihJoSGj5pvJuJKOSnGSG1jClOR2lFEl3_EhHlcyUPlEVpknrnblASxzwhlG1s-rd3JY4fSs0eZAAm2JxptBF1lqdd8xA8EOqrlzoWyzaWhg-JzAznC1ss7UEcE9Pk_tJv_5yuBecqdjM-csf9eA7FGDRoEOtDLrWalC8vQwSy8lA)


## Conclusión
1.  El uso de K-Means tiene dos ventajas principales: 
    - Primero, es fácil de entender
    - Y segundo, es muy rápido comparado con muchos otros algoritmos de clustering

2.  K-Means también tiene algunas desventajas.  
    - Primero, no tiene una inicialización especificada de los puntos de cluster y tiene una alta variación de modelos de clustering basados en la inicialización de los puntos de cluster
    - En segundo lugar, la obtención de resultados precisos depende de las métricas de medición de la distancia.
Y por último, existe la posibilidad de que un centroide no tenga puntos de datos en su grupo, por lo que no puede ser actualizado.
