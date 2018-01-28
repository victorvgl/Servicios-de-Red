# Servidor de Correo

![imagen](./img/portada.jpg)

---

### [Instalación y Administración de Servicios de Correo Electrónico](#1)

+ Instalaremos el Servicio SMTP en Windows 2012 Server y haremos la siguiente configuración:

  + Establecer como IP todas las asignadas
  + Limitar el número de conexiones a 50
  + Habilitar el registro en formato W3C, diario y en una carpeta determinada
  + Configurar envío de mensajes dentro de nuestra red local: Aceptar la conexión al servidor y la retransmisión de mensajes a todos los equipos menos los que aparecen en la lista (incluir una IP cualquiera en la lista para impedir su acceso y retransmisión)
  + Establecer autenticación anónima
  + Comprobar la existencia del dominio AD predeterminado. Crea un dominio de tipo alias para disponer de cuentas en otro dominio.
  + Configuraremos diferentes configuraciones y haremos las pruebas desde un cliente con Opera Mail.


### [Instalación y Administración de Servicios de Correo Electrónico con hMailServer](#2)

+ Vamos a configurar hMailServer en Window Server 2012. Instalaremos el programa y configuraremos dos dominios `asir.edu` y `srd.edu` con dos cuentas para dos usuarios ficticios. Configuraremos el servidor DNS y haremos una serie de configuraciones de prueba dentro de hMailServer. Realizaremos una serie de pruebas desde un cliente.


---

#  <a name="1"></a> 1. Instalación y Administración de Servicios de Correo Electrónico




+ Vamos al Administrador del servidor `Agregar roles y características` y agregamos el ISS.

![imagen](./img/001.png)

+ Iniciamos el asistente para agregar roles y características.

![imagen](./img/002.png)

+ Seguimos los pasos como siempre hasta llegar a características para agregar el Servidor SMTP.


![imagen](./img/005.png)

+ Agregamos características.


![imagen](./img/006.png)


+ Iniciamos la instalación.


![imagen](./img/007.png)


+ Vamos al Administrador ISS 6.0


![imagen](./img/008.png)

+ Configuramos el Servidor SMTP, ponemos la dirección IP de nuestor servidor limitando el número de conexiones a 50 y habilitar el registro en formato W3C.


![imagen](./img/009.png)


+ Ahora vamos a acceso, Conexión para agregar o denegar acceso.

![imagen](./img/011.png)

+ En mi caso, solo voy a dar acceso al cliente por lo que pondré la IP que tengo asignada en él.


![imagen](./img/012.png)


+ En retransmisión, le daré permiso de retransmisión a todos los equipos que se autentican correctamente.

![imagen](./img/030.png)

+ Configuración del Mensaje


![imagen](./img/014.png)


+ Configuración de la entrega.


![imagen](./img/015.png)


+ Añadimos el acceso anónimo a la autentificación.


![imagen](./img/016.png)
![imagen](./img/017.png)

+ En enrutamiento LDAP, desactivado.


![imagen](./img/018.png)

### Creando el dominio SMTP

Ya con le Servidor SMTP configurado, vamos a crear desde este un nuevo dominio SMTP.

+ Especificamos el nuevo dominio como alias.

![imagen](./img/020.png)

+ Añadimos el dominio que queramos.

![imagen](./img/021.png)

+ Comprobamos que las carpetas en la ruta `C:/inetpub/mailroot`


![imagen](./img/022.png)


### Cliente

