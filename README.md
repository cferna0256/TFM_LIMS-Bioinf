# TFM Máster Bioinformática

En este documento se detallan los pasos seguidos durante la realización del Trabajo Final de Máster, en el cual se configura un sistema de gestión de la información de los laboratorios (LIMS) open source mediante herramientas ágiles de gestión de proyectos.

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
Para agilizar el proceso de instalación, se aporta una copia del sistema operativo Ubuntu con la instalación Senaite ya realizada. Tan solo hay que instalarla en una máquina virtual oracle mediante el menú "Archivo / Importar servicio virtualizado". Una vez instalada, ejecutarla e iniciar sesión mediante usuario "senaite" y contraseña "admin". Una vez dentro, abrir la terminal ejecutar los siguientes comandos:

--------------------------------------
$ conda activate senaite

$ cd /home/senaite/senaitelims

$ bin/instance fg

--------------------------------------

De esta forma, se inicia el servicio de senaite. Una vez que nos aparezca un mensaje del tipo "INFO Zope ready to handle requests" abrimos una navegador de internet y vamos a la dirección localhost. Se nos abrirá la página principal de Senaite.

## Configuraciones realizadas
Se ha configurado un ejemplo sencillo de un servicio de secuenciación. Este servicio ofrecerá secuenciación unidireccional o bidireccional y, dependiendo del tipo de muestra, habrá que realizar una extracción previa de material genético y/o una PCR previas a la secuenciación.

### Usuarios y permisos
Para acceder al sistema se han configurado tres usuarios, además del rol de admin:

- Laboratory Manager: tiene toda clase de permisos e modificación de análisis, instrumentos y aprobación de resultados y muestras (user: labman / pass: labman).
- Laboratory Clerk: tiene permisos de registro de muestras y validación de resultados (user: labclerk / pass: labclerk).
- Laboratory Analyst: tiene permisos solo de registro de muestras e introducción de resultados (user: labanalyst / pass: labanalyst).

Todos ellos pertenecen al mismo laboratorio: Sequencing Service.


### Clientes
Con el objetivo de identificar las muestras y los análisis realizados en cada una de ellas, se dan de alta clientes "ficticios": North Hospital, Public Health Institute y FernaLabs.

### Muestras
Para el registro de muestras, se configuran los campos de la plantilla de registro, dejando solo los necesarios. También se crean los siguientes Tipos de Muestreo: PCR Product, Plasmid, Tissue, DNA. Además, modificamos el identificador de muestra (ID) para que aparezcan la fecha de registro de la muestra y el cliente.

### Análisis
Se dan de alta las siguientes categorías de análisis:
- Pre-Sequencing
- Standard Sequencing

Dentro de "Pre-sequencing" se configuran los siguientes servicios de análisis:
- DNA extraction (A260/A280) - unidades nm ratio
- PCR - unidades pb

Dentro de "Standard Sequencing" se configuran los siguientes análisis:
- Forward - GC content (%)
- Forward - Length (pb)
- Forward - Fasta File (-)
- Reverse - GC content (%)
- Reverse - Length (pb)
- Reverse - Fasta File (-)

Se configuran los Perfiles de Análisis, para que aparezcan por defecto los servicios anteriores a la hora de registrar muestras:
- DNA Extraction: incluye el servicio DNA extraction.
- PCR: incluye el servicio PCR
- Bidirectional Sequencing: incluye los servicios de Forward - X y Reverse-X.
- Unidirectional Sequencing: incluye los servicios Reverse-X.

### Lotes analíticos
Los lotes anaíticos permiten registrar varias muestras a la vez e identificarlas como un conjunto. Configuramos las etiquetas para "Standard Sequencing".

###








