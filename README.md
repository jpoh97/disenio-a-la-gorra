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

## Episodio 7 - Todo lo que siempre quisiste saber sobre los Tests

Tipos de tests:

- las definiciones varían según el autor
- hay definiciones difusas, contradictorias, ambiguas, etc
- el problema es que hay distintas maneras de categorizar los tests y generalmente se piensa en una sola

Categorías:

- de acuerdo al alcance a nivel "código"
- de acuerdo a qué testean
- de acuerdo a como están implementados
- de acuerdo a como ejecutan
- de acuerdo a como se comportan
- de acuerdo a quien lo hace

De acuerdo al alcance a nivel "código"

- test unitarios (solitarios)
- tests de componentes
- tests end to end/tests de sistema/test de integración (test sociales)

Tests unitarios

Def 1: verifican el comportamiento de una unidad
Qué es una unidad? Un método? Una clase? Un "componente"?
Def 2: tests que ejecutan en menos de 10ms
Relacionada con la funcionalidad y no con el alcance de código
- de acuerdo a cómo se hace

Últimamente se los implementa simulando todo lo que la "unidad" bajo test utiliza, por eso también se los llama test solitarios

Ventajas:

- cambios en dependencias no impactan en el resultado del test
- "chicos"

Desventajas:

- cambios en dependencias no impactan en el resultado del test
- están acoplados al diseño, si el diseño cambia los tests se ven impactados
- gran confusión con TDD debido al nombre del framework xUnit
- obligan a "simular" todo aquellos que no es "la unidad testeada"
- más orientados a la "implementación" que a la funcionalidad

Tests de componentes

- verifican el correcto funcionamiento de un "componente"

Qué es un componente? Una clase? Un módulo? Un "java Bean"?
- mismas ventajas y desventajas que los tests unitarios

Tests de integración

- verifican que "partes" implementadas independiente funcionen "conectadas"
- también llamados "system test" o "end to end tests" o "tests sociales"

De acuerdo al alcance a nivel de "código" - conclusión: según mi opinión, la categoría menos interesante porque tiene que ver con el cómo y no con el qué

De acuerdo a qué testean

- Tests funcionales
- Tests no funcionales (de performance, de escalabilidad, de seguridad, de usabilidad)

Tests funcionales

- verifican una "funcionalidad" sin importar el alcance a nivel de "código" (puede abarcar varios métodos, clases, etc)

Ventajas:

- pensados desde el punto de vista funcional y no implementativo
- mas relacionados con las "reglas de negocio"

Desventajas

-cambios en alguna dependencia puede fallar varios tests

Pueden ser unitarios, de integración, etc

De acuerdo a cómo están implementados

- test de caja negra: "desconocen" la implementación de lo que testean
- de caja blanca: acoplados a la implementación de lo que testean

Paradoja: cuando hacemos TDD debemos escribir tests de caja negra, sin embargo conocemos la implementación

De acuerdo a cómo ejecutan

- test aislados (no hay dependencia entre los tests, no comparten "datos de prueba", permiten la paralización de la ejecución)
- test secuenciales (deben ser ejecutados en cierta secuencia, el resultado de un test impacta en la ejecución de otro)
- test compartidos (test con "datos de prueba" compartidos, ej. La misma base de datos)

De acuerdo a cómo se comportan

- tests determinísticos (siempre dan el mismo resultado)
- tests erráticos (a veces funcionan, a veces no funcionan, no cumplen la regla de "el test debe estar en control de todo", muy común que suceda con tests compartidos)
- tests frágiles (fallan al cambiar la implementación de lo que se testea, no al cambiar el qué de lo que testean. Ejemplo: tests con mocks, tests de ui)
- tests "insoportables" (tests que tardan mucho)

De acuerdo a quién lo hace

- test de programador

Son los tests escritos por los programadores y tiene por objetivo "ayudar" al programador en su proceso de desarrollo.

Pueden ser funcionales, no funcionales, unitarios, de integración, desarrollados haciendo TDD o testing, etc

- test de QA

Son los tests creados por gente que no tiene por objetivo principal programar

De acuerdo a cómo se hacen

- tests automatizados (tests programados, tests récord y play)
- tests manuales (pre-definidos, exploratorios)

Tipo de Tests

- funcionales
- de programador
- automatizados, programados
- preferiblemente de caja negra
- preferiblemente determinísticos
- preferiblemente aislados
- preferiblemente "sociales"

Características:
- deben correr rápido (< 10 ms x test)
- deben tener las mismas características a nivel diseño, que cualquier otra pieza de software (aunque a veces es conveniente repetir el "setup", más aún si se puede reiniciar el test y se está trabajando con objetos mutables)

Estructura de los tests

