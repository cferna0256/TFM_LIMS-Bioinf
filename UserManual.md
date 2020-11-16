# Manual de usuario
Una vez que se arranca la instancia de Senaite (ver apartado de Instalación en README.md) entrar al sistema con usuario "labclerk" o "labman":

Una vez dentro, nos aparecerá el menú principal de Senaite-LIMS. En él podemos ver un menú a la izquierda con varias opciones:



Clicamos sobre "Batches". Se nos abrirán los batches (lotes analíticos) pendientes o en proceso. En Senaite, lo mejor es crear un batch para gestionar varias muestras.

Clicamos en "Add" para crear un Batch. Podemos llamar al Batch como queramos para tenerlo identificado, aunque no es obligatorio. Podemos también rellenar el campo "Client"
para saber a qué cliente pertenece el lote (recomendable).

Una vez creado el Batch se le asigna un identificador único. Dentro del Batch clicamos en la pestaña "Samples" para crear muestras dentro del mismo lote. Por defecto nos genera
una única muestra, pero podemos cambiar el número al que queramos.

Tras darle al botón "Add" se nos abre una pantalla de registro de muestras "Request new analysis" donde el apartado Client ya está relleno (recoge esta información del propio batch).

Tenemos que rellenar los campos obligatorios y también el campo "Sample Template", el cual nos va a añadir los análisis por defecto (recomendable). Si clicamos en este campo 
podemos ver las plantillas de muestreo disponibles. Creamos muestras con una de ellas y vemos que se nos rellena el campo "Sample Type" automáticamente. Así mismo, si clicamos en 
el campo "Lab Analysis" vemos que nos ha marcado los servicios de análisis por defecto.

Para copiar los campos en todas las muestras, podemos clicar en la flecha que aparece a la derecha de cada campo.

Una vez rellenos los campos clicamos en el botón "Save". Se nos generarán las muestras con un identificador único que muestra el código del cliente, el tipo de muestra y  la fecha
de muestreo. Así mismo, las muestras vienen ya en estado "Recibido" de manera automática.

Desde el rol de "labman" y tras haber registrado y recibido las muestras, clicamos en la parte izquierda en "Worksheets". Clicamos en "Add", seleccionando "labanalyst" como analista
y "Standard Sequencing" como plantilla. Se nos genera un Worksheet con un identificador único. Nos aparecen todos los análisis de las muestras creadas anteriormente. Los seleccionamos
y abajo del todo clicamos en el botón "Assign" para asignarlas al analista. Tras asignar los análisis, clicamos en la pestaña "Add Blank Reference" para añadir muestras de control 
para los análisis registrados. Tras ello, cerramos sesión.

Entramos al sistema con usuario "labanalyst" que es el que va a introducir los resultados. Desde el mismo Worksheet anterior podemos visualizar los análisis que deben realizarse para
cada muestra. Introducimos valores que queramos (es una prueba). Una vez introducidos los valores, clicamos en "Submit".

Una vez introducidos los resultados, salimos y entramos como "labclerk" o "labman". Podemos ver las muestras anteriores desde la pestaña Batch, clicando en nuestro lote. Una vez allí,
clicamos en las muestras y en la pestaña "View" vamos a "Lab Analysis". Seleccionamos los análisis y clicamos en "Verify" De esta forma, habremos verificado los resultados de 
los análisis.
