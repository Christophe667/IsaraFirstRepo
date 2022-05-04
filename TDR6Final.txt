## Date : 10.05.2020
## VP & VT
## Script TDR6


######## EXERCICE OPTIONNEL : utilisez le package rstudioapi pour afficher le poly dans le Viewer


######## EXERCICE  : importez DesIris.txt, testez les scripts et commentez

# Import
iris1 <- read.table("DesIris.txt", header=TRUE, dec=".", sep=" ")  

# S?lection dans une table 
iris1[ ,1]   # s?lection d'une colonne par son num?ro avec [,n]
iris1[1, ]   # s?lection d'une ligne par son num?ro avec [n,]
iris1[1,2]  # s?lection d'une case avec [nlig,ncol]


iris1$SepalLength    # poursuivez les commentaires

iris1[c(1,5,10), ] #sélectionner les lignes 1 5 et 10
iris1[-(5:30), ] # désélectionner lignes  5 à 30
iris1[ ,1:4] #sélectionner les colonnes 1 à 4
iris1[c(1,5,10) , 1:4] #sélectionner lignes 1 5 10 pour les colonnes de 1 à 4
iris1[iris1$Species=="virginica" , ] # sélection conditionnelle
iris1[iris1$SepalLength > 7 , ] # sélectionner sépales taille>7
iris1[iris1$SepalLength < 6  &  iris1$Species=="virginica", ] #sélectionner ligne espece virginica avec sépales > 6

# S?lection dans un vecteur
iris1$SepalLength[iris1$Species=="virginica"] #longueur des sépales pour espece virginica
iris1[iris1$Species=="virginica", ]$SepalLength

# Calculs sur des sous-ensembles
apply(iris1[,1:4], MARGIN=2, mean) #pour les colonnes 1 à 4, calcul de la moyenne de la longueur des sépales / pétales
tapply(iris1$SepalLength, iris1$Species, mean) # moyenne de la taille des sépales pour les différentes espèces




######## EXERCICE  : cr?ation du vecteur slv pour "sepal length  virginica" et statistiques

# cr?er slv
slv <- iris1$SepalLength[iris1$Species=="virginica"]

# testez et commentez
mean(slv)
var(slv)
sqrt(var(slv))
sd(slv)
min(slv)
max(slv)
range(slv)
sort(slv)
rev(slv)
sum(slv)
cumsum(slv)
median(slv)
quantile(slv,0.25)
quantile(slv)
length(slv)


######## EXERCICE  : cr?ation de variables

# le nom des lignes
n <- nrow(iris1)           # nrow() : nombre de lignes
noms <- paste("iris", 1:n) # paste() : coller
head(noms)

# le rapport de forme
rapport <- iris1$PetalLength/iris1$PetalWidth  
head(rapport)

# v?rification des longueurs 
length(noms); length(rapport); nrow(iris1)

# ajout
names(iris1)
iris1$noms <- noms
names(iris1)

iris2 <- data.frame(iris1, rapport)
names(iris2)

autre <- 1:3
iris1$num <- autre
iris1$num

# Quelle est l'esp?ce pour laquelle les p?tales ont la forme la plus ?troite 



######## EXERCICE  : t3var

t3var <- read.table("t3var.txt",header=TRUE,sep="\t") #import des données
head(t3var)
names(t3var) #identification noms variables : sexe, poi, tai

#statistiques
dim(t3var) #Nb ligne et colonne
str(t3var) # Nb variables et Nb individus

#select 1, 10 , 20
t3var[c(1,10,20),]

#select femmes > 170cm
femp170 <- t3var[t3var$tai > 170 & t3var$sexe=="f",]
femp170
nrow(femp170) #Nb de femme de plus de 170 cm

#variables pr individus 1 à 20 sauf première
t3var[10:20, -1]

tai <- t3var$tai
sexe <- t3var$sexe
taifmoy <- mean(tai[sexe=="f"]) #taille moyenne des femmes
taifmoy

#select femmes taille>à la moyenne
fsupmoy <- t3var[tai>taifmoy & sexe=="f" ,]
fsupmoy
nrow(fsupmoy) #Nb femmes taille > moyenne

#Moyenne poids pour tous
poi <- t3var$poi
mean(poi)

#Moyenne poids homme 
mean(poi[sexe=="h"])

#moyenne poids femme
mean(poi[sexe=="f"])

#variance poids pour tous
var(poi)

#variance poids homme
var(poi[sexe=="h"])

#variance poids femme
var(poi[sexe=="f"])

#calcul IMC

