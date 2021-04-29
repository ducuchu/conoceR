## Tus primeros pasos

*R* es un entorno y lenguaje de programación con enfoque al análisis estadístico (un lenguaje siempre tiene una estructura). Es ampliamente utilizado en investigación especialmente por su característica de ser _reproducible_ (todos pueden ver el código y utilizarlo en sus análisis). Es creado por estadísticos, por lo tanto es especialmente útil para hacer estos análisis.

## R versus otros software

Creo que lo más importante de *R* es que es _software libre_ significa que puedes usarlo libremente y distribuirlo. También significa que hay muchas personas dispuesto a ayudarte y hacen este tipo de ayuda o cursos. Las comunidades de software libre, mantienen los paquetes, los crean y ayudan. Aquí hay algunas razones para utilizar *R*:
- Es multiplataforma (puede ser instalado en equipos con diferentes sistemas operativos).
- Es software libre
- Tiene una amplia gama de paquetes que pueden ampliar las funcionalidades de cálculo y graficación (Ciencias naturales, ciencias sociales, ingeniería, etc.)
- Específico para realizar: limpieza, análisis, visualización y modelado de datos 

## Interfaz de usuario
*R* es un lenguaje de programación, lo que permite ser versatil pero al mismo tiempo, es más difícil de aprender para los usuarios. Es por eso, que generalmente se utilizan interfaces que faciliten esta tarea. Como se puede ver en la imagen, *R* es el "motor" mientras que el modelo del carro, es la interfaz. Los usuarios deben sentirse cómodos con la interfaz que seleccionen. Colocó algunas interfaces que se pueden usar. En este ejemplo utilizaremos RStudio, por su facilidad y funcionalidad.

