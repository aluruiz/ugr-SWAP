## Practica 1
### Presentación de las herramientas - por Paula Ruiz

### Instalación y configuración.
Empezamos creando las dos máquinas virtuales con Ubuntu Server 16.04, a las cuales les instalamos OpenSSH server y LAMP server desde el principio dentro de la inicialización del programa.

A continuación, configuramos las redes dentro de la configuración de VirtualBox para que ambos servidores tengan la conexión entre ellos y la máquina principal que está en Windows.

![configuración NAT](./capturas/red_parte1.PNG)
![configuración Adaptador Solo-Anfitrión](./capturas/red_parte2.PNG)

Además, preparamos los servidores para que puedan tener comunicación entre ellos y el host. Para ello les añadimos los IPs correspondientes mediante la interfaz de sincronización enp0s8 (ya que por defecto no están definidos) todo esto en el archivo /var/network/interfaces, 192.168.56.100 (Máquina 1) y 192.168.56.200 (Máquina 2).

![network interface configuración 1](./capturas/network_interface_1.PNG)
![network interface configuración 2](./capturas/network_interface_2.PNG)

Activamos el __enp0s8__ mediante el comando `ifup enp0s8`. Y la configuración de ambas máquinas quedaría tal que así:

![ifconfig 1](./capturas/ifconfig_1.PNG)
![ifconfig 2](./capturas/ifconfig_2.PNG)

Probamos haciendo ping entre ambas máquinas tienen conexión entre ellas:

`ping 192.168.56.100`

![Ping a Máquina 1](./capturas/ping2a1.PNG)

`ping 192.168.56.200`

![Ping a Máquina 2](./capturas/ping1a2.PNG)

_A partir de aquí solo mostrare las capturas de pantalla de una única máquina, ya que hago paralelamente lo mismo en ambas._

### Funcionamiento LAMP
Para comprobar el funcionamiento de LAMP probamos que cual es la versión que usamos de apache y si esta funcionando.

![Prueba Apache2](./capturas/comprobacion_apache.PNG)

También comprobamos la versión de php y si está en funcionamiento.

![Prueba PHP](./capturas/comprobacion_php.PNG)

Y por último, probamos si podemos meternos en MySQL como base de datos del servidor.

![Prueba MySQL](./capturas/comprobacion_mysql.PNG)

### Funcionamiento SSH
Para comprobar el funcionamiento de ssh hemos usado la orden `shh ipmaquina -l usuario` entre ambas máquinas.

Prueba de la 1 a la 2:

![SSH de la 1 a la 2](./capturas/ssh_1a2.PNG)

Prueba de la 2 a la 1:

![SSH de la 2 a la 1](./capturas/ssh_2a1.PNG)

### Funcionamiento cURL
Para la comprobación de cUrl creamos un documento HTML.

![Documento HTML](./capturas/archivo_html.PNG)

Y comprobamos mediante cUrl que tenemos acceso al mismo mediante la máquina 2 a la máquina 1.

![Prueba cUrl de la 2 a la 1](./capturas/comprobacion_curl_2.PNG)

Y comprobamos mediante cUrl que tenemos acceso al mismo mediante la máquina 1 a la máquina 2.

![Prueba cUrl de la 1 a la 2](./capturas/comprobacion_curl_1.PNG)

Y también comprobamos desde el nuestro navegador (HOST) que podemos acceder al mismo archivo.

![Prueba HOST](./capturas/comprobacion_html.PNG)
