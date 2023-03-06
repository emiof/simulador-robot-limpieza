## Introducción
En este proyecto se simula la operación de múltiples robots autónomos de limpieza (‘Roombas’), utilizando el framework de Mesa en Python. La simulación ocurre dentro de un espacio bidimensional, en el que existe una cantidad predefinida de suciedades a limpiar. 

## Agentes
- **Robot de limpieza**: ‘Roomba’, opera de forma autónoma y se mueve semi-aleatoriamente por el espacio. Cuando encuentra una suciedad, la elimina. Posee un número limitado de movimientos que puede realizar dentro del espacio, antes de volverse permanentemente inmóvil (pérdida total de batería). En la búsqueda de suciedades, el robot analiza las celdas que yacen en su vecindad; la cantidad de celdas que puede analizar es variable. 
- **Suciedad**: es un agente ‘pasivo’ y estático. Representa una suciedad sobre el suelo que debe ser limpiada por los robots de limpieza. 

## Interacción entre agentes
Entre agentes solamente se comunica información posicional, y el tipo de agente que son. Cuando un robot de limpieza encuentra un agente en su vecindad, determina si es otro robot o una suciedad, y su posición, y realiza su siguiente movimiento en el espacio según dicha determinación. Los robots de limpieza pueden modificar el entorno al eliminar del espacio agentes de suciedad. Los agentes de suciedad no interactúan activamente con otros agentes. 

## Entorno 
El espacio es una matriz bidimensional que representa la superficie a limpiar. Cada celda en el espacio puede contener solamente un agente. 

## Parámetros 
En la simulación, el comportamiento de los robots de limpieza y las características del entorno son personalizables. Es posible modificar las dimensiones del espacio, el número inicial de suciedades y robots, y el radio del ‘sensor’ de los robots, el cual determina la cantidad de celdas en su vecindad que puede analizar antes de dar un paso. 

## Descripción del proceso 
De forma general, la simulación sigue los siguientes pasos durante su ejecución: 
1. El modelo (clase Floor), elemento central de la simulación, es instanciado. En dicha instanciación, crea el espacio de la simulación, e instancia y posiciona en él a los agentes (las suciedades son posicionadas aleatoriamente, y los robots en el primer renglón, aleatoriamente). El modelo reúne y coordina todos los elementos de la simulación. 
2. Tras la creación del entorno y sus agentes, cada robot (clase Cleaner), por cada iteración de la simulación, realiza lo siguiente: 
2.1. Si aún le es posible hacer movimientos, analiza n cantidad de celdas en su vecindad (n determinado por el radio de su ‘sensor’). 
2.2 Si encuentra una o más suciedades (clase Dirt), selecciona la más cercana a su actual posición, y define el próximo movimiento que mejor lo acercaría a dicha suciedad. 
2.3 Si no encuentra una suciedad, define aleatoriamente su próximo movimiento. 
2.4 Si en su posición siguiente existe una suciedad, el robot, mediante Floor, la elimina. 
3. El paso número 2 se repite hasta que el entorno esté libre de suciedades, se haya realizado el número máximo de iteraciones, o si la duración temporal de la simulación es igual o mayor al tiempo límite previamente definido. 

## Resultados
Comprendimos que los robots de limpieza son altamente ineficientes cuando se mueven de forma puramente aleatoria y el radio de su ‘sensor’ se limita únicamente a las celdas adyacentes; con estas características, un número relativamente alto de robots en el espacio podría no ser suficiente para lograr una limpieza total, antes de la finalización de la simulación. Esta ineficiencia es derrotada por un incremento en el radio del ‘sensor’ de los robots, el cual les permite realizar movimientos mejor orientados, y evitar la total impredictibilidad del movimiento aleatorio. 

https://github.com/emiof/simulador-robot-limpieza 