Figura 1: Analogía de interfaz de usuario
![alt text](https://raw.githubusercontent.com/ducuchu/conoceR/gh-pages/GithubR1.png)


## Conociendo RStudio
RStudio es una buena interfaz de usuario, porque te permite observar en cuatro paneles, la información importante de tu código. Abajo se tiene un diagrama de las diferentes ventanas de R y como se pueden conectar entre sí. Aunque se puede trabajar por separado, una forma intuitiva de verlo es la siguiente: (1) Colocas tu código en el panel para esto (el código se le llama script) (2) el código se ejecuta en el área de consola (coloquialmente se le da el nombre de "correr el código"), el código genera variables y gráficas que puedes visualizarlo en los dos paneles derechos (superior e inferior).
Figura 2: Interfaz RStudio
![alt text](https://raw.githubusercontent.com/ducuchu/conoceR/gh-pages/GithubR2.png)

### Tipos de datos

Hay 5 tipos de datos básicos en R (**para asignar una variable se coloca <- o =**)

| Tipo | Definición | código |  Notas | 
| ------------- | ------------- | ------------- | ------------- |
| Numérico/Numeric  | números decimales   | ``` a <-1.3 ``` | Nota el punto decimal |
| Entero/Integer  | números enteros   | ``` a <-1 ``` | Nota que no tiene punto decimal |
| Texto/Character  | cadenas de caracteres   | ``` a <- "Hola" ``` | utiliza " " |
| Logico/logical  | Verdadero o falso   | ``` a <- TRUE ``` | *no* utiliza "" |

Estos datos (tipos *atomicos*) se pueden agrupar produciendo

| Dimensión | Homogéneo | Heterogéneo | 
| ------------- | ------------- | ------------- |
| **una** dimensión  | ***vector***   | lista |
| **dos** dimensiones  | matrix   | ***data frame*** |
| **n** dimensiones  | array   |  | 

En código:
```markdown
#Tipos de datos
#Asignar variables

i<-1

#como saber que tipo de variable es
is.numeric(i)
is.character(i)
is.integer(i)

#Como trasnformarlo a otro tipo de variable
d<-as.integer(i)
d
is.numeric(d)
is.integer(d)
d.9<-d-0.1
is.integer(d.9)
```
#### Conociendo los vectores

Los vectores son, el elemento más básico que contienen la misma clase de datos.

```markdown
#Trabajando con Vectores
#Mi primer vector
pH<-c(7.2,7.8,7.6,6.8,8.1,9.6)

#Operaciones
d.9*pH
pH+pH
d.9+pH
pHo<-d.9*pH
#Selección de valores  --- comando: nombre vector[]
pH[3]

vector<-c("hola",1.2,TRUE)
d.9*vector
vector+vector
d.9+vector

#Creando secuencias de numeros --- comando: inicial:final
x<-c(1:6)

```
#### Matrices

Las matrices son un arreglo de dos dimensiones donde los elementos son del mismo tipo, generalmente numéricos. Especialmente útiles para hacer análisis matricial. Maneja **número de filas y número de columnas, que se conocen como dimensiones**. 

```markdown
#creando matrices:

dim(x) <- c(4,5) # ¿Que hace dim? coloca help(dim) en consola y lo veras.
x

matrix(data = 1:20, nrow = 4, ncol = 5, byrow = F)
y<-matrix(data = 1:20, nrow = 4, ncol = 5, byrow = T)
dim(y) #genera las dimensiones filas y columnas

#Encontrando datos y operaciones
y[1,1]

x*y

```
#### Data Frames

Las bases de datos son un conjunto de datos, que puede entenderse como una lista de vectores. Puede estar conformado por diferentes tipos de datos. Es la tabla de datos por excelencia: las columnas son las variables que se miden y las filas las observaciones. 


```markdown
#Aca se observa como una Dataframe es un listado de vectores
#Edad (años), peso (kg), estatura (cm), genero (F:Femenino, M:Masculino y O:Otro)
db <- data.frame(edad=c(19,20,27,21,21,18,25),
                  peso=c(45,52,140,70,63,90,98), 
                  estatura=c(1.50,1.60,1.55,1.72,1.67,1.60,1.56),
                  genero=c("F","M","F","M","M","F","F"))
db

#revisa la clase:
class(db)

#puedo obtener y cambiar el nombre de las columnas muy facilmente

#muestra los nombres de las columnas
colnames(db) 

colnames(db)<-c("age","weight","height","gender")

#Primos pasos para analizar datos

#Seleccionar una columna
db$age

#Estadística descriptiva
#media (mean), desviación estandar (sd), valor mínimo (min), valor máximo (max)
mean(db$age)

#creando columnas rapidamente
db$IMC<-db$weight/(db$height)^2
view(db)

#viendo las diferentes funciones genericas que tiene R
help("groupGeneric")

#extrañendo datos de un archivo .csv
#por facilidad es bueno seleccionar la ubicacion
db<-read.csv("dbtestate.csv")

#Bases de datos precargadas en R (existen varias)

#En R existen varias bases de datos precargados
data()
head(cars)

cars

```
### Paquetes en R

Un paquete en R permite:
-Reproducibilidad
-Aumento de las características del análisis
-Flexibilidad

Es una colección de funciones, datos y código R que permite generar una instrucción específica para R. Hay paquetes
muy específicos para cada área del conocimiento (ejemplo: vegan).

```markdown
#puedes saber que paquetes tienes en:
search()

#instalando paquetes en R
install.packages("psych")
install.packages("ggplot2")

# Se requiere cargar el paquete cada vez que se utiliza (cargar paquetes en memoria)
library(ggplot2)
library(psych)

```

## Manipulación de datos
```markdown
###############################################################################
# Manipulando los datos

# Utilización de una base precargada del paquete ggplot2


# Como ver el resumen de una DataFrame
head(mpg)

#resumiendo nuestras variables
str(mpg)
summary(mpg) #puede determinar si hay NA
describe(mpg) #función del paquete psych

## Tabla de frecuencias (por variable)
table(mpg$cyl)
hist(mpg$cyl)
#Frecuencias relativas
prop.table(table(mpg$cyl))

#graficando rapidamente factores
table(mpg$class)
barplot(table(mpg$class))

#Necesitamos saber si hay datos faltantes NA
table(mpg$cyl,useNA="ifany")

#Cruzando datos rapidamente
table(mpg$cyl, mpg$class)
boxplot(mpg$cyl~mpg$class)

```

### Bibliografía
1. Libro: R for Data Science [Github](https://r4ds.had.co.nz/index.html)
2. Angelo Santana, Carmen N. Hernández, Departamento de Matemáticas (2016) [link](https://estadistica-dma.ulpgc.es/cursoR4ULPGC/index.html)
3. Paúl Bravo L. & Francisco Salgado C. (2019) [link](https://bookdown.org/chescosalgado/intro_r/)
4. Sonia Mendizábal. Taller introducción a R [Github](https://songeo.github.io/introduccion-r-bookdown/)
5. Repositorio de RLadies  [Github](https://github.com/rladies)


