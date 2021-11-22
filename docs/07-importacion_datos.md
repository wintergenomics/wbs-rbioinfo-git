---
output:
  pdf_document: default
  html_document: default
---

# Importación y exportación de datos

R puede importar datos de una amplia variedad de tipos de archivo con las funciones en base además de que esta capacidad es ampliada con el uso de paqueterías específicas.

## Tipos de datos que puedo importar y exportar
Existen diversos tipos de datos que se pueden importar y exportar en R. Las tres fuentes más comunes para la importación o exportación de datos son:

**Datos en formato texto (o tabulares)**
- CSV: .csv (comma separated values o datos separados por comas)
- TXT
- Otros datos en formato texto

**Formatos de otros programas (software propietario)**
- EXCEL: .xls y .xlsx
- SPSS: .sav y .por
- STATA: .dta
- SAS: .sas

**Formatos propios de R**
- R objects: .RData o .rda
- Serialized R objects: .rds

## ¿De dónde puedo obtener los datos?

- Datos propios: son datos obtenidos mediante trabajo experimental por parte de mi grupo de trabajo o míos.
- Datos de sets de datos precargados en R
- Datos obtenidos de bases de datos en internet 

Las paqueterías más utilizadas para la importación y exportación de datps son: 
- r-base
- readr
- haven

## ¿Cuáles son las diferencias entre R base y las paqueterías ampliadas?

R tiene más de 20 años. Las funciones de R-base se construyeron pensando en  los estadísticos de hace 20 años (hoy se llamarían analistas de datos).  Modificar las funciones de R-base haría que el código antiguo dejase de funcionar, así que la mayoría de avances y mejoras se producen en las paqueterías.

Las funciones de `readr` emulan las funciones equivalentes de R-base mejorándolas y haciéndolas más consistentes; por ejemplo para leer datos CSV la función de R-base es `read.csv()`; mientras que la función equivalente de "readr" es `read_csv()`. Las dos hacen lo mismo, leer datos en formato CSV, pero las nuevas funciones tienen algunas ventajas:
- Son más rápidas
- Encajan más en el workflow/paradigma de la investigación reproducible. 

Algunas de las funciones de R-base heredan algunas opciones del sistema operativo y las variables de entorno, haciendo posible que un script que funciona en un ordenador no funcione en otro.

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


```r
library(readr)
```

Conocer más sobre las paqueterías

```r
help(package=readr) #Read Rectangular Text Data

help(package= haven) #Importa y Exporta 'SPSS', 'Stata' y archivos 'SAS'
```

Visualiza la documentación de la función read_csv de la paquetería `readr`. 

```r
help(read_csv, package = "readr")
```


A veces es conveniente saber que package contiene una función. Podemos hacerlo con la función `find` para encontrar en qué paquetería está la función `help`.

```r
find("read_csv")
```

```
## [1] "package:readr"
```


```r
find("read.csv")
```

```
## [1] "package:utils"
```


## Importación de datos

### Importar datos de los datasets de R

R contiene datasets que pueden ser utilizados directamente. Para dar un vistazo a los paquetes disponibles en R usamos `data()`

Guardamos el listado de datasets en un data.frame llamado `sets`

```r
sets <- as.data.frame(data()[[3]])
sets
```

