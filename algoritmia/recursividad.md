---
description: >-
  Se llama recursividad (o recursión) a un proceso mediante el que una función
  se llama a sí misma de forma repetida, hasta que se satisface alguna
  determinada condición
---

# 2.3 Recursividad

### 2.3.1 ¿Qué es la Recursividad?

> In computer science, recursion is a method of solving a problem where the solution depends on solutions to smaller instances of the same problem. Such problems can generally be solved by iteration, but this needs to identify and index the smaller instances at programming time. Recursion solves such recursive problems by using functions that call themselves from within their own code.

En informática, podemos entender la **recursividad** cómo un método para resolver un problema donde la solución depende de soluciones a instancias más pequeñas del mismo problema. Tales problemas se pueden resolver por el uso de funciones que se llaman a sí mismas, además, se necesita identificar el caso final, la condición para finalizar el proceso, llamado **caso base**.

Generalmente, si la primera llamada al subprograma se plantea sobre un problema de tamaño u orden N, cada nueva ejecución recurrente del mismo se planteará sobre problemas, de igual naturaleza que el original, pero de un tamaño menor que N. De esta forma, al ir reduciendo progresivamente la complejidad del problema que resolver, llegará un momento en que su resolución sea total.

Las claves para construir un proceso de recursividad son:

* Cada llamada recurrente se debería definir sobre un **problema de menor complejidad** \(algo más fácil de resolver\).
* **Ha de existir al menos un caso base** para evitar que la recurrencia sea infinita.

### 2.3.2 Entendiendo la Recursividad

Se llama **recursividad** \(o **recursión**\) a un proceso mediante el que una función se llama a sí misma de forma repetida, hasta que se satisface alguna determinada condición.

La mayoría de los lenguajes de programación dan soporte a la **recursividad** permitiendo a una función llamarse a sí misma, de tal forma podríamos construir alternativas en los lenguajes imperativos a estructuras de bucles \(loops\) como while y for que son usadas para realizar tareas repetitivas.

{% hint style="info" %}
Podemos transformar en muchos casos los algoritmos recursivos en iterativos con más o menos dificultad y viceversa.
{% endhint %}

**Tipos de algoritmos recursivos:**

* **Lineales**: Cada invocación genera una nueva invocación y sólo una, excepto la última. Ejemplo: Calcular el [factorial de un número](recursividad.md#2-3-4-caso-practico-2-factorial-de-n).
* **Múltiples**: Una misma invocación puede generar más de una invocación. Ejemplo: [Fibonacci](recursividad.md#2-3-6-caso-practico-4-fibonacci).

En general las soluciones recursivas son:

* Menos eficientes que las iterativas.
* Más claras y sencillas que las iterativas.

> Lo correcto es; pensar en recursivo, implementar en iterativo.

{% hint style="warning" %}
A continuación se plantean una serie de casos prácticos para comprender la técnica de recursividad. Ejemplos basados en JavaScript.
{% endhint %}

### 2.3.3 Caso práctico 1: Suma infinita desde N

```javascript
sum = (num) => {
    console.log(num);
    sum(num + 1);
}

sum(10);
```

{% hint style="danger" %}
Cómo se puede ver en este ejemplo, el algoritmo se ejecuta de forma infinita ya que no dispone de ninguna condición \(caso base\) para salir del proceso. Aquí podemos ver una implementación no acabada o mal planteada de la Recursividad.
{% endhint %}

### 2.3.4 Caso práctico 2: Factorial de N

```javascript
factorial = (num) => {
    return num === 0 ? 1 : num * factorial(num - 1);
}

const n = 10;
const result = factorial(n);
console.log(result);
```

### 2.3.5 Caso práctico 3: Potencia de un número elevado a N

```javascript
exponentiation = (base, exponent) => {
    return (exponent === 1) ? base : base * exponentiation(base, exponent - 1);
}

const base = 2;
const exponent = 6;
const result = exponentiation(base, exponent);
console.log(result);
```

### 2.3.6 Caso práctico 4: Fibonacci

Programa recursivo que calcula la función de Fibonacci de un número N. El valor de la función de Fibonacci se obtiene de la siguiente manera:

* Fibonacci\(0\) = 1
* Fibonacci\(1\) = 1
* Fibonacci\(n\) = Fibonacci\(n-1\) + Fibonacci\(n-2\)

```javascript
fibonacci = (num) => {
    if (num === 0) return 1;
    if (num === 1) return 1;

    return fibonacci(num-1) + fibonacci(num-2);
}

const n = 10;
for (let i = 0; i <= n; i++) {
    const result = fibonacci(i);
    console.log(`i: ${i} fibonacci: ${result}`);
}
```

### 2.3.7 Caso práctico 5: Torres de Hanoi

\[...\]

### 2.3.8 Bibliografía

Referencias en español:

1. [https://es.wikipedia.org/wiki/Recursi%C3%B3n](https://es.wikipedia.org/wiki/Recursi%C3%B3n)
2. [https://es.wikipedia.org/wiki/Recursi%C3%B3n\_\(ciencias\_de\_computaci%C3%B3n\)](https://es.wikipedia.org/wiki/Recursi%C3%B3n_%28ciencias_de_computaci%C3%B3n%29)
3. [https://es.wikipedia.org/wiki/Factorial](https://es.wikipedia.org/wiki/Factorial)
4. [https://es.wikipedia.org/wiki/Sucesi%C3%B3n\_de\_Fibonacci](https://es.wikipedia.org/wiki/Sucesi%C3%B3n_de_Fibonacci)
5. [https://es.wikipedia.org/wiki/Torres\_de\_Han%C3%B3i](https://es.wikipedia.org/wiki/Torres_de_Han%C3%B3i)

Referencias en inglés:

1. [https://en.wikipedia.org/wiki/Recursion](https://en.wikipedia.org/wiki/Recursion)
2. [https://en.wikipedia.org/wiki/Recursion\_\(computer\_science\)](https://en.wikipedia.org/wiki/Recursion_%28computer_science%29)

