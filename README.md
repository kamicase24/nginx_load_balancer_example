# Balanceador de Cargas y proxy inverso con nginx

El archivo nginx.conf contiene la configuración de NGINX para establecer un equilibrador de carga básico. A continuación, se describen las principales características del archivo:

1. Se definen 3 archivos html que representarían los servicios
2. Se inicia los 3 servicios con Docker utilizando el siguiente comando
    `docker run --rm -v /path/to/file/index.1.html:/usr/share/nginx/html/index.html --network default nginx`
3. Se define un grupo de servidores llamado "localhost" utilizando la directiva upstream.
4. Los servidores dentro del grupo "localhost" son: 172.17.0.1:8004, 172.17.0.1:8003 y 172.17.0.1:8000.
5. Se configura un servidor que escucha en el puerto 80 utilizando la directiva server.
6. La ubicación / en este servidor está configurada para redirigir el tráfico hacia los servidores del grupo "localhost" utilizando la directiva proxy_pass.
