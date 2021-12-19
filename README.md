# LAMP

#### Explicación previa

Con el docker-compose, montaremos tres contenedores, uno con Apache, otro con MySQL y uno con PHPmyAdmin. En el "Dockerfile" se encuentra la configuración de apache con PHP. Es importante respetar la estructura de carpetas que se presenta a continuación. 

La carpeta "src", será donde metamos nuestros archivos .html o .php para desplegar en el Apache de Docker. 

#### Preparación del entorno 

Lo primero que haremos es crear una carpeta de trabajo, que puede llamarse "ENTORNO_PHP_MYSQL". Dentro de esta, crearemos el archivo _docker-compose.yaml_, en el cual copiaremos el contenido del archivo docker que se encuentra en este repositorio. En esta carpeta también tendremos que crear un archivo con nombre _Dockerfile_, en el cual también copiaremos el contenido del Dockerfile que hay en este repositorio. Por último, crearemos una carpeta dentro de nombre _php_ y dentro de esta carpeta otra carpeta de nombre _src_.

![imagen](https://user-images.githubusercontent.com/80277545/146682822-1b5071eb-6794-4097-8334-15c9c17be434.png)

En caso de utilizar Linux, este proceso se resume a crear el directorio "ENTORNO_PHP_MYSQL" y dentro de este ejecutar _git clone https://github.com/Zoser777/LAMP .

#### Configuración de los archivos

Podemos abrir el documento .yaml y modificar usuario, contraseña, etc. Estos són los que posteriormente usaremos para acceder a PHPmyAdmin y MySQL.

![imagen](https://user-images.githubusercontent.com/80277545/146683152-50cba285-5243-4d35-8193-3d3461f7aadf.png)

#### Desplegando entorno

Una vez tenemos creados los documentos y modificado los parametros correspondientes, podemos situarnos en la carpeta "ENTORNO_PHP_MYSQL" y ejecutar "docker compose up" y se empezarán a montar los contenedores. 

#### Accediendo a los contenedores

Para acceder a cada uno de los contenedores ejecutaremos desde la terminal "docker exec -it ID_CONTENEDOR /bin/bash", 
una vez dentro de cada contenedor prodemos acceder a sus diversos programas. 

#### Acceder a PHPmyAdmin

Para acceder a PHPmyAdmin tendremos que poner en nuestro navegador "localhost:8080", el usuario y contraseña serán los que habremos establecido en el archivo Docker-compose.yaml . 

![imagen](https://user-images.githubusercontent.com/80277545/146683542-858a6e21-de38-4226-a5ef-da66db7957e6.png)



