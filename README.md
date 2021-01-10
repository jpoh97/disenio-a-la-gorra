# Diseño a la gorra

## Episodio 1 - Qué es Diseñar y Cómo hacer que un diseño nos "Enseñe"

Algunas definiciones (marcos conceptuales):
1. Diseño es la *definición* que usamos para construir
2. Código fuente == Diseño de software
3. Programar es diseñar y diseñar es programar
4. Software = *Modelo computable* de un *dominio de problema* de la realidad
5. Proceso de aprendizaje a través de formalización de conocimiento: observar la realidad (lenguaje natural), proyectarla (lenguaje formal), reflexionamos sobre el modelo y sobre el dominio de conocimiento (aprendemos)...
Proceso iterativo/incremental. ¡Aprendemos a medida que creamos el modelo!
6. Objeto = *representación* esencial de un *ente* del dominio de problema. Esa representación se realiza a través de los *mensajes* que sabe *responder*
7. En los diseños "pasa el tiempo" y deben "enseñarnos"

Heurísticas que enseña el video:
1. Crear objetos completos
2. Tener un único constructor/mensaje de construcción de instancia principal. El resto debe estar implementado en función de este
3. ¡No romper el encapsulaminto! (Adiós clases anémicas)
4. Si hay variables de instancia sin inicializar, eso indica que conviene separar en dos objetos
5. Si la construcción de un objeto es compleja/implica mucho "paso del tiempo", utilizar un Builder
6. Si un framework me obliga a tener constructores sin parámetros (ej. Hibernate) eso no significa que lo tengamos que usar

Ideas principales:
* Hay que tener en cuenta el *paso del tiempo* en el dominio de problema
* Hay que tener en cuenta el *paso del tiempo* en los diseños
* Los diseños deben *enseñar* lo que representan
* Un objeto debe *representar* el ente del dominio de problema *desde el momento en que existe*
* Un objeto debe "enseñar" de manera explícita *qué necesita para representar* ese ente

## Episodio 2 - Objetos Válidos

Heurística importante tomada del segundo episodio de diseño a la gorra @10pines
3. Crear objetos válidos

Conclusiones:
1. Un objeto debe *representar* el ente de dominio *de manera válida desde el momento en que existe*
2. Un objeto debe "enseñar" de manera explícita *qué necesita para representar* ese ente y fallar si se le crea incorrectamente*

## Episodio 3 - Modelar los "Conjuntos de Objetos"

¡Los objetos no viven aislados!

Heurísticas:

4. Usar una metáfora para "mappear" el problema (no usar nombres de patrones en las clases)
5. Modelar los "conjuntos" de objetos (Distintas implementaciones del "conjunto")
6. Usar updates atómicos

## Episodio 4 - No usar null

Heurística 6: *No usar* null/nil (es un objeto que representa más de un ente de la realidad)

Tip: Representar la nada especializada por medio de null object o encapsular que puede ser null con optional o explicit absent message

¿Cuándo usar cada uno?
Sistema nuevo y sé que puede ser "null"

Leng. Dinámicamente tipado:
1. Explicit Absent Message
2. Null Object

Leng. Estáticamente tipado:
1. Optional
2. Null Object

Sistema existente, no podía ser "null" y ahora si:

Leng. Dinámicamente tipado:
1. Null Object
2. Explicit Absent Message

Leng. Estáticamente tipado:
1. Null Object
2. Optional

Sistema existente, se rompió encapsulamiento y hay chequeo por null en todos lados

Leng. Dinámica tipado: 
1. Explicit Absent Message y a arreglar todo!

Leng. Estáticamente tipado:
1. Optional y a arreglar todo!

## Episodio 5 - Código Repetido e Historia de los Closures

Los lenguajes de programación representan el estado de conocimiento de aquellos que los crearon... Cómo cualquier modelo/sistema.
Debemos ir más allá del lenguaje de programación y entender que significa hacer un modelo computable

Características de los closures:

1. No tienen nombre
2. Bindean al contexto de ejecución donde se los crea
3. Full closure: también bindean el return (non-local return. Solo Smalltalk y Ruby)
4. La sintaxis de uso debe ser sencilla
5. Uso principal: parametrizar "código"

Código repetido significa que nos falta una abstracción

## Episodio 6 - TDD y Roles de Clases

Simplicidad de smalltalk: todo "bloque de código" es un closure

TDD es mucho más que tests que se escriben primero y hay que hacer pasar después

¿Qué es TDD?

Técnica de desarrollo basada en características del aprendizaje
* Iterativa e incremental
* Basada en Feedback Inmediato

Side-Effect:
* Recuerda todo lo aprendido
* Y permite asegurarnos de no haber "desaprendido"

Incluye análisis, diseño, programación y testing

¿Cómo se hace TDD?

1. Escribir un test
* Debe ser el más sencillo que se nos ocurra
* Debe fallar al correrlo
2. Correr todos los tests
* Implementar la solución más simple que haga pasar el/los tests
3. Reflexionó - ¿Se puede mejorar el código?
* Si->Refactorizar. GOTO 2
* No->GOTO 1

El *tiempo* que tardó en *cada paso* de TDD, es un indicio de qué tan bien estoy realizando la técnica

Los test unitarios están "acoplados" al diseño (mejor usar sociable tests)

Puedo verificar qué tan bien hice los tests usando mutation testing (por lo menos de manera manual)

TDD hace que los *programadores* semana los *primeros usuarios* del sistema que desarrollan

La culpa no es de TDD ¡Estamos "sufriendo" nuestros diseños!

Un programador no es buen programador si *no sabe testear*

TDD *jerarquizó* el testing

TDD hace *explícito* todos los "tests" que corremos en nuestra cabeza

TDD nos da *seguridad* al momento de refactorizar (feedback rápido)

Evita que el sistema se convierta en un sistema legacy (aquel que tengo miedo de modificar)

TDD *no* implica *buen diseño*

Aunque si implica diseños más desacoplados

Es importante poder extender clases para no caer en "soluciones estructuradas"

Extender clases nos permite que sus instancias cumplan *distintos roles según el contexto*
