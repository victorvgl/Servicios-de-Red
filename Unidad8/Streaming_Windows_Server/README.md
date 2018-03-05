
>Práctica Realizada por:
>
>[Carlos Delgado Hernández](https://github.com/carlsjdh)
>
>[Carmelo González Domínguez](https://github.com/SilverGG)
>
>[Víctor García Luis](https://github.com/victorvgl)

# Instalación y Configuración de un Servidor Multimedia

![imagen](./img/portada.jpg)

---

### [Instalación y Configuración de un Servidor Multimedia – Smooth Streaming](#1)

+ Vamos a instalar un servidor Multimedia `ISS Media Services` para el servidor web ISS, para poder dar un servicio en streaming mediante un nuevo sitio web que crearemos con anterioridad. Para ellos también, crearemos un nuevo dominio, en nuestor caso, `midominio.ext` con el alias `bunny` especificado en la práctica que estará asociado a dicho sitio web.

+ Descargaremos emisiones codificadas, cambiaremos su configuración, instalaremos `Silverligh` y haremos comprobaciones.

+ Por último analizaremos los servicios multimedia instalados y su funcionamiento.

### [Instalación y Configuración de un Servidor Multimedia-Codificación de contenido propio](#2)

+ Ahora vamos a seguir utilizando los servicios multimedia pero esta vez, con contenido propio.

+ Vamos a Descargar e instalar Microsoft Expression Encoder junto con la característica de Experiencia de Escritorio en nuestro servidor Windows 2012.

+ Volveremos a crear un sitio web asociado a un registro DNS y a una carpeta física guardada donde queramos. Usaremos un archivo de audio en mp3 como prueba para usar el Encoder.

+ Comprobaremos su funcionamiento.


---
#  <a name="1"></a> 1. Servidor Multimedia – Smooth Streaming

## Instalación y configuración

+ Lo primero que tenemos que hacer, es ir al [Enlace Oficial](https://www.microsoft.com/es-es/download/details.aspx?id=27955) de microsoft y descargar el **IIS Media Services**.


![imagen](./img/1.png)

+ Seguimos el asistente de instalación hasta finalizar la misma.


![imagen](./img/2.png)

+ Creamos el nuevo registro DNS con el dominio `midominio.ext` y le añadimos un host A con la IP de nuestro servidor y un alias hacia dicho host.

![imagen](./img/3.png)

+ Creamos el nuevo Sitio `Bunny` en nuestro servidor ISS y como podemos comprobar desde el administrador del ISS, tenemos los servicios multimedia activos tras la instalación anterior.


![imagen](./img/5.png)

+ Creamos una carpeta en la ruta que queramos para almacenar el ejemplo de emisiones multimedia codificadas que nos descargaremos desde el servidor del aula. Descomprimimos y el archivo SmoothStreamingPlayer.html lo renombraremos como index.html para que nuestro sitio lo reconozca como página principal.

![imagen](./img/8.png)

+ Enlazamos el sitio a la carpeta anteriormente creada.


![imagen](./img/6.png)

+ Modificamos la url del archivo anteriormente renombrado con la dirección de nuestro dominio.


![imagen](./img/9.png)

## Instalación de Silverlight y comprobación.

+ Abrimos un navegador con la dirección `bunny.midominio.ext` e instalamos el Silverlight.


![imagen](./img/10.png)

+ Seguimos los pasos de instalación.


![imagen](./img/11.png)

+ Recargamos la página y como podemos comprobar, funciona correctamente. Hacemos la comprobación desde un cliente y también funciona correctamente.


![imagen](./img/12.png)


## Limitación de velocidad

+ En los ajustes del ISS de nuestro sitio, podemos limitar la velocidad de transmisión, opción muy importante para poder albergar a un mayor número de usuarios simultáneos.

![imagen](./img/25.png)

+ Entramos y como podemos comprobar, no tenemos ninguna limitación a ninguna extensión de archivos multimedia.

![imagen](./img/26.png)

+ Vamos a limitar por ejemplo, los archivos multimedia de tipo mp4. Para ello, le damos `botón derecho/Modificar`

![imagen](./img/27.png)

+ Le cambiamos el valor de limitación al que queramos.


![imagen](./img/28.png)

+ Y ya solo nos queda habilitar la opción que por defecto viene sin limitación.

![imagen](./img/29.png)

## Smooth Streaming

+ Ahora vamos a ver otra característica de transmisión por secuencia suave que nos permite añadir nuevas emisiones multimedia y modificar la que ya tenemos, como quitarle una pista de audio, añadir otra, etc.

![imagen](./img/30.png)

+ Vamos al apartado `Modificar transmisión por secuencias suave`

![imagen](./img/31.png)

+ Aquí podremos ver las emisiones multimedia, modificarla, añadir y quitar pistas, etc..

![imagen](./img/32.png)


#  <a name="2"></a> 1. Servidor Multimedia – Codificación de contenido propio

## Instalación y configuración.

+ Vamos al asistente para agregar roles y características y agregamos **Experiencia de escritorio**


![imagen](./img/13.png)

+ Seguimos el proceso de instalación hasta finalizar.

![imagen](./img/14.png)

+ Vamos al [Enlace](https://www.microsoft.com/es-es/download/details.aspx?id=27870) para descargar el Microsoft Expressión Encoder.


![imagen](./img/15.png)

+ Hacemos la instalación después de descargarlo.


![imagen](./img/16.png)
![imagen](./img/17.png)

+ Creamos el nuevo registro DNS `tudominio.ex` con un host tipo A con la IP de nuestro servidor y un alias `playlist` apuntando al host.


![imagen](./img/18.png)

+ Creamos el nuevo sitio web `Playlist` y lo asociamos a la ruta con la carpeta que hemos creado en C: llamada **playlist**.

![imagen](./img/19.png)

## Expression encoder

+ Abrimos el Expression encoder y abrimos un Proyecto de Silverlight.

![imagen](./img/20.png)

+ Añadimos los elementos multimedia que queremos codificar ( en neustro caso es un archivo en mp3) y le especificamos la ruta creada anteriormente.

![imagen](./img/21.png)

+ Al acabar la codificación podemos comprobar que en la ruta C:/playlist vemos que se han generado los archivos codificados.


![imagen](./img/23.png)

+ Ahora debemos añadir Default.html a los documentos predeterminados o renombrar el archivo para poder acceder directamente a nuestro sitio `playlisit.tudominio.ex`

![imagen](./img/22.png)

## Comprobación

+ Como podemos comprobar funciona correctamente tanto desde el servidor como el cliente.

![imagen](./img/24.png)

---