```
##      Package                                                        LibPath
## 1   datasets /Library/Frameworks/R.framework/Versions/4.1/Resources/library
## 2   datasets /Library/Frameworks/R.framework/Versions/4.1/Resources/library
## 3   datasets /Library/Frameworks/R.framework/Versions/4.1/Resources/library
## 4   datasets /Library/Frameworks/R.framework/Versions/4.1/Resources/library
## 5   datasets /Library/Frameworks/R.framework/Versions/4.1/Resources/library
## 6   datasets /Library/Frameworks/R.framework/Versions/4.1/Resources/library
## 7   datasets /Library/Frameworks/R.framework/Versions/4.1/Resources/library
## 8   datasets /Library/Frameworks/R.framework/Versions/4.1/Resources/library
## 9   datasets /Library/Frameworks/R.framework/Versions/4.1/Resources/library
## 10  datasets /Library/Frameworks/R.framework/Versions/4.1/Resources/library
## 11  datasets /Library/Frameworks/R.framework/Versions/4.1/Resources/library
## 12  datasets /Library/Frameworks/R.framework/Versions/4.1/Resources/library
## 13  datasets /Library/Frameworks/R.framework/Versions/4.1/Resources/library
## 14  datasets /Library/Frameworks/R.framework/Versions/4.1/Resources/library
## 15  datasets /Library/Frameworks/R.framework/Versions/4.1/Resources/library
## 16  datasets /Library/Frameworks/R.framework/Versions/4.1/Resources/library
## 17  datasets /Library/Frameworks/R.framework/Versions/4.1/Resources/library
## 18  datasets /Library/Frameworks/R.framework/Versions/4.1/Resources/library
## 19  datasets /Library/Frameworks/R.framework/Versions/4.1/Resources/library
## 20  datasets /Library/Frameworks/R.framework/Versions/4.1/Resources/library
## 21  datasets /Library/Frameworks/R.framework/Versions/4.1/Resources/library
## 22  datasets /Library/Frameworks/R.framework/Versions/4.1/Resources/library
## 23  datasets /Library/Frameworks/R.framework/Versions/4.1/Resources/library
## 24  datasets /Library/Frameworks/R.framework/Versions/4.1/Resources/library
## 25  datasets /Library/Frameworks/R.framework/Versions/4.1/Resources/library
## 26  datasets /Library/Frameworks/R.framework/Versions/4.1/Resources/library
## 27  datasets /Library/Frameworks/R.framework/Versions/4.1/Resources/library
## 28  datasets /Library/Frameworks/R.framework/Versions/4.1/Resources/library
## 29  datasets /Library/Frameworks/R.framework/Versions/4.1/Resources/library
## 30  datasets /Library/Frameworks/R.framework/Versions/4.1/Resources/library
## 31  datasets /Library/Frameworks/R.framework/Versions/4.1/Resources/library
## 32  datasets /Library/Frameworks/R.framework/Versions/4.1/Resources/library
## 33  datasets /Library/Frameworks/R.framework/Versions/4.1/Resources/library
## 34  datasets /Library/Frameworks/R.framework/Versions/4.1/Resources/library
## 35  datasets /Library/Frameworks/R.framework/Versions/4.1/Resources/library
## 36  datasets /Library/Frameworks/R.framework/Versions/4.1/Resources/library
## 37  datasets /Library/Frameworks/R.framework/Versions/4.1/Resources/library
## 38  datasets /Library/Frameworks/R.framework/Versions/4.1/Resources/library
## 39  datasets /Library/Frameworks/R.framework/Versions/4.1/Resources/library
## 40  datasets /Library/Frameworks/R.framework/Versions/4.1/Resources/library
## 41  datasets /Library/Frameworks/R.framework/Versions/4.1/Resources/library
## 42  datasets /Library/Frameworks/R.framework/Versions/4.1/Resources/library
## 43  datasets /Library/Frameworks/R.framework/Versions/4.1/Resources/library
## 44  datasets /Library/Frameworks/R.framework/Versions/4.1/Resources/library
## 45  datasets /Library/Frameworks/R.framework/Versions/4.1/Resources/library
## 46  datasets /Library/Frameworks/R.framework/Versions/4.1/Resources/library
## 47  datasets /Library/Frameworks/R.framework/Versions/4.1/Resources/library
## 48  datasets /Library/Frameworks/R.framework/Versions/4.1/Resources/library
## 49  datasets /Library/Frameworks/R.framework/Versions/4.1/Resources/library
## 50  datasets /Library/Frameworks/R.framework/Versions/4.1/Resources/library
## 51  datasets /Library/Frameworks/R.framework/Versions/4.1/Resources/library
## 52  datasets /Library/Frameworks/R.framework/Versions/4.1/Resources/library
## 53  datasets /Library/Frameworks/R.framework/Versions/4.1/Resources/library
## 54  datasets /Library/Frameworks/R.framework/Versions/4.1/Resources/library
## 55  datasets /Library/Frameworks/R.framework/Versions/4.1/Resources/library
## 56  datasets /Library/Frameworks/R.framework/Versions/4.1/Resources/library
## 57  datasets /Library/Frameworks/R.framework/Versions/4.1/Resources/library
## 58  datasets /Library/Frameworks/R.framework/Versions/4.1/Resources/library
## 59  datasets /Library/Frameworks/R.framework/Versions/4.1/Resources/library
## 60  datasets /Library/Frameworks/R.framework/Versions/4.1/Resources/library
## 61  datasets /Library/Frameworks/R.framework/Versions/4.1/Resources/library
## 62  datasets /Library/Frameworks/R.framework/Versions/4.1/Resources/library
## 63  datasets /Library/Frameworks/R.framework/Versions/4.1/Resources/library
## 64  datasets /Library/Frameworks/R.framework/Versions/4.1/Resources/library
## 65  datasets /Library/Frameworks/R.framework/Versions/4.1/Resources/library
## 66  datasets /Library/Frameworks/R.framework/Versions/4.1/Resources/library
## 67  datasets /Library/Frameworks/R.framework/Versions/4.1/Resources/library
## 68  datasets /Library/Frameworks/R.framework/Versions/4.1/Resources/library
## 69  datasets /Library/Frameworks/R.framework/Versions/4.1/Resources/library
## 70  datasets /Library/Frameworks/R.framework/Versions/4.1/Resources/library
## 71  datasets /Library/Frameworks/R.framework/Versions/4.1/Resources/library
## 72  datasets /Library/Frameworks/R.framework/Versions/4.1/Resources/library
## 73  datasets /Library/Frameworks/R.framework/Versions/4.1/Resources/library
## 74  datasets /Library/Frameworks/R.framework/Versions/4.1/Resources/library
## 75  datasets /Library/Frameworks/R.framework/Versions/4.1/Resources/library
## 76  datasets /Library/Frameworks/R.framework/Versions/4.1/Resources/library
## 77  datasets /Library/Frameworks/R.framework/Versions/4.1/Resources/library
## 78  datasets /Library/Frameworks/R.framework/Versions/4.1/Resources/library
## 79  datasets /Library/Frameworks/R.framework/Versions/4.1/Resources/library
## 80  datasets /Library/Frameworks/R.framework/Versions/4.1/Resources/library
## 81  datasets /Library/Frameworks/R.framework/Versions/4.1/Resources/library
## 82  datasets /Library/Frameworks/R.framework/Versions/4.1/Resources/library
## 83  datasets /Library/Frameworks/R.framework/Versions/4.1/Resources/library
## 84  datasets /Library/Frameworks/R.framework/Versions/4.1/Resources/library
## 85  datasets /Library/Frameworks/R.framework/Versions/4.1/Resources/library
## 86  datasets /Library/Frameworks/R.framework/Versions/4.1/Resources/library
## 87  datasets /Library/Frameworks/R.framework/Versions/4.1/Resources/library
## 88  datasets /Library/Frameworks/R.framework/Versions/4.1/Resources/library
## 89  datasets /Library/Frameworks/R.framework/Versions/4.1/Resources/library
## 90  datasets /Library/Frameworks/R.framework/Versions/4.1/Resources/library
## 91  datasets /Library/Frameworks/R.framework/Versions/4.1/Resources/library
## 92  datasets /Library/Frameworks/R.framework/Versions/4.1/Resources/library
## 93  datasets /Library/Frameworks/R.framework/Versions/4.1/Resources/library
## 94  datasets /Library/Frameworks/R.framework/Versions/4.1/Resources/library
## 95  datasets /Library/Frameworks/R.framework/Versions/4.1/Resources/library
## 96  datasets /Library/Frameworks/R.framework/Versions/4.1/Resources/library
## 97  datasets /Library/Frameworks/R.framework/Versions/4.1/Resources/library
## 98  datasets /Library/Frameworks/R.framework/Versions/4.1/Resources/library
## 99  datasets /Library/Frameworks/R.framework/Versions/4.1/Resources/library
## 100 datasets /Library/Frameworks/R.framework/Versions/4.1/Resources/library
## 101 datasets /Library/Frameworks/R.framework/Versions/4.1/Resources/library
## 102 datasets /Library/Frameworks/R.framework/Versions/4.1/Resources/library
## 103 datasets /Library/Frameworks/R.framework/Versions/4.1/Resources/library
## 104 datasets /Library/Frameworks/R.framework/Versions/4.1/Resources/library
##                       Item
## 1            AirPassengers
## 2                  BJsales
## 3   BJsales.lead (BJsales)
## 4                      BOD
## 5                      CO2
## 6              ChickWeight
## 7                    DNase
## 8           EuStockMarkets
## 9             Formaldehyde
## 10            HairEyeColor
## 11            Harman23.cor
## 12            Harman74.cor
## 13                Indometh
## 14            InsectSprays
## 15          JohnsonJohnson
## 16               LakeHuron
## 17        LifeCycleSavings
## 18                Loblolly
## 19                    Nile
## 20                  Orange
## 21           OrchardSprays
## 22             PlantGrowth
## 23               Puromycin
## 24               Seatbelts
## 25                  Theoph
## 26                 Titanic
## 27             ToothGrowth
## 28           UCBAdmissions
## 29          UKDriverDeaths
## 30                   UKgas
## 31             USAccDeaths
## 32               USArrests
## 33          USJudgeRatings
## 34   USPersonalExpenditure
## 35               UScitiesD
## 36                VADeaths
## 37                WWWusage
## 38             WorldPhones
## 39             ability.cov
## 40                airmiles
## 41              airquality
## 42                anscombe
## 43                  attenu
## 44                attitude
## 45                 austres
## 46       beaver1 (beavers)
## 47       beaver2 (beavers)
## 48                    cars
## 49                chickwts
## 50                     co2
## 51                 crimtab
## 52             discoveries
## 53                   esoph
## 54                    euro
## 55       euro.cross (euro)
## 56                eurodist
## 57                faithful
## 58  fdeaths (UKLungDeaths)
## 59                  freeny
## 60       freeny.x (freeny)
## 61       freeny.y (freeny)
## 62                  infert
## 63                    iris
## 64                   iris3
## 65                 islands
## 66  ldeaths (UKLungDeaths)
## 67                      lh
## 68                 longley
## 69                    lynx
## 70  mdeaths (UKLungDeaths)
## 71                  morley
## 72                  mtcars
## 73                  nhtemp
## 74                  nottem
## 75                     npk
## 76      occupationalStatus
## 77                  precip
## 78              presidents
## 79                pressure
## 80                  quakes
## 81                   randu
## 82                  rivers
## 83                    rock
## 84                   sleep
## 85  stack.loss (stackloss)
## 86     stack.x (stackloss)
## 87               stackloss
## 88       state.abb (state)
## 89      state.area (state)
## 90    state.center (state)
## 91  state.division (state)
## 92      state.name (state)
## 93    state.region (state)
## 94       state.x77 (state)
## 95           sunspot.month
## 96            sunspot.year
## 97                sunspots
## 98                   swiss
## 99                treering
## 100                  trees
## 101                  uspop
## 102                volcano
## 103             warpbreaks
## 104                  women
##                                                               Title
## 1                       Monthly Airline Passenger Numbers 1949-1960
## 2                                 Sales Data with Leading Indicator
## 3                                 Sales Data with Leading Indicator
## 4                                         Biochemical Oxygen Demand
## 5                             Carbon Dioxide Uptake in Grass Plants
## 6                    Weight versus age of chicks on different diets
## 7                                              Elisa assay of DNase
## 8   Daily Closing Prices of Major European Stock Indices, 1991-1998
## 9                                     Determination of Formaldehyde
## 10                        Hair and Eye Color of Statistics Students
## 11                                               Harman Example 2.3
## 12                                               Harman Example 7.4
## 13                                 Pharmacokinetics of Indomethacin
## 14                                   Effectiveness of Insect Sprays
## 15                   Quarterly Earnings per Johnson & Johnson Share
## 16                                    Level of Lake Huron 1875-1972
## 17                             Intercountry Life-Cycle Savings Data
## 18                                    Growth of Loblolly pine trees
## 19                                           Flow of the River Nile
## 20                                           Growth of Orange Trees
## 21                                        Potency of Orchard Sprays
## 22                       Results from an Experiment on Plant Growth
## 23                       Reaction Velocity of an Enzymatic Reaction
## 24                         Road Casualties in Great Britain 1969-84
## 25                                 Pharmacokinetics of Theophylline
## 26                            Survival of passengers on the Titanic
## 27           The Effect of Vitamin C on Tooth Growth in Guinea Pigs
## 28                                Student Admissions at UC Berkeley
## 29                         Road Casualties in Great Britain 1969-84
## 30                                     UK Quarterly Gas Consumption
## 31                            Accidental Deaths in the US 1973-1978
## 32                                  Violent Crime Rates by US State
## 33        Lawyers' Ratings of State Judges in the US Superior Court
## 34                                        Personal Expenditure Data
## 35          Distances Between European Cities and Between US Cities
## 36                                   Death Rates in Virginia (1940)
## 37                                        Internet Usage per Minute
## 38                                           The World's Telephones
## 39                                   Ability and Intelligence Tests
## 40             Passenger Miles on Commercial US Airlines, 1937-1960
## 41                                New York Air Quality Measurements
## 42      Anscombe's Quartet of 'Identical' Simple Linear Regressions
## 43                                The Joyner-Boore Attenuation Data
## 44                               The Chatterjee-Price Attitude Data
## 45      Quarterly Time Series of the Number of Australian Residents
## 46                           Body Temperature Series of Two Beavers
## 47                           Body Temperature Series of Two Beavers
## 48                             Speed and Stopping Distances of Cars
## 49                                     Chicken Weights by Feed Type
## 50                          Mauna Loa Atmospheric CO2 Concentration
## 51                                    Student's 3000 Criminals Data
## 52                          Yearly Numbers of Important Discoveries
## 53                        Smoking, Alcohol and (O)esophageal Cancer
## 54                              Conversion Rates of Euro Currencies
## 55                              Conversion Rates of Euro Currencies
## 56          Distances Between European Cities and Between US Cities
## 57                                         Old Faithful Geyser Data
## 58                      Monthly Deaths from Lung Diseases in the UK
## 59                                            Freeny's Revenue Data
## 60                                            Freeny's Revenue Data
## 61                                            Freeny's Revenue Data
## 62               Infertility after Spontaneous and Induced Abortion
## 63                                       Edgar Anderson's Iris Data
## 64                                       Edgar Anderson's Iris Data
## 65                            Areas of the World's Major Landmasses
## 66                      Monthly Deaths from Lung Diseases in the UK
## 67                             Luteinizing Hormone in Blood Samples
## 68                               Longley's Economic Regression Data
## 69                         Annual Canadian Lynx trappings 1821-1934
## 70                      Monthly Deaths from Lung Diseases in the UK
## 71                                    Michelson Speed of Light Data
## 72                                       Motor Trend Car Road Tests
## 73                         Average Yearly Temperatures in New Haven
## 74            Average Monthly Temperatures at Nottingham, 1920-1939
## 75                           Classical N, P, K Factorial Experiment
## 76                    Occupational Status of Fathers and their Sons
## 77                                Annual Precipitation in US Cities
## 78                      Quarterly Approval Ratings of US Presidents
## 79           Vapor Pressure of Mercury as a Function of Temperature
## 80                                Locations of Earthquakes off Fiji
## 81                 Random Numbers from Congruential Generator RANDU
## 82                           Lengths of Major North American Rivers
## 83                           Measurements on Petroleum Rock Samples
## 84                                             Student's Sleep Data
## 85                                 Brownlee's Stack Loss Plant Data
## 86                                 Brownlee's Stack Loss Plant Data
## 87                                 Brownlee's Stack Loss Plant Data
## 88                                       US State Facts and Figures
## 89                                       US State Facts and Figures
## 90                                       US State Facts and Figures
## 91                                       US State Facts and Figures
## 92                                       US State Facts and Figures
## 93                                       US State Facts and Figures
## 94                                       US State Facts and Figures
## 95                     Monthly Sunspot Data, from 1749 to "Present"
## 96                                   Yearly Sunspot Data, 1700-1988
## 97                               Monthly Sunspot Numbers, 1749-1983
## 98         Swiss Fertility and Socioeconomic Indicators (1888) Data
## 99                                 Yearly Treering Data, -6000-1979
## 100              Diameter, Height and Volume for Black Cherry Trees
## 101                           Populations Recorded by the US Census
## 102       Topographic Information on Auckland's Maunga Whau Volcano
## 103                     The Number of Breaks in Yarn during Weaving
## 104                  Average Heights and Weights for American Women
```