+ Nos descargamos el instalador de Opera Mail en el siguiente [Enlace](http://www.opera.com/es/computer/mail) y hacemos la instalación.

![imagen](./img/025.png)

+ Seguimos el asistente de  configuración de correo.


![imagen](./img/026.png)

+ Añadimos el servidor de entrada y salida, en mi caso, la ip del servidor de correo.


![imagen](./img/029.png)


+ Hacemos una prueba y comprobamos que nos llega correctamente el correo enviado.


![imagen](./img/038.png)

### Cifrado TLS

+ Vamos hacer otra prueba pero ahora con cifrado TLS y autentificación básica. Marcamos el cifrado TLS y vamos a Autenticación.


![imagen](./img/039.png)


+ En Autenticación, marcamos la Autenticación básica, que requiere el cifrado TLS y el dominio predeterminado `victor.local`.


![imagen](./img/040.png)

### Cliente

+ Volvemos al cliente, y en propiedades de la cuenta, pestaña Servidores, marcamos la Conexión segura TLS.


![imagen](./img/042.png)

+ Aceptamos el certificado, es normal que nos avise que los firmantes no están registrados ya que no es un certificado oficial.


![imagen](./img/043.png)

+ Volvemos hacer la prueba y nos llega correctamente.

![imagen](./img/044.png)

+ Comprobamos que dentro de las carpetas, nos aparecen los correos.

![imagen](./img/045.png)



#  <a name="2"></a> 2. Instalación y Administración de Servicios de Correo Electrónico con hMailServer

### Configuración inicial

+ Lo primero que tenemos que hacer, es quitar el Servidor SMTP de la práctica anterior para que no nos de conflicto con el hMailServer. Vamos a quitar roles y características y lo quitamos.

![imagen](./img2/001.png)

+ Confirmamos que queremos quitar el servidor SMTP.


![imagen](./img2/002.png)
![imagen](./img2/003.png)

+ Lo segundo que tenemos que hacer para que el hMailServerfuncione correctamente, es instalar el Framework 3.5, vamos a agregar roles y características y lo instalamos.


![imagen](./img2/004.png)

### hMailServer

+ Nos descargamos hMailServer del siguiente [Enlace](https://www.hmailserver.com/download) y realizamos la instalación.

![imagen](./img2/005.png)
![imagen](./img2/007.png)

+ Entramos a la interfaz para empezar a configurar el hMailServer.


![imagen](./img2/008.png)

+ Agregamos dos nuevos dominios, `asir.edu` y `srd.edu`


![imagen](./img2/009.png)

+ Agregamos en el apartado backup, una carpeta creada anteriormente para hacer las copias de seguridad.


![imagen](./img2/011.png)

+ Hacemos y Diagnóstico y comprobamos que no nos da error en Backup desde los dos dominios.

asir.edu
![imagen](./img2/012.png)

srd.edu
![imagen](./img2/013.png)

+ Añadimos dos cuentas a cada dominio, una de ellas, con una configuración diferente para ver algunas de las distintas opciones que podemos configurar.

+ Añadimos el nuevo usuario cambiándole el tamaño máximo que puede subir.

![imagen](./img2/015.png)


+ Podemos configurar una respuesta automática con la fecha que queramos en la pestaña Auto-reply.


![imagen](./img2/017.png)

+ En la pestaña Forwading, podemos agregar un correo para que los correos entrantes a esta cuenta sean enviados a la que queramos.


![imagen](./img2/018.png)

+ En la pestaña signature, podemos añadir un texto o html automaticamente.

![imagen](./img2/019.png)

+ Creamos el otro usuario en el dominio con una configuración diferente.

![imagen](./img2/020.png)

+ Creamos los otros dos usuarios en el otro dominio.

![imagen](./img2/021.png)

+ Podemos poner rangos de IP y varios protocolos de correo. Tanto para el servidor como para los clientes.

![imagen](./img2/026.png)
![imagen](./img2/027.png)

+ Es importante, que desmaquemos el autoban para que podamos enviar y recibir los correos.

![imagen](./img2/029.png)

### Administrador DNS

+ Vamos al administrador DNS del servidor y añadimos dos nuevas zonas de búsqueda directa con el nombre de nuestro dominios y le añadimos un host A apuntando a nuestro servidor mediante su IP y un Intercambiador de correos MX apuntando al Hosta A.

![imagen](./img2/022.png)
![imagen](./img2/023.png)

+ Como podemos comprobar, al hacer el diagnóstico, ya no nos da ningún error.

asir.edu
![imagen](./img2/024.png)

srd.edu
![imagen](./img2/025.png)

### Cliente

+ Ahora vamos hacer una serie de pruebas desde el cliente. Comprobamos que podemos enviar y recibir desde un usuario a otro.

![imagen](./img2/030.png)

+ Funciona correctamente.

![imagen](./img2/031.png)

### Lista de distribución

+ Vamos hacer otra prueba con una lista de distribución. Crearemos una lista y añadiremos a esta la configuración y los usuarios de correo que queramos para redirigir el correo entrante a estos.

![imagen](./img2/032.png)

+ Añadimos los usuario que queramos a la lista de distribución.

![imagen](./img2/033.png)

+ Hacemos una prueba mandado un correo a `empleados@asir.edu` que es el nombre de la lista que he creado con los usuarios victor@asir.edu y alfon@asir.edu.

![imagen](./img2/034.png)
![imagen](./img2/035.png)

+ Mandando un correo de prueba, automaticamente nos llega a los usuarios añadidos a la lista.

![imagen](./img2/036.png)

+ Comprobamos el contenido y que nos llega correctamente desde `empleados@asir.edu`

usuario victor
![imagen](./img2/041.png)

usuario alfon
![imagen](./img2/042.png)
