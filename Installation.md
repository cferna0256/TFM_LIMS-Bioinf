## Instalación de Senaite LIMS

Para llevar a cabo la instalación, seguimos los pasos detallados en la página web de Senaite (https://www.senaite.com/docs/installation).

NOTA: para el paso "Install System Dependencies" de la guía de instalación hay que modificar el fichero "sudoers". Para ello, ejecutamos el siguiente comando:

$ sudo gedit /etc/sudoers

Se nos abrirá el fichero en un editor de texto. Tenemos que añadir los usuarios al final, siguiendo este esquema:

-------------------------------
#includedir /etc/sudoers.d

#Usuario actual

root ALL=(ALL:ALL) ALL

senaite ALL=(ALL:ALL) ALL

------------------------------

## Instalar copia de máquina virtual
Para agilizar el proceso de instalación, se aporta una copia del sistema operativo Ubuntu con la instalación Senaite ya realizada. Tan solo hay que instalarla en una máquina virtual Oracle mediante el menú "Archivo / Importar servicio virtualizado". Una vez instalada, ejecutarla e iniciar sesión mediante usuario "senaite" y contraseña "admin". Una vez dentro, abrir la terminal ejecutar los siguientes comandos:

--------------------------------------
$ conda activate senaite

$ cd /home/senaite/senaitelims

$ bin/instance fg

--------------------------------------

De esta forma, se inicia el servicio de senaite. Una vez que nos aparezca un mensaje del tipo "INFO Zope ready to handle requests" abrimos una navegador de internet y vamos a la dirección localhost. Se nos abrirá la página principal de Senaite.

