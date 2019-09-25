# Curso de BD y REST API
## Instaladores
+ https://www.apachefriends.org/xampp-files/7.3.9/xampp-windows-x64-7.3.9-0-VC15-installer.exe
+ https://code.visualstudio.com/
+ https://git-scm.com/
+ https://www.getpostman.com/
+ https://dev.mysql.com/downloads/workbench/
+ https://getcomposer.org/
+ https://getcomposer.org/

# Martes:
#### Links de SQL
+ Documentacion de W3Schools (ahi esta todo, los updates, inserts, joins y demas): https://www.w3schools.com/sql/
+ https://dev.mysql.com/doc/refman/8.0/en/example-auto-increment.html
+ https://dev.mysql.com/doc/refman/5.7/en/data-type-defaults.html

#### APIs para jugar con los valores
+ De posts y comentarios(es la documentacion, alli esta el link base y los endpoints) : https://jsonplaceholder.typicode.com
+ De auditorias: (es la documentacion, alli esta el link base y los endpoints): https://github.com/gggiovanny/dicas-auditorias-api

#### Links de REST API
+ Reglas de una REST API: https://hackernoon.com/restful-api-designing-guidelines-the-best-practices-60e1d954e7c9
+ Verbos HTTP: https://www.tutorialspoint.com/http/http_methods
+ Video que seria chido que vieran en su casita: https://www.youtube.com/watch?v=u2Ms34GE14U

#### Instalacion de laravel
+ https://medium.com/@david.quezada.m/tutorial-api-restful-con-laravel-5-6-en-menos-de-1000-palabras-e14249fef9a9

# Miercoles
#### Archivo .htaccess
```
# Turn rewrite engine on
Options +FollowSymlinks
RewriteEngine on

# Rewrite all those to insert /folder
RewriteRule ^(.*)$ /api/public/api/$1 [L]
```
