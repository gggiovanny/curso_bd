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
3. Ruta para checar que se instalo bien el laravel: http://localhost/laravel/public/
4. Lo siguiente es modificar el archivo .env que se encuentra en la raíz de nuestro proyecto para que tenga los datos de la conexion de nuestra base de datos. Deberia quedar asi dicha seccion (para los valores por defecto de xampp, cambienlo si cambiaron contraseñas):
```
[...]
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=test
DB_USERNAME=root
DB_PASSWORD=
[...]
```
##### Link que puede ayudar
+ https://medium.com/@david.quezada.m/tutorial-api-restful-con-laravel-5-6-en-menos-de-1000-palabras-e14249fef9a9

# Miercoles
1. Teniendo una consola abierta en la ruta del proyecto, crear un archivo controlador con el siguiente comando:
```
php artisan make:controller tablaController -r
```
2. Luego agregar el archivo `laravel/routes/api.php`:
```php
Route::apiResource('nombre_tabla', 'tablaController');   
```
3. Guardar y verificar que se halla echo correctamente con el comando
```
php artisan route:list
```
4. Ahora editar el archivo controlador. Seguir las indicaciones de los senseis.
+ Funcion para hacer select: `DB::select( DB::raw("SELECT * FROM nombre_tabla"))`.
+ Funcion para hacer inserts o en general sentencias que no regresen ningun valor: `DB::statement( "INSERT INTO tabla VALUES (17, 'algoxd')" )`
+ Ruta para consultar las tablas: http://localhost/laravel/public/api/nombre_tabla

+ Link util: https://fideloper.com/laravel-raw-queries
+ Otro link util: https://likegeeks.com/es/errores-en-diseno-de-base-de-datos/
### Cosas random
+ Tipo de dato para fecha recomendado para mysql: `timestamp`.
+ Valor para obtener la fecha actual y ponerla por defecto: `current_timestamp`
+ Ejemplo 
```sql
CREATE TABLE auditorias (
	idAuditoria smallint not null auto_increment,
    idUser int(11) not null,
    descripcion varchar(255) null,
    fechaCreacion timestamp not null default current_timestamp,
    
    idEmpresa int(11) null,
    idDepartamento int(11) null,
    idClasificacion int(11) null,
    
    terminada bit not null default 0,
    fechaGuardada timestamp null,
    
    PRIMARY KEY (idAuditoria),
    FOREIGN KEY (idUser) REFERENCES users(id),
    FOREIGN KEY (idEmpresa) REFERENCES empresas(idEmpresa),
    FOREIGN KEY (idDepartamento) REFERENCES departamentos(idDepartamento),
    FOREIGN KEY (idClasificacion) REFERENCES clasificaciones(idClasificacion)    
);
```
# Reto
CREAR TABLAS EN SU DB CON LA TEMATICA DE UN RESTAURANTE
RECUERDA QUE UN RESTAURANTE NECESITA TENER INFORMACION DE LA LOS PLATILLOS,
DE LAS ORDENES QUE SE HICIERON EN EL DÍA
E INFORMACION DE LAS MESAS


Tipo de dato para fecha recomendado para mysql: timestamp.
Valor para obtener la fecha actual y ponerla por defecto: current_timestamp

Tipo de dato para dinero: decimal(15,2)
## Una posible respuesta
```sql
CREATE TABLE PLATILLO (
	idPlatillo smallint AUTO_INCREMENT NOT NULL,
    nombre varchar(255) NOT NULL,
    precio decimal(15, 2),
    estatus bit not null default 1,
    
    CONSTRAINT PK_PLATILLO PRIMARY KEY (idPlatillo)   
);

CREATE TABLE PEDIDO (
	idPedido int AUTO_INCREMENT NOT NULL,
    mesa tinyint NOT NULL,
	fecha timestamp NOT NULL DEFAULT current_timestamp,
    
    CONSTRAINT PK_PEDIDO PRIMARY KEY (idPedido)
);

CREATE TABLE PEDIDO_PLATILLOS (
    idPedido int NOT NULL,
    idPlatillo smallint NOT NULL,
    cantidad tinyint NOT NULL DEFAULT 1,
    
    CONSTRAINT FK_PEDIDO_PLATILLOS_PEDIDO FOREIGN KEY(idPedido) REFERENCES PEDIDO(idPedido),
    CONSTRAINT FK_PEDIDO_PLATILLOS_PLATILLO FOREIGN KEY(idPlatillo) REFERENCES PLATILLO(idPlatillo),
	CONSTRAINT PK_PEDIDO_PLATILLOS PRIMARY KEY (idPedido, idPlatillo)
);
```
