# ISS Window Server

![imagen](./img/portada.png)

---

### [Práctica de IIS Windows 2012 Server IV](#1)

+ Crearemos una nueva zona de búsqueda directa en los servicios DNS asociado al
dominio miEmpresa y crearemos  la carpeta Miempresa con una subcarpeta
llamada principal.

+ Crearemos un nuevo sitio Web denominado miEmpresa asociado a la carpeta creada
anteriormente con acceso a través de la dirección (www.miEmpresa.com)

+ Crearemos un sitio web denominado "pagos" como subdominio de miEmpresa (pagos.miEmpresa.com) y configuraremos este último para ser accedido de forma segura, vía ‘https’ con un certificado autofirmado.

+ Crearemos un nuevo sitio seguro (tienda.miempresa.com) con la generación de
un Certificado Digital a través de la aplicación OpenSSL.

### [Práctica de IIS Windows 2012 Server IV B](#2)

+ Vamos  a  crear  un  nuevo  sitio  web  (empleados.miEmpresa.com) destinado a almacenar información privada de los empleados.

+ Crearemos carpetas privadas para cada usuario y una para todos los empleados

+ Los usuarios serán creados en Active directory con el nombre correspondiente de su carpeta de acceso.


---

#  <a name="1"></a> 1. IIS Windows 2012 Server IV


+ Vamos a los servicios DNS de nuestro servidor y creamos una nueva Zona de búsqueda directa.

![imagen](./img/001.png)

+ Agregamos el dominio `miEmpresa.com` como nos indíca la práctica.

![imagen](./img/002.png)

+ Seguimos los pasos de configuración hasta Finalizar el Asistente para la nueva zona.

![imagen](./img/003.png)

+ Le añadimos un registro de host.


![imagen](./img/004.png)

+ Le añadimos ( opcional) un alias para acceder con www.


![imagen](./img/005.png)

+ Ahora vamos a los servicios ISS para agregar los sitios webs indicados en la práctica.


![imagen](./img/006.png)

+ Añadimos los datos a agregar al sitio web.


![imagen](./img/007.png)

+ Comprobamos su funcionamiento desde el servidor.

![imagen](./img/008.png)

+ Volvemos a los servicios DNS para agregar el subdominio de miEmpresa denominado `pagos`.

![imagen](./img/009.png)



![imagen](./img/010.png)

+ Le añadimos un registro de host.


![imagen](./img/011.png)

+ Le añadimos ( opcional) un alias para acceder con www.


![imagen](./img/012.png)

+ Volvemos a los servicios ISS para agregar el nuevo sitio web.


![imagen](./img/013.png)

+ Comprobamos su funcionamiento desde el servidor.


![imagen](./img/014.png)

+ Comprobamos su funcionamiento desde el cliente.


![imagen](./img/015.png)

## 1.1 Certificado autofirmado

+ Vamos al administrador del ISS y le damos a Certificados de servidor


![imagen](./img/016.png)

+ Creamos un certificado autofirmado


![imagen](./img/017.png)

+ Rellenamos el campo, el almacén de certificado como Personal y aceptar.


![imagen](./img/018.png)

+ Ya tenemos el certificado creado.

![imagen](./img/019.png)

+ Ahora modificamos el sitio web creado anteriormente.


![imagen](./img/020.png)

+ Le cambios el `Tipo por https` y el puerto ` el puerto seguro 443`. Elejimos el nombre de certificado creado anteriormente.


![imagen](./img/021.png)

+ Eliminamos el enlace a www.pagos.miempresa.com con el tipo http y desde el puerto 80.


![imagen](./img/022.png)

+ Como podemos comprobar, funciona correctamente ya que no es una entidad certificadora oficial.

![imagen](./img/023.png)

+ Podemos acceder perfectamente.

![imagen](./img/025.png)

## 1.2 Solicitud del Certificado

+ Lo primero que vamos a hacer es añadir otro subdominio en miEmpresa.com llamado `tienda`

![imagen](./img/026.png)

+ Le añadimos el registro host y un alias (opcional) www.

![imagen](./img/027.png)

+ Agregamos el sitio web tienda.

![imagen](./img/028.png)

