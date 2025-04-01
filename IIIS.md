# Configuracion de Servidor Web IIS con php en windows Server2019
 [Descripcion de que es IIS para que sirve etc]

 # Instalacion Php
 ### Primer Paso

 Buscaremos la pagina de php daremos click en descargas y seleccionaremos la opcion de  Binaries are available for Microsoft Windows. 
 
![imagen paso 1](https://github.com/DARCKBLACK06/Guias-WindowsServer2019/blob/main/Imagenes/Paso1.PNG)

 ### Segundo paso 
 En el apartado de PHP 8.4 seleccionaremos descargaremos el paquete zip de VS17 x64 Non Thread Safe 
 
![imagen Paso 2](https://github.com/DARCKBLACK06/Guias-WindowsServer2019/blob/main/Imagenes/Paso2.PNG)

 ### Tercer Paso 
 Descargar el modulo FastCGI en la seccion Which version do I choose? daremos en la parte VS16 & VS17 seleccionaremos la version X64
 
![Imagen paso 3](https://github.com/DARCKBLACK06/Guias-WindowsServer2019/blob/main/Imagenes/Paso3.PNG)

 ### Cuarto paso 
 Vamos a descomprimir el archivo zip que descargamos y lo pegaremos en el disco local "c" 
 
 ![Imagen paso 4](https://github.com/DARCKBLACK06/Guias-WindowsServer2019/blob/main/Imagenes/Paso4.PNG)

 ### Quinto paso
 Agregaremos la ruta de php a las variables de entorno del sistema copiamos la ruta "C:\php" y dando click derecho en este equipo y propiedades esto nos llevara a las propiedades de sistema una vez ahi daremis click en Configuracion avanzada del sistema en opciones avanzadas seleccionaremos variables de entorno y en la seccion variables del sistema seleccionaremos Path y daremos click en editar, seleccionamos nuevo y pegamos la direccion de php que es "C:\php" y guardaremos los cambios 
 
![Imagen paso 5](https://github.com/DARCKBLACK06/Guias-WindowsServer2019/blob/main/Imagenes/Paso5.PNG)  
![Imagen paso 5.1](https://github.com/DARCKBLACK06/Guias-WindowsServer2019/blob/main/Imagenes/Paso5.1.PNG)
![Imagen paso 5.2](https://github.com/DARCKBLACK06/Guias-WindowsServer2019/blob/main/Imagenes/Paso5.2.PNG)

 ### Sexto paso
 Instalaremos la extension Vs redistribute dando click derecho y ejecutar como administrador aceptamos los terminos y condiciones y daremos click en instalar
 
![Imagen paso 6](https://github.com/DARCKBLACK06/Guias-WindowsServer2019/blob/main/Imagenes/Paso6.PNG)

 > [!NOTE]
 >Para comprobar que php esta instalado abriremos una ventana del sismbolo del sistema presionando win+x y escribiremos cmd una ves en la ventana de cmd escribiremos php --version debera de aparecer 
 >"PHP x.x.x".
> 
![Imagen comprobacion cmd](https://github.com/DARCKBLACK06/Guias-WindowsServer2019/blob/main/Imagenes/Comprobacion-cmd.PNG)

 # Instalacion de Servicios IIS
 [Descripcion de que es IIS]

 Paso 1
 Lo Primero que hay que hacer es irnos al meno de inicio y abrir el administrador de servidor

 ![Imagen comprobacion cmd](https://github.com/DARCKBLACK06/Guias-WindowsServer2019/blob/main/Imagenes/Captura-1.PNG)

 Paso 2
 
 ### Instalacion de IIS, FTP y CGI

 Daremos click en la opcion de agregar roles y caracteristicas daremos click en siguiente, seleccionamos instalacion basada en caracteristicas o en roles , seleccionamos un servidor del grupo de servidores en roles del servidor seleccionamos servidor web (IIS) damos click en agregar carcteristicas y siguiente hasta llegar al apartado de  servicios del rol, bucaremos el apartado "Desarrollo de aplicaciones"y marcaremos la opcion "CGI" abajo buscaremos la opcion que dice serevidor ftp y seleccionamos las siguientes casillas, damos click en siguiente marcamos la opcion Reiniciar automaticamente y damos en click en instalar
  ![Imagen comprobacion cmd](https://github.com/DARCKBLACK06/Guias-WindowsServer2019/blob/main/Imagenes/Captura-2.PNG)
  ![Imagen comprobacion cmd](https://github.com/DARCKBLACK06/Guias-WindowsServer2019/blob/main/Imagenes/Captura-3.PNG)
  ![Imagen comprobacion cmd](https://github.com/DARCKBLACK06/Guias-WindowsServer2019/blob/main/Imagenes/Captura-4.PNG)
  ![Imagen comprobacion cmd](https://github.com/DARCKBLACK06/Guias-WindowsServer2019/blob/main/Imagenes/Captura-5.PNG)
  
Paso 3 
Una vez finalizada la instalacion en el incio del panel de administracion de servidor no aparece el servidor IIS 

 ![Imagen comprobacion cmd]![Imagen comprobacion cmd](https://github.com/DARCKBLACK06/Guias-WindowsServer2019/blob/main/Imagenes/Captura-6.PNG)

 Daremos click sobre el servidor IIS y esto nos llevara al serevidor IIS ahi le daremos click derecho donde dice el nombre de nuestro servidor y seleccionaremos administrador de IIS 

 ![Imagen comprobacion cmd]![Imagen comprobacion cmd](https://github.com/DARCKBLACK06/Guias-WindowsServer2019/blob/main/Imagenes/Captura-7.PNG)

 En este apartado daremos click en el nombre de nuestro servidor y nos iremos a sitios en acciones daremos click en agregar sitio web 
  ![Imagen comprobacion cmd]![Imagen comprobacion cmd](https://github.com/DARCKBLACK06/Guias-WindowsServer2019/blob/main/Imagenes/Captura-8.PNG)
 
 Acontinuacion se muestra un ejemplo de configuracion del sitio web para esto se necesita lo siguiente:
 DNS 
 Carpeta con los archivos web
 Nombre del sitio 

  ![Imagen comprobacion cmd]![Imagen comprobacion cmd](https://github.com/DARCKBLACK06/Guias-WindowsServer2019/blob/main/Imagenes/Captura-9.PNG)

En este ejemplo la carpeta se coloco en el dico "C:" puede poner la carpeta donde usted deseé 

 ![Imagen comprobacion cmd]![Imagen comprobacion cmd](https://github.com/DARCKBLACK06/Guias-WindowsServer2019/blob/main/Imagenes/Captura-10.PNG)

 Agregar un servidor FTP 
En el apartado de sitios ,daremos click en agregar stios ftp 

 ![Imagen comprobacion cmd]![Imagen comprobacion cmd](https://github.com/DARCKBLACK06/Guias-WindowsServer2019/blob/main/Imagenes/Captura-11.PNG)

Agregaremos su nombre del servidor y la direccion de la carpeta que añadiremos a ftp en este caso se uso Netsecure-FTP igual alojada en el disco "C:"

 ![Imagen comprobacion cmd]![Imagen comprobacion cmd](https://github.com/DARCKBLACK06/Guias-WindowsServer2019/blob/main/Imagenes/Captura-12.PNG)

Damos click en siguiente y se usara las siguientes configuraciones 
Todas las IPs asignadas
Sin  SSL

 ![Imagen comprobacion cmd](https://github.com/DARCKBLACK06/Guias-WindowsServer2019/blob/main/Imagenes/Captura-13.PNG)

Informacion de autenticacion y autorizacion
Marcaremos las siguientes opciones 

Autenticacion : Anonima 
Autorizacion : Todos los usuarios
Permisos : Leer,Escribir 

 ![Imagen comprobacion cmd](https://github.com/DARCKBLACK06/Guias-WindowsServer2019/blob/main/Imagenes/Captura-14.PNG)

Configuraciones 

Nos iremos ala Pagina Principal de Nuestro dominio 

 ![Imagen comprobacion cmd](https://github.com/DARCKBLACK06/Guias-WindowsServer2019/blob/main/Imagenes/Captura-15.PNG)

En el apartado IIS configuraremos lo siguiente:

Documento predeterminado 
Asignaciones de controlador

Configuracion del documento predeterminado daremos doble click sobre el esto nos llevara a este apartado en acciones daremos click en agregar escribiendo "index.php" y aceptar

 ![Imagen comprobacion cmd](https://github.com/DARCKBLACK06/Guias-WindowsServer2019/blob/main/Imagenes/Captura-16.PNG)

 Configuracion de asignaciones de controlador daremos doble click sobre el esto nos llevara a este apartado en acciones daremos click en agregar asignacion de modulo agregando las siguientes configuraciones:

 Ruta de acceso escribiremos
 ```bash
 *.php
 ```
 Modulo seleccionaremos
 ```bash
 FastCgiModule
 ```

 Ejecutable 
 Nos dirijiremos a la carpeta de php instalada previamente en este caso disco local "C:\php" seleccionando 
 ```bash
 C:\php\php-cgi.exe
 ```
 Nombre 
 Podemos poner el que nosotros queramos
 Ejemplo 
 ```bash
 FastCgiPhp
 ```
Configuracion final

 ![Imagen comprobacion cmd](https://github.com/DARCKBLACK06/Guias-WindowsServer2019/blob/main/Imagenes/Captura-17.PNG)
 ![Imagen comprobacion cmd](https://github.com/DARCKBLACK06/Guias-WindowsServer2019/blob/main/Imagenes/Captura-18.PNG)
 ![Imagen comprobacion cmd](https://github.com/DARCKBLACK06/Guias-WindowsServer2019/blob/main/Imagenes/Captura-19.PNG)
Damos click en aceptar y luego en si.

Con esto abremos terminado de configurar nuestro servidor IIS y FTP ahora buscaremos nuestra pagina web atraves de nuestro dns.

> [!NOTE]
> Si no tenemos una documento index.html podemos crear un documento info.php que sera con lo que podramos comprobar que nuestro servidor web funciona correctamente.

![Imagen comprobacion cmd]![Imagen comprobacion cmd](https://github.com/DARCKBLACK06/Guias-WindowsServer2019/blob/main/Imagenes/Captura-20.PNG)




