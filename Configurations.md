## Configuraciones realizadas
Se ha configurado un ejemplo sencillo de un servicio de secuenciación. Este servicio ofrecerá secuenciación estándar de tipo Sanger y, dependiendo del tipo de muestra, habrá que realizar una extracción previa de material genético y/o una PCR previas a la secuenciación.

### Usuarios y permisos
Para acceder al sistema se han configurado tres usuarios, además del rol de admin:

- Laboratory Manager: tiene toda clase de permisos e modificación de análisis, instrumentos y aprobación de resultados y muestras (user: labman / pass: labman).
- Laboratory Clerk: tiene permisos de registro de muestras y validación de resultados (user: labclerk / pass: labclerk).
- Laboratory Analyst: tiene permisos solo de registro de muestras e introducción de resultados (user: labanalyst / pass: labanalyst).

Todos ellos pertenecen al mismo laboratorio: Sequencing Service.

### Clientes
Con el objetivo de identificar las muestras y los análisis realizados en cada una de ellas, se dan de alta clientes "ficticios": North Hospital y Public Health Institute.

### Análisis.
Los análisis se deben configurar a través de las siguientes tablas:
- Analysis Categories.
- Analysis Services.

Se dan de alta las siguientes categorías de análisis:
- Pre-Sequencing
- Standard Sequencing

Dentro de "Pre-sequencing" se configuran los siguientes servicios de análisis:
- DNA extraction (A260/A280) (nm ratio)
- PCR (pb)

Dentro de "Standard Sequencing" se configuran los siguientes análisis:
- Forward - GC content (%)
- Forward - Length (pb)
- Forward - Chromatogram (-)
- Forward - Sequence (-)
- Reverse - GC content (%)
- Reverse - Length (pb)
- Reverse - Chromatogram (-)
- Reverse - Sequence (-)

Se configuran las plantillas de Análisis, para que aparezcan por defecto los servicios anteriores a la hora de registrar muestras de cada tipo:
- Tissue-Sequencing: incluye los servicios pertenecientes a Pre-Sequencing y a "Standard Sequencing".
- DNA-Sequencing: incluye los servicios "DNA extraction" y los pertenecientes a "Standard Sequencing".
- PCR Product-Sequencing: incluye los servicios pertenecientes a "Standard Sequencing".

### Muestras.

Las muestras son los objetos básicos para LIMS, mediante los cuales vamos a poder obtener información de los resultados. En Senaite, se llaman Analysis Request (petición de análisis). Para configurar las muestras primero hay que configurar las siguientes tablas:
- Sample Type.
- Sample/Analysis Template.

Además, también utilizamos la información aportada por los clientes, los usuarios y los análisis, aparte de las siguientes tablas para añadir mayor información a la muestra:
- Container. 
- Sub-Group -> le cambiamos el nombre a "Organism".
- Sample Condition -> le cambiamos el nombre a "Primers".

Para el registro de muestras, se configuran los campos de la plantilla de registro, dejando solo los necesarios. Añadimos también dos campos llamados "Organism" y "Primers".

También se crean los siguientes Tipos de Muestreo: PCR Product, Tissue, DNA. Además, modificamos el identificador de muestra (ID) para que aparezcan la fecha de registro de la muestra y el cliente.

### Especificaciones de análisis
Para configurar las especificaciones de análisis tenemos que tener previamente configurados los análisis y las muestras.

### Instrumentos

Para dar de alta instrumentos tenemos que configurar las siguientes tablas:
- Instrument Types
- Manufacturers
- Methods
- Instruments

Se configuran los siguientes tipos de instrumentos (Instrument Types):
- Thermo Cycler.
- Sequencing Instruments.
- DNA Extraction.

Configuramos los siguientes fabricantes (Manufacturers):
- Agilent Technologies.
- Thermo Fischer Scientific.
- Fluidigm.

Configuramos los siguientes métodos:
- Spectrophotometry.
- Standard PCR.
- Standard Sanger Sequencing.

Configuramos los siguientes instrumentos:
- 2100 Bioanalyzer -> para DNA Extraction.
- 3500 Genetic Analyzer -> para Standard Sequencing.
- Biomark HD System -> para PCR.


### Configuraciones generales (SetUp)

Senaite permite una serie de configuraciones generales. En nuestro caso, modificamos las siguientes:
- Security -> Allow access to worksheets only to assigned anaysts = False
            -> Only lab managers can create and manage worksheets = False
- Accounting -> Include and display pricing information = False
- Samples -> Auto-receive samples = True
- Analysis -> Categorise analysis services = True
            -> Default count of Sample to add = 1
- Id Server -> Modificamos el campo Sample ID = {clientId}-{sampleType}-{yymmdd}


### Informes.
Para configurar los informes primero tenemos que entrar en el menú de confguración del add-on senaite.impress. En él encontraremos varios campos, de los cuales parametrizamos los siguientes:
- "Default template: Default.pt" -> para que salga por defecto la plantilla "Default".
- "Default Paper Format: Landscape" -> para que salga por defecto el informe de manera apaisada.
- "Default orientation: A4 210.0x297.0 mm" -> dimensiones A4 por defecto.
- Store Multi-Report PDFs Individually: True" -> para que, al imprimir informes de varias muestras éstos se alamcenen de manera independiente.

Además de esta paremetrización, se realizan los cambios en la plantilla Default.pt, dentro de senaite.impress, tal como se detalla en el documento "Modifications.md".