Conocer la información de los paquetes disponibles 

```r
paquetes <- library(help = "datasets")
head(paquetes$info[[2]])
```

```
## [1] "AirPassengers           Monthly Airline Passenger Numbers 1949-1960"   
## [2] "BJsales                 Sales Data with Leading Indicator"             
## [3] "BOD                     Biochemical Oxygen Demand"                     
## [4] "CO2                     Carbon Dioxide Uptake in Grass Plants"         
## [5] "ChickWeight             Weight versus age of chicks on different diets"
## [6] "DNase                   Elisa assay of DNase"
```

Cargar sets de datos directamente de estas bases


```r
datos_R<- iris
datos_R  
```

```
##     Sepal.Length Sepal.Width Petal.Length Petal.Width    Species
## 1            5.1         3.5          1.4         0.2     setosa
## 2            4.9         3.0          1.4         0.2     setosa
## 3            4.7         3.2          1.3         0.2     setosa
## 4            4.6         3.1          1.5         0.2     setosa
## 5            5.0         3.6          1.4         0.2     setosa
## 6            5.4         3.9          1.7         0.4     setosa
## 7            4.6         3.4          1.4         0.3     setosa
## 8            5.0         3.4          1.5         0.2     setosa
## 9            4.4         2.9          1.4         0.2     setosa
## 10           4.9         3.1          1.5         0.1     setosa
## 11           5.4         3.7          1.5         0.2     setosa
## 12           4.8         3.4          1.6         0.2     setosa
## 13           4.8         3.0          1.4         0.1     setosa
## 14           4.3         3.0          1.1         0.1     setosa
## 15           5.8         4.0          1.2         0.2     setosa
## 16           5.7         4.4          1.5         0.4     setosa
## 17           5.4         3.9          1.3         0.4     setosa
## 18           5.1         3.5          1.4         0.3     setosa
## 19           5.7         3.8          1.7         0.3     setosa
## 20           5.1         3.8          1.5         0.3     setosa
## 21           5.4         3.4          1.7         0.2     setosa
## 22           5.1         3.7          1.5         0.4     setosa
## 23           4.6         3.6          1.0         0.2     setosa
## 24           5.1         3.3          1.7         0.5     setosa
## 25           4.8         3.4          1.9         0.2     setosa
## 26           5.0         3.0          1.6         0.2     setosa
## 27           5.0         3.4          1.6         0.4     setosa
## 28           5.2         3.5          1.5         0.2     setosa
## 29           5.2         3.4          1.4         0.2     setosa
## 30           4.7         3.2          1.6         0.2     setosa
## 31           4.8         3.1          1.6         0.2     setosa
## 32           5.4         3.4          1.5         0.4     setosa
## 33           5.2         4.1          1.5         0.1     setosa
## 34           5.5         4.2          1.4         0.2     setosa
## 35           4.9         3.1          1.5         0.2     setosa
## 36           5.0         3.2          1.2         0.2     setosa
## 37           5.5         3.5          1.3         0.2     setosa
## 38           4.9         3.6          1.4         0.1     setosa
## 39           4.4         3.0          1.3         0.2     setosa
## 40           5.1         3.4          1.5         0.2     setosa
## 41           5.0         3.5          1.3         0.3     setosa
## 42           4.5         2.3          1.3         0.3     setosa
## 43           4.4         3.2          1.3         0.2     setosa
## 44           5.0         3.5          1.6         0.6     setosa
## 45           5.1         3.8          1.9         0.4     setosa
## 46           4.8         3.0          1.4         0.3     setosa
## 47           5.1         3.8          1.6         0.2     setosa
## 48           4.6         3.2          1.4         0.2     setosa
## 49           5.3         3.7          1.5         0.2     setosa
## 50           5.0         3.3          1.4         0.2     setosa
## 51           7.0         3.2          4.7         1.4 versicolor
## 52           6.4         3.2          4.5         1.5 versicolor
## 53           6.9         3.1          4.9         1.5 versicolor
## 54           5.5         2.3          4.0         1.3 versicolor
## 55           6.5         2.8          4.6         1.5 versicolor
## 56           5.7         2.8          4.5         1.3 versicolor
## 57           6.3         3.3          4.7         1.6 versicolor
## 58           4.9         2.4          3.3         1.0 versicolor
## 59           6.6         2.9          4.6         1.3 versicolor
## 60           5.2         2.7          3.9         1.4 versicolor
## 61           5.0         2.0          3.5         1.0 versicolor
## 62           5.9         3.0          4.2         1.5 versicolor
## 63           6.0         2.2          4.0         1.0 versicolor
## 64           6.1         2.9          4.7         1.4 versicolor
## 65           5.6         2.9          3.6         1.3 versicolor
## 66           6.7         3.1          4.4         1.4 versicolor
## 67           5.6         3.0          4.5         1.5 versicolor
## 68           5.8         2.7          4.1         1.0 versicolor
## 69           6.2         2.2          4.5         1.5 versicolor
## 70           5.6         2.5          3.9         1.1 versicolor
## 71           5.9         3.2          4.8         1.8 versicolor
## 72           6.1         2.8          4.0         1.3 versicolor
## 73           6.3         2.5          4.9         1.5 versicolor
## 74           6.1         2.8          4.7         1.2 versicolor
## 75           6.4         2.9          4.3         1.3 versicolor
## 76           6.6         3.0          4.4         1.4 versicolor
## 77           6.8         2.8          4.8         1.4 versicolor
## 78           6.7         3.0          5.0         1.7 versicolor
## 79           6.0         2.9          4.5         1.5 versicolor
## 80           5.7         2.6          3.5         1.0 versicolor
## 81           5.5         2.4          3.8         1.1 versicolor
## 82           5.5         2.4          3.7         1.0 versicolor
## 83           5.8         2.7          3.9         1.2 versicolor
## 84           6.0         2.7          5.1         1.6 versicolor
## 85           5.4         3.0          4.5         1.5 versicolor
## 86           6.0         3.4          4.5         1.6 versicolor
## 87           6.7         3.1          4.7         1.5 versicolor
## 88           6.3         2.3          4.4         1.3 versicolor
## 89           5.6         3.0          4.1         1.3 versicolor
## 90           5.5         2.5          4.0         1.3 versicolor
## 91           5.5         2.6          4.4         1.2 versicolor
## 92           6.1         3.0          4.6         1.4 versicolor
## 93           5.8         2.6          4.0         1.2 versicolor
## 94           5.0         2.3          3.3         1.0 versicolor
## 95           5.6         2.7          4.2         1.3 versicolor
## 96           5.7         3.0          4.2         1.2 versicolor
## 97           5.7         2.9          4.2         1.3 versicolor
## 98           6.2         2.9          4.3         1.3 versicolor
## 99           5.1         2.5          3.0         1.1 versicolor
## 100          5.7         2.8          4.1         1.3 versicolor
## 101          6.3         3.3          6.0         2.5  virginica
## 102          5.8         2.7          5.1         1.9  virginica
## 103          7.1         3.0          5.9         2.1  virginica
## 104          6.3         2.9          5.6         1.8  virginica
## 105          6.5         3.0          5.8         2.2  virginica
## 106          7.6         3.0          6.6         2.1  virginica
## 107          4.9         2.5          4.5         1.7  virginica
## 108          7.3         2.9          6.3         1.8  virginica
## 109          6.7         2.5          5.8         1.8  virginica
## 110          7.2         3.6          6.1         2.5  virginica
## 111          6.5         3.2          5.1         2.0  virginica
## 112          6.4         2.7          5.3         1.9  virginica
## 113          6.8         3.0          5.5         2.1  virginica
## 114          5.7         2.5          5.0         2.0  virginica
## 115          5.8         2.8          5.1         2.4  virginica
## 116          6.4         3.2          5.3         2.3  virginica
## 117          6.5         3.0          5.5         1.8  virginica
## 118          7.7         3.8          6.7         2.2  virginica
## 119          7.7         2.6          6.9         2.3  virginica
## 120          6.0         2.2          5.0         1.5  virginica
## 121          6.9         3.2          5.7         2.3  virginica
## 122          5.6         2.8          4.9         2.0  virginica
## 123          7.7         2.8          6.7         2.0  virginica
## 124          6.3         2.7          4.9         1.8  virginica
## 125          6.7         3.3          5.7         2.1  virginica
## 126          7.2         3.2          6.0         1.8  virginica
## 127          6.2         2.8          4.8         1.8  virginica
## 128          6.1         3.0          4.9         1.8  virginica
## 129          6.4         2.8          5.6         2.1  virginica
## 130          7.2         3.0          5.8         1.6  virginica
## 131          7.4         2.8          6.1         1.9  virginica
## 132          7.9         3.8          6.4         2.0  virginica
## 133          6.4         2.8          5.6         2.2  virginica
## 134          6.3         2.8          5.1         1.5  virginica
## 135          6.1         2.6          5.6         1.4  virginica
## 136          7.7         3.0          6.1         2.3  virginica
## 137          6.3         3.4          5.6         2.4  virginica
## 138          6.4         3.1          5.5         1.8  virginica
## 139          6.0         3.0          4.8         1.8  virginica
## 140          6.9         3.1          5.4         2.1  virginica
## 141          6.7         3.1          5.6         2.4  virginica
## 142          6.9         3.1          5.1         2.3  virginica
## 143          5.8         2.7          5.1         1.9  virginica
## 144          6.8         3.2          5.9         2.3  virginica
## 145          6.7         3.3          5.7         2.5  virginica
## 146          6.7         3.0          5.2         2.3  virginica
## 147          6.3         2.5          5.0         1.9  virginica
## 148          6.5         3.0          5.2         2.0  virginica
## 149          6.2         3.4          5.4         2.3  virginica
## 150          5.9         3.0          5.1         1.8  virginica
```

