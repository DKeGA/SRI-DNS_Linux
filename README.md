# SRI-DNS_Linux

##Configuración de docker-compose.yml

Para poder levantar el contenedor tendremos que crear un archivo docker-compose.yml el cual configuraremos de la siguiente forma:

services:
    bind9:
        container_name: asir_bind9
        image: internetsystemsconsortium/bind9:9.16
        networks:
            bind9_subnet:
                ipv4_address: 10.1.0.222
        volumes:
         - /home/asir2a/Escritorio/DNS/config:/etc/bind
         - /home/asir2a/Escritorio/DNS/zonas:/var/lib/bind
    asir_cliente:
        container_name: asir_cliente
        image: alpine
        networks:
            - bind9_subnet
        stdin_open: true #docker run -i
        tty: true        #docker run -t
        dns:
            - 10.1.0.222
    alpine_cliente:
        container_name: alpine_cliente
        image: alpine
        stdin_open: true 
        tty: true        
        dns:
            - 10.1.0.222
networks:
    bind9_subnet:
        external: true

