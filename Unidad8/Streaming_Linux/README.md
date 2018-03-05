
>Práctica Realizada por:
>
>[Carlos Delgado Hernández](https://github.com/carlsjdh)
>
>[Carmelo González Domínguez](https://github.com/SilverGG)
>
>[Víctor García Luis](https://github.com/victorvgl)

# Instalación y Configuración de un Servidor Multimedia Linux

![imagen](./img/portada.gif)

---

### [Instalación y Configuración de un Servidor Multimedia (Audio)](#1)

+ Vamos a instalar un servidor Multimedia ( Audio)  en un servidor linux.

+ Descargaremos y configuraremos todo lo necesario para su correcto funcionamiento.

+ Haremos una serie de comprobaciones desde el mismo servidor y un cliente al igual que accederemos a este desde un navegador y desde un software de reproducción multimedia para comprobar su correcto funcionamiento.

---
#  <a name="1"></a> 1. Servidor Multimedia – Audio

## Instalación y configuración

+ Descargamos e instalamos el paquete **Icecast**

![imagen](./img/Screenshot_1.png)

+ Se nos abrirá el asistente de configuración pero como más adelante vamos a configurarlo desde los archivos de configuración le damos a **NO** y dejamos que terminen la instalación.

![imagen](./img/Screenshot_2.png)

+ Vamos al archivo de configuración `/etc/icecast2/icecast.xml` y configuramos lo siguiente:

```
<source-password>contraseña_source</source-password>
<admin-user>tu_usuario</admin-user>
<admin-password>contraseña_administrador</admin-password>
```

![imagen](./img/Screenshot_3.png)

+ Ahora editaremos el fichero `/etc/default/icecast2` para habilitar el script *init.d* por lo que pondremos la *habilitar en verdadero*.

![imagen](./img/Screenshot_4.png)

+ Iniciamos el servicio y comprobamos que está activo.

![imagen](./img/Screenshot_5.png)

+ A continuación instalamos el codificador vorbis **ices2**.

![imagen](./img/Screenshot_6.png)

+ Creamos un nuevo directorio `mkdir /etc/ices2` y copiamos el archivo de configuración del codificador que está en la ruta ` /usr/share/doc/ices2/examples/ices-playlist.xml` para pasarlo a la ruta anteriormente creada.

![imagen](./img/Screenshot_7.png)

+ Editamos el fichero de configuración del codificador y establecemos los parámetros de nuestra emisora mediante las siguientes etiquetas:

```
<name>Mi Estación de Radio</name>
<genre>Pop-Rock</genre>
<description>Radio musical dedicada al pop y al rock</description>

<param name=”file”>/etc/icecast2/playlist.txt</param>

<port>8000</port>
<password>tu_contraseña</password>
<mount>/radiostation</mount>

```
![imagen](./img/Screenshot_8.png)
![imagen](./img/Screenshot_9.png)
![imagen](./img/Screenshot_23.png)

+ Recopilamos unos cuantos ficheros de audio en formato **ogg** creamos el directorio `/tmp/música` y copiamos los mismos dentro de este.

![imagen](./img/Screenshot_11.png)

+ Desde el directorio `/etc/icecast2` creamos un **playlist.txt** que va a guardar la lista de reproducción. Le cambiamos los permisos para evitar futuros conflictos.

![imagen](./img/Screenshot_12.png)

+ Generamos la lista de reproducción de la siguiente manera y la comprobamos.

![imagen](./img/Screenshot_13.png)

+ Antes de ejecutar el codificador, necesitamos crear un directorio para los Logs de ices2. `mkdir /var/log/ices2`


![imagen](./img/Screenshot_14.png)

+ Ejecutamos el codificador en background

![imagen](./img/Screenshot_18.png)

## Comprobaciones

+ Abrimos un navegador desde el mismo servidor para comprobar su funcionamiento. Entramos desde `localhost:8000` y ponemos nuestro usuario y contraseña anteriormente configurados.

![imagen](./img/Screenshot_15.png)

+ Podemos comprobar que accedemos correctamente


![imagen](./img/Screenshot_16.png)

+ Ahora vamos a *Mountpoint List* y comprobamos que podemos escuchar la radio en stream correctamente pulsando en **M3U**

![imagen](./img/Screenshot_25.png)

+ Abrimos y se escucha perfectamente


![imagen](./img/Screenshot_26.png)

+ Podemos ver las stats configuradas anteriormente mientras está en funcionamiento.


![imagen](./img/Screenshot_27.png)

+ Comprobamos el estado del servidor en funcionamiento.


![imagen](./img/Screenshot_28.png)

## Cliente

+ Ahora comprobamos que efectivamente podemos entrar desde un cliente.


![imagen](./img/Screenshot_29.png)

+ Podemos ver, las ips conectadas en tiempo real al servidor, en mi caso, veo la IP del cliente.


![imagen](./img/Screenshot_30.png)

+ Por último, vamos a añadir manualmente la dirección de nuestro servidor desde un cliente para comprobar que podemos acceder desde un software de reproducción multimedia.


![imagen](./img/Screenshot_31.png)

+ Añadimos la dirección.

![imagen](./img/Screenshot_32.png)

+ Buscamos el servidor desde el reproductor.

![imagen](./img/Screenshot_33.png)

+ Podemos acceder correctamente.

![imagen](./img/Screenshot_34.png)

---