Conocer los nombres de las columnas 

```r
names(datos_R)
```

```
## [1] "Sepal.Length" "Sepal.Width"  "Petal.Length" "Petal.Width"  "Species"
```

Visualizar las primeras filas de la tabla

```r
head(datos_R)
```

```
##   Sepal.Length Sepal.Width Petal.Length Petal.Width Species
## 1          5.1         3.5          1.4         0.2  setosa
## 2          4.9         3.0          1.4         0.2  setosa
## 3          4.7         3.2          1.3         0.2  setosa
## 4          4.6         3.1          1.5         0.2  setosa
## 5          5.0         3.6          1.4         0.2  setosa
## 6          5.4         3.9          1.7         0.4  setosa
```


```r
summary(iris)
```

```
##   Sepal.Length    Sepal.Width     Petal.Length    Petal.Width   
##  Min.   :4.300   Min.   :2.000   Min.   :1.000   Min.   :0.100  
##  1st Qu.:5.100   1st Qu.:2.800   1st Qu.:1.600   1st Qu.:0.300  
##  Median :5.800   Median :3.000   Median :4.350   Median :1.300  
##  Mean   :5.843   Mean   :3.057   Mean   :3.758   Mean   :1.199  
##  3rd Qu.:6.400   3rd Qu.:3.300   3rd Qu.:5.100   3rd Qu.:1.800  
##  Max.   :7.900   Max.   :4.400   Max.   :6.900   Max.   :2.500  
##        Species  
##  setosa    :50  
##  versicolor:50  
##  virginica :50  
##                 
##                 
## 
```


