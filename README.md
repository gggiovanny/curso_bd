# Curso de BD y REST API
## Instaladores
+ https://www.apachefriends.org/xampp-files/7.3.9/xampp-windows-x64-7.3.9-0-VC15-installer.exe
+ https://code.visualstudio.com/
+ https://git-scm.com/
+ https://www.getpostman.com/
+ https://dev.mysql.com/downloads/workbench/
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
1. Ubicarse con una consola en la carpeta de archivos web del servidor web de xampp y abrir una consola alli. La ruta por defecto de dicha carpeta en windows es `C:\\xampp\htdocs`.
  + Pueden abrir esa carpeta en el explorador de archivos y presionar `shift + click derecho` en cualquier espacio vacio y en el menu contextual les va a aparecer "Abrir consola de comandos aqui" o "Abrir powershell aqui".
  +  Pueden apretar `tecla windows + r` y escribir `cmd` en la ventana de ejecutar que se abre. Una vez en la consola, escribir 
  ```
  cd C:\\xampp\htdocs
  ```
2. Teniendo instalado [composer](https://getcomposer.org/) previamente, ejecutar en consola:
```
composer create-project laravel/laravel
```
  Aqui se descargaran los archivos necesarios y se creara el proyecto en una carpeta llamada *laravel*. Esta carpeta puede ser      renombrada posteriormente.
3. Lo siguiente es modificar el archivo .env que se encuentra en la raíz de nuestro proyecto para que tenga los datos de la conexion de nuestra base de datos. Deberia quedar asi dicha seccion (para los valores por defecto de xampp, cambienlo si cambiaron contraseñas):
[...]
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=test
DB_USERNAME=root
DB_PASSWORD=
[...]
4. Comando para crear controller:
```
php artisan make:controller nombreController -r
```

##### Link que puede ayudar
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
