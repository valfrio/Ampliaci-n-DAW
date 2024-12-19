# Configuración de un Servidor Nginx con Hosts Virtuales y Directorios de Usuario

## Conexion SSH

Nos conectaremos en la máquina virtual mediante ssh para comenzar la práctica.

![1](includes/images/1.png)

## Creacion de Usuarios

Ahora crearemos los usuarios que necesitaremos para la práctica y le damos una contraseña a cada uno.
Le añadimos -m y -s, para que se cree el directorio home y se le asigne un shell.

![2](includes/images/2.png)


## Creación de las Carpetas public_html

Ahora crearemos las carpetas public_html en cada uno de los directorios home de los usuarios.
Para hacerlo usamos el comando su seguido del nombre de usuario y después creamos la carpeta.

![3](includes/images/3.png)

## Asignación de Permisos

Para que los usuarios public_html, cambiaremos las ACLs de los directorios public_html de cada usuario. Para ello usaremos el comando setfacl y compronbamos que se han asignado correctamente con getfacl.

![4](includes/images/4.png)

## Creación de Páginas Web Estáticas

Se creará una página web estática en cada uno de los directorios public_html de los usuarios.

![5](includes/images/5.png)

Para el otro usuario, haremos lo mismo.

![6](includes/images/6.png)

## Configuración de Nginx

Instalamos Nginx con el comando `sudo apt install nginx`.

![7](includes/images/7.png)

Con el comando `sudo systemctl status nginx.service` comprobamos que el servicio está activo.

## Generación de Certificados SSL

Generemos los certificados SSL

![8](includes/images/8.png)

Ahora configurar los hosts virtuales en Nginx. Para ello, crearemos un archivo de configuración en la carpeta /etc/nginx/sites-available para cada uno de los usuarios.

![9](includes/images/9.png)

Para el otro usuario, haremos lo mismo.

![10](includes/images/10.png)

Ahora crearemos un enlace simbólico en la carpeta /etc/nginx/sites-enabled con el comando `sudo ln -s /etc/nginx/sites-available/huginweb /etc/nginx/sites-enabled/huginweb`. Después comprobamos el archivo de configuración con `sudo nginx -t`.


## Comprobación de los Hosts Virtuales

Se comprobará que los hosts virtuales están funcionando correctamente. Para ello añadiremos las direcciones IP de los hosts virtuales en el archivo /etc/hosts.

![11](includes/images/11.png)

## Comprobación de Funcionamiento de los Hosts Virtuales

Ahora intentamos acceder a las páginas web de los usuarios desde un navegador.

![12](includes/images/12.png)

La página funcionando correctamente.

![13](includes/images/13.png)

Para el otro usuario, haremos lo mismo.

![14](includes/images/14.png)