### Importar datos desde internet 

Esta base de datos de cáncer de mama se obtuvo de la Universidad de Wisconsin del Dr. William Wolberg. El conjunto de datos provienen de un estudio de cáncer de mama en Wisconsin. Hay 681 casos de tumores potencialmente cancerosos, de los cuales 238 son realmente malignos. Cada característica se evalúa en una escala del 1 al 10, siendo 1 el más cercano a benigno y 10 el más cercano a maligno. 

Para descargar archivos de internet, usamos la función `download.file()`.


```r
help("download.file")
```

La función `download.file()` pide como argumento la url o la dirección de internet del archivo que queremos descargar y en dest, el nombre que tendrá el archivo en nuestra computadora.


```r
download.file(
  url = "https://raw.githubusercontent.com/jboscomendoza/r-principiantes-bookdown/master/datos/breast-cancer-wis.data", 
  dest = "breast-cancer-wis.data"
)
```


```r
tabla_cancer<-read_table("breast-cancer-wis.data")
```

```
## 
## -- Column specification --------------------------------------------------------
## cols(
##   `1000025,5,1,1,1,2,1,3,1,1,2` = col_character()
## )
```


```r
bcancer <- read.table(file = "breast-cancer-wis.data", header = FALSE, sep = ",")
```


```r
head(bcancer)
```

