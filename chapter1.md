---
title: Data
description: >-
  This is a template chapter.


---
## Population data

```yaml
type: NormalExercise
lang: r
xp: 100
skills: 1
key: b9c7132246
```

Introduction

`@instructions`
The dataset is available from webpage [http://vliss.helsinki.fi/chapter2/province91-population.html](url). Use read.table() to read the data.

Province91 population VARIABLES:
Auxiliary variables in the frame (x-variables). Values of x-variables known for all population elements:
    Stratum indicator
    Cluster indicator
    Id = Case ID
    Municipality
    POP91 = Population in 1991
    HOU85 = Number of households (1985 Census)
    URB85 = Urbanization (1=town, 0=other)
Potential study variables (y-variables):
    LAB91 = Size of labour force
    UE91 = Number of unemployed

NOTE: Here we make an (UNREALISTIC) assumption that all values of the y-variables also are known. This is for pedagogical purposes. In practice, y-values are known (measured) for the sample elements only but x-variables are assumed known.

`@hint`
Run codes.


`@sample_code`
```{r}
# read Province91 text dataset
province91 <- read.table("province91.txt",header = TRUE)

# print head of dataset
head(province91)

# more info
str(province91)
install.packages("Hmisc")
library(Hmisc)
describe(province91)

# Add labels:
label(province91$Stratum) <- "Stratum" 
label(province91$Cluster) <- "Cluster" 
label(province91$Id) <- "Id number" 
label(province91$Municipality) <- "Name of municipality"
label(province91$POP91) <- "Population in 1991" 
label(province91$POP91) <- "Population in 1991" 
label(province91$LAB91) <- "Labour force in 1991" 
label(province91$UE91) <- "Unemployed in 1991" 
label(province91$HOU85) <- "Households in 1985" 
label(province91$URB85) <- "Urbanization in 1985"

# the structure of the data
str(province91)
# view the data
View(province91)
```
`@solution`
```{r}
# read Province91 text dataset
province91 <- read.table("province91.txt",header = TRUE)

# print head of dataset
head(province91)

# more info
str(province91)
install.packages("Hmisc")
library(Hmisc)
describe(province91)

# Add labels:
label(province91$Stratum) <- "Stratum" 
label(province91$Cluster) <- "Cluster" 
label(province91$Id) <- "Id number" 
label(province91$Municipality) <- "Name of municipality"
label(province91$POP91) <- "Population in 1991" 
label(province91$POP91) <- "Population in 1991" 
label(province91$LAB91) <- "Labour force in 1991" 
label(province91$UE91) <- "Unemployed in 1991" 
label(province91$HOU85) <- "Households in 1985" 
label(province91$URB85) <- "Urbanization in 1985"

# the structure of the data
str(province91)
# view the data
View(province91)
```






---
## Descriptive statistics for population

```yaml
type: NormalExercise

xp: 100

key: a54011584f
```

Descriptive statistics for population

`@instructions`
Try commands summary(), tapply().

`@hint`
Run codes.

`@pre_exercise_code`
```{r}
province91 <- read.table("province91.txt",header = TRUE)
```
`@sample_code`
```{r}
# some basic statistics
summary(province91)

# Unemployed in 1991 by stratum
tapply(province91$UE91, province91$Stratum, mean) # use na.rm=TRUE if missing values

# Correlations:
# first select variables
corrdata <- c("POP91", "LAB91", "UE91", "HOU85", "URB85")
popdata <- province91[ ,corrdata]
cor(popdata)
#round(cor(popdata, use="complete.obs"),2)
# save matrix
corrmatrix <- cor(popdata) 

# Visualize correlations
install.packages("corrplot") # install package corrplot
library(corrplot) # load package corrplot
corrplot(corrmatrix, method = "circle")
corrplot(corrmatrix, method = "number")
corrplot(corrmatrix, method = "ellipse")
corrplot(corrmatrix, method=c("number"))
```
`@solution`
```{r}
# some basic statistics
summary(province91)

# Unemployed in 1991 by stratum
tapply(province91$UE91, province91$Stratum, mean) # use na.rm=TRUE if missing values

# Correlations:
# first select variables
corrdata <- c("POP91", "LAB91", "UE91", "HOU85", "URB85")
popdata <- province91[ ,corrdata]
cor(popdata)
#round(cor(popdata, use="complete.obs"),2)
# save matrix
corrmatrix <- cor(popdata) 

# Visualize correlations
install.packages("corrplot") # install package corrplot
library(corrplot) # load package corrplot
corrplot(corrmatrix, method = "circle")
corrplot(corrmatrix, method = "number")
corrplot(corrmatrix, method = "ellipse")
corrplot(corrmatrix, method=c("number"))
```




