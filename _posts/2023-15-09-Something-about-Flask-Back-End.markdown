---
title:  "Somethig about Flask Back-end"
date:   2023-09-15 13:24:23
categories: [Flask]
tags: [Flask]
---
Mostraré algunos de los scripts que uso el flask para (Get,Post,Delete etc..) más la 
conexión a base de datos, archivo configuarción y otros.



Esto sería lo primero: Conexión a base de datos

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



