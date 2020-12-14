# Modificaciones realizadas en código

## Modificaciones realizadas en senaite.core:
Para adaptar el software a los requerimientos del flujo de trabajo de un servicio de secuenciación es necesario modificar y añadir algunos de los campos que aparecen en el registro de muestras (Analysis Request). Para ello, se modifica el add-on estándar llamado senaite.core, concretamente, el fichero "analysisrequest.py":

- Cambio en línea 340 -> "label = 'Primers'" para indicar el tipo de organismo al que pertenece la muestra, usando los registros de la tabla "AnalysisRequestSubGroup" .
- Cambio en línea 370 -> "required = 1" para hacer el campo "Template" obligatorio.
- Cambio en línea 553 -> "label = 'Primers'" para indicar el tipo de Primers a utilizar, usando los registros de la tabla "Sample Condition".
- Cambio en línea 700 -> "required = 1" para hacer el campo "Specifications" obligatorio.

## Modificaciones realizadas en senaite.impress:
Para adaptar los informes de resultados generados desde Senaite-LIMS se modifica el add-on senaite.impress, concretamente, el fichero Default.pt, el cual es la plantilla de informe.

- Cambio en "attachments per row = 1" para que salga por defecto un fichero adjunto en cada fila en vez de dos.
- Añadimos una clase de estilo CSS llamada "break" para que aparezcan los resultados en varias líneas. Esto es necesario par resultados en los que aparece la secuencia de DNA, la cual supera los 300 caracteres.
    <style type="text/css">
      .break {
        width: 30px;
        word-wrap: break-word;
        word-break:break-all;
      }
    </style>

- Aplicamos esta clase dentro del campo "Results" del informe:
    <td class="text-right break">
           <span class="result" tal:content="structure python:model.get_formatted_result(analysis)">23</span>
    </td>

- Modificamos las dimensiones de la tabla de resultados:
        <!-- Analysis in POC and Category -->
            <table class="table table-sm table-condensed">
              <colgroup>
                <!-- Category -->
                <col style="width: 20%;">
                <!-- Result -->
                <col style="width: 50%">
                <!-- Unit -->
                <col style="width: 5%">
                <!-- Range -->
                <col style="width: 10%">
                <!-- Out of Range -->
                <col style="width: 5%">
              </colgroup>

- Añadimos los campos "Organism" y "Primers" al apartado "Summary" del informe:
    <tr>      
      <td class="label" i18n:translate="">Organism</td>
          <td tal:content="model/SubGroup/title|nothing"></td>
    </tr>           
    <tr>
      <td class="label" i18n:translate="">Primers</td>
          <td tal:content="model/SampleCondition/title|nothing"></td>
    </tr>


