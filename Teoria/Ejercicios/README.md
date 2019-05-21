### Tema 1:

## Ejercicio 1

__Buscar información sobre las tareas o servicios web para los que se usan más los programas que comentamos al principio.__

Apache: servidor web.

nginx: inicialmente fue creado como servidor web para paginas con mucho trafico. Tambien se usa bastante como balanceador de carga.

thttpd: servidor web de codigo libre. Es simple, pequeño, portatil, rapido y seguro ya que utiliza los requerimientos minimos de un servidor HTTP.

Cherokee: servidor web multiplataforma. Es rapido y completamente funcional sin dejar de ser libiano.

Node.js: Entorno en tiempo de ejecucion multiplataforma. Fue creado con el enforque de ser util en la creacion de programas de red altamente escalables.

### Tema 2:

## Ejercicio 1

|  Componente   | An (%) | An-1 (%) | Resultado (%) |
|---------------|--------|----------|---------------|
| Web           | 85     | 97.75    | 99.6625       |
| Aplicacion    | 90     | 99       | 99.9          |
| Base de datos | 99.9   | 99.9999  | 99.9999       |
| DNS           | 98     | 99.96    | 99.9992       |
| Cortafuegos   | 85     | 97.75    | 99.6625       |
| Switch        | 99     | 99.99    | 99.9999       |
| Data Center   | 99.99  | 99.99    | 99.99         |
| ISP           | 95     | 99.75    | 99.9875       |
| TOTAL         | -      | -        | 99,204        |

## Ejercicio 2
__Buscar frameworks y librerías para diferentes lenguajes que permitan hacer aplicaciones altamente disponibles con relativa facilidad.__

PM2: es un gestor de procesos en produccion para las aplicaciones Node.js con un balanceador de carga incorporado. Con ella podemos evitar los tiempo de inactividad.

Vaadin: plataforma de codigo abierto para el desarrollo de aplicaciones web. Incluye tanto un conjunto de componentes web, como un conjunto de herramientas y starters de aplicaciones.

### Tema 3:

## Ejercicio 1
__Buscar con qué órdenes de terminal o herramientas podemos configurar bajo Windows y bajo Linux el enrutamiento del tráfico de un servidor para pasar el tráfico desde una subred a otra.__

Para Windows podemos usar:

`route ADD [destino] MASK [mascara] [gateway] [metrica]`

Para Linux podemos usar:

	`route add -net [destino] netmask [mascara] gw [gateway]`