```
##        V1 V2 V3 V4 V5 V6 V7 V8 V9 V10 V11
## 1 1000025  5  1  1  1  2  1  3  1   1   2
## 2 1002945  5  4  4  5  7 10  3  2   1   2
## 3 1015425  3  1  1  1  2  2  3  1   1   2
## 4 1016277  6  8  8  1  3  4  3  7   1   2
## 5 1017023  4  1  1  3  2  1  3  1   1   2
## 6 1017122  8 10 10  8  7 10  9  7   1   4
```


```r
nombres <- c("id", "clump_t", "u_csize", "u_cshape", "m_adh", "spcs", "b_nuc", 
             "b_chr", "n_nuc", "mit", "class")
```


```r
bcancer <- read.table(file = "breast-cancer-wis.data", header = FALSE, sep = ",",
                      col.names = nombres)
```


```r
head(bcancer)
```

```
##        id clump_t u_csize u_cshape m_adh spcs b_nuc b_chr n_nuc mit class
## 1 1000025       5       1        1     1    2     1     3     1   1     2
## 2 1002945       5       4        4     5    7    10     3     2   1     2
## 3 1015425       3       1        1     1    2     2     3     1   1     2
## 4 1016277       6       8        8     1    3     4     3     7   1     2
## 5 1017023       4       1        1     3    2     1     3     1   1     2
## 6 1017122       8      10       10     8    7    10     9     7   1     4
```

