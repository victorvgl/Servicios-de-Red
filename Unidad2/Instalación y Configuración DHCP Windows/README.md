
# Instalación y Configuración DHCP Windows

![imagen](./img/portada.png)

#### Práctica de instalación y configuración del DHCP en window server, se harán ámbitos, exclusiones, reservas de IP, superámbitos etc...

---

# 1. Instalación del DHCP en Window Server 2012

Dentro del Administrador del servidor, vamos a *Agregar roles y características.*

![imagen](./img/00.png)

Vamos a roles del servidor y marcamos la casilla *Servidor DHCP*

![imagen](./img/01.png)

Agregamos la características

![imagen](./img/02.png)

Seguimos con la instalación estándard

![imagen](./img/03.png)

![imagen](./img/04.png)

Una vez llegado a resultados, cuando termine, nos aparecerá una pestaá llamada `Completar configuración DHCP` la pinchamos y vamos a autorización.

![imagen](./img/05.png)

![imagen](./img/06.png)

Ponemos el nombre del equipo para las credenciales.

![imagen](./img/07.png)

Luego le damos a confirmar y cerramos la ventana.

![imagen](./img/08.png)

# 1.1 Configuración DHCP

Ahora tenemos que ir a la pestaña Herramientas/DHCP.

![imagen](./img/09.png)

Dentro de DHCP, iremos al dominio, IPV4 click derecho y pulsaremos en `Nuevo Ámbito`

![imagen](./img/10.png)

Le ponemos un nombre al ámbito, le damos a siguiente y comenzamos por poner el intervalo de direcciones que queremos que estén dentro de este ámbito.

![imagen](./img/11.png)

Le damos a siguiente y ahora vamos a excluir alguna IP que no queremos que excluya el ámbito, ( debe estar dentro del intervalo anterior)

![imagen](./img/12.png)

seguimos la configuración estandad

![imagen](./img/13.png)

Ahora tenemos que poner la ip del router ( puerta de enlace )

![imagen](./img/14.png)

Nombre de dominio y DNS predeterminado de la configuración del servidor.

![imagen](./img/15.png)

Activamos el ámbitos.

![imagen](./img/16.png)

Ya podemos comprobar que tenemos el ámbito activado.

![imagen](./img/17.png)

# 2 Comprobación del ámbito desde el cliente

+ Si la instalación ha ido bien, vamos al cliente **(Tenemos tanto el cliente como el servidor configurado en la misma red internamente)** y comprobamos que nos da IP por DHCP y que esta, está dentro del rango asignado en el ámbito.

Comprobación funcionando.

![imagen](./img/18.png)

Comprobación desde el servidor

![imagen](./img/19.png)

# 2.1 Creación de un segundo ámbito

+ Ahora vamos a crear un segundo ámbito con otra IP para más adelante, hacer reservas y un superámbito. Tenemos que seguir los mismos pasos anteriores pero con una IP o una máscara diferente ya que si es igual, detectará que ya está usada en el priemr ámbito.

Segundo ámbito

![imagen](./img/20.png)

Volvemos hacer la exclusión de la IP o IPs que queramos

![imagen](./img/21.png)

Ya tenemos los dos ámbitos creados.

![imagen](./img/22.png)

+ **Como solo estamos probando con un cliente, hasta que el primer ámbito no se llene, tendremos que desactivar el primer ámbito para probar el segundo, este funcionará exactamente igual que el primero poniendo otra tarjeta de red, ya que solo disponemos de un router y las ips son diferentes. El resultado es exactamente el mismo pero con la IP 173.**

# 3. Creación de un Superámbito

+ Ahora vamos a crear un superámbito para unir los dos ámbitos creados anteriormente.

Le damos botón derecho en IPv4 y pulsamos en nuevo superámbito. Le ponemos el nombre que queramos.

![imagen](./img/23.png)

Marcamos los dos ámbitos disponibles y le damos a siguiente.

![imagen](./img/24.png)

Nos saldrá los dos ámbitos que vamos añadir al superámbito, le damos a finalizar.

![imagen](./img/25.png)

Podemos comprobar que se ha creado correctamente. ( si desactivamos el superámbito, se desactivan lkos dos ámbitos)

![imagen](./img/26.png)

Ahora vamos hacer una reserva dentro de los rangos puesto en cualquiera de los dos ámbitos, añadimos la IP que queremos utilizar y la MAC del cliente. Si la IP no está utilizada, el ámbito agregará automáticamente esa IP al cliente.

![imagen](./img/27.png)

Como podemos comprobar, con el superámbito creado y los dos ámbitos activos, funciona correctamente.

![imagen](./img/28.png)
