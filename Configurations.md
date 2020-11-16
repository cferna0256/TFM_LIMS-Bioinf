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

### Configuraciones generales (SetUp)

Senaite permite una serie de configuraciones generales. En nuestro caso, modificamos las siguientes:
- Accounting -> Include and display pricing information = False
- Samples -> Auto-receive samples = True
- Analysis -> Categorise analysis services = True
            -> Default count of Sample to add = 1
- Id Server -> Modificamos el campo Sample ID = {clientId}-{sampleType}-{yymmdd}








