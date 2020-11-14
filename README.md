# TFM Máster Bioinformática

En este documento se detallan los pasos seguidos durante la realización del Trabajo Final de Máster, en el cual se configura un sistema de gestión de la información delos laboratorios (LIMS) open source mediante herramientas ágiles de gestión de proyectos.

## Instalación de Senaite LIMS

Para llevar a cabo la instalación, seguimos los pasos detallados en la página web de Senaite (https://www.senaite.com/docs/installation).

NOTA: para el paso "Install System Dependencies" hay que modificar el fichero "sudoers". Para ello, ejecutamos el siguiente comando:

$ sudo gedit /etc/sudoers

Se nos abrirá el fichero en un editor de texto. Tenemos que añadir los usuarios al final, siguiendo este esquema:

#includedir /etc/sudoers.d

#Usuario actual
root ALL=(ALL:ALL) ALL
senaite ALL=(ALL:ALL) ALL
