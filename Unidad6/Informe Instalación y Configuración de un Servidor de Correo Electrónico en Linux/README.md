
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

![imagen](./img/011.png)

+ s

![imagen](./img/012.png)

+

![imagen](./img/012.png)

+

![imagen](./img/013.png)

+

![imagen](./img/014.png)

+

![imagen](./img/015.png)

+

![imagen](./img/016.png)

+

![imagen](./img/017.png)

+

![imagen](./img/018.png)



![imagen](./img/019.png)

+

![imagen](./img/020.png)

+

![imagen](./img/021.png)

+

![imagen](./img/022.png)

+

![imagen](./img/023.png)

+

![imagen](./img/024.png)

+

![imagen](./img/025.png)

+

![imagen](./img/026.png)
