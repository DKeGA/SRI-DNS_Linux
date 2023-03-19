# SRI-DNS_Linux

## Configuración de docker-compose.yml

Para poder levantar el contenedor tendremos que crear un archivo docker-compose.yml el cual configuraremos de la siguiente forma:

    -Servicios:

        -Servicio: bind9

            -Nombre del contenedor: asir_bind9

            -Nombre de la imagen: internetsystemsconsortium/bind9:9.16

            -Network:

                -Nombre de la red: bind9_subnet

                -Ip de la red: 10.1.0.222

            -Volumenes:

                /home/asir2a/Escritorio/Linux_DNS/conf:/etc/bind

                /home/asir2a/Escritorio/Linux_DNS/zonas:/var/lib/bind

        -Servicio: asir_cliente

            -Nombre del contenedor: asir_cliente

            -Nombre de la imagen: alpine

            -Network:

                -bind9_subnet

                -stdin_open: true

                -tty: true

                -dns: 10.1.0.222

        -Servicio: alpine_cliente

            -Nombre del contenedor: alpine_cliente

            -Nombre de la imagen: alpine

            -stdin_open: true

            -tty: true

            -dns: 10.1.0.222

    -Redes:

        -bind9_subnet:

            -external: true


## Ficheros de configuración

Dentro del directorio de configuración encontraremos tres archivos 

* named.conf
* named.conf.local
* named.conf.options

## Configuración de las zonas

En este directorio encontraremos un archivo de configuración llamado:

* db.asir.com

Dentro de este encontraremos varios registros a configurar:

1. NS
    - Indicca a donde ir a buscar la dirección IP de un dominio
2. A
    - Devuelve una dirección iPv4 de 32 bits que se usa para asignar nombres de host a una dirección IP
3. CNAME
    - Alias de un nombre
4. TXT
    - Indica un mensaje que asignemos 
5. SOA
    - Almacena información sobre un dominio o una zona.


## Levantar y comprobar el servicio

Una vez configurado todo el servicio procederemos a levantarlo, para ello nos situaremos en la carpeta donde este el fichero docker-compose.yml. Una vez en dicha carpeta usaremos el comando "docker-compose up".

Una vez el servicio este levantado, para comprobar si funciona haremos un ping a la ip del servicio.















