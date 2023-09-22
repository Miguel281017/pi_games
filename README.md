Proyecto Individual 1 - Data Science datapt03 - Henry


# Proyecto Individual Steam, plataforma multinacional de videojuegos de Miguel Britez

![](https://i0.wp.com/xperimentalhamid.com/wp-content/uploads/2021/05/Steam-Unlocked.png?fit=1300%2C800&ssl=1&is-pending-load=1)

## API de Sistema de consultas y recomendaciones de juego.


## Introducción

Este proyecto simula el rol de un MLOps Engineer, es decir, la combinación de un Data Engineer y Data Scientist, para la plataforma multinacional de videojuegos Steam. Para su desarrollo, se entregan unos datos y se solicita un Producto Mínimo Viable que muestre una API deployada en un servicio en la nube y la aplicación de un modelo de Machine Learning.

## Contexto

Steam es una plataforma de distribución digital de videojuegos desarrollada por Valve Corporation. Fue lanzada en septiembre de 2003 como una forma para Valve de proveer actualizaciones automáticas a sus juegos, pero finalmente se amplió para incluir juegos de terceros. Cuenta con más de 325 millones de usuarios y más de 25.000 juegos en su catálogo. Es importante tener en cuenta que las cifras publicadas por SteamSpy son hasta el año 2017, porque a principios de 2018 Steam limitó la forma de obtener estadísticas, por eso no hay datos tan precisos.

## Desarrollo y arquitectura

En un principio se cuenta con 3 archivos json:

* australian_user_reviews.json: Contiene datos relacionados a reseñas y recomendaciones.
* australian_users_items.json: Contiene datos relacionados a usuarios, juegos, horas jugadas.
* output_steam_games.json: Contiene datos relacionados a los videojuegos, empresas desarrolladoras, género del juego.

Se realiza ETL de cada uno de los tres archivos: se abren se limpian, corrigen y desanidan. Se guardan como csv. De aquí obtenemos:

* games.csv
* games_desanidado.csv
* 2reviews_desanidado.csv
* items_desanidado.csv

Luego de un EDA, estudiando las necesidades del negocio y la naturaleza de las consultas requeridas, hacemos uniones entres los archivos, groupby, recortes y eliminación de columnas innecesarias, guardando archivos csv mucho más compactos y sencillos, que nos utilizaremos dependiendo de la consulta:

* userdata.csv
* reviews_desanidado.csv
* userforgenre.csv
* developer.csv
* sentiment_analysis.csv
* recomendacion_juego.csv

Se cuenta con los archivos ipynb correspondientes para hacer un seguimiento del ETL y EDA (la explicación de los procesos se encuentra dentro de cada archivo).
Los archivos son:

* ETL_Games.ipynb
* ETL_Items.ipynb
* ETL_Reviews.ipynb

* transformaciones.ipynb (aquí se hace una transformación distinta que obedece a las necesidades de cada consulta específica, relacionando los 3 csv anteriores)




 En ([main.py](https://github.com/Miguel281017/pi_games/blob/main/main.py)) encontraremos: 

* La creación de la API
* La importación de las librerías necesarias
* La importación de los distintos csv que utilizaremos
* Las 7 funciones disponibles para ser consultadas mediante la API

En el archivo requirements.txt tenemos la lista de las librerías a utilizar

Los resultados están disponibles en un sitio de Render de acceso público, desde donde se pueden realizar las consultas

## Las funciones API : 
1. userdata(user_id: str): Proporcionar cantidad de dinero gastado, porcentaje de recomendaciones positivas y cantidad de items del usuario solicitado.
2. countreviews(fecha1: str,fecha2: str): Proporcionar cantidad de usuarios que dieron opiniones entre las fechas dadas y el porcentaje de recomendaciones positivas.
3. genre(genero: str): Proporcionar el puesto en el que se encuentra el género indicado en el ranking de horas jugadas.
4. userforgenre(genero: str): Proporcionar 5 usuarios con más horas de juego en el género indicado.
5. developer(desarrollador: str): Proporcionar cantidad de items y porcentaje de contenido gratis por año de la empresa indicada.
6. sentiment_analysis(año: int): Proporcionar la cantidad de reseñas del año indicado, categorizadas en positivo, negativo y neutral.
7. recomendacion_juego(item_id: int): Proporcionar una lista con 5 juegos recomendados similares al ingresado.


## Enlaces

Acceso a la aplicación ([FastApi](https://pi-games.onrender.com/docs))

Video en ([Youtube](https://youtu.be/9d8_CqSPvzE))

