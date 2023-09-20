# Proyecto_Individual_1

Steam, plataforma multinacional de videojuegos.
![](https://blog.soyhenry.com/content/images/2021/05/PRESENTACION-3.jpg)

## API de Sistema de consultas y recomendaciones de juego.


## Introducción

Este proyecto simula el rol de un MLOps Engineer, es decir, la combinación de un Data Engineer y Data Scientist, para la plataforma multinacional de videojuegos Steam. Para su desarrollo, se entregan unos datos y se solicita un Producto Mínimo Viable que muestre una API deployada en un servicio en la nube y la aplicación de dos modelos de Machine Learning, por una lado, un análisis de sentimientos sobre los comentarios de los usuarios de los juegos y, por otro lado, la recomendación de juegos a partir de dar el nombre de un juego y/o a partir de los gustos de un usuario en particular.

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

* 1userdata.csv
* 2reviews_desanidado.csv
* 4userforgenre.csv
* 5developer.csv
* 6sentiment_analysis.csv
* 7recomendacion_juego.csv

Se cuenta con los archivos ipynb correspondientes para hacer un seguimiento del ETL y EDA (la explicación de los procesos se encuentra dentro de cada archivo), y tener disponible el proceso ante la eventual llegada de nuevos datos.
Los archivos son:

* ETL_Games.ipynb
* ETL_Items.ipynb
* ETL_Reviews.ipynb

* transformaciones.ipynb (aquí se hace una transformación distinta que obedece a las necesidades de cada consulta específica, relacionando los 3 csv anteriores)

* prueba_funciones.ipynb (notebook donde se encuentran importadas las librerías y desarrolladas las 7 funciones. Se utiliza como prueba antes del main.py)

## Resultados

En el archivo main.py tenemos:

* La creación de la API
* La importación de las librerías necesarias
* La importación de los distintos csv que utilizaremos
* Las 7 funciones disponibles para ser consultadas mediante la API

En el archivo requirements.txt tenemos la lista de las librerías a utilizar

Los resultados están disponibles en un sitio de Render de acceso público, desde donde se pueden realizar las consultas


## Enlaces

Tenemos disponibles todos los archivos ipynb, txt, py, csv necesarios en el siguiente repositorio de GITHUB:

* https://github.com/Jeremias44/Proyecto_Individual_1.git

Tenemos disponible un sitio en Render para realizar las consultas mencionadas en la introducción:

* Sitio principal: https://consultas-steam-jeremias-pombo.onrender.com/

* Sitio de consultas: https://consultas-steam-jeremias-pombo.onrender.com/docs

Tenemos un video donde se muestra el funcionamiento de la API respondiendo a distintas consultas:

* Link de Youtube: https://www.youtube.com/watch?v=NIOKhnZ9J7E&ab_channel=JEREM%C3%8DASPOMBO

