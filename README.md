# Tool wear prediction (Detección de desgaste de herramientas)

## Contexto
Haciendo uso de una fresadora CNC, se han realizado una serie de experimentos de mecanizado en bloques de cera de 2" x 2" x 1.5". Se han recopilado datos de la maquina tales como, la velocidad de avance, presión de sujeción, etc. Cada experimento ha moldeado la pieza de cera hasta obtener una forma de "S". (*test_artifact.jpg*)

## Contenido
Contamos con 18 experimentos, que incluyen, el número de experimento, el material (cera), la velocidad de avance y la presión de sujeción. Las salidas por cada experimento incluyen la condición de la herramienta (si la herramienta esta desgastada o no) y si la herramienta pasó la inspección visual. (*train.csv*)

Los 18 experimentos, se han recopilado con una tasa de muestreo de 100 ms (se muestran por separado en los archivos *experiment_01.csv - experiment_18.csv)*. Cada archivo tiene mediciones de los 4 motores en la fresadora CNC (ejes X, Y, Z y husillo). Estas mediciones de la CNC se pueden utilizar de dos maneras:

1. Tomando cada medición de la CNC como una observación independiente, donde se indica la operación que se está realizando en la columna **Machining_Process**. Las operaciones de mecanizado activas se etiquetan como **"Layer 1 Up", "Layer 1 Down", "Layer2 Up", "Layer 2 Down", "Layer 3 Up" y "Layer 3 Down"**.

2. Tomando cada uno de los 18 experimentos (la serie temporal completa) como una observación para la clasificación de series temporales.

Hay que tener en cuenta que algunas variables no reflejarán con precisión el funcionamiento de la fresadora CNC. Esto generalmente se puede detectar cuando **M1_CURRENT_FEEDRATE lee 50**, cuando **X1 ActualPosition lee 198**, o cuando **M1_CURRENT_PROGRAM_NUMBER no lee 0**. La fuente de estos errores no ha sido identificada.

## Motivación
Se puede realizar una clasificación binaria supervisada para la identificación de herramientas de corte desgastadas y no desgastadas. Se han realizado 8 experimentos con una herramienta no desgastada y 10 experimentos con una herramienta desgastada (*tool_condition*).
