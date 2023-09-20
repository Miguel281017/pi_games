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

Se cuenta con los archivos ipynb correspondientes para hacer un seguimiento del ETL y EDA (la explicación de los procesos se encuentra dentro de cada archivo), y tener disponible el proceso ante la eventual llegada de nuevos datos.
Los archivos son:

* ETL_Games.ipynb
* ETL_Items.ipynb
* ETL_Reviews.ipynb

* transformaciones.ipynb (aquí se hace una transformación distinta que obedece a las necesidades de cada consulta específica, relacionando los 3 csv anteriores)




 En ([main.py](https://github.com/Miguel281017/pi_games/blob/main/main.py)) 

* La creación de la API
* La importación de las librerías necesarias
* La importación de los distintos csv que utilizaremos
* Las 7 funciones disponibles para ser consultadas mediante la API

En el archivo requirements.txt tenemos la lista de las librerías a utilizar

Los resultados están disponibles en un sitio de Render de acceso público, desde donde se pueden realizar las consultas

Las funciones API : def userdata( User_id : str ): Devuelve cantidad de dinero gastado por el usuario, el porcentaje de recomendación en base a reviews.recommend y cantidad de items.
def countreviews( YYYY-MM-DD y YYYY-MM-DD : str ): Devuelve Cantidad de usuarios que realizaron reviews entre las fechas dadas y, el porcentaje de recomendación de los mismos en base a reviews.recommend.
def genre( género : str ): Devuelve el puesto en el que se encuentra un género sobre el ranking de los mismos analizado bajo la columna PlayTimeForever.
def userforgenre( género : str ): Devuelve Top 5 de usuarios con más horas de juego en el género dado, con su URL (del user) y user_id.
def developer( desarrollador : str ): Devuelve Cantidad de items y porcentaje de contenido Free por año según empresa desarrolladora.
def sentiment_analysis( año : int ): Según el año de lanzamiento, se devuelve una lista con la cantidad de registros de reseñas de usuarios que se encuentren categorizados con un análisis de sentimiento.
def recomendacion_juego( id de producto ): Ingresando el id de producto, recibimos una lista con 5 juegos recomendados similares al ingresado.


## Enlaces

Acceso a la aplicación ([FastApi](https://pi-games.onrender.com/docs))

