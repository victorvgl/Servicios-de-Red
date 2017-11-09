# ISS Window Server

![imagen](./img/portada.png)

---

### [Práctica de IIS Windows 2012 Server I](#1)

+ Vamos a realizar la instalación y configuración del ISS en Window Server 2012. Comprobaremos los accesos y crearemos un pequeño sitio web con varias páginas de prueba.

### [Práctica de IIS Windows 2012 Server II](#2)

+ Crearemos una nueva zona de busca directa y añadiremos un nuevo dominio y subdominio. Luego haremos dos sitios webs nuevos y los enlazaremos al nuevo dominio y subdominio.

### [Práctica de IIS Windows 2012 Server III](#3)

+ Crearemos un directorio virtual dentro de uno de los Sitios Web anteriores. Crearemos una serie de carpetas de prueba y comprobaremos sus resultados.

---

#  <a name="1"></a> 1. IIS Windows 2012 Server I


+ Vamos al Administrador del servidor `Agregar roles y características` y agregamos el ISS.

![imagen](./img/01.png)

+ Seguimos el asistente de configuración.


![imagen](./img/02.png)

+ Le damos a siguiente en el Rol de servidor web.


![imagen](./img/03.png)

+ Añadimos `Autentificación básica y Autentificación de windows` en los servicios de Rol


![imagen](./img/04.png)

+ Instalamos la configuración


![imagen](./img/05.png)

+ Comprobamos lso resultados de la instalación


![imagen](./img/06.png)

+ Abrimos el navegador web y probamos que tenemos acceso a nuestro `localhost`


![imagen](./img/07.png)

+ Comprobamos también con la IP estática del servidor.

![imagen](./img/08.png)


+ Vamos a añadir un nuevo host en el dominio de prácticas anteriores

![imagen](./img/09.png)



![imagen](./img/010.png)


+ Comprobamos que tenemos acceso desde el navegador.

![imagen](./img/011.png)

+ Vamos a añadirle un CNAME y comprobamos que funciona correctamente


![imagen](./img/012.png)

+ comprobación


![imagen](./img/013.png)

+ Añadimos un index de prueba en la carpeta `C:\Inetpub\wwwroot.` y comprobamos


![imagen](./img/014.png)

+ Hacemos la comprobación desde el cliente

![imagen](./img/015.png)

+ Comprobación


![imagen](./img/016.png)

+ Vamos a la ruta `C:\Inetpub\wwwroot.` y añadimos dos carpetas con un index cada una.


![imagen](./img/017.png)

+ Vamos a `Herramientas > Administrador de Internet Information Services (ISS)`

+ Creamos dos sitios Web enlazados a las carpetas creadas anteriormente.

![imagen](./img/020.png)


+ Comprobamos


![imagen](./img/018.png)

+ Comprobamos

![imagen](./img/019.png)

---

#  <a name="2"></a> 2. IIS Windows 2012 Server II

+ Creamos un nuevo Disco para almacenar los nuevos sitios Web.

![imagen](./img/101.png)

+ Le damos formato al disco


![imagen](./img/102.png)

+ Vamos a `Herramientas > Administrador de Internet Information Services (ISS)`


![imagen](./img/103.png)

+ Agregamos los dos sitios Webs que nos pide la práctica


![imagen](./img/104.png)

+ Configuramos el sitio web 1 con el nombre de host de la nueva zona que crearemos más adelante.


![imagen](./img/105.png)

+ Configuramos el sitio web 2 con el nombre de host del subdominio.

![imagen](./img/106.png)

+ comprobamos que se han creado correctamente

![imagen](./img/107.png)

+ Ahora vamos a `Herramientas > DNS`


![imagen](./img/108.png)

+ Hacemos una nueva zona de Búsqueda Directa.


![imagen](./img/109.png)

+ Le añadimos un Host, un Alias, etc..


![imagen](./img/110.png)

+ Creamos el subdominio dentro del nuevo dominio creado anteriormente y lo enlazamos con el dominio.


![imagen](./img/111.png)

+ Comprobamos desde el servidor al sitio web1


![imagen](./img/112.png)

+ Comprobamos desde el servidor al sitio web2


![imagen](./img/113.png)

+ Comprobamos desde el cliente


![imagen](./img/114.png)

+ Comprobamos desde el cliente


![imagen](./img/115.png)

+ Hacemos un `nslookup` desde el cliente


![imagen](./img/116.png)

---

# <a name="3"></a> 3. IIS Windows 2012 Server III

+ Creamos la carpeta Departamentos y dentro de esta otras tres llamadas administración, contabilidad e informática. Le ponemos un index de prueba en cada una de ellas.


![imagen](./img/201.png)

+ Vamos a `herramientas > Administrador de internet Information Services (ISS) `


![imagen](./img/202.png)


+ Agregamos un directorio virtual en uno de los dos sitios Webs creados anteriormente.

![imagen](./img/203.png)


+ Le ponemos el Alias que queramos y la ruta de la carpeta creada anteriormente.


![imagen](./img/204.png)


+ Vemos los directorios virtuales creados en el sitio web.

![imagen](./img/205.png)


+ Probamos que podemos acceder correctamente y ver lo añadido en el index.html

![imagen](./img/206.png)




![imagen](./img/207.png)


![imagen](./img/208.png)

---
