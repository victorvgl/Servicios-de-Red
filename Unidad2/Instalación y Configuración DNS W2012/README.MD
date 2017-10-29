
# Instalación y configuración de un servidor DNS


![imagen](./img/portada.jpg)

---
- [Configuración del servidor DNS](#1)
- [Registros a la zona de Búsqueda directa](2)
- [Configuración y comprobación desde el cliente](3)


### Objetivo:

+ Vamos a configurar un servidor DNS en Window 2012 Server con una zona de búsqueda directa para el servidor y una zona inversa para la subred. Tendremos que tener acceso a internet desde el cliente teniendo en este, la IP del  servidor como DNS.


# 1. Configuración del Servidor DNS <a name="1"></a>

+ Le ponemos una IP Fija al servidor y como DNS nuestra propia IP.

![imagen](./img/01.png)

+ Vamos a la adminitración del servidor, herramientas y administrador DNS. Le damos botón derecho en nuestro servidor y `Configurar un servidor DNS`


![imagen](./img/03.png)

+ Seguimos el asistente para configurar el servidor.

![imagen](./img/04.png)

+ Creamos la zona de búsqueda directa e inversa.


![imagen](./img/05.png)

+ Ahora nos pedirá crear la zona de búsqueda directa para configurarla.


![imagen](./img/06.png)

+ El tipo de zona será la principal para que cree una zona que se actualice directamente desde este servidor.


![imagen](./img/07.png)

+ Seleccionamos como queremos que se repliquen los datos DNS por la red. Seleccionamos para todo los servidores DNS que se ejecuten en el controlador de dominio creado en prácticas anteriores.


![imagen](./img/08.png)

+ Le ponemos un nombre a la zona ( el que queramos )


![imagen](./img/09.png)

+ A continuación tendremos que crear y configurar la zona de búsqueda inversa.


![imagen](./img/010.png)

+ Creamos de nuevo un tipo de zona Principal.


![imagen](./img/011.png)

+ Para todos los servidores DNS que se ejecuten en nuestro controlador de dominio.


![imagen](./img/012.png)


+ Como estamos usando IPv4, seleccionamos una zona de búsqueda inversa para IPv4.


![imagen](./img/013.png)

+ Escribimos el id de red o el nombre de zona.


![imagen](./img/014.png)

+ Permitimos actualizaciones dinbámicas seguras.


![imagen](./img/015.png)

+ Añadimos la IP de un servidor DNS público para que nuestro servidor reenvie las consultas.


![imagen](./img/016.png)

+ Finalizamos la instalación.


![imagen](./img/017.png)

+ Comprobamos que se ha creado correctamente los reenviadores.


![imagen](./img/018.png)

+ Como podemos ver, ya tenemos nuestras zonas instaladas y configuradas.

![imagen](./img/019.png)

+ Comprobamos que tenemos acceso a internet, teniendo como DNS nuestra misma IP.


![imagen](./img/020.png)

# 2. Añadir registros a la zona de búsqueda directa<a name="2"></a>


+ Añadimos un registro de dirección de host para asignar un nombre de dominio DNS a una dirección IP.


![imagen](./img/101.png)

+ Le ponemos la IP del servidor.


![imagen](./img/102.png)

+ Añadimos un alias al nombre de dominio.


![imagen](./img/103.png)

+ Yo lo voy a llamar server pero le ponemos poder el que queramos.


![imagen](./img/105.png)

+ Añadimos un host llamado Printer y le ponemos una IP.


![imagen](./img/106.png)

+ Añadimos un servidor de correo.


![imagen](./img/107.png)

+ Le ponemos el nombre.


![imagen](./img/108.png)

+ Dentro de la zona directa, creamos una subzona llamada servicios.


![imagen](./img/109.png)

+ Agregamos a la subzona un servidor ftp y le ponemos una IP.


![imagen](./img/110.png)


+ Creamos el equipo de administrador del sistema con su IP.


![imagen](./img/111.png)

### 2.1 Comprobación desde el servidor.

+ Realizamos varios `nslookup` con los nombres de los registros creados anteriormente.

![imagen](./img/112.png)

# 3. Cliente

+ Le ponemos una IP fija al cliente para tenerlo identificado más facilmente desde el servidor. Le añadimos la IP del servidor como DNS.

![imagen](./img/02.png)

+ Comprobamos que tenemos acceso a internet

![imagen](./img/401.png)

+ Comprobamos que se ha añadido un nuevo registro en el servidor desde que hemos conectado con el cliente. Efectivamente, podemos ver `Victor-Pc con su IP` en el servidor.

![imagen](./img/201.png)

+ Hacemos `nslookup` a los registros creados en el servidor y vemos que nos da tanto la dirección y nombre del servidor, como la dirección y nombre del propio registro.


![imagen](./img/202.png)

---
