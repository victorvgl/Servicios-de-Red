
>Práctica Realizada por:
>
>[Carlos Delgado Hernández](https://github.com/carlsjdh)
>
>[Carmelo González Domínguez](https://github.com/SilverGG)
>
>[Víctor García Luis](https://github.com/victorvgl)


# ISS Window Server

![imagen](./img/portada.png)

---

### [Práctica de IIS Windows 2012 Server V](#1)

+ Vamos a realizar las instalaciones y configuraciones necesarias para obtener un Servidor Web con
soporte PHP y accesos a bases de datos relacionales, acceso FTP y gestor de bases de datos. Sobre
este servidor, podremos realizar instalaciones de aplicaciones integradas (CMS, e-commerce, etc)
desde el propio servidor o en modo remoto desde un cliente W7.

+ Crearemos un nuevo sitio Web denominado miEmpresa asociado a la carpeta creada
anteriormente con acceso a través de la dirección "www.miEmpresa.com".

+ Comprobaremos  la instalación correcta de PHP colocando un fichero index.php en el sitio web destinado
a gestionar el CMS Drupal (www.miEmpresa.com ó miEmpresa\principal) con el siguiente código:
<?php phpinfo(); ?>

+ Crearemos un sitio web denominado "pagos" como subdominio de miEmpresa (pagos.miEmpresa.com) y configuraremos este último para ser accedido de forma segura, vía ‘https’ con un certificado autofirmado.

+ instalaremos el servidor de bases de datos
relacionales MySQL para tus sitios Web gestionados por IIS

### [Práctica de IIS Windows 2012 Server VI B](#2)

+ Instalaremos un Servidor FTP FileZilla en Windows 2012 Server con un usuario de prueba para acceder desde un cliente y un registro DNS para acceder al sitio a través de la dirección `ftp.miEmpresa.com`

+ Comprobaremos accesos desde el cliente a phpMyAdmin desde un navegador `phpmyadmin.miEmpresa.com`. Comprobaremos el acceso al sitio ftp creado anteriormente
a través del navegador y a través de filezilla.

+ Descargaremos CMS Drupal dodne configuraremos y crearemos el sitio drupal.


### [Práctica de IIS Windows 2012 Server VII B](#3)

# 1. Instalación y configuración php en Window Server

+ Nos descargamos el instalador del siguiente [Enlace](http://windows.php.net/download/)
y realizamos la instalación.

![imagen](./img/1_install_php.png)


+ Realizamos la instalación


![imagen](./img/2_install_php.png)

+ Elegimos la opción ISS FastCGI


![imagen](./img/3_fastCGI.png)

+ Necesitamos instalar roles CGI para poder activar el FastCGI


![imagen](./img/3_Problema_CGI.png)

+ Instalamos el CGI

![imagen](./img/4_CGI_Rol.png)


+ Seguimos con la instalación por defecto.


![imagen](./img/5_inst_3.png)

+ Añadimos el sitio web que vamos a utilizar, en este caso, `php` y le ponemos como prioridad el index.php.


![imagen](./img/6_subir_php.png)

+ Creamos las carpetas del dominio y subdominio donde vamos a crear el index.php


![imagen](./img/7_file_php.png)

+ Ahora vamos a crear el dominio `webcms.com` y el subdominio `php`


![imagen](./img/8_dns.png)


+ Probamos el acceso.


![imagen](./img/10_php_info.png)

+ Ahora vamos a instalar el `mysql-server` desde el siguiente [enlace](http://dev.mysql.com/downloads/installer/
.)


![imagen](./img/11_mysql.png)

+ Empezamos con la configuración


![imagen](./img/12_install_complete.png)

+ Lo configuramos solo como server


![imagen](./img/12_server_only.png)

+ Tipo server machine, puerto 3306 y le damos acceso al cortafuego.


![imagen](./img/13_server_install.png)


+ Comprobamos que se instala todo correctamente


![imagen](./img/14_final_install.png)


+ Creamos el usuario en el servidor `php_user` y probamos que podemos acceder desde el cliente

![imagen](./img/15.png)

+ Accedemos desde el cliente


![imagen](./img/16.png)

---

#  <a name="2"></a> 1. IIS Windows 2012 Server V

+ Instalamos Filezilla en el servidor

![imagen](./img/15_filezilla_install_server.png)

+ Seguimos con la instalación por defecto


![imagen](./img/16_portFZ_Server.png)




![imagen](./img/16.png)




![imagen](./img/17_user_filezilla.png)


+ Creamos la carpeta `ftp_users`

![imagen](./img/18_Desktop_ftpuser.png)

+ Añadimos un usuario llamado `ftpuser` y le damos permisos.


![imagen](./img/19_User_permisos_Ftpuser.png)


+ Elegimos el directorio de webcms que es donde queremos acceder desde fuera

![imagen](./img/20_ftp_user.png)

+ Comprobamos el acceso desde el servidor vía web


![imagen](./img/21_web_ftp_server.png)

+ Podemos acceder correctamente


![imagen](./img/22_web_ftp_server.png)




![imagen](./img/24_español_drupal.png)




![imagen](./img/26_error_drupal.png)




![imagen](./img/26_gtranslate.png)




![imagen](./img/26_permisos_drupal_solución_error.png)




![imagen](./img/27_activar_multi.png)




![imagen](./img/28_temas.png)




![imagen](./img/29_bloques.png)




![imagen](./img/30_crear_pagina.png)




![imagen](./img/31_menu_paginas.png)




![imagen](./img/base_dedatos_cms.png)




![imagen](./img/privilegios.png)
