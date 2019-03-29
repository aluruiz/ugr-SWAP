## Practica 2
### Colna la informacion de un sitio web - por Paula Ruiz

### Funcionamiento de la copia de archivos por ssh.
Esta funcion sirve para crear un archivo tar.tgz de un equipo y dejarlo directamente en el equipo destino si no disponemos espacio en nuestro disco local.

En esta ocasion vamos a crear una carpeta en nuestra maquina 1, con diferentes tipos de archivos.

![Creacion carpeta](./capturas/creacion_carpeta.PNG)

Y ahora vamos a aplicar a la carpeta creada la compresion al archivo tar.tgz en nuestra maquina 2.

`tar czf - copia_Archivos | ssh 192.168.56.200 'cat > ~/tar.tgz'`

![Comprimo carpeta](./capturas/paso_carpeta.PNG)

Y ahora comprobamos que el archivo comprimido se encuentra en nuestra maquina 2.

![Revision carpeta](./capturas/revision_carpeta.PNG)
