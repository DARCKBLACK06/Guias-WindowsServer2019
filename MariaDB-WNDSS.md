
## Pasos para instalar MariaDB en windows server 2019

Primero iremos a la pagina oficial de mariadb en nuestro navegador y seleccionamos Download MariaDB Server.

![Captura1]()

Aqui seleccionaremos la version,sistema operativo,arquitectura y tipo de paquete que necesitemos siempre debemos elegir una version estable para que no tengamos problemas de incompatibilidad con otros programas.

![Captura2]()

Antes de instalar el programa descargado tendremos que hacer otra configuracion en el firewall.

Para eso vamos a ir al menu de inicio de windows y buscar firewall

![Captura3]()

Nos meteremos a configuracion avanzada para habilitar el puerto de entrada y salida para mariadb.

![Captura4]()

Una vez en la configuracion avanzada del firewall tendremos que habilitar los puertos que usa mariadb que por defecto es el puerto 3306 para ello no iremos a las sigueintes secciones para hablitar el puerto de entrada y salida.

Habilitar puerto de entrada para ello iremos a reglas de entrada y aqui crearemos una nueva regla.

![Captura5]()

Aqui especificaremos que tipo de regla quermos crear hay 3 tipos de regla por defecto (Programa, Puerto , Predefinida ) y una perzonalizada. 

Elegiremos la opcion puerto y daremos en siguiente, aqui nos dira que tipo de regla queremos habilitar TCP o UDP tambien nos pedira el numero de puerto que queremos habilitar por defecto lo dejaremos en TCP y escribiremos el puerto que usa mariadb por defecto 
```bash
3306
```
![Captura6]()

Una vez escrito le damos click en siguiente, nos pedira el tipo de accion de esta regla nos dara tres opciones:
* Conexion segura
* Permitir conexion si es segura
* Bloquear conexion

Elegimos conexion segura y daremos click en siguiente.

![Captura7]()

Nos pedira el tipo de perfil de la regla aqui nos mostrara tres opciones:
* Dominio
* Privado 
* Publico

Dejaremos marcadas las tres opciones por defecto si no tenemos una configuracion en especifico y daremos click en sigueinte.
![Captura8]()

Como paso final nos pedira el nombre y una descripcion esta es opcional.

![Captura9]()

>[!Note]
>Se recomienda agregar un nombre y descripcion relacionado al uso que se le dara para tenerlo mejor identificado.

### Estos pasos son los mismos para habilitar el puerto de salida del firewall.

Sigue los pasos anteriores,guarda y actualiza la pagina para confirmar que se hayan guardado las configuraciones.

![Captura10]()

### Una vez realizado estas configuraciones podemos instalar MariaDB sin ningun problema.

Daremos doble click sobre el instalador de MariaDB que descargamos,esto ejecutara el instalador donde daremos click en next.

![Captura11]()

Aceptamos los terminos y condiciones y damos click en next,nos mostrara los programas que se instalaran si no queremos instalar alguno de ellos le damos click y seleccionamos la opcion "Entire feature will be unavailable",una vez configurado a nuestras opciones daremos click en next.

![Captura12]()

En este paso nos pedira que crear una contrasena para el usuario root que viene por defecto,en  esta seccion tambien podemos habilitar la opcion de que el usuario root se pueda conectar remotamente a la base de datos esta opcion viene desactivada por defecto para habilitar solo daremos click sobre el recuadro y con eso estara habilitada,tambien vendra la opcion de usar UTF8 por defecto en el servidor esta opcion tambien viene desactivada por defecto si queremos usarla tendremos que habilitar,una vez configurado como nosotros queramos damos click en next.

![Captura13]()

En esta ventana vendran las siguientes opciones:
* Install as service
* Enable Networking
* Innodb Engine setting

Dejamos todo por defecto y damos click en next.

![Captura14]()

Una vez configurado todo damos click en instalar y listo.

![Captura15]()

Una vez finalizada la instalacion solo damos click en finish y listo con esto tendremos instalado gestor de base de datos en windows server.

![Captura16]()

Para poder probar que nuestra instalacion fue correcta crearemos una base de datos para poder conectarnos mediante el cliente "HeidiSQL" que viene instalado por defecto en MariaDB.

>[!NOTE]
>Este cliente solo estara instalado si en el proceso de instalacion no marcamos la opcion "Entire feature will be unavailable" la cual desactiva la opcion para instalarlo.

En inicio buscaremos "MYSQL CLIENT(MARIADB)" y lo ejecutaremos, al abrirlo nos pedira una contrasena esta sera la misma que creamos en la instalacion.

![Captura18]()

Al introducir la contrasena nos mostrara lo sigueinte lo cual quiere decir que nuestra instalacion fue correcta y ahora podemos crear bases de datos y usuarios.

![Captura18]()

Introduciremos los siguientes comandos.

CREATE DATABASE NombreBasedeDatos;
CREATE USER 'USUARIO'@'%' IDENTIFIED BY 'CONTRASENA';
GRANT ALL PRIVILEGES ON NombreBasedeDatos.* TO 'USUARIO'@'%';
FLUSH PRIVILEGES;
EXIT;

![Captura19]()

Una vez realizado el paso anterior nos dirigimos a HEIDISQL para introducir nuestro usuario y la contrasena y asi poder ingresar a una base de datos.

Una vez en Heidisql nos pedira una direccion ip,nombre,contrasena,el nombre de la base de datos a la cual tenemos accesso y el puerto.
* IP:n este caso usamos el localhost pero en otra maquina deberemos de usar la ip o dns de nuestro servidor.
* Contrasena:Esta nos sera asignada por el administrador que nos registro en la base de datos
* Nombre de la base de datos: Asignada por el administrador
* Puerto: si no se usa un puerto diferente el 3307 por ejemplo deberemos de usar el puerto asignado por default 3306.

![Captura20]()

Una vez agregados todos los datos y confirmarlos daremos click en aceptar e ingresaremos a la base de datos mediante el cleinte HeidiSQL concluyendo con la instalacion de MariaDB.
![Captura21]()

>[!Note]
>Recuerda no guardar la contrasena en el gestor de base de datos como medida de seguridad y que no se haga un mal uso de este acceso a la base de datos.



















