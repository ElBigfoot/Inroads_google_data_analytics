---
title: "cyclistyic_Inroadsgoogle_data_ana"
author: "Óscar González"
date: "2023-06-01"
output: html_document
---



##  Paquetes necesarios para Cyclistic------------------------------------------
options=(warn=-1)
install.packages("tidyverse")
install.packages("modeest")
install.packages("lubridate")
install.packages("ggplot2")
install.packages("scales")
install.packages("dplyr")

## Librerias necesarias para el proyecto----------------------------------------

library(tidyverse)
library(lubridate)
library(ggplot2)
library(scales)
library(dplyr)
library(janitor)
library(readr)
library(stringr) 
library(skimr)
library(scales)
library(data.table)
library(plyr)
library(readxl)
library(modeest)
#library(viridis)

### Preguntar 

#=====================
# PASO 1: Recopilación de Datos
#=====================
## Convertir CSV a Dataframe ------------------------------------------->


### abril 2022 a abril 2023
Abril_22 <- read_csv("/home/elbigfut/Escritorio/proyecto_data_analytics_googleInroads/Abril_2022/abril_2022_tripdata.csv")
Mayo_22 <- read_csv("/home/elbigfut/Escritorio/proyecto_data_analytics_googleInroads/Mayo_2022/mayo_2022_tripdata.csv")
Junio_22 <- read_csv("/home/elbigfut/Escritorio/proyecto_data_analytics_googleInroads/Junio_2022/junio_2022_tripdata.csv")
Julio_22 <- read_csv("/home/elbigfut/Escritorio/proyecto_data_analytics_googleInroads/Julio_2022/julio_2022_tripdata.csv")
Agosto_22 <- read_csv("/home/elbigfut/Escritorio/proyecto_data_analytics_googleInroads/Agosto_2022/agosto_2022_tripdata.csv")
Sept_22 <- read_csv("/home/elbigfut/Escritorio/proyecto_data_analytics_googleInroads/Sept_2022/sept_2022_tripdata.csv")
Oct_22 <- read_csv("/home/elbigfut/Escritorio/proyecto_data_analytics_googleInroads/Oct_2022/oct_2022_tripdata.csv")
Nov_22 <- read_csv("/home/elbigfut/Escritorio/proyecto_data_analytics_googleInroads/Nov_2022/nov_2022_tripdata.csv")
Dic_22 <- read_csv("/home/elbigfut/Escritorio/proyecto_data_analytics_googleInroads/Dic_2022/dic_2022_tripdata.csv")
Enero_23 <- read_csv("/home/elbigfut/Escritorio/proyecto_data_analytics_googleInroads/Enero_2022/enero_2022_tripdata.csv")
Febrero_23 <- read_csv("/home/elbigfut/Escritorio/proyecto_data_analytics_googleInroads/Febrero_2022/febrero_2023_tripdata.csv")
Marzo_23 <- read_csv("/home/elbigfut/Escritorio/proyecto_data_analytics_googleInroads/Marzo_2022/marzo_2023_tripdata.csv")
Abril_23 <- read_csv("/home/elbigfut/Escritorio/proyecto_data_analytics_googleInroads/Abril_2022/abril_2023_tripdata.csv")

#====================================================
# Paso 2: juntas datos y obtener un solo archivo 
#====================================================

# Se crea un dataframe con los datos con el comando join
# Se renombran las columnas 
colnames(Abril_22)
colnames(Mayo_22)
colnames(Junio_22)
colnames(Julio_22)
colnames(Agosto_22)
colnames(Sept_22)
colnames(Oct_22)
colnames(Nov_22)
colnames(Dic_22)
colnames(Enero_23)
colnames(Febrero_23)
colnames(Marzo_23)
colnames(Abril_23)

# Se renombran las columnas 

ride_id = id_viaje
rideable_type = bici_id 
started_at = inicio_tiempo  
ended_at = finalizo_tiempo  
start_station_name = desde_nombre_estacion 
start_station_id = desde_estacion_id 
end_station_name = nombre_estación 
end_station_id = hacia_estacion_id 
member_casual = tipoUsuario

# Se revisan los dataframes y se buscan incongruencias

str(Abril_22)
str(Mayo_22)
str(Junio_22)
str(Julio_22)
str(Agosto_22)
str(Sept_22)
str(Oct_22)
str(Nov_22)
str(Dic_22)
str(Enero_23)
str(Febrero_23)
str(Marzo_23)
str(Abril_23)

# Se convierte id_viaje y bici_id a caracter para ordenar correctamente.


Abril_22 <- mutate(Abril_22, id_viaje = as.character(id_viaje)
                 ,bici_id = as.character(bici_id))
Mayo_22 <- mutate(Mayo_22, id_viaje = as.character(id_viaje)
                    ,bici_id = as.character(bici_id))  
Junio_22 <-mutate(Junio_22, id_viaje = as.character(id_viaje)
                    ,bici_id = as.character(bici_id))
Julio_22 <-mutate(Julio_22, id_viaje = as.character(id_viaje)
                  ,bici_id = as.character(bici_id))
Agosto_22 <-mutate(Agosto_22, id_viaje = as.character(id_viaje)
                  ,bici_id = as.character(bici_id))
Sept_22 <-mutate(Sept_22, id_viaje = as.character(id_viaje)
                  ,bici_id = as.character(bici_id))
Oct_22 <-mutate(Oct_22, id_viaje = as.character(id_viaje)
                  ,bici_id = as.character(bici_id))
Nov_22 <-mutate(Nov_22, id_viaje = as.character(id_viaje)
                ,bici_id = as.character(bici_id))
Dic_22 <-mutate(Dic_22, id_viaje = as.character(id_viaje)
                ,bici_id = as.character(bici_id))
Enero_23 <-mutate(Enero_23, id_viaje = as.character(id_viaje)
                ,bici_id = as.character(bici_id))