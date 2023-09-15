---
title:  "Somethig about Flask Back-end"
date:   2023-09-15 13:24:23
categories: [Flask]
tags: [Flask]
---
Mostraré algunos de los scripts que uso el flask para (Get,Post,Delete etc..) más la 
conexión a base de datos, archivo configuarción y decorador de "Before request" para
la protección de rutas.



Esto sería lo primero: Conexión a base de datos.

``` python
#################################################################################
######################## MODULO DE CONEXION A BASE DE DATOS #####################
#################################################################################


from flask_mysqldb import MySQLdb
from . import config

db = MySQLdb.connect(host=config.MYSQL_HOST,         # your host, usually localhost
                     user=config.MYSQL_USER ,        # your username
                     passwd= config.MYSQL_PASSWORD,  # your password
                     db=config.MYSQL_DB)             # name of the data base

#################################################################################                     
```

Si os habeis fijado, el modulo anterior importa tanto MySQLdb como config.

``` python

#################################################################################
######################## MODULO DE VARIABLES DE CONFIGURACION ###################
#################################################################################


MYSQL_HOST="xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx"
MYSQL_USER="xxxxxxxxxxxxxxxxx"
MYSQL_PASSWORD="xxxxxxxxxxxxxxxxxxx"
MYSQL_DB="xxxxxxxxxxxxxxxxxx"
MYSQL_PORT=3306
MYSQL_SECRET="xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx"
APP_SECRET="xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx"
PEXELS_APIKEY="xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx"


#################################################################################
#################################################################################
#################################################################################


```

La protección de rutas se puede hacer de diversas formas. Una de las más
cómodas es usar un decorador llamando a su función decoradora.

``` python


@app.before_request
def before_request_func():
     print("before_request executing!")



```
Otro script que no debe faltar es un control sobre un mal enrutamiento
para controlar o redirigir el error 404 y renderizar un HTML generado
para este uso concreto.

``` python


#################################################################################
################## CONTROL DE RUTAS NO EXISTENTES (RENDERIZA 404 PAGE) ##########
################################################################################# 
 
 
@app.errorhandler(404)
def not_found(e):
  return render_template("salida.html",mensaje="Recurso no encontrado. Error 404")



#################################################################################


```

En el siguiente script se verá como (sin decorador), incluimos el condicional
sobre una del las c(lave/valor) de "FLASK SESSION" para evitar accesos no
autorizados.

``` python


#################################################################################
################## FUNCION QUE DEVUELVE TABLA FAVORITOS (ALL) ###################
#################################################################################

@app.route("/ver_favoritos")
def ver_favoritos():
    if not session["email"]:
         return render_template("salida.html",mensaje="No tiene acceso a este recurso, pero hay otros mundos")
    encontrados=todos_los_favoritos.consulta()
    if encontrados:
         return jsonify(encontrados)
    else:
        Dom.mensaje_error("No hay nada que mostrar")
        return "error"

#################################################################################


```

Ahora mostraré una de las funciones que llaman a consultas a base de datos y al
módulo encargado.

Estamos usando SQl directamente. Otra de las posiblesformas de trabajar sería 
usando un ORM como pueda ser SQLAlchemy.


``` python


#################################################################################
################## FUNCION QUE DEVUELVE TABLA FAVORITOS (ALL) ###################
#################################################################################

@app.route("/ver_favoritos")
def ver_favoritos():
    if not session["email"]:
         return render_template("salida.html",mensaje="No tiene acceso a este recurso, pero hay otros mundos")
    encontrados=todos_los_favoritos.consulta()
    if encontrados:
         return jsonify(encontrados)
    else:
        Dom.mensaje_error("No hay nada que mostrar")
        return "error"



#################################################################################
###########################  LECTURA TABLA FAVORITOS ############################
#################################################################################

from . import connection

def consulta():
   try:  
        db = connection.db
        cursor = db.cursor()
            # campos de favoritos (   0-id...... 1-nombre ....2-url   )
        cursor.execute("SELECT * FROM favoritos ")
        favoritos_all= cursor.fetchall()
        cursor.close()
     
   except:
       return False   
    
   return favoritos_all

   


```


Esto es una pequeña demostración. Para ver otras publicaciones al respecto
pueden encontrarme en  [LinkedIn][linkedin]

[linkedin]: https://www.linkedin.com/in/e-cabrera-blazquez/