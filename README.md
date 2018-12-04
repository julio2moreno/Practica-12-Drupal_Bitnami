# Practica-12-Drupal_Bitnami
###### Amazon Elastic Compute Cloud (Amazon EC2) es un servicio web que proporciona capacidad informática en la nube segura y de tamaño modificable. Está diseñado para simplificar el uso de la informática en la nube a escala web para los desarrolladores.
###### Bitnami es una empresa que ofrece instaladores que nos permiten realizar la instalación y configuración de aplicaciones web de una forma muy sencilla.

## Iniciar una instancia EC2
Lo primero que hay que hacer es abrir la consola de administración de AWS. Cuando la pantalla se cargue, escriba su nombre de usuario y contraseña para comenzar. A continuación seleccionamos Amazon EC2.
Le damos en  ``Launch Instance`` para crear y configurar una máquina virtual.

## Configuracion de la instancia
Ahora en la opcion del panel de la izquierda tenemos que seleccionar ``Community AMIs`` y en la barra del buscador ponemos ``drupal`` que es la instancia que vamos a crear.
vamos a coger la version 18.04 que es ``bitnami-drupal-8.6.3-0-linux-debian-9-x86_64-hvm-ebs`` damos en ``select``.

Damos ``continue``, en la opcion 2 tendremos que seleccionar ``t2.medium``, ya que la que viene por defecto no tiene suficiente memoria para arrancar la instancia y cuando se crea la instancia aparece un mensaje de error ``low memory``, en la opcion 6 donde configuraremos las reglas de seguridad y en ``add rule`` seleccionamos ``http`` y ``https`` para que nos deje acceder desde cualquier sitio y Launch.

 La siguiente pantalla muestra pares de claves. Los pares de claves se utilizan para conectarse a las instancias de EC2 mediante un programa de shell seguro (SSH).
 Seleccionamos la segunda opcion ``create a new key pair`` y ponemos un nombre a ese archivo y nos descargamos un archivo en extension .pem y seleccionamos ``Launch instances``.
 
 ## Conectarse a la instancia mediante Windows
 Una vez iniciada la instancia, deberá conectarse a ella mediante SSH.
 Lo primero que tenemos que tener instalado PuTTy para poder acceder via SSh: 
 
 Para descargar puTTY for Windows: https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html
 
Tenemos que cambiar el par de claves a .ppk que es la extension de claves privadas que utiliza PuTTy.
Por eso abrimos puTTYgen en la ventana seleccionamos ``load`` seleccionamos el archivo que anteriormente se nos ha descargado con la extension .pem, seleccionamos ``view all files`` y renombramos el archivo, a continuacion ``save private key``.

En el panel de la instancias nos vamos a ``connect`` y copiamos el public DNS. En el programa puTTY ponemos lo que hemos copiado. Ejemplo:``bitnami@ec2-52-90-146-135.compute-1.amazonaws.com``, en la barra lateral nos vamos a la opcion de ``ssh > Auth`` y ponemos la nueva clave que hemos creado.
- IMPORTANTE: Para conectar por defecto el usuario  es ``root`` hay que cambiarlo por el user ``bitnami``

 ## Conectarse a la instancia mediante Mac/Linux 
 Abrimos un terminal, damos permisos al archivo donde se encuentra el par de claves y con chmod cambiamos los permisos.
 
 ``chmod 400 archivoejemplo.pem ``
 
 Nos vamos al menu de instancias y en ``connect`` copiamos el public DNS y lo pegamos en el terminal.
 - IMPORTANTE: Para conectar por defecto el usuario  es ``root`` hay que cambiarlo por el user ``bitnami``

 ``ssh -i "archivoejemplo.pem" bitnami@ec2-52-90-146-135.compute-1.amazonaws.com``

 ## Instalación y configuración de Drupal
 Ahora vamos a instalar y configurar drupal con una maquina ubuntu ``bitnami-drupal-8.6.3-0-linux-debian-9-x86_64-hvm-ebs``, con el Drupal preinstalado con bitnami este  instalador incluye todo el software necesario para ejecutarse.
 
Añadimos la ip de IPv4 Public IP a nuestra url del explorador se nos abrira la pagina por defecto de drupal, en la parte de derecha aparece ``log in`` donde meteremos el usuario y la contraseña para que podamos configurar Drupal que: 
Para conocer la contraseña y el usuario se pueden hacer de dos maneras:

1.- Mediante el panel de las intancias:
Vamos a la pestaña de ``actions`` y en ``instance settings`` aparece la opcion de ``get system log`` donde aparecera un recuadro con el ``user`` y el ``password`` para acceder a la  configuracion de Wordpress. 

*Alguna vez me ha ocurrido de que no sale el usuario ni la contraseña en este proceso por la seguridad.

2.- Via ssh:
En ``/home`` existe un fichero llamado ``bitnami_credentials`` donde usaremos el comando cat para ver el usuario y la contraseña.

``cat bitnami_credentials``

Aparece un recuadro con el ``user`` y ``password``.

 ## Finalizar la instancia
En la consola de EC2. Haga clic en el botón Actions de la maquina que se quiere eliminar, vaya a ``Instance State`` y apareceran diferentes opciones ente ellas

- ``start`` inicio  de la maquina.

- ``stop`` apagar  de la maquina.

- ``reboot`` reinicio de la maquina.

- ``terminate`` eliminacion de la  maquina, este proceso dura varios minutos hasta que se finalize por completa la estancia.


![alt text](http:///github.com/julio2moreno/Practica-12-Drupal_Bitnami/escudo.png)

Practica-12-Drupal_Bitnami/escudo.png

![alt text](https://github.com/julio2moreno/Practica-12-Drupal_Bitnami/blob/master/escudo.png)
