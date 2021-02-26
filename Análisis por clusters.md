# Análisis por clusters (o conglomerados)
***
El análisis de clúster o conglomerados tiene como objetivo agrupar elementos en grupos homogéneos en función de las similitudes o similaridades entre ellos. Normalmente se agrupan las observaciones, aunque puede también aplicarse para agrupar variables. Estos métodos se conocen también con el nombre de métodos de clasificación automática o no supervisada, o de reconocimiento de patrones sin supervisión.

En general existen tres métodos:

* Partición de los datos:
        Algoritmo k-medias
* Métodos jerárquicos:
        Métodos aglomerativos
        Métodos divisivos
* Clúster basado en modelos:
        Bietápico

El análisis de conglomerados estudia tres tipos de problemas:

**Partición de los datos:** Disponemos de datos que sospechamos son heterogéneos y se desea dividirlos en un número de grupos prefijado, de manera que:

    1. cada elemento pertenezca a uno y solo uno de los grupos.
    2. todo elemento quede clasificado.
    3. cada grupo sea internamente homogéneo.

Por ejemplo: se dispone de una base de datos de compras de clientes y se desea hacer una tipología de estos clientes en función de sus pautas de consumo. Este método se basa fuertemente en la matriz de los datos.

**Construcción de jerarquías:** Deseamos estructurar los elementos de un conjunto de forma jerárquica por su similitud.

Por ejemplo: tenemos una encuesta de atributos de distintas profesiones y queremos ordenarlas por similitud. Una clasificación jerárquica implica que los datos se ordenan en niveles, de manera que los niveles superiores contienen a los inferiores. Este tipo de clasificación es muy frecuente en biología, al clasificar animales, plantas etc. Estrictamente, estos métodos no definen grupos, sino la estructura de asociación en cadena que pueda existir entre los elementos. Sin embargo, como veremos, la jerarquía construida permite obtener también una partición de los datos en grupos.
Estos métodos se basa fuertemente en una matriz de distancias o similaridades.

**Clúster basado en modelos**: En este caso, se parte de la hipótesis de que los datos han sido generados de una mixtura de distribuciones. Entonces lo que hay que estimar son los parámetros desconocidos de esta mixtura usando el método de máxima verosimilitud. Las observaciones son asignadas al grupo que tiene mayor probabilidad de haberlas generado. Estos métodos utilizan algoritmos de optimización para estimar los parámetros desconocidos.

