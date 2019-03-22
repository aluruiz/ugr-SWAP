## Practica 1
### Presentacion de las herramientas - por Paula Ruiz

#### Instalacion y configuracion.
Empezamos creando las dos maquinas virtuales con Ubuntu Server 16.04, a las cuales les instalamos OpenSSH server y LAMP server desde el principio dentro de la inicialización del programa.

A continuacion configuramos las redes dentro de la configuracion de VirtualBox para que ambos servidores tengan la conexion entre ellos y la maquina principal que esta en windows. (*duda al profesor*).

![configuracion NAT](/capturas/red_parte1.png)
![configuracion Adaptador Solo-Anfitrión](/capturas/red_parte2.png)

Ademas, preparamos los servidores para que puedan tener comunicacion entre ellos y el host. Para ello les añadimos los IPs correspondientes mediante la interfaz de sincronizacion enp0s8 (ya que por defecto no estan definidos) todo esto en el archivo /var/network/interfaces, 192.168.56.100 (Maquina 1) y 192.168.56.200 (Maquina 2).

![network interface configuration 1](/capturas/network_interface_1.png)
![network interface configuration 2](/capturas/network_interface_2.png)

Activamos el enp0s8 mediante el comando `ifup enp0s8`. Y la configuracion de ambas maquinas quedaria tal que asi:

![ifconfig 1](/capturas/ifconfig_1.png)
![ifconfig 2](/capturas/ifconfig_2.png)

Probamos haciendo ping entre ambas maquinas que funcionan

`ping 192.168.56.100`
![Ping a Maquina 1](/capturas/ping2a1.png)
`ping 192.168.56.200`
![Ping a Maquina 2](/capturas/ping1a2.png)

#### Funcionamiento LAMP

#### Funcionamiento SSH

#### Funcionamiento cURL
