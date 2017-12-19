
>Práctica Realizada por:
>
>[Carlos Delgado Hernández](https://github.com/carlsjdh)
>
>[Carmelo González Domínguez](https://github.com/SilverGG)
>
>[Víctor García Luis](https://github.com/victorvgl)

---

# Apache Linux

![imagen](./img/hqdefault-e1484652166844.jpg)


# Introducción

+ Vamos a realizar las instalaciones y configuraciones necesarias para obtener un Servidor Web con
soporte PHP y accesos a bases de datos relacionales, gestor de bases de datos.
Sobre este servidor, podremos realizar instalaciones de aplicaciones integradas (CMS, e-commerce, etc)

+ Crearemos un nuevo sitio Web denominado miEmpresa asociado una carpeta
 con acceso a través de la dirección "www.miEmpresa.com".

+ Comprobaremos  la instalación correcta de PHP colocando un fichero index.php en el sitio web destinado
a gestionar el CMS Drupal (www.miEmpresa.com

+ Comprobaremos  la instalación correcta de PHP colocando un fichero index.php en el sitio web destinado
  a gestionar el CMS Drupal (www.miEmpresa.com ó miEmpresa\principal) con el siguiente código:
  <?php phpinfo(); ?>

+ Crearemos un sitio web denominado "pagos" como subdominio de miEmpresa (pagos.miEmpresa.com) y configuraremos este último para ser accedido de forma segura, vía ‘https’ con un certificado autofirmado.

+ instalaremos el servidor de bases de datos relacionales MySQL


# Apache Linux


+ Instalamos apache `apt-get in apache2`

![imagen](./img/001.png)

+ Comprobamos desde un navegador que podemos acceder correctamente desde nuestro localhost


![imagen](./img/002.png)

+ Creamos un DNS local, vamos al fichero de configuración `/etc/hosts` y añadimos la IP de nuestro servidor y el nombre del dominio.


![imagen](./img/003.png)

+ Comprobamos que podemos acceder y funciona correctamente


![imagen](./img/004.png)

# PHP

+ Instalamos php

![imagen](./img/008.png)

+ Instalamos las librerias necesarias para el funcionamiento de php

![imagen](./img/009.png)

+ Vamos a la ruta `/var/www/html` y le cambiamos el **index.html por index.php**


![imagen](./img/010.png)

+ Comprobamos

![imagen](./img/011.png)

+ Añadimos al fichero de configuración los siguientes cambios con la ruta de de la carpeta empleados que creamos.


![imagen](./img/012.png)

+ Generamos el certificado auto firmado

![imagen](./img/013.png)


![imagen](./img/014.png)

+ Comprobamos que tenemos las claves generadas

![imagen](./img/015.png)


+ Añadimos al fichero de configuración lo siguiente:


![imagen](./img/016.png)


+ Añadimos un html al subdominio y comprobamos.


![imagen](./img/017.png)

+ Creamos la carperta privada en `/var/www` y añadimos un usuario con una contraseña


![imagen](./img/018.png)

+ Comprobamos si se generó el htaccess

![imagen](./img/019.png)

+ Volvemos al archivo de configuración y añadimos lo siguiente

![imagen](./img/020.png)


+ Comprobamos que al acceder nos  pide usuario y contraseña


![imagen](./img/021.png)


+ Accedemos correctamente con el usuario y contraseña anteriormente creados


![imagen](./img/022.png)

# Mysql y Phpmyadmin


+ Instalamos **mysql-server** y **phpmyadmin**


![imagen](./img/023.png)

+ Comprobamos que está instalado

![imagen](./img/024.png)





![imagen](./img/025.png)


+ Accedemos desde el navegador y podemos ver que funciona correctamente


![imagen](./img/026.png)

+ Comprobamos que podemos acceder


![imagen](./img/027.png)

+ Añadimos al DNS **php.miempresa.com**

![imagen](./img/028.png)


+ Añadimos al fichero de configuración lo siguiente:

![imagen](./img/029.png)

+ Creamos la base de datos cms y un usuario con todos los privilegios

![imagen](./img/030.png)

![imagen](./img/031.png)

+ Volvemos al fichero de configuración y añadimos lo siguiente:

![imagen](./img/032.png)

+ Añadimos al DNS **cms.miempresa.com**

![imagen](./img/033.png)

+ Nos descargamos **Drupal** del siguiente enlace [Enlace Drupal](https://www.drupal.org/)
 y lo ponemos en la carpeta asociada al virtual host de cms. Comprobamos que funciona correctamente

![imagen](./img/034.png)