### Exportar archivos CSV 

Vamos a guardar el data.frame `bcancer` como un archivo csv llamado **"bcancer.csv"** y **bcancer2.csv** utilizando el comando `write_._csv()` y `write.csv()` respectivamente. Las tablas se guardarán en nuestro directorio de trabajo actual.

```r
write_csv(bcancer, file = "bcancer.csv")
```


```r
write.csv(bcancer, file= "bcancer2.csv")
```


### Archivos CSV

También podemos trabajar con datos de archivos de texto de nuestra computadora. Importa archivos de texto plano con formato CSV (*coma-separated values*) que descargamos anteriormente. Usamos la función `read.csv` o `read_csv`.


```r
bcancer_tabla <- read_csv("bcancer.csv")
```

```
## Rows: 699 Columns: 11
```

```
## -- Column specification --------------------------------------------------------
## Delimiter: ","
## chr  (1): b_nuc
## dbl (10): id, clump_t, u_csize, u_cshape, m_adh, spcs, b_chr, n_nuc, mit, class
```

```
## 
## i Use `spec()` to retrieve the full column specification for this data.
## i Specify the column types or set `show_col_types = FALSE` to quiet this message.
```


```r
head(bcancer_tabla)
```

```
## # A tibble: 6 x 11
##        id clump_t u_csize u_cshape m_adh  spcs b_nuc b_chr n_nuc   mit class
##     <dbl>   <dbl>   <dbl>    <dbl> <dbl> <dbl> <chr> <dbl> <dbl> <dbl> <dbl>
## 1 1000025       5       1        1     1     2 1         3     1     1     2
## 2 1002945       5       4        4     5     7 10        3     2     1     2
## 3 1015425       3       1        1     1     2 2         3     1     1     2
## 4 1016277       6       8        8     1     3 4         3     7     1     2
## 5 1017023       4       1        1     3     2 1         3     1     1     2
## 6 1017122       8      10       10     8     7 10        9     7     1     4
```


```r
names(bcancer_tabla)
```

```
##  [1] "id"       "clump_t"  "u_csize"  "u_cshape" "m_adh"    "spcs"    
##  [7] "b_nuc"    "b_chr"    "n_nuc"    "mit"      "class"
```


```r
head(bcancer_tabla)
```

```
## # A tibble: 6 x 11
##        id clump_t u_csize u_cshape m_adh  spcs b_nuc b_chr n_nuc   mit class
##     <dbl>   <dbl>   <dbl>    <dbl> <dbl> <dbl> <chr> <dbl> <dbl> <dbl> <dbl>
## 1 1000025       5       1        1     1     2 1         3     1     1     2
## 2 1002945       5       4        4     5     7 10        3     2     1     2
## 3 1015425       3       1        1     1     2 2         3     1     1     2
## 4 1016277       6       8        8     1     3 4         3     7     1     2
## 5 1017023       4       1        1     3     2 1         3     1     1     2
## 6 1017122       8      10       10     8     7 10        9     7     1     4
```
Algunas veces los datos tienen ciertos problemas que hay que arreglar para importar correctamente los datos a R. `read_csv()` tiene opciones que facilitan la importación de archivos CSV: 

