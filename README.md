# SRI-DNS_Linux

##Configuración de docker-compose.yml

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


