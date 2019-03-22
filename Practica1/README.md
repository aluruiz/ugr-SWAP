## Practica 1
### Presentacion de las herramientas - por Paula Ruiz

#### Instalacion y configuracion.
Empezamos creando las dos maquinas virtuales con Ubuntu Server 16.04, a las cuales les instalamos OpenSSH server y LAMP server desde el principio dentro de la inicialización del programa.

A continuacion configuramos las redes dentro de la configuracion de VirtualBox para que ambos servidores tengan la conexion entre ellos y la maquina principal que esta en windows. (*duda al profesor*).

![configuracion NAT](/capturas/red_parte1.PNG)
![configuracion Adaptador Solo-Anfitrión](/capturas/red_parte2.PNG)

Ademas, preparamos los servidores para que puedan tener comunicacion entre ellos y el host. Para ello les añadimos los IPs correspondientes mediante la interfaz de sincronizacion enp0s8 (ya que por defecto no estan definidos) todo esto en el archivo /var/network/interfaces, 192.168.56.100 (Maquina 1) y 192.168.56.200 (Maquina 2).

![network interface configuration 1](/capturas/network_interface_1.PNG)
![network interface configuration 2](/capturas/network_interface_2.PNG)

Activamos el enp0s8 mediante el comando `ifup enp0s8`. Y la configuracion de ambas maquinas quedaria tal que asi:

![ifconfig 1](/capturas/ifconfig_1.png)
![ifconfig 2](/capturas/ifconfig_2.png)

Probamos haciendo ping entre ambas maquinas tienen conexion entre ellas:

`ping 192.168.56.100`

![Ping a Maquina 1](/capturas/ping2a1.PNG)

`ping 192.168.56.200`

![Ping a Maquina 2](/capturas/ping1a2.PNG)

**A partir de aqui solo mostrare las capturas de pantalla de una unica maquina, ya que hago paralelamente lo mismo en ambas.**

#### Funcionamiento LAMP
Para comprobar el funcionamiento de LAMP probamos que cual es la version que usamos de apache y si esta funcinando.

![Prueba Apache2](/capturas/comprobacion_apache.PNG)

Tambien comprobamos la version de php y si esta en funcionamiento.

![Prueba PHP](/capturas/comprobacion_php.PNG)

Y por ultimo, probamos si podemos meternos en MySQL como base de datos del servidor.

![Prueba MySQL](/capturas/comprobacion_mysql.PNG)

#### Funcionamiento SSH
Para comprobar el funcionamiento de ssh hemos usado la orden `shh ipmaquina -l usuario` entre ambas maquinas.

Prueba de la 1 a la 2:

![SSH de la 1 a la 2](/capturas/ssh_1a2.PNG)

Prueba de la 2 a la 1:

![SSH de la 2 a la 1](/capturas/ssh_2a1.PNG)

#### Funcionamiento cURL
Para la comprobacion de cUrl creamos un documento HTML.

![Documento HTML](/capturas/archivo_html.PNG)

Y comprobamos mediante cUrl que tenemos acceso al mismo mediante la maquina 2 a la maquina 1.

![Prueba cUrl de la 2 a la 1](/capturas/comprobacion_curl_2.PNG)

Y comprobamos mediante cUrl que tenemos acceso al mismo mediante la maquina 1 a la maquina 2.

![Prueba cUrl de la 1 a la 2](/capturas/comprobacion_curl_1.PNG)

Y tambien comprobamos desde el nuestro navegador (HOST) que podemos acceder al mismo archivo.

![Prueba HOST](/capturas/comprobacion_html.PNG)