- setup (creación de los objetos que se utilizarán como "datos de prueba" durante el test
- exercise (ejercita la funcionalidad específica que se está testeando. Determina QUÉ se está testeando
- assert (verifica que los resultados sean los esperados)

Datos de prueba != Casos de prueba

Dato de prueba: ejemplos concretos que "definen" un caso de prueba

Caso de prueba: generalización que incluye los datos de prueba

Lo que inicialmente nos parece un caso de prueba puede convertirse en dato de prueba al generalizar la solución

... por eso conviene esperar para nombrar los tests

"Inducción incorrecta"

Inducción: pasa para 1, pasa para N, pasa para N+1

Inducción incorrecta: pasa para 1, pasa para 2, pasa para N

## Episodio 8 - Buenos Aires vs. (London vs. Chicago)

London vs Chicago: serie de videos grabados por Sandro Mancuso y Bob Martin

London Way (Libro: Growing Object-Oriented Software, Guided by Tests):

* "Test unitarios" que mockean todo lo que no se testea directamente
* Se empieza desde el tope del árbol de ejecución (interfaces)
* Los tests definen como debe ser las implementación -> Hay que tener la idea de como implementarlo de entrada

Conclusiones - Diseño:
* Diseño orientado al problema computable, no al negocio
* Organización del proyecto en base al problema computable
* Uso de DTOs para comunicación entre "capas"
* Sobre uso de Json
* Uso de ids en vez de objetos
* 5 clases para registrar un usuario...
* Se expone la password a objetos externos

Bob Martin: Java es un lenguaje procedural orientado a objetos (enfoques puros no existen)

Conclusiones - Tests:
* Test de api de caja blanca (solo lo podes hacer así si ya sabes como vas a hacer la implementación)
* Los tests siguen la misma estructura
* Hay casos sin testear (Usuario con username vacio, Se puede usar followers y followees que no existen, podes seguirte a vos mismo, etc)

Frases
* "I don't like to use classes that are not mine"
* "We are using the mocking to design the behavior" Ya conoce lo que quiere hacer
* "Mocking is not about testing, it is about designing the collaboration between classes" Las clases no colaboran, los objetos si
* "Mocking tests are couple to implementation" 

Hechos
* 11 minutos en escribir el primer test. Clases: UserAPI, UserService, RegistrationData, User
* 4 minutos para hacerlo pasar

Chicago Way:
* Crear clases que representen los casos de uso (CreateUser, Login, GetUsers, etc)
* Escribir tests en base a las clases de casos de uso
* No empezar por las interfaces
* No usar mocking
* Estilo "mas procedural" de solución

Conclusiones - Diseño:
* Clases que representan casos de uso
* Una clase x Api
* UseCaseContext, ApiContext -> Objetos globales
* DTOs para comunicación entre "capas" (CreateUserRequest igual a User)
* Uso de variables de instancia
* Clases sin comportamiento (estructuras de datos)
* Clases con un solo método que únicamente forwardean mensaje
* Inconsistencia en el manejo de casos de error (A veces levanta excepción. A veces retorna boolean)
* Copia de objetos debido a no ser inmutables
* Se expone la password a objetos externos, que además es publica
* No hay clases "service"

![Screenshot](/Episodio 8 - 1.jpg)

Conclusiones - Tests:
* Test de Excepciones sin aserciones de que no sucedió lo que no tenia que pasar
* SetUp muy grande (no es solo setup, hace exercise)
* Se puede postear con palabras inapropiadas
* Hay casos sin testear (Usuario con username vacio, Si follower o followee no existe lo relaciona con null, podes seguirte a vos mismo, etc)

Frases:
* "We have tested that the assignment operator works"
* "I use data structure without constructors because they tend to grow"

Hecho:
La primera vez que corre tests, son 2 tests juntos y pasan de entrada

Buenos Aires Way:
* Empezar testeando y modelando el negocio
* Dejar interfaces para el final
* Usar metáforas para concretizar el negocio
* Diseñar objetos con heurísticas vistas hasta ahora

Concepto de tecnología perfecta: Poder pensar en el negocio mas allá de la tecnología, dejando el problema de la tecnología para mas adelante (no preocuparse de entrada por la memoria o procesador)

A nivel de arquitectura: no empezar por las interfaces para evitar tener lógica en las interfaces o código repetido. Ser agnósticos a cualquier interfaz

Es normal tener código que solo se utiliza en los tests, ya que estos utilizan el modelo al igual que cualquier interfaz

No importa si este código no se usa en producción, actualmente no es algo critico esa memoria de mas. Los test son nuestros primeros usuarios y si necesitan algún código se debe agregar

Lo que no se debe hacer es cambiar métodos privados a públicos para acceder desde el test

TDD: Es una técnica de programación, no de testing. Si no vamos a diseñar mientras hacemos TDD, entonces para que lo hacemos? es un problema común en el enfoque de Mancuso y Bob Martin, se enfocan mas en los tests que en el diseño.

Definir si usar el inside-out o out-in puede depender en cuanto conoces el negocio. Lo ideal seria iniciar en el medio. Ni empezar por el detalle ni por lo mas abstracto

En Java privado no es al objeto, significa privado a la clase (pierde sentido el encapsulamiento)

Ser consiente desde el punto de vista de los baby steps en dar los pasos mas que pequeños posibles (no hacer tests muy grandes de entrada)
Crear copias de colecciones al retornar para asegurar encapsulamiento (no te lo modifican desde afuera)

Usar TDD como mecanismo de modelado del problema, pero también lo puedes usar como mecanismo de implementación de la api (usar TDD para todo)

Respecto la metodología
* Diseño basado en el negocio
* Se pudo resolver el problema sin mocks ni clases ficticias (use cases)
* Se usaron objetos completos, válidos, inmutables y sin null
* No se rompió el encapsulamiento
* No fue necesario usar DTOs, Json, etc
* No fue necesario usar ids entre los objetos de negocio
* Por concentrarnos en el negocio, detectamos mas casos de error

Es muy fácil criticar, es muy difícil hacer. Para los programadores es muy fácil criticar el código hecho por otras personas porque no conocemos el contexto

La critica objetiva no existe, uno critica siempre desde lo subjetivo. Lo importante es que esa subjetividad se construya con tiempo, experiencia, estudio... es una subjetividad entrenada
