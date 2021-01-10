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

![](https://github.com/jpoh97/disenio-a-la-gorra/blob/main/screenshots/Episodio%208%20-%201.jpg)

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

![](https://github.com/jpoh97/disenio-a-la-gorra/blob/main/screenshots/Episodio%208%20-%202.jpg)

No importa si este código no se usa en producción, actualmente no es algo critico esa memoria de mas. Los test son nuestros primeros usuarios y si necesitan algún código se debe agregar

Lo que no se debe hacer es cambiar métodos privados a públicos para acceder desde el test

TDD: Es una técnica de programación, no de testing. Si no vamos a diseñar mientras hacemos TDD, entonces para que lo hacemos? es un problema común en el enfoque de Mancuso y Bob Martin, se enfocan mas en los tests que en el diseño.

Definir si usar el inside-out o out-in puede depender en cuanto conoces el negocio. Lo ideal seria iniciar en el medio. Ni empezar por el detalle ni por lo mas abstracto

En Java privado no es al objeto, significa privado a la clase (pierde sentido el encapsulamiento)

Ser consiente desde el punto de vista de los baby steps en dar los pasos mas que pequeños posibles (no hacer tests muy grandes de entrada)
Crear copias de colecciones al retornar para asegurar encapsulamiento (no te lo modifican desde afuera)

Usar TDD como mecanismo de modelado del problema, pero también lo puedes usar como mecanismo de implementación de la api (usar TDD para todo)

![](https://github.com/jpoh97/disenio-a-la-gorra/blob/main/screenshots/Episodio%208%20-%203.jpg)

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

## Episodio 09 - Buenos Aires vs. (London vs. Chicago) - Parte 2

![](https://github.com/jpoh97/disenio-a-la-gorra/blob/main/screenshots/Episodio%209%20-%201.jpg)

Es mejor que los mensajes sean en positivo y no en negativo

Donald Knuth: Premature optimization is the root of all evil

Una manera sencilla de ver si un caso de prueba esta siendo testeado es retornando un valor

Esta bien tener redundancia cuando se esta testeando para asegurarse que nada cambie en el modelo (constantes por ejemplo)

Usar la clase Collections para crear colecciones inmutables

Lo importante de TDD no es testear los datos, es testear la funcionalidad

Debe existir un limite de cuantos datos voy a testear. Ser cuidadoso con la inducción incorrecta. Ya es un problema de datos y no de lógica

Hay objetos específicos para los problemas tecnológicos, un objeto de dominio debería porque conocer de tecnología

No es bueno empezar a testear por la raíz del árbol, ya que todo lo que testeamos para los objetos inferiores los terminamos testeando desde la raíz y tendríamos tests mas largos y pesados. Es mas recomendable empezar por el medio

A medida que se va avanzando se da cuenta que probar la consistencia de un objeto puede requerir varias aserciones

Eso de "no conviene implementar código que solo usan los tests", es algo temporal, puede suceder que después lo necesites en cualquier otro contexto

Todo lo que tiene que ver concurrencia, escalabilidad, performance, etc. son problemas que no se resuelven con TDD. Estamos pensando en tecnología perfecta

No nos debemos preocupar por resolver problemas que aun no surgen, más cuando impacta el diseño actual que tratamos de hacer funcional con problemas no funcionales. Esto por hacer optimizaciones tempranas

Esto para evitar decisiones de diseño tempranas que quizá no sean las mejores cuando tenes el big picture (se ve todo el sistema)

Hacer abstracciones tempranas no es bueno a nivel de diseño porque después es muy difícil sacarlas de la cabeza

Entre mas podamos aplazar ese tipo de decisiones de diseño no funcionales es mejor. Y cuando se haga, debemos realizar testing para verificar que funcione correctamente

Como programadores somos observadores de un dominio central que es el de negocio, pero al mismo tiempo tenemos dominios periféricos (persistencia, concurrencia, distribución, etc).  

Puedo resolver cada problema de dominio con objetos que comparten mensajes

Voy a tener objetos preocupados por la concurrencia, otros por la persistencia y los objetos del dominio de negocio. Lo interesante es que cada uno juegue su juego y que sean cohesivos

Nos preocupamos mas por el dominio tecnológico porque es el que mas conocemos. Nosotros sabemos mas de tecnología que de finanzas, salud, etc.

Son distintos dominios de conocimientos. Ninguno es más importante, están al mismo nivel

A la final se resuelve cada uno por su lado y luego vemos como colaboran entre ellos (los objetos)

Quizá es exagerado y en algunos casos no es fácil despegarse del tema tecnológico, pero es lo ideal (tecnología perfecta)

La etapa 3 (refactorización) no es obligatoria, no es necesario hacerlo todo el tiempo. Hay momentos donde conviene aplicarla y momentos en que no. Si la aplicas muy temprano quizá tus abstracciones queden limitadas a los casos que has visto...

Mientras que si las aplicamos mas tardes, pueden aparecer mas casos y realizar abstracciones mas interesantes

Alan Kay: Las cosas se repiensan y se rehacen. Esto es software

El test debe estar en control de todo. Cuando testeamos concurrencia, debemos buscar ese control

Independiente de si estas usando TDD o no. Estos tests de concurrencia son mas complejos. Por eso nos preocupamos primero por los tests funcionales y luego hacemos este tipo de test (ya no es TDD, es testing)

A veces se necesitan cosas que no hacen parte del tema funcional de un sistema (ejemplo: usuarios).

A veces es mejor encapsular cierto código en vez de retornar un valor, para solucionar un problema común en múltiples partes

El Optional de java es propenso a errores también

## Episodio 10 - Buenos Aires vs. (London vs. Chicago) - Parte 3

El id solo debería responder si es igual a otro.

2 opciones para crear un id: Lo haces en tu objeto de dominio, lo delegas a la interfaz o ids por sesión (va en contra de rest pero es mas seguro)

La opción mas aconsejable es dejar a cargo a la interfaz para no ensuciar mi modelo con un problema de la interfaz Rest. No todas las interfaces van a necesitar un id.

Esta bien si se testea múltiples veces un método desde otro objeto o el mismo. No nos debemos preocupar por testear de mas, es algo que hacemos todo el tiempo. No debería ser diferente si son clases propias o del lenguaje/framework.

Los objetos deben colaborar con otros para hacer cosas.

Desde una interfaz rest puedo testear algo de negocio y verificar que me retorne un código http. Es algo que no he testeado hasta el momento. No importa si este test vuelve a probar la lógica de negocio

Un test puede incluir a los otros y agregar algo más.

Todo aquello que yo no pueda controlar desde el test, lo debo de alguna manera controlar simulándolo

Ciertas cosas que pensamos como natural (hacer un LocalDateTime.now()), no nos damos cuenta que nos acoplamos a una única manera de obtener la hora lo cual no es valioso en ciertos casos (usar un reloj para obtener la hora que se inyecta al objeto)

Hay cosas que no son del dominio de negocio, son del dominio computacional del sistema (i.e. un usuario en un sistema bancario).

Cuando hablamos de negocio nos referimos a la parte funcional y también a lo no funcional (i.e. users) que son requisitos para hacer un buen sistema

Y que también son un problema en si mismo y lo debemos resolver.

No armamos nuestro esquema de trabajo en base a separaciones de subsistemas, clases o paquetes, sino a nivel funcional. Esa funcionalidad puede tocar varios subsistemas

El proceso seguido es de cierta forma un inside - out, pero un poco distinto a lo propuesto por bob martin. Importante resaltar las diferencias a nivel de diseño en cada propuesta. Es algo que se debe tomar en cuenta. No solo se analiza la forma del proceso, también el resultado

A veces se necesita escuchar algo que ya te dijeron pero de otra forma para capturar la idea. Es algo que genera personas como Alan Kay.

## Episodio 11 - Buenos Aires vs. (London vs. Chicago) - Parte 4

Se refactoriza el código para retornar una custom exception en vez de Runtime ya que esta ultima debería retornar un status 500 (error de servidor)

Son errores de problema funcional, de como se esta usando el sistema y no errores de programación

* Si tenemos un map y adentro un if, se puede aplicar un filter primero
* y -> (x -> x).apply(y) == x -> x (es equivalente al closure de adentro)
* (y -> f(y)).apply(z) == f(z)

Este ultimo es equivalente a aplicar el closure.

Todo esto es gracias a pensar mas de forma funcional y no imperativa.

Gracias a que los test son sociables (no se mockea), no tenemos que modificar los tests al realizar este tipo de refactors

Estos son los resultados de como se comporta las distintas implementaciones de TDD respecto a los errores

Algunos errores en chicago se deben a que el proceso es guiado por la interfaz y no por la funcionalidad

![](https://github.com/jpoh97/disenio-a-la-gorra/blob/main/screenshots/Episodio%2011%20-%201.jpg)

Al realizar modificaciones, podemos empezar por los tests de más arriba, más abajo y del medio. Los de mas abajo no agregan valor porque estaríamos testeando el agregar un getter. Los de más arriba son más complejos porque se debe modificar demasiadas cosas para que pase un test

Empezar por el medio del árbol seria lo mejor de los 2 mundos (se evitan los 2 problemas anteriores).

La manera en que lo hace Mancuso es útil cuando sabes lo que vas a hacer desde antes. Esto contradice un poco el objetivo de hacer TDD de descubrir a medida que vamos haciendo

## Episodio 12 - Buenos Aires vs. (London vs. Chicago) - Parte 4B

Ser cuidadosos de los tests que brindan una falsa sensación de seguridad, que pasan aun cuando el código no funciona correctamente. Pasa mucho cuando se utilizan mocks y no se prueba las colaboraciones

Lo difícil de realizar cambios en un sistema legacy es que no sabes todo lo que impacta el cambio. Si se puede mantener el cambio lo mas pequeño posible, entonces lo hacemos de manera más segura

Los tests de programadores son los tests que escribimos como programadores haciendo TDD. Los tests de aceptación son los que debería escribir un usuario y van muy por arriba del árbol de ejecución y que debería testear todo una funcionalidad

Son tests mas lentos y que abarcan mas, y que por lo general no lo escribe un programador. Tienen como objetivo asegurarse que la funcionalidad desde el punto de vista del usuario es correcta. 

El objetivo de los tests de programador es asegurarse que el código funciona

## Episodio 13 - Buenos Aires vs. (London vs. Chicago) - Parte 5

TDD nos permite diseñar un objeto antes de implementarlo. Lo diseño desde la necesidad.

Algunas abstracciones tienen que ver mas con el conocimiento/experiencia que tenga el desarrollador y no con la técnica. Se puede aplicar TDD pero tener toda la lógica en el controller debido a la débil capacidad de abstracción. No importa si se usa outside-in o inside-out.

Cuestiones de experiencia de diseño.

Kent Beck: Cuando me paro del escritorio, para saber que tengo que hacer cuando vuelva dejo un test fallando.

Esta bien tener objetos distintos para retornar en el api y que no sean los mismos del dominio, así nos desacoplamos

En el enfoque outside-in puede pasar que necesitemos cosas que no pertenecen al dominio desde muy temprano, por ejemplo los ids de base de datos.

La identidad del objeto debe estar ligada al ciclo de vida del objeto, por lo tanto es normal instanciarlo en el constructor.

El id en el ORM es problema del ORM y no del objeto. Estos ids no son necesarios para el objeto, la identidad viene dada por el hecho de ser objeto. Solo es necesario porque va a ser usado en el mundo externo como un puntero al objeto.

El constructor debe verificar que se creen objetos completos mas que asignar ids. Usarlo así es muy cómodo, pero lo que debe evitar es usarlo en el modelo. Es algo que pasa en la implementación London y Chicago que en vez de trabajar con objetos usan ids.

El problema de las bases de datos relacionales es otro, es un problema tecnológico. El verdadero id del objeto es transparente para el desarrollador, y no tiene nada ver con el id de la base de datos. Si tenes que hacer una chambonada, que sea una chambonada orientada a objetos!

Alan Kay: Podemos llamar a las clases de una manera distinta a la que nos ofrecen los frameworks en general (ejemplo: Controller). Debemos ir mas allá de los estereotipos que nos ofrecen los frameworks.

Outside-in (escuela London) viene con un uso obsesivo de mocks, sin embargo la técnica se puede aplicar sin necesidad de usar mocks.

Con esta técnica puede llegar a pasar que encontremos casos funcionales que no están cubiertos (a pesar de que el coverage sea 100%)

Para definir cual técnica usar, debemos cuestionar en donde están las incertidumbres del sistema a modelar. Aplicando XP, debemos buscar el estrés pronto y no al final. Si tenes incertidumbre sobre la arquitectura (o el working skeleton) es una buena opción usar outside-in

El modelo debe prestar un servicio dentro de un ecosistema mas grande, esta es una de las razones para usar outside-in. Se toma en cuenta todo el ecosistema del diseño.

No estoy diseñando en términos del dominio, estoy descubriendo la arquitectura. Se acopla mucho a la accidentalidad de lo que se esta pidiendo.

Configurar un framework es un trabajo repetitivo. Normalmente la mayor incertidumbre es entender el dominio de negocio.

A la final es lo que genera mayor valor al cliente. Es lo más cambiante. Es fácil perderse cuando se sigue esta técnica outside-in ya que es fácil desviarse por otras ramas, para esto es importante tener un trace bullet y no perder el foco.

La tecnica a escoger, sea outside-in (London) o inside-out (Chicago) o middle-out (Buenos Aires) depende de la necesidad de negocio particular. Que nos interesa más: el negocio, la base de datos, el frontend? Desde allí debemos partir

## Episodio 14 - Buenos Aires vs. (London vs. Chicago) - Parte 6

Con TDD la idea es estar desacoplado de recursos externos. No tiene sentido aplicar la persistencia, es mejor tener implementaciones en memoria para los tests.

En TDD, se debe correr los tests a medida que hago refactors, pero cuando estos refactors son automatizados no es necesario correrlos.

Cuando realizamos mucho copy - paste es momento de crear nuevas abstracciones.

Cuando se necesita parametrizar un llamado a un código, se puede hacer usando diferentes mensajes.

Nunca hay que hacer refactors con tests fallando!

Cuando se hacen refactors que no son automatizados, se deben correr los tests para verificar que todo siga funcionando.

Por medio de refactors automatizados podemos agregar semántica, sacar código repetido y hacer mas entendible el código (tests y el modelo).

Cuando tenemos un decorator que repite código (todos los métodos tienen una misma lógica pero solo cambia el llamado o solo forwardea)

Se puede tener una lista de comandos que ejecutan las acciones.

Cuando se usa un method object, todas las variables locales al método tienen que pasar a ser variables de instancia de la clase. Es uno de los objetivos del method object.

Cuando estamos interfaceando con el mundo exterior que recibimos cosas que no son objetos (por ejemplo Jsons), en esos casos voy a necesitar tener cadenas de ifs. Necesito comparar lo que viene del mundo exterior para tomar una decisión.

Se podría reemplazar por polimorfismo, pero no siempre es la mejor opción.

Cuando uno aprende a encadenar refactorings, uno puede hacer grandes cambios de diseño. El no usarlo de esta forma es un handicap muy grande. Nos sacamos el mejor provecho.

InvocationHandler es una interfaz en Java que podemos implementar cuando queremos que un objeto se comporte como un proxy dinámico. Se implementa el método invoke que recibe el Method (que se debería llamar Message) que se le esta enviando al objeto.

Este invoke puede forwadear el mensaje en el caso de que no sepa que responder. Te permite responder dinámicamente un mensaje que un objeto no sabe responder. Si aparece un nuevo mensaje no tengo que hacer nada, automáticamente el proxy sabe que debe invocar el invoke

Y este puede forwardear el mensaje.

En este episodio vimos como hacer varios cambios de diseño a través de refactoring automatizado, como hacer TDD con recursos externos y como sacar cierto código repetido vía metaprogramación que lo metimos por medio de refactors automatizados.

Cuando uno empieza a hacer cambios de diseño encadenando refactorings, empieza a entender las dependencias que existen entre los objetos que tenemos en nuestro modelo de una manera distinta a cuando lo hacemos manualmente.

Empieza a darse cuenta de ciertos acoplamientos que antes no conocía. Se entiende porque hay que hacer ciertos cambios en cierto orden. Se vuelve evidente las relaciones entre los objetos.

Los refactorings automatizados explican el proceso por el cual piensa un programador. Es automatizar el proceso de pensamiento del programador y te ordena tu proceso de cambio.

TDD te ordena tu proceso de desarrollo, el refactoring te ordena tu proceso de cambio.
