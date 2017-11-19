# ISS Window Server

![imagen](./img/portada.png)

---

### [Práctica de IIS Windows 2012 Server IV](#1)

+ Crearemos una nueva zona de búsqueda directa en los servicios DNS asociado al
dominio miEmpresa y crearemos  la carpeta Miempresa con una subcarpeta
llamada principal.

+ Crearemos un nuevo sitio Web denominado miEmpresa asociado a la carpeta creada
anteriormente con acceso a través de la dirección "www.miEmpresa.com".

+ Haremos un sitio web denominado "pagos" como subdominio de miEmpresa (pagos.miEmpresa.com) y configuraremos este último para ser accedido de forma segura, vía ‘https’ con un certificado autofirmado.

+ Haremos un nuevo sitio seguro (tienda.miempresa.com) con la generación de
un Certificado Digital a través de la aplicación OpenSSL.

### [Práctica de IIS Windows 2012 Server IV B](#2)


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
