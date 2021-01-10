# Diseño a la gorra

## Episodio 1

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

## Episodio 2

Heurística importante tomada del segundo episodio de diseño a la gorra @10pines
3. Crear objetos válidos

Conclusiones:
1. Un objeto debe *representar* el ente de dominio *de manera válida desde el momento en que existe*
2. Un objeto debe "enseñar" de manera explícita *qué necesita para representar* ese ente y fallar si se le crea incorrectamente*
