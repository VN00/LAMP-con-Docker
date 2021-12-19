# LAMP con Docker

## Instalación en Ubuntu
#### Explicación previa

Con el docker-compose, montaremos tres contenedores, uno con Apache, otro con MySQL y uno con PHPmyAdmin. En el "Dockerfile" se encuentra la configuración de apache con PHP. Es importante respetar la estructura de carpetas que se presenta a continuación. 

La carpeta "src", será donde metamos nuestros archivos .html o .php para desplegar en el Apache de Docker. 

#### Preparación del entorno 

Lo primero que haremos es crear una carpeta de trabajo, que puede llamarse "ENTORNO_PHP_MYSQL". Dentro de esta, crearemos el archivo _docker-compose.yaml_, en el cual copiaremos el contenido del archivo docker que se encuentra en este repositorio. En esta carpeta también tendremos que crear un archivo con nombre _Dockerfile_, en el cual también copiaremos el contenido del Dockerfile que hay en este repositorio. Por último, crearemos una carpeta dentro de nombre _php_ y dentro de esta carpeta otra carpeta de nombre _src_.


![imagen](https://user-images.githubusercontent.com/80277545/146685326-0cb4a09e-91f3-4a01-b43b-59291a2b36b6.png)


En caso de utilizar Linux, este proceso se resume a crear el directorio "ENTORNO_PHP_MYSQL" y dentro de este ejecutar _git clone https://github.com/Zoser777/LAMP .

![imagen](https://user-images.githubusercontent.com/80277545/146687132-20066833-38db-4cad-8524-96759f3066da.png)



#### Estructura:

![imagen](https://user-images.githubusercontent.com/80277545/146685361-5e5ec4ed-4783-44be-91f9-4cdc179a43b1.png)



#### Configuración de los archivos

Podemos abrir el documento .yaml y modificar usuario, contraseña, etc. Estos són los que posteriormente usaremos para acceder a PHPmyAdmin y MySQL.

![imagen](https://user-images.githubusercontent.com/80277545/146685285-19520ed8-8928-4db3-a860-70370ae9eb12.png)



#### Desplegando entorno

Instalamos Docker:

      sudo apt install docker.io
      
      
Instalamos Curl:

      sudo apt install curl

Instalamos Docker compose con el siguiente comando:

      sudo curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose

Damos permisos necesarios: 

      sudo chmod +x /usr/local/bin/docker-compose
      
Comprobamos que docker funciona:

      docker-compose --version
      
![imagen](https://user-images.githubusercontent.com/80277545/146685556-e20727da-5f35-42c7-a4d3-400f2a004d0c.png)



Una vez tenemos creados los documentos y modificado los parametros correspondientes, podemos situarnos en la carpeta "ENTORNO_PHP_MYSQL" y ejecutar "docker-compose up" y se empezarán a montar los contenedores. 

      docker-compose up -d


Se empezarán a descargar las imagenes de los contenedores y a montarse.

![imagen](https://user-images.githubusercontent.com/80277545/146685711-2a60f340-7ae3-487a-b38a-558aad20e803.png)

Una vez finalizado, podemos ejecutar "docker ps" para ver que están funcionando los tres contenedores:

      docker ps
 
![imagen](https://user-images.githubusercontent.com/80277545/146685745-5c138f54-e58d-499f-b2a9-e78cc8d4b11b.png)



#### Acceder a PHPmyAdmin

Para acceder a PHPmyAdmin tendremos que poner en nuestro navegador "localhost:8080", el usuario y contraseña serán los que habremos establecido en el archivo Docker-compose.yaml . 

![imagen](https://user-images.githubusercontent.com/80277545/146685791-2b690471-8e23-4230-a38e-6160ce0125cb.png)

En mi caso, el usuario y contraseña es "administrador" y "12345": 

![imagen](https://user-images.githubusercontent.com/80277545/146685826-f572fd88-46c1-4d69-bf06-2f2587f05bd8.png)

Accedemos:

![imagen](https://user-images.githubusercontent.com/80277545/146685860-a4727dde-87f6-4790-9894-dbce8dd85a6f.png)


# Configurar Apache con Netbeans 

#### Instalamos Netbeans

Primero instalamos el JDK (herramientas de java para que pueda funcionar)

            apt install openjdk-8-jdk
            
Posteriormente instalamos Netbeans con Snap:

            snap install netbeans --classic
            
Abrimos el Netbeans y comprobamos que funcione: 

![imagen](https://user-images.githubusercontent.com/80277545/146686232-a73551d4-4838-4a5d-9ddf-8e62ceba3e8c.png)

##### Configuramos apache

![imagen](https://user-images.githubusercontent.com/80277545/146686351-e49c4184-b941-47dd-a1bc-818279579817.png)

Ahora optenemos la IP del contendor:


![imagen](https://user-images.githubusercontent.com/80277545/146687315-8c52aef0-05cf-4b48-ad1c-f986d3876c1a.png)


Si ponemos la IP, nos tendría que solventar con la pagina: 

![imagen](https://user-images.githubusercontent.com/80277545/146687326-5b113752-762d-404f-b380-43ea09c1dff0.png)

 Este "Forbidden" se debe a que no tenemos ninguna pagina cargada, si nos vamos a nuestra carpeta "ENTORNO_PHP_MYSQL", dentro de "php", "src" creamos un index.html con cualquier contenido, nos saldrá en Apache. 
Si analizamos el docker-compose.yaml, esto se debe a que está creado el volumen. 

![imagen](https://user-images.githubusercontent.com/80277545/146688726-011915b6-bf06-49b2-8574-354eea443ed2.png)

Ahora si recargamos el navegador, nos sale el siguiente resultado: 

![imagen](https://user-images.githubusercontent.com/80277545/146688762-8e6df365-da12-4a16-9f5e-7c617bd020b4.png)



