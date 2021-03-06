---
description: >-
  Backtracking es una estrategia algorítmica que busca todas las posibles
  soluciones dado un conjunto de variables inicial para encontrar el resultado
  definido por el problema
---

# 2.4 Backtracking

### 2.4.1 ¿Qué es Backtracking?

> Backtracking is a general algorithm for finding all \(or some\) solutions to some computational problems, notably constraint satisfaction problems, that incrementally builds candidates to the solutions, and abandons a candidate \("backtracks"\) as soon as it determines that the candidate cannot possibly be completed to a valid solution.

**Backtracking** \(o **vuelta atrás**\) es una **técnica algorítmica para encontrar soluciones a problemas que tienen una solución completa**, en los que el orden de los elementos no importa, y en los que existen una serie de variables, a cada una de las cuales, debemos asignarle un valor teniendo en cuenta unas restricciones dadas.

O lo que es lo mismo, es una **estrategia algorítmica que busca todas las posibles soluciones dado un conjunto de variables inicial** para encontrar el resultado definido por el problema.

La técnica de **Backtracking** se apoya en el uso de la [recursividad](recursividad.md) para la búsqueda exhaustiva de todas las combinaciones posibles.

El termino fue utilizado por primera vez por el matemático [D.H. Lehmer](https://es.wikipedia.org/wiki/Derrick_Henry_Lehmer) en la década de 1950.

### 2.4.2 Explicando la técnica Backtracking con un caso práctico

Dado un conjunto de números enteros {14, 10, 6} encontrar si existe algún subconjunto cuya suma sea igual a 20.

![](../.gitbook/assets/backtracking_diagram_1.png)

### 2.4.3 Entendiendo la técnica Backtracking

**Backtracking** es una técnica algorítmica para hacer una búsqueda exhaustiva y sistemática por todas las configuraciones posibles del espacio de búsqueda del problema.

Se suele aplicar en la resolución de un gran número de problemas, muy especialmente en los de **decisión** y **optimización**.

* **Problemas de decisión**: Búsqueda de las soluciones que satisfacen ciertas restricciones.
  * Ejemplo: [Problema de las N-Reinas](backtracking.md#2-4-5-caso-practico-el-problema-de-las-8-reinas).
* **Problemas de optimización**: Búsqueda de la mejor solución en base a una función objetivo.
  * Ejemplo: [Problema de la mochila](backtracking.md#2-4-7-extra).

{% hint style="danger" %}
**Los algoritmos de tipo Backtracking suelen ser muy ineficientes**. Aunque se utilizan para resolver problemas para los que no existe un algoritmo eficiente.

Para mejorar la técnica de Backtracking se recomienda el uso de la programación paralela.
{% endhint %}

De forma general, el método del Backtracking, concebido como tal, genera todas las secuencias de forma sistemática y organizada, de manera que prueba todas las posibles combinaciones de un problema hasta que encuentra la correcta.

En general, la forma de actuar consiste en elegir una alternativa del conjunto de opciones en cada etapa del proceso de resolución, y si esta elección no funciona \(no nos lleva a ninguna solución\), la búsqueda vuelve al punto donde se realizó esa elección, e intenta con otro valor. Cuando se han agotado todos los posibles valores en ese punto, la búsqueda vuelve a la anterior fase en la que se hizo otra elección entre valores. Si no hay más puntos de elección, la búsqueda finaliza.

La técnica de Backtracking es usada en muchos ámbitos de la programación, por ejemplo, para el cálculo de expresiones regulares o para tareas de reconocimiento de texto y de sintaxis de lenguajes regulares. También es usado incluso en la implementación de algunos lenguajes de programación y da soporte a muchos algoritmos en inteligencia artificial.

De forma matemática:

* El conjunto de soluciones se expresa en tuplas, donde cada una es el valor de la solución.

$$
s = (v_1, v_2, ... v_n)
$$

* El conjunto parcial de soluciones será aquel en que se encuentre en cierto nivel K:

$$
s_p = (v_1, v_2, ... v_k) → K <= n
$$

* Si se puede añadir un elemento más, la solución avanza a otro nivel \(K+1\).
* Si no existe ningún valor, se retrocede al valor \(K-1\).
* Se continua hasta que una solución parcial sea una solución al problema o hasta que no queden mas posibilidades a probar.

El resultado es equivalente a hacer **una búsqueda en profundidad** en el árbol de soluciones. Sin embargo, este árbol es implícito, no se almacena en ningún lugar.

Los hijos de un nodo del nivel K son las prolongaciones posibles al añadir una nueva etapa.

Para examinar el conjunto de posibles soluciones es suficiente con recorrer el árbol construyendo soluciones parciales a medida que se avanza en el recorrido.

**Los números de cada nodo marcan el recorrido del árbol.**

Los **nodos hoja** representan que puede no haber una solución por ese camino y hay que volver atrás, o bien que es una solución.

### 2.4.4 Eficiencia

La **eficiencia** consiste en la medida del coste en el uso de recursos que necesita el algoritmo para llevar a cabo su tarea.

Los recursos más importantes son:

* Tiempo de ejecución
* Espacio de almacenamiento

En conclusión, podemos decir que debido al coste creado en tiempo y memoria \(por la pila recursiva\) los algoritmos de vuelta atrás no son todo lo eficientes que deberían, y debemos dejarlos para resolver parte de otros problemas o problemas reducidos. Aún así, la gran ventaja que tienen es que si hay solución la encontrarán.

**Ventajas:**

* Si existe una solución, la calcula.
* Es un esquema sencillo de implementar.
* Adaptable a las características especificas de cada problema.

**Desventajas:**

* Coste exponencial en la mayoría de los casos.
* Si el espacio de búsqueda es infinito, la solución, aunque exista, no se encontrará nunca.
* Por termino medio consume mucha memoria al tener que almacenar las llamadas recursivas.

**La aplicación del Backtracking antes de programar consiste en:**

* Qué tipo de árbol es adecuado para el problema
  * ¿Cómo es la representación de la solución \(tupla\)?
* Cómo generar un recorrido según el árbol
  * Generar un nuevo nivel.
  * Generar los niveles hermanos.
  * Retroceder en el árbol.
* Determinar cómo es la forma del árbol de Backtracking, o lo que es lo mismo, cómo es la representación de la solución.
* Elegir el esquema de algoritmo adecuado, adaptándolo en caso necesario.
* Implementar las funciones genéricas para la aplicación concreta: según la forma del árbol y las características del problema.
* Posibles mejoras usando variables locales con valores acumulados, realizar podas del árbol, etc.

La medida se denomina **complejidad** del algoritmo y pueden ser agrupadas por soluciones:

* **Dependencia del procesador:** Aunque fijemos el tamaño y los valores concretos del vector y el valor buscado, el algoritmo tardará tiempos distintos en ordenadores diferentes.
* **Dependencia con el tamaño de la entrada:** No se tarda igual buscar en un vector de 10 elementos, que buscar en uno de 1.000.000.
* **Dependencia de valores de la entrada:** Aunque fijemos el tamaño del vector, no se tarda lo mismo en buscar un valor que está en la primera posición que otro que no esté en el vector.

#### 2.4.4.1 Dependencia del procesador

* No medir tiempo en segundos, sino en número de operaciones elementales ejecutadas.

**Operación elemental:** Toda operación que tarda un tiempo constante en cualquier procesador razonable.

Tipicamente se consideran elementales las asignaciones, operaciones aritméticas y relacionales con tipos de datos de tamaño fijo, acceso a arrays.

En general se cuenta solo con un tipo de operación concreta, la más relevante para la eficiencia del algoritmo.

Es una medida independiente del procesador.

#### 2.4.4.2 Dependencia con el tamaño de la entrada

* Uno o más valores relacionados con los datos de entrada que sirven de parámetros para expresar las funciones que miden el uso de recursos del algoritmo.
* En el caso de algoritmos que trabajan sobre colecciones de datos, suele ser el número de datos que contienen.
* Para algoritmos de cálculo con enteros de tamaño arbitrario, se suele usar el número de bits de esos enteros. Se tratan cómo un array de bits.
* Expresar la complejidad no mediante un valor sino por una función cuyo parámetro\(s\) es el tamaño de la entrada.
* El tamaño de la entrada, si es un único valor, se suele denominar n.
* La complejidad temporal se denominará mediante la función T\(n\).
* La complejidad espacial se denominará mediante la función E\(n\).
* De esa función nos interesa, más que su forma concreta, su ritmo de crecimiento.

#### 2.4.4.3 Dependencia de valores de la entrada.

* Dividir el análisis en casos.
* Analizar subconjuntos de las entradas cuya complejidad es la misma para todas las entradas de ese subconjunto \(análisis de peor y mejor caso\).
* Calcular un promedio, dado una distribución estadística de las entradas. Tipicamente se supone que todas las posibles entradas son equiparables \(Análisis de caso promedio y tiempo amortizado\).

**Cota superior \(Análisis del peor caso\)**

* Calcula la complejidad del algoritmo para las entradas \(del mismo tamaño\) que maximizan la complejidad.

$$
Tworst (n) = max[T(n, input)]
$$

**Cota inferior \(Análisis en el mejor caso\)**

* Calcula la complejidad del algoritmo para las entradas \(del mismo tamaño\) que minimizan la complejidad.

$$
Tbest (n) = min[T(n, input)]
$$

### 2.4.5 Búsqueda secuencial

* **Operación elemental:** Elegimos contar comparaciones en las que intervenga un elemento del vector.
* **Tamaño de la entrada:** Elegimos tomar como tamaño de entrada el número de elementos del vector.
* **Cota superior \(Análisis del peor caso\):** Para vectores de tamaño n, las entradas que hacen que el algoritmo trabaje más son aquellas en que el valor buscado no se encuentra en el vector.

$$
T_w = n
$$

* **Cota inferior \(Análisis del mejor caso\):** Las entradas que hacen que el algoritmo trabaje menos son aquellas en que el valor buscado está en la primera posición del vector.

$$
T_b = 1
$$

### 2.4.6 Árboles de búsqueda

Cómo ya hemos comentado anteriormente el algoritmo de vuelta atrás proporciona una manera sistemática de generar todas las posibles soluciones siempre que se puedan resolver por etapas, lo que se asemeja mucho a una búsqueda combinatoria \(probar todas la posibles combinaciones\).

Para conseguir este estudio tan exhaustivo del problema, se considera que se trabaja con un árbol \(figura 1\) que cuya existencia es sólo implícita, para nosotros cada nodo del nivel k representa una parte de la solución y nuestro árbol estará formado por las K etapas que se considerarán ya realizadas.

![Figura 1: &#xC1;rbol de b&#xFA;squeda](../.gitbook/assets/backtracking_diagram_2.png)

La búsqueda realizada sobre el árbol es una búsqueda en profundidad. En el transcurso de la búsqueda si se encuentra un estado incorrecto, se ha de retroceder hasta la decisión anterior y si existe uno o más caminos aún no explorados que puedan conducir a la solución, el recorrido del árbol continúa por uno de ellos \(hijos si nos referimos a un árbol\). Si no quedasen más alternativas la búsqueda fallaría y el problema no tendría solución. En este caso en el que consideramos el problema en forma de árbol, la solución sería un camino que llevara desde el nodo raíz hasta uno nodo hoja, y las soluciones parciales llevarían desde el nodo raíz a los nodos interiores del árbol.

### 2.4.7 Notación asintótica

* Dada una función **f\(n\)** la notación **O\(f\(n\)\)** representa al conjunto de funciones con la siguiente propiedad:

![](../.gitbook/assets/image.png)

_Cuando **g\(n\)** pertenece a las cotas superiores de **f\(n\)**, si y solo si, existe un **n\(sub-cero\)** que pertenece al conjunto de número naturales positivos y existe un **c** que pertenece al conjunto de reales positivos, tal que, para todo **n**, ese **n** tiene que ser mayor a ese **n\(sub-cero\)**, que cumpla que **g\(n\)** sea menor o igual que **c** por **f\(n\)**._

* El conjunto **O\(f\(n\)\)** se denomina conjunto de cotas superiores generado por **f\(n\)**.
* Toda función que pertenece a **O\(f\(n\)\)** se dice que está acotada superiormente por **f\(n\)**.
* El conjunto **O\(f\(n\)\)** representa a las funciones que:
  * Tienen un ritmo de crecimiento igual o menor que **f\(n\)**.
  * No importa las constantes de proporcionalidad \(positivas\) por las que esté multiplicaba la función \(podemos ajustar el valor de **c** en la definición\).
  * Solo importa el comportamiento para valores de **n** grandes, con tendencia a infinito.

![](../.gitbook/assets/image%20%281%29.png)

### 2.4.8 Branch & Bound

**Branch & Bound \(Ramificación y poda\)** consiste en una variante del esquema de Backtracking.

Se define como un método capaz de **buscar más rápido** las **soluciones de un problema**, aplicando **estrategias de exclusión \(poda\)** en los nodos que no conducen a una solución optima, **en base a un coste asociado al nodo**.

Basado en un recorrido del **árbol de expansión \(en profundidad\)**, se aplica sobre todo a problemas de optimización.

Las estrategias para encontrar la soluciones más optimas se denomina **poda \(pruning\)**. Una poda consta de cotas que permiten excluir de la búsqueda ramas que no conducen a una solución \(se evita ramificar nodos\).

Para determinar que nodo va a ser ramificado, dependiendo de la estrategia, necesitamos una estructura capaz de almacenar aquellos nodos pendientes de ser analizados **\(Lista de Nodos Vivos, LNV\)**.

Un nodo vivo en el árbol es el que tiene posibilidades de ser ramificado, es decir, el que ha sido creado y no ha sido explorado, ni podado todavía. La LNV contiene nodos pendientes de tratar por el algoritmo.

#### 2.4.8.1 Estrategias de ramificación

En un algoritmo de ramificación y poda se realizan tres etapas:

1. **Etapa de selección:** Se encarga de extraer un nodo de la LNV. La forma de escogerlo depende de la estrategia de ramificación.
2. **Etapa de ramificación:** Se generan los posibles hijos del nodo seleccionado en la etapa anterior.
3. **Etapa de poda:** Se estudian los nodos generados en la etapa de ramificación. Solo aquellos que pasan cierto filtro se introducen en la LNV. El resto de nodos son podados.

El recorrido del árbol depende de cómo se gestiona la LNV. Existen tres tipos:

* **Recorrido en profundidad - LIFO \(Last in, first out\):** La lista se trata como una pila.

![](../.gitbook/assets/backtracking_diagram_lifo.png)

* **Recorrido en anchura - FIFO \(First in, first out\):** La lista se trata como una cola.

![](../.gitbook/assets/backtracking_diagram_fifo.png)

* **Estrategia de mínimo coste \(nodo más prometedor\):** Se utiliza una cola con prioridades para almacenar nodos ordenados por su coste.

Entre todos los nodos de la lista de nodos vivos, elegir el que tenga mayor beneficio \(o menor coste\) para explorar a continuación.

En caso de empate \(de beneficio o coste estimado\) deshacerlo usando un criterio FIFO o LIFO.

* **Estrategia coste FIFO:** Seleccionar de la LNV el que tenga mayor beneficio y en caso de empate escoger el primero que se introdujo.
* **Estrategia coste LIFO:** Seleccionar de la LNV el que tenga mayor beneficio y en caso de empate escoger el último que se introdujo.

{% hint style="info" %}
El objetivo es utilizar la estrategia que permita encontrar la solución más rápido.
{% endhint %}

#### 2.4.8.2 Estrategias de poda

Para cada nodo establecemos una estimación de la mejor solución posible a partir de él \(cota\).

Las cotas determinan cuando se puede realizar una poda del árbol, si el valor de la cota es peor que la mejor solución obtenida hasta ese momento, no se exploran sus hijos.

Para cada nodo "i" podemos tener:

* Cota inferior\(i\) de la mejor solución alcanzable a partir del nodo "i".
* Cota superior\(i\) de la mejor solución alcanzable a partir del nodo "i".
* Estimación del beneficio \(o coste\) que se puede encontrar a partir de ese nodo. Se puede obtener a partir de las cotas, usar la media o una de ellas.

Si M\(i\) es la mejor solución alcanzable a partir del nodo "i", se debe verificar lo siguiente:

$$
CotaInferior(i) <= M(i) <= CotaSuperior(i)
$$

#### 2.4.8.3 Tiempo de ejecución

El tiempo de ejecución de un algoritmo de B&B depende de:

* **El número de nodos recorridos**, dependencia de la efectividad de la poda.
* **El tiempo empleado en cada nodo**, tiempo necesario para hacer las estimaciones e coste y gestionar la lista de nodos vivos en función de la estrategia de ramificación.

En el **peor caso**, el tiempo de un algoritmo B&B será igual al de un algoritmo de Backtracking \(o peor incluso, si tenemos en cuenta el tiempo que requiere la LNV\).

En el **caso promedio**, se suelen obtener mejoras con respecto a Backtracking.

La "clave" consiste en buscar un equilibrio en la precisión con respecto a Backtracking.

* **Muy precisas:** Mayor poda, se recorren menos nodos, pero aumenta el tiempo en realizar estimaciones.
* **Poco precisas:** Menor poda, se recorren más nodos, pero disminuye el tiempo de las estimaciones.

### 2.4.9 Backtracking vs. Branch & Bound

En **Backtracking**, tan pronto como se genera un nuevo hijo del nodo en curso, dicho hijo pasa a ser el nodo en curso.

En **B&B**, se generan todos los hijos del nodo en curso antes de que cualquier otro nodo vivo pase a ser el nuevo nodo en curso \(no se realiza un recorrido en profundidad por defecto\).

En consecuencia:

* En Backtracking, los únicos nodos vivos son los que está en el camino de la raíz al nodo en curso.
* En B&B puede haber más nodos vivos que en Backtracking, que se almacenan en una lista de nodos vivos.

En Backtracking, el test de comprobación realizado por la funciones de evaluación nos indica únicamente si un nodo concreto nos puede llevar a una solución o no.

En B&B, sin embargo, se acota el valor de la solución a la que nos puede conducir un nodo concreto, de forma que esta acotación nos permite:

* Podar el árbol \(si sabemos que no nos va a llevar a una solución mejor de la que ya tenemos\).
* Establecer el orden de ramificación \(de modo que comenzaremos explorando las ramas mas prometedores del árbol\).

### 2.4.10 Caso práctico Backtracking: El problema de las 8-Reinas

El problema de las **n-Reinas \(N-Queens\)** es un juego cuyo objetivo consiste en colocar **n-reinas en una tablero de ajedrez \(n\*n\) sin que se amenacen entre ellas según las normas del ajedrez** \(que no estén en la misma fila, columna o diagonal\).

**Restricciones explicitas:**

$$
s_i = [1, 2, 3, 4, 5, 6, 7, 8] → 1 <= i <= 8
$$

$$
|s_i|^8 = 8^8 = 16.777.216
$$

**Restricciones implícitas:**

Podemos deducir que cada reina se ha de colocar en una columna, partiendo del caso inicial que la reina "i" se colocara en la fila "i".

* Las restricciones para este problema consiste en que dos reinas no pueden colocarse en la misma fila.

$$
(y_i, y_j) → y_i <> y_j
$$

* Todas las reinas deben estar en columnas diferentes:

$$
(x_i, x_j) → x_i <> x_j
$$

* Todas las reinas deben estar en diagonales diferentes:

$$
(x_i, x_j) → |j-i| <> |x_j-x_i|
$$

Gracias a la primera restricción implícita podemos decir que todas las soluciones son permutaciones de {1, 2, 3, 4, 5, 6, 7, 8}, lo que reduce el espacio de soluciones a 8! = 40320.

**1º Paso: Representación de la solución**

Utilizaremos un vector de n elementos, donde el valor del indice sera la columna y el valor la posición de la fila. El valor -1 significará celda no ocupada.

![](../.gitbook/assets/backtracking_diagram_n_queens.png)

**2º Paso: Representación del árbol**

![](../.gitbook/assets/backtracking_diagram_n_queens_b.png)

**3º Paso: Codificación**

Ejemplo en pseudocódigo:

```c
const n = 8;

function validation(solution=array[n] of int, k: int): boolean
{
    for i=0 to k-1 DO
        // absoluteValue = |x-y|
        if (solution[i] === solution[k] or absoluteValue(solution[i], solution[k]) === absoluteValue(i, k)) then
            return false;
        end
    end
    
    return true;
}

function nQueens(solution=array[n] of int, stage: int): boolean
{
    if stage > n then return false;
    
    success = false;
    solution[stage] = 0;
    
    repeat
        solution[stage] = solution[stage] + 1;
        
        if validation(solution, stage) then
            if stage <> n THEN
                success = queens(solution, stage + 1);
            else
                success = true;
            end
        end
    until (solution[stage] === n) OR success === true;
    
    return success;
}
```

Ejemplo en JavaScript:

[http://jsfiddle.net/rocketegg0/wu6cpp5v/](http://jsfiddle.net/rocketegg0/wu6cpp5v/)

### 2.4.11 Caso práctico B&B

{% file src="../.gitbook/assets/backtracking\_branch\_bound.pdf" caption="backtracking\_branch\_bound" %}

### 2.4.12 Otros casos prácticos

Otros problemas que se pueden resolver con Backtracking:

1. [Problema de la mochila](https://es.wikipedia.org/wiki/Problema_de_la_mochila).
2. Problema del laberinto.
3. [Problema del salto de caballo](https://es.wikipedia.org/wiki/Problema_del_caballo).
4. [Problema de los cuadrados mágicos](https://es.wikipedia.org/wiki/Cuadrado_m%C3%A1gico).
5. Sudoku

### 2.4.13 Extra

{% embed url="https://www.youtube.com/watch?v=XQYGwKiqV3Y" %}

{% embed url="https://www.youtube.com/watch?v=vdVpRjO7g84" %}

{% embed url="https://www.youtube.com/watch?v=ifXvZ8qfIiU" %}

### 2.4.14 Bibliografía

Referencias en español:

1. Curso Técnico Superior Universitario: Programación avanzada. [Ilerna Online](https://www.ilerna.es/es/fp-universidad/programacion-avanzada-tecnico-superior-universitario-484).
2. Grado en Ingeniería Informática. Temario: Backtraking y Hashing. [UCAM Murcia](https://online.ucam.edu/estudios/grados/informatica-a-distancia).
3. [https://es.wikipedia.org/wiki/Vuelta\_atr%C3%A1s](https://es.wikipedia.org/wiki/Vuelta_atr%C3%A1s)
4. [El esquema algorítmico del Backtracking](https://openlibra.com/es/book/el-esquema-algoritmico-del-backtraking)

Referencias en inglés:

1. [https://en.wikipedia.org/wiki/Backtracking](https://en.wikipedia.org/wiki/Backtracking)

