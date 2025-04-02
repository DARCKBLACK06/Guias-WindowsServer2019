# Politicas de Grupo para Windows Server: 
## Configuracion de Acceso y Personalizacion de Escritorio 

[Descripcion de que son las GPOS]


### Restringir Acceso al Panel de Control mediante GPOS

 Nos dirijimos al menu de inicio y en la seccion de Herramientas Administrativas desplegamos el menu y seleccionamos Administracion de directivas de Grupo

 ![Imagen de inicio Gpos](https://github.com/DARCKBLACK06/Guias-WindowsServer2019/blob/main/Gpos%2FCaptura1.png)

Esto nos llevara a la siguiente ventana donde en la seccion bosque desplegaremos entraremos a dominios y nos iremos a nuestro dominio en este caso netsecure.com

![Imagen de Bosque](https://github.com/DARCKBLACK06/Guias-WindowsServer2019/blob/main/Gpos%2FCaptura2.png)

Aqui se nos desplegara el siguiente menu donde nos iremos a "Objetos de directivas de grupo" aqui por defecto estaran dos directivas creadas con el nombre Default Domain aqui

![Imagen directivas](https://github.com/DARCKBLACK06/Guias-WindowsServer2019/blob/main/Gpos%2FCaptura3.png)

Daremos click derecho y crearemos una nueva gpo le pondremos un nombre para identificarlo en este caso Area-ventas y aceptar con esto la directiva de grupo se habra creado 

![Imagen crear-gpo](https://github.com/DARCKBLACK06/Guias-WindowsServer2019/blob/main/Imagenes%2FCaptura4.PNG)

![Imagen ejemplo creado](https://github.com/DARCKBLACK06/Guias-WindowsServer2019/blob/main/Imagenes%2FCaptura5.PNG)

Ahora daremos click derecho sobre el nombre de nuestra Gpo y seleccionaremos editar.

![Editar gpo](https://github.com/DARCKBLACK06/Guias-WindowsServer2019/blob/main/Imagenes%2FCaptura6.PNG)

Esto nos llevara al editor de administracion de directivas de grupo.

![Editor Gpo](https://github.com/DARCKBLACK06/Guias-WindowsServer2019/blob/main/Imagenes%2FCaptura7.PNG)

Aqui nos iremos a configuracion de usuario , directivas y plantillas administrativas.

![Plantillas administrativas ](https://github.com/DARCKBLACK06/Guias-WindowsServer2019/blob/main/Imagenes%2FCaptura8.PNG)

Aqui configuaremos el panel de control y la configuracion del equipo para que no puedan ser manipulados por los usuarios, nos iremos a Panel de control y seleccionaremos la que tiene el nombre Prohibir el acceso a configuracion de Pc y a Panel de control.

![Prohibir PNLCTRL](https://github.com/DARCKBLACK06/Guias-WindowsServer2019/blob/main/Imagenes%2FCaptura9.PNG)

Daremos doble click sobre ella y nos mostrara el sigueinte menu donde estara en No configurada por defecto la Habilitaremos y agregaremos un comentario esto es opcional despues damos click en Aplicar y Aceptar.

![Habilitar](https://github.com/DARCKBLACK06/Guias-WindowsServer2019/blob/main/Imagenes%2FCaptura10.PNG)

>[!Note]
>Esto prohibiera cualquier intento de acceso a la configuracion del dispositivo que sea anadido al active directory por lo cual para realizar modificaciones debera de ser realizada por un administrador.

## Establecer fondo de pantalla predeterminado y prohibir su modificacion 

Para poder configurar un fondo de pantalla predeterminado para los usuarios deberemos de crear una carpeta con nuestros fondos de pantalla antes de anadir esta configuracion en la GPO.

Crearemos la carpeta con un nombre que sea facil de recordar en este caso Wallpapers-Netsecure aqui estaran nuestros fondos de pantalla.

![Carpeta](https://github.com/DARCKBLACK06/Guias-WindowsServer2019/blob/main/Imagenes%2FCaptura11.PNG)

>[!Note]
>Es importante que nuestros fondos de pantalla sean en formato JPG para que no tenga problemas de compatibilidad.

Una vez creada podemos moverla de lugar a una carpeta en especifico o dejarala donde la cramos en este caso sera movida al Disco Local "C:"

![Carpeta Movida](https://github.com/DARCKBLACK06/Guias-WindowsServer2019/blob/main/Imagenes%2FCaptura11.PNG)

Una vez movida la carpeta de lugar daremos click derecho sobre ella y nos iremos a propiedades y compartir carpeta.

![Propiedades Carpeta](https://github.com/DARCKBLACK06/Guias-WindowsServer2019/blob/main/Imagenes%2FCaptura12.PNG)

Damos click en compartir esto nos llevara a un menu donde podremos agregar al grupo de trabajo o usuario,escribiremos el nombre si lo sabemos o podemos darle click en la flecha y seleccionar buscar personas.

![Buscar Personas](https://github.com/DARCKBLACK06/Guias-WindowsServer2019/blob/main/Imagenes%2FCaptura13.PNG)

Si desconocemos el nombre del usuario o grupo de trabajo seleccionamos buscar personas esto nos llevara al siguiente menu donde podremos escribir una referencia a lo que buscamos o examinar y buscar la carpeta donde se encuentre si esta en una ubicacion diferente.

Damos click en opciones avanzadas esto nos llevara al siguiente menu donde estara la ubicacion de nuestro dominio Columnas,consultas,etc.

![Opciones Avnzds](https://github.com/DARCKBLACK06/Guias-WindowsServer2019/blob/main/Imagenes%2FCaptura14.PNG)

Damos click en buscar ahora esto desplegara la lista de usuarios y grupos de trabajo aqui buscaremos el que deseamos anadir y damos click en aceptar 

![Compartir](https://github.com/DARCKBLACK06/Guias-WindowsServer2019/blob/main/Imagenes%2FCaptura15.PNG)

Si el grupo de trabajo es correcto al darle click en aceptar a las diferentes ventanas nos aparecera de la siguiente manera donde lo dejaremos en lectura esto para que no pueda ser modificada damos click en commpartir y listo,podemos anadir mas grupos de trabajo si queremos que estos tengan los cambios tambien.

![Compartit1.2](https://github.com/DARCKBLACK06/Guias-WindowsServer2019/blob/main/Imagenes%2FCaptura16.PNG)

Al finalizar iremos a propiedades de la carpeta y compartir donde tendra una ubicacion similar a esta "\\DARCKBLACKCI\Wallpaper-Netsecure", copiaremos y guardaremos la direccion que se nos muestra.

![Direccion](https://github.com/DARCKBLACK06/Guias-WindowsServer2019/blob/main/Imagenes%2FCaptura17.PNG)

Seguiremos los pasos anteriores donde configuramos el panel de control y nos dirijiremos al apartado de configuracion de usuario,plantillas administrativas,Active desktop,Active desktop.

![Active desktop](https://github.com/DARCKBLACK06/Guias-WindowsServer2019/blob/main/Imagenes%2FCaptura18.PNG)

Aqui tendremos que habilitar tres configuraciones para que el fondo de pantalla sea activado,el usuario no pueda modificarlo y anadir el fondo de pantalla que deseamos.

Seleccionaremos la opcion habilitar desktop daremos doble click y cambiaremos de No configuraa a Habilitada esto para prohibir que sea desactivada por alguien mas, aplicamos y guardamos los cambios.

![HActiveD](https://github.com/DARCKBLACK06/Guias-WindowsServer2019/blob/main/Imagenes%2FCaptura19.PNG)

Realizamos el paso anterior con la configuracion "No permitir cambios" esto para que el usuario no pueda cambiar el fondo de pantalla, aplicamos y guardamos cambios.

![No permitir C](https://github.com/DARCKBLACK06/Guias-WindowsServer2019/blob/main/Imagenes%2FCaptura20.PNG)

Ahora seleccionaremos "Tapiz del escritorio" cambiaremos de No configurada a Habilitar despues con la direccion que copiamos anteriormente donde dice nombre de papel tapiz con el nombre de nuestra imagen, Asi nos debera de quedar aplicaremos y guardaremos cambios.

![Wallpaper](https://github.com/DARCKBLACK06/Guias-WindowsServer2019/blob/main/Imagenes%2FCaptura21.PNG)

>[!Note]
>Podemos seleccionar un estilo para el papel tapiz depende de como queramos que sea mostrado ya sea centrado,ajustado,relleno,etc

Una vez guardadas las configuraciones en la ventana de administracion de directivas copiaremos la gpo creada en este caso area-ventas la pegaremos en el area donde queramos aplicar estas configuraciones o si queremos que se aplique para todos los usuarios la pegamos en la carpeta principal de nuestro dominio al pegar la gpo nos mostrara un mensaje de que vincuaremos la gpo creada daremos en aceptar con esto los cambios seran aplicados a los usuarios.

![cap22](https://github.com/DARCKBLACK06/Guias-WindowsServer2019/blob/main/Imagenes%2FCaptura-22.PNG)
![cap23](https://github.com/DARCKBLACK06/Guias-WindowsServer2019/blob/main/Imagenes%2FCaptura-23.PNG)

Para finalizar en una ventana de simbolo de sistema ejecutaremos el sigueinte comando para que las directivas de grupo sean actualizadas.

```bash
gpupdate /force
```
![cap24](https://github.com/DARCKBLACK06/Guias-WindowsServer2019/blob/main/Imagenes%2FCaptura-24.PNG)
