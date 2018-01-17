# FTP WINDOW SERVER Y LINUX

![imagen](./img/portada.png)

---

## [Práctica de FTP en Windows 2012 Server](#1)

+ Instalaremos el Servicio FTP en Windows 2012 Server, a través de Agregar roles y características (IIS)

+ Accederemos a la creación y configuración de Sitios FTP por medio de la Administración de IIS.

+ Crearemos tres sitios FTP asociados a rutas y carpetas y probaremos diferentes configuraciones.

+ Haremos diferentes comprobaciones desde un cliente, tanto por web como por software.

## [ Práctica de Instalación y Configuración del Servicio FTP en Linux Ubuntu](#2)

+ Instalaremso el servicio SSH en el servidor Linux.

+ Crearemos dos usuarios con diferentes niveles y privilegios de acceso al fylesystem.

+ Haremos varias comprobaciones por SSH.

+ Probaremos diferentes operaciones de acceder, compartir, subir y descargar archivos entre servidor y cliente.

---

#  <a name="1"></a> 1. Servidor FTP Window Server

### Instalación

+ Comenzamos `agregando roles y características` en Window Server.

![imagen](./img/001.png)

+ Seguimos los pasos de configuración y desplegamos la casilla **Servidor web (ISS)** marcar
la casilla Servidor FTP.

![imagen](./img/002.png)

+ Confirmamos la selección de instalación.

![imagen](./img/003.png)

+ Iniciamos la instalación.

![imagen](./img/004.png)

### Sitio FTP 1

+ Vamos al Administrador del (ISS) y Agregamos un nuevo sitio FTP.

![imagen](./img/005.png)

+ Agregamos el nuevo sitio y como se especifica en la práctica, la **Ruta de acceso física** será C:\

![imagen](./img/006.png)

+ Ponemos la dirección IP de nuestro servidor, que inicie automaticamente y **Sin SSL**

![imagen](./img/007.png)

+ Solo el usuario Administrador tendrá acceso al sitio, sin acceso anónimos y en modo lectura y escritura.

![imagen](./img/009.png)
![imagen](./img/018.png)

+ Añadimos un nuevo subdominio `ftp.miEmpresa.com`

![imagen](./img/010.png)

+ Empezamos las comprobaciones y comprobamos que podemos acceder con nuestro usuario y contraseña desde un navegador.

![imagen](./img/011.png)
![imagen](./img/012.png)

+ Podemos acceder correctamente.

![imagen](./img/013.png)

+ Comprobamos que podemos acceder desde el navegador de un cliente.

![imagen](./img/014.png)

+ Comprobamos que podemos acceder desde el explorador de archivos.

![imagen](./img/015.png)

+ Podemos acceder correctamente

![imagen](./img/016.png)

