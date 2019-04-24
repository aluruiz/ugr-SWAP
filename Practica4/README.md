## Practica 4.
### Asegurar una granja web - por Paula Ruiz.

### Crear e instalar un certificado SSL autofirmado.
#### Primero instalamos en la Máquina 1

Lo primero que vamos a hacer en esta práctica es instalar un certificado SSL para brindar más seguridad al visitante de una página web. El protocolo SSL es un protocolo que se ubica en la pila de protocolos sobre TCP/IP, por lo que proporciona servicios de comunicación segura entre cliente y servidor.

Así que empezamos activando el module SSL de Apache con el comando `a2enmod ssl`.

![a2enmod ssl](./capturas/a2enmod.PNG)

Y a continuación activamos el servicio de apache y creamos el directorio donde vamos a crear las claves, y las creamos mediante OpenSSL.

`service apache2 restart
mkdir /etc/apache2/ssl
openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout /etc/apache2/ssl/apache.key -out /etc/apache2/ssl/apache.crt`

![Openssl](./capturas/openssl.PNG)

A continuación editamos el archivo _/etc/apache2/sites-available/default-ssl.conf_ añadiendo las siguientes líneas:

`SSLCertificateFile /etc/apache2/ssl/apache.crt
SSLCertificateKeyFile /etc/apache2/ssl/apache.key`

![Certificados](./capturas/default-ssl.PNG)

Por último, activamos el sitio default-ssl y reiniciamos Apache.

`a2ensite default-ssl
service apache2 reload`

![Reinicio Apache](./capturas/a2ensite.PNG)

Y ya solo queda que comprobemos que esto funciona:

![Comprobación m1](./capturas/https_ub1.PNG)

#### Y después lo copiamos a la Máquina 2 y al balanceador mediante Rsync

Ahora vamos a copiar las claves del certificado al balanceador y a la máquina 2 mediante el comando:

`rsync -avz -e ssh 192.168.20.100:/etc/apache2/ssl/ /home/paula/ssl/`

Primero lo pasamos al home de cada máquina, y a continuación en la máquina 2 lo movemos a su propia carpeta en _/etc/apache2/ssl_, mientras que en el balanceador podemos dejarlo en el mismo home.

A continuación una breve trayectoria de las configuraciones en ambos servidores.

__En el balanceador:__

![Copia balanceador](./capturas/rsync_balanceador.PNG)

Una vez tenemos la copia de las claves para el certificado, nos dirigimos al directorio _/etc/nginx/conf.d/default.conf_ y lo modificamos para que pueda escuchar también el _https_ desde el puerto _443_.

![Config balanceador](./capturas/nginx-configuracion.PNG)

Y comprobamos que todo funciona mediante la orden:

`curl -k https://192.168.20.105/index.html`

![Comprobación balanceador](./capturas/https_nginx.PNG)

__En la máquina 2:__

![a2enmod m2](./capturas/a2enmod-ssl-maquina2.PNG)

![Copia máquina 2](./capturas/rsync_maquina2.PNG)

Una vez que lo tenemos aquí, hacemos los mismos pasos que hemos hecho antes para la máquina 1, excepto lo de crear el certificado.

Activamos el sitio y reiniciamos apache

![Reiniciar Apache m2](./capturas/maquina2-reload-apache.PNG)

Y por último comprobamos que todo funciona:

![Comprobación m2](./capturas/https_ub2.PNG)

###Configurar cortafuego con IPTABLES.

Para configurar el cortafuegos, lo primero que creamos es un script con la configuración básica para un cortafuegos en Ubuntu, lo llamare _script_iptables.sh_ y lo ubicare en la carpeta _/usr/local/bin/_.

![Script cortafuegos](./capturas/firewall_config.PNG)

A continuación, vamos a hacer que se ejecute cada vez que se inicie la máquina. Para ello crearemos un demonio y lo ubicaremos en la carpeta _/etc/systemd/system/_ y lo llamaremos _config-iptables.service_.

![Creacion del Demonio](./capturas/demonio.PNG)

Una vez creado, mediante los siguientes comandos, lo activamos.

`systemctl daemon-reload
systemctl enable config-iptables.service`

![activación](./capturas/activar-demonio.PNG)

Y ya por último mediante `netstat -tulpn` y `iptables -L -n -v` comprobamos que todo funciona bien.

![Netstat](./capturas/netstat.PNG)

![ipTables](./capturas/iptables.PNG)
