>Práctica Realizada por:
>
>[Carlos Delgado Hernández](https://github.com/carlsjdh)
>
>[Carmelo González Domínguez](https://github.com/SilverGG)
>
>[Víctor García Luis](https://github.com/victorvgl)

# Instalación y Configuración de un Servidor de VOIP sobre Ubuntu.

![imagen](./img/portada.png)

---

### [Instalación y Configuración de un Servidor VOIP](#1)

+ Instalación de la distribución `Elastix` basada en Debian.
+ Configuración del servidor `Elastix`.
+ Configuración del software cliente.
+ Pruebas de conectividad.

---
#  <a name="1"></a> 1. Servidor VOIP

## Instalación y configuración

+ Descargamos la imagen `iso` de la página web [Elastix](https://www.elastix.org/es/downloads/).


![imagen](./img/1.png)


+ Creamos una `máquina virtual` para instalar la distribución anteriormente descargada.


![imagen](./img/2.png)


+ Establecemos los parámetros de configuración generales:

![imagen](./img/3.png)

![imagen](./img/4.png)

+ Una vez terminado el proceso de instalación, la máquina se iniciará.

![imagen](./img/5.png)

+ Seleccionamos `(1) Using a Web Browser` y nos mostrará la IP del servidor para acceder a través de la wb.


![imagen](./img/6.png)


+ Una vez dentro, configuramos el servidor para funcionar como `Servidor Voip`.


![imagen](./img/7.png)

+ El servicio necesita de una licencia. Nos registraremos en la página web [3CX](https://www.3cx.com/).


![imagen](./img/8.png)

+ Nos mandan la clave de licencia al correo asociado al registro de la cuenta. Es una clave para ofrecernos un servicio de prueba.


![imagen](./img/10.png)

![imagen](./img/11.png)


+ Registramos un usuario para la consola de nuestro servidor Voip.


![imagen](./img/12.png)

+ Asignamos una IP estática, en este caso, el servidor `Elastix`.

![imagen](./img/13.png)

![imagen](./img/a.png)


+ Seguiremos rellenando datos para la configuración del servicio


![imagen](./img/14.png)

![imagen](./img/15.png)

![imagen](./img/16.png)

+ Establecemos la longitud del número de extensión de llamada `3 Digits`.


![imagen](./img/18.png)

![imagen](./img/19.png)


+ Registro de los datos del usuario asociado a la licencia `3cx`.


![imagen](./img/21.png)


+ Ya tenemos todo listo para arrancar el servicio.

![imagen](./img/23.png)

+ Si accedemos a la IP del servidor, nos muestra el panel de inicio de sesión.

![imagen](./img/24.png)

+ Iniciamos el servicio con el usuario y contraseña previamente especificados.


![imagen](./img/25.png)


+ Y esto sería el panel de control principal que nos encontraríamos al conectarnos a Elastix.


![imagen](./img/26.png)


+ Ahora descargamos el cliente de `Voip` para establecer las llamadas. El software necesario se llama `Softphone` disponible para Windows.


![imagen](./img/27.png)


+ Podemos ver los usuarios registrados para realizar llamadas. Por defecto sale el usuario registrado al servicio.


![imagen](./img/28.png)


+ Agregamos un número de teléfono en el apartado de extensiones del panel de control de `Elastix`.


![imagen](./img/29.png)





![imagen](./img/30.png)


+ Iniciamos el `software cliente`


![imagen](./img/31.png)

+ Agregamos el usuario `Pepe` creado anteriormente.


![imagen](./img/33.png)


![imagen](./img/34.png)


+ Ahora tenemos el programa configurado para el usuario `Pepe`.


![imagen](./img/35.png)


+ En el servidor podemos observar como nos muestra si está conectado el usuario


![imagen](./img/36.png)


+ Ahora creamos otro usuario `María` para realizar las pruebas de llamadas entre distintos clientes.


![imagen](./img/37.png)


+ Procedemos a marcar el número asociado al usuario `Pepe` desde el usuario `Maria`. El programa cliente de `Pepe` nos muestra esto:


![imagen](./img/38.png)


+ El usuario `Pepe` contesta a la llamada y se establece la conexión `Voip`.


![imagen](./img/39.png)