+ Nos descargamos el [OpenSSL](http://moodle26.iespuertodelacruz.es/mod/resource/view.php?id=6943)

+ Realizamos la instalación del OpenSSL.

![imagen](./img/029.png)


![imagen](./img/030.png)

+ Vamos al administrador del ISS y `Creamos una solicitud de certificado`.

+ Rellenamos los campos requeridos para el certificado.

![imagen](./img/032.png)

+ El proveedor de servicios `Microsoft RSA` y la Longitud en bits `2048`.


![imagen](./img/033.png)

+ Guardamos la solicitud con el nombre `certreq.txt`.


![imagen](./img/034.png)

+ finalizamos.


![imagen](./img/035.png)

+ Comprobamos que se ha hecho la solicitud correctamente.


![imagen](./img/036.png)

## 1.3 Certificado con OpenSSL

+ Lo primero que tenemos que hacer es meter en la carpeta `C:\OpenSSL\bin` la solicitud del certificado creada anteriormente. Luego, abrimos una consola y hacemos lo siguiente:

+ Generamos la clave privada, nos pide una contraseña para protegerla. `openssl genrsa -des3 -out cakey.pem 2048`

![imagen](./img/037.png)

+ Ahora, hay que crear un certificado digital de la CA que contendrá información sobre la misma.. rellenamos toda la información que nos pide. Por linea de comando decimos que es válido por un año. `openssl req -new -x509 -key cakey.pem -out cacert.pem -days 365`


![imagen](./img/038.png)


+ Vemos como queda el certificado

![imagen](./img/039.png)


+ Ahora, creamos el certificado digital de nuestro Web.
`openssl x509 -req -days 365 -in certreq.txt -CA cacert.pem -CAkey cakey.pem -CAcreateserial -out iis.crt`


![imagen](./img/040.png)

+ Vemos el certificado generado

![imagen](./img/041.png)

+ Completamos la solicitud del certificado.

![imagen](./img/042.png)

+ Le ponemos la ruta del certificado.


![imagen](./img/043.png)

+ Agregamos el enlace de sitio


![imagen](./img/044.png)

+ Podemos comprobar que ya tenemos generado los sitios con http y https especificado en la práctica y solo nos falta hacer las comprobaciones que podemos acceder perfectamente.


![imagen](./img/045.png)


+ Comprobamos que nos avisa de un posible problema con la entidad certificadora cosa que es correcto ya que nosotros no somos ninguna empresa certificadora.


![imagen](./img/047.png)



+ Comprobamos que podemos acceder desde el servidor con https


![imagen](./img/048.png)



+ Comprobamos que podemos acceder desde el cliente con https.


![imagen](./img/050.png)


+ Comprobamos que podemos acceder desde el servidor con http.


![imagen](./img/051.png)


+ Comprobamos que podemos acceder desde el cliente con http.


![imagen](./img/052.png)

# <a name="2"></a>  2. IIS Windows 2012 Server IV B

+ Necesitamos  crear  una  carpeta  empleados  (dentro  de  miEmpresa)  y,  dentro  de  esta,  tres o cuatro subcarpetas personales con nombres de empleados y una, denominada común, a la que tendrán acceso todos los empleados, pero no otros usuarios sin identificar.

![imagen](./img/055.png)

+ Crearemos  el  nuevo  sitio  web,  como  subdominio  de  nuestro  dominio  principal,  asociado a la carpeta genérica empleados.

![imagen](./img/053.png)

+ Le añadimos un registro host

![imagen](./img/054.png)

+ Agregamos un nuevo sitio web `empleados.miempresa.com`

![imagen](./img/056.png)

+ Activamos el `exámen de directorios` y comprobamos el acceso.

![imagen](./img/057.png)

+ Añadimos un `index.html` en cada subcarpeta y comprobamos su acceso.

![imagen](./img/058.png)

![imagen](./img/059.png)

![imagen](./img/060.png)

![imagen](./img/061.png)

## 2.1 Autenticación

+ Ahora vamos a modificar en el servicio ISS la Autentificación anónima y básica.

![imagen](./img/062.png)

+ Le ponemos a empleados, la `Autenticación anónima deshabilitada` y la `Autenticación básica` Habilitada.

![imagen](./img/093.png)

## 2.2 Usuario en Active Directory

+ Vamos al servicio de Active Directory

![imagen](./img/065.png)

+ Creamos los Usuario anteriormente nombrados en las carpetas.

![imagen](./img/067.png)

+ Creamos el grupo empleados.

 ![imagen](./img/069.png)

 + Añadimos al grupo empleados los usuarios creados anteriormente.

![imagen](./img/070.png)

+ Ahora tenemos que deshabilitar las herencias antes de dar los permisos para que cada empleado acceda a su carpeta y todo puedan acceder a `personal`

![imagen](./img/071.png)


![imagen](./img/072.png)


+ Para la carpeta empleados añadimos el grupo Administradores con control total y empleados creado anteriormente.


![imagen](./img/073.png)


![imagen](./img/074.png)

+ Ahora vamos a añadir el usuario a su carpeta correspondiente para que solo tenga acceso él y el administrador.


![imagen](./img/075.png)


![imagen](./img/076.png)

+ Hacemos lo mismo con los demás usuarios


![imagen](./img/080.png)

+ Añadimos el grupo empleados a la carpeta personal para que todos los usuarios tengan acceso con su login a esta carpeta.

![imagen](./img/081.png)

## 2.3 Comprobaciones

+ Comprobamos que podemos acceder con el usuario y password.


![imagen](./img/085.png)

![imagen](./img/086.png)

+ Comprobamos que no nos pide contraseña en la página principal creada en esta práctica y vemos las carpetas creadas en los pasos anteriores.

![imagen](./img/088.png)

+ Comprobamos el acceso desde el cliente.

![imagen](./img/089.png)

![imagen](./img/090.png)

![imagen](./img/091.png)

---
