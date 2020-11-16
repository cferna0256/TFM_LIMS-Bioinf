# Manual de usuario
## Workflow estándar

### Creación de lote analítico (batch)
Una vez que se arranca la instancia de Senaite (ver apartado de Instalación en README.md) entrar al sistema con usuario "labclerk" o "labman". Una vez dentro, nos aparecerá el menú principal de Senaite-LIMS. En él podemos ver un menú a la izquierda con varias opciones. Clicamos sobre "Batches" y se nos abrirán los lotes analíticos pendientes o en proceso. Clicamos en "Add" para crear un nuevo lote. Podemos llamar al Batch como queramos para tenerlo identificado, aunque no es obligatorio. Podemos también rellenar el campo "Client" para saber a qué cliente pertenece el lote (recomendable). Una vez creado el lote se le asigna un identificador único.

### Creación de muestras asociadas al lote
Dentro del lote creado clicamos en la pestaña "Samples" para crear muestras dentro del mismo. Por defecto nos genera una única muestra, pero podemos cambiar el número al que queramos. Tras darle al botón "Add" se nos abre una pantalla de registro de muestras "Request new analysis" donde el apartado "Client" ya está relleno (recoge esta información del propio lote). Tenemos que rellenar los campos obligatorios y también el campo "Sample Template", el cual nos va a añadir los análisis por defecto (recomendable). Si clicamos en este campo podemos ver las plantillas de muestreo disponibles. Creamos muestras con una de ellas y vemos que se nos rellena el campo "Sample Type" automáticamente. Así mismo, si clicamos en el campo "Lab Analysis" vemos que nos ha marcado los servicios de análisis por defecto.

NOTA: Para copiar los campos en todas las muestras, podemos clicar en la flecha que aparece a la derecha de cada campo.

Una vez rellenos los campos clicamos en el botón "Save" y se nos generarán las muestras con un identificador único que muestra el código del cliente, el tipo de muestra y la fecha y hora de muestreo. Así mismo, las muestras vienen ya en estado "Recibido" de manera automática.

### Crear una hoja de trabajo (worksheet)
Desde el rol de "labman" y tras haber registrado y recibido las muestras, clicamos en la parte izquierda en "Worksheets". Clicamos en "Add", seleccionando "labanalyst" como analista y "Standard Sequencing" como plantilla. Se nos genera un Worksheet con un identificador único. Nos aparecen todos los análisis de las muestras creadas anteriormente. Los seleccionamos y abajo del todo clicamos en el botón "Assign" para asignarlos al analista. Tras asignar los análisis, clicamos en la pestaña "Add Blank Reference" para añadir muestras de control para los análisis registrados. Tras ello, cerramos sesión.

### Introducción de resultados en las muestras
Entramos al sistema con usuario "labanalyst" que es el que va a introducir los resultados. Desde el mismo Worksheet anterior podemos visualizar los análisis que deben realizarse para cada muestra, incluyendo la muestra blanco (QC). Introducimos valores que queramos (es una prueba). Una vez introducidos los valores, clicamos en "Save" y en "Submit" para aprobar los análisis (la muestra se queda en estado pendiente de verificación). También tenemos la opción "Reject", que cancela los análisis para esa muestra.

NOTA: al hacer "Submit" el analista ya no podrá modificar los resultados.

### Verificación e los resultados
Una vez introducidos los resultados, salimos y entramos como "labclerk" o "labman". Podemos ver las muestras anteriores desde la pestaña Batch, clicando en nuestro lote y en la pestaña "To be verified" (muestras pendientes de verificación). Una vez allí, clicamos en las muestras y, en la pestaña "View", vamos a "Lab Analysis". Seleccionamos los análisis y clicamos en "Verify" De esta forma, habremos verificado los resultados de los análisis. También encontramos la opción "Retract", que rechaza los resultados para que el analista realice modificaciones y la opción "Reject", que cancela los análisis.

### Publicación de resultados
Una vez verificados los resultados, el último paso que nos queda es publicar los resultados. Para ello, dentro del batch anterior vamos a la pestaña "Verified" (muestras verificadas), seleccionamos la muestra y clicamos en "Publish". Se nos abrirá una ventana nueva con un informe con los datos de la muestra, el cual habrá que guardar (botón "Save"). También nos aparece la opción "Invalidate", que hará que las muestras vayan para atrás en el flujo descrito (volverán a estado "Pendiente de verificación").
Una vez publicados los resultados, la muestra presentará un porcentaje del 100%.

### Cierre de lotes
Cuando todas las muestras del batch hayan sido validadas se debe cerrar el lote. Para ello, abrimos el lote creado desde el usuario "labman", lo seleccionamos y clicamos en "Close".

