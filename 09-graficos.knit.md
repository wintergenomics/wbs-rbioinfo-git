
# Gráficos en R

R es un lenguaje de programación y entorno computacional dedicado a la estadística que dispone de múltiples funciones diseñadas para la representación gráfica de datos.

Revisa la presentación completa [aquí](https://drive.google.com/u/0/uc?id=1t_zGzI25aQp3j3ffs1RnIcyUzgee7azf&export=download)


## Tipos de gráficos en R

Existe una gran variedad de gráficos que pueden utilizarse según el tipo de datos que se tengan.

<img src="https://i.pinimg.com/originals/77/e3/7e/77e37ee70c22a193b429d8cbf6dfd0cb.png"/>
[Fuente](https://www.r-graph-gallery.com/)

## Paqueterías para graficar en R

Existen diversas paqueterías en R que facilitan la creación de gráficos. Cada paquetería permite crear diversos tipos de gráficos.

+ **[graphics](https://www.rdocumentation.org/packages/graphics/versions/3.6.2)**
+ [grid](https://cran.r-project.org/package=grid) 
+ [Lattice](https://cran.r-project.org/web/packages/lattice/lattice.pdf)
+ **[ggplot2](https://cran.r-project.org/package=ggplot2)**
+ [gganimate](https://cran.r-project.org/package=gganimate)
+ [Highcharts](https://cran.r-project.org/package=highcharter)
+ [bbplot](https://github.com/bbc/bbplot)
+ [ggfortify](https://cran.r-project.org/package=ggfortify)


## Gráficos de base R

R cuenta con el paquete base de graphics para la construcción de gráficos. La función `plot` es la función básica que permite crear:

+ Líneas 
+ Barras
+ Boxplots
+ Matrices de dispersión

## Paletas de colores en R 

Los colores son uno de los elementos esenciales de un gráfico. Forman parte de la estética y por tanto, los podemos utilizar tanto para representar variables, como para destacar elementos dentro de la visualización.

[Aquí](http://www.stat.columbia.edu/~tzheng/files/Rcolor.pdf) y [aquí](https://htmlcolorcodes.com/) puedes revisar los colores disponibles en R que puedes usar en tus gráficas.

## ggplot2

[ggplot2](https://cran.r-project.org/package=ggplot2) es una de las paqueterías más populares en R para crear una gran variedad de gráficos. `ggplot2` es un sistema para la creación declarativa de gráficos basado en la gramática de gráficos. En esta gramática, se separan los elementos o las partes de un gráfico en diferentes capas o layers, y así es más fácil modificarlos.

`ggplot2` funciona a través de la grámatica de gráficos donde se dan los datos, las variables que queremos a graficar y la geometría deseada.

Instalación de ggplot2

```r
install.packages("tidyverse")
install.packages("ggplot2")
```

Cargar la librería de trabajo

```r
library(ggplot2)
```

Importamos el set de datos que puedes descargar de [aquí](https://drive.google.com/u/0/uc?id=1TlR9xgKl7Laf8-SNwoq3W2MXkD19AQ9d&export=download)


```r
datos <- read.csv("iris.csv")
```

















