- `col_names`: `read_csv()` asume que la primera fila contiene los nombres de las variables. Esto puede cambiarse con **`col_names = FALSE`**. También puedes proveer los nombres a las variables (o columnas) con `col_names = c("X1", "X2")`

- `skip`:`read_csv()` por defecto importa todas las filas del archivo, pero puedes hacer que comience a importar en la fila que quieras con `skip = n`

- `na`: En algunos ficheros con datos tabulares, los NAs se especifican con algún carácter. Esto podemos tratarlo al leer los datos con el argumento `na = "xxx"`


### Archivos TXT

Importa y exporta los archivos de texto plano con formato de tabla (data.frame). Exportemos la tabla anterior como archivo txt usando `write.table`.


```r
write.table(x = bcancer, file = "bcancer.txt", sep = ",", 
            row.names = FALSE, col.names = TRUE)
```

Para importar un archivo txt, usamos `read.table`. El argumento `header` permite incorporar el encabezado del archivo que queremos importar mientras que el argumento `sep`. En el siguiente comando, el argumento `sep=","` le indica a R que nuestros datos están separados por el símbolo **","** o *coma*.

```r
bcancer_txt <- read.table("bcancer.txt")
```



```r
head(bcancer_txt)
```

```
##        id clump_t u_csize u_cshape m_adh spcs b_nuc b_chr n_nuc mit class
## 1 1000025       5       1        1     1    2     1     3     1   1     2
## 2 1002945       5       4        4     5    7    10     3     2   1     2
## 3 1015425       3       1        1     1    2     2     3     1   1     2
## 4 1016277       6       8        8     1    3     4     3     7   1     2
## 5 1017023       4       1        1     3    2     1     3     1   1     2
## 6 1017122       8      10       10     8    7    10     9     7   1     4
```

## Archivos xlsx o de Excel

Para importar o exportar archivos de Excel, es necesario utilizar la paquetería `"openxlsx"` que permite trabajar con documentos de Excel en R. La instalación de paqueterías se realiza sólo una vez. Una vez que la librería o paquetería esté instalada, puedes omitir este paso.


```r
install.packages("openxlsx", dependencies = TRUE)
```

Ahora cargaremos las paqueterías. El llamado de librerías deberá hacerse cada que inicies una nueva sesión en R.

```r
library(openxlsx)
```

### Importación de datos xlsx o de Excel

Importaremos un nuevo set de datos de Excel que puedes descargar de [aquí](https://drive.google.com/u/0/uc?id=1DmLiZZGq_MVkLYCMZ7rdeHydUZAoP-YW&export=download). Recuerda guardarlos en tu carpeta de trabajo.


```r
datosXLSX <- read.xlsx("iris.xlsx")
```



```r
head(datosXLSX)
```

```
##   Sepal.Length Sepal.Width Petal.Length Petal.Width Species
## 1          5.1         3.5          1.4         0.2  setosa
## 2          4.9           3          1.4         0.2  setosa
## 3          4.7         3.2          1.3         0.2  setosa
## 4          4.6         3.1          1.5         0.2  setosa
## 5            5         3.6          1.4         0.2  setosa
## 6          5.4         3.9          1.7         0.4  setosa
```

### Exportación de datos en Excel

Vamos a exportar el data.frame `datosXLSX` que creamos anteriormente como un archivo de Excel llamado **"datos.xlsx"** utilizando el comando `write.xlsx()`. El archivo se guardará en nuestro directorio de trabajo  actual.


```r
write.xlsx(tablaDE, "datos.xlsx")
```


## Ejercicio

Vamos a crear un data.frame para practicar cómo exportar los datos.

```r
DosisX <- c(46, 20, 80, 100, 63)
DosisY <- c(6, 50, 70, 70, 63)
Lcelular <- c("MCF7", "Hela", "IPC-366", "T47D", "ZR75-1")
tablaDE <- data.frame(DosisX, DosisY, Lcelular)
tablaDE
```

```
##   DosisX DosisY Lcelular
## 1     46      6     MCF7
## 2     20     50     Hela
## 3     80     70  IPC-366
## 4    100     70     T47D
## 5     63     63   ZR75-1
```

### Exportar como TXT

Vamos a guardar el data.frame `tablaDE` como un archivo de texto llamado **"datos.txt"** utilizando el comando `write.table()`. La tabla se guardará en nuestro directorio de trabajo  actual.

```r
write.table(tablaDE, "datos.txt")
```


### Exportar como CSV

Vamos a guardar el data.frame `tablaDE` como un archivo csv llamado **"datos.csv"** utilizando el comando `write.csv()`. La tabla se guardará en nuestro directorio de trabajo  actual.

```r
write.csv(tablaDE, "datos.csv")
```

### Argumentos al exportar

Así como al importar archivos existen diversos argumentos que podemos utilizar para darles ciertas indicaciones a R, también lo podemos hacer al momento de exportar los datos. Los siguientes argumentos se pueden usar con `write.csv()` y `write.table()`.

`row.names=FALSE` nos permite suprimir los nombres de las filas

```r
write.csv(tablaDE, "datos1.csv", row.names=FALSE)
```

Para indicar la separación del archivo utilizamos `sep`. Vamos a usar la tabulación como separador poniendo `sep="\t"`.

```r
write.csv(tablaDE, "datos2.csv", row.names=FALSE, sep="\t")
```

Para suprimir los nombres de las columnas, usamos `col.names=FALSE`

```r
write.csv(tablaDE, "datos3.csv", row.names=FALSE, sep="\t", col.names=FALSE)
```