+ Nos descargamos el software WinSCP en el cliente Windows desde este [Enlace](https://winscp.net/eng/download.php), y realizamos la instalación.

![imagen](./img/019.png)

+ Configuramos la conexión al sitio ftp y establecemos la conexión.

![imagen](./img/020.png)

+ Funciona correctamente.

![imagen](./img/021.png)

### Sitio FTP 2

+ Creamos otro sitio FTP y esta vez asociado a `C:\inetpub\wwwroot` con otro subdominio a nuestro dominio `ftp2.miempresa.com`

![imagen](./img/022.png)

+ Dirección IP de nuestro servidor, inicio automático y esta vez si Permitimos un certificado SSL. Usaremos el certificado creado en prácticas anteriores.

![imagen](./img/024.png)

+ Los accesos anónimos no estarán permitidos, todos los usuarios podrán acceder y tendrán permisos de lectura y escritura.

![imagen](./img/025.png)
![imagen](./img/027.png)


+ Comprobamos la conexión desde WinSCP y como podemos ver, nos detecta el certificado y nos avisa que no es un certificado oficial, osea, todo correcto.

![imagen](./img/026.png)

+ Comprobamos la conexión.

![imagen](./img/028.png)

+ Podemos acceder correctamente.

![imagen](./img/029.png)

### Sitio FTP 3

Creamos otro sitio FTP y esta vez asociado a `una carpeta del servidor` con otro subdominio a nuestro dominio `ftp3.miempresa.com`

![imagen](./img/030.png)

+ Ponemos la IP de nuestro servidor, inicio automático y sin certificado.

![imagen](./img/031.png)

+ Daremos acceso a usuarios anónimos y solo se podrá consultar y leer.

![imagen](./img/032.png)
![imagen](./img/033.png)

+ Comprobamos desde el navegador del servidor.

![imagen](./img/034.png)

+ Comprobamos desde el navegador del cliente.

![imagen](./img/035.png)

### Configuración para tener los tres sitios en funcionamiento simultaneamente.

+ Tendremos que tener los subdominios creados en nuestro dominio, en mi caso los he creado todos anteriormente como se puede comprobar en la siguiente imágen.

+ Luego tendremos que cambiarle el puerto de los sitios ftp para asignarles un puerto diferente
a cada uno y así poder entrar a los tres sin necesidad de parar ninguno.

+ Comprobaciones de acceso de los tres sitios FTP simultaneamente, tanto por IP como por dominio.

![imagen](./img/036.png)

![imagen](./img/037.png)

![imagen](./img/038.png)

![imagen](./img/039.png)

![imagen](./img/040.png)

![imagen](./img/041.png)

![imagen](./img/042.png)

---

#  <a name="2"></a> 1. Servicio FTP Linux

+ Instalamos el Servicio **SSH** `apt-get install ssh`.

![imagen](./img/043.png)

+ Creamos dos cuentas de usuarios con diferentes privilegiso y niveles de acceso al filesystem.

![imagen](./img/044.png)

+ Comprobamos que podemos acceder con el usuario1 al servidor por SSH.

![imagen](./img/045.png)

+ Comprobamos que podemos acceder con el usuario2 al servidor por SSH.

![imagen](./img/046.png)

+ Comprobamos que podemos lanzar una aplicación a través de SSH desde el servidor hacia Linux.

![imagen](./img/047.png)

+ Comprobamos que podemos acceder y obtener un archivo por `sftp` desde el usuario1.

![imagen](./img/048.png)

+ Comprobamos que podemos acceder y obtener un archivo por `sftp` desde el usuario2.

![imagen](./img/049.png)

+ Comprobamos que podemos subir un archivo por `scp` desde el usuario1 y usuario2.

![imagen](./img/050.png)
![imagen](./img/051.png)

+ Instalamos el paquete **proftpd** `apt-get install proftpd`

![imagen](./img/052.png)

+ El fichero de configuración se encuentra en la ruta `/etc/proftpd` y es el fichero que modificaremos según las necesidades que queramos.

![imagen](./img/053.png)

+ Algunos parámetros a modificar del archivo de configuración.

  + **DefaultRoot** -> Descomentamos borrando la almohadilla #. Esto nos va a permitir que cuando cada usuario acceda a su cuenta del FTP, estos accederán directamente a su carpeta “home”. Si queremos que todos los usuarios que inicien sesión accedan por defecto a una misma carpeta, debemos cambiar el parámetro DefaultRoot y añadir la ruta a la que queramos que accedan.

  + **ServerName** -> Nos permite establecer un nombre al servidor.

  + **AccessGrantMsg** -> Mensaje de bienvenida.(Hay que añadirlo manualmente al final del archivo).

  + **AccessDenyMsg:** -> Mensaje de error al iniciar.(Hay que añadirlo manualmente al final del archivo).

+ Comprobamos que podemos acceder con el usuario1 y usuario2.

![imagen](./img/054.png)

+ Comprobamos que podemos subir un archivo por ftp.

![imagen](./img/055.png)
![imagen](./img/056.png)

---
