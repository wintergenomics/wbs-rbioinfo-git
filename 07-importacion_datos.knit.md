
# Importación y exportación de datos

## Estableciendo nuestro directorio de trabajo

Establecer nuestro directorio de trabajo nos permite tener una mejor organización mientras trabajamos en R. 
Para conocer nuestro directorio de trabajo actual, usamos `getwd()`

```r
getwd() 
```

Asigna a un objeto la ruta de la carpeta de trabajo. Recuerda cambiar */docs/mydir* por los nombres de tus carpetas de trabajo

```r
directory <- "C:/docs/mydir" #Windows
directory <- "/home/users/mydir"  #Mac OS o linux
```

`setwd()` permite ajustar el directorio de trabajo. Vamos a ajustarlo a la ruta de trabajo que guardamos en `directory`

```r
setwd(directory)
```

## Importación de datos
### Archivos CSV

Importa archivos de texto plano con formato CSV (*coma-separated values*). Los datos los puedes descargar de [aquí](https://drive.google.com/u/0/uc?id=1TlR9xgKl7Laf8-SNwoq3W2MXkD19AQ9d&export=download). Recuerda guardarlos en la carpeta de trabajo que asignaste en el paso anterior.

```r
datosRCSV <- read.csv("iris.csv")
```

















































