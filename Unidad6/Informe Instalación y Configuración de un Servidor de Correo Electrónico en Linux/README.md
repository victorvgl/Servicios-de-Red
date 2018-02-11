
>Práctica Realizada por:
>
>[Carlos Delgado Hernández](https://github.com/carlsjdh)
>
>[Carmelo González Domínguez](https://github.com/SilverGG)
>
>[Víctor García Luis](https://github.com/victorvgl)


# Servidor de correo Linux

![imagen](./img/portada.jpg)

---

### [Instalación de Postfix](#1)

+ Instalamos *Postfix* con `sudo apt install postfix` y se nos desplegará una ventana de configuración del servicio.  

# <a name="1"></a>


![imagen](./img/004.png)  

![imagen](./img/001.png)

+ Escogemos *Sitio de Internet*.

![imagen](./img/002.png)

+ Establecemos *miempresa.com* como dominio del que hará uso *Postfix*.  

![imagen](./img/003.png)

+ Comprobamos con *netstat -utap* que el servicio *smtp* esta en modo escucha.  

![imagen](./img/005.png)

+  Añadimos los usuarios *loli* y *colego* (necesarios para la comprobación del funcionamiento del servicio *smtp*).  

![imagen](./img/007.png)

+  Una vez creados, accedemos al puerto 25 vía *telnet* y mandamos un correo de *loli* a *colego*.  

![imagen](./img/006.png)

+ Para acceder al buzón de *colego*, nos dirigiremos a `/var/spool/mail/` donde podremos comprobar que ha recibido el correo de *loli*.  

![imagen](./img/008.png)


+ Nos dirigimos al cliente, e instalamos *evolution* (un gestor de mensajería).  

![imagen](./img/009.png)

+ Establemos los enlaces en el *DNS* local al servidor, los dominios *smtp.miempresa.com* y *pop.miempresa.com*.  

![imagen](./img/010.png)

+ Probamos a enviar un correo dentro del dominio.  

![imagen](./img/012.png)

+ Y como podemos ver, se ha enviado correctamente.  

![imagen](./img/011.png)


### [IMAP](#2)  

+ Instalamos *IMAP* en el servidor vía *apt install dovecot-imapd*.  

![imagen](./img/013.png)

+ Comprobamos que el servicio está en escucha con `netstat -utap`.  

![imagen](./img/014.png)

+ Hecho esto, instalamos el gestor de correo *squirrelmail*.  

![imagen](./img/015.png)

+ Nos dirigimos a `/etc/apache2/sites-available` y establecemos las siguientes líneas de texto en *apache.conf*.  

![imagen](./img/017.png)

+ Activamos la página en `/etc/apache2/sites-enabled` con un enlace simbólico al previamente creado *apache.conf*.  

![imagen](./img/018.png)

+ Reiniciamos el servicio para cargar la nueva configuración.  

![imagen](./img/019.png)

+ Y comprobamos su funcionamiento desde cliente y servidor.  

![imagen](./img/020.png)


![imagen](./img/021.png)


![imagen](./img/022.png)



![imagen](./img/023.png)


### [POP3](#3)  

+ Instalamos el servicio *pop3* con `sudo apt install dovecot-pop3d`.  

![imagen](./img/024.png)

+ Comprobamos que está en modo escucha con el comando `netstat -puta`.  

![imagen](./img/025.png)

+ Nos aseguramos que la línea *disable_plaintext_auth* del fichero `/etc/dovecot/conf.d` sea igual a *no*.   

![imagen](./img/026.png)  

Por motivos aún desconocidos, el *evolution* o el *postfix* nos han dado bastantes problemas a la hora de enviar correos a cuentas de gmail, hecho que no nos ha permitido terminar la prática.
