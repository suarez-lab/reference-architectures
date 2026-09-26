# Bucle autónomo acotado

[English](bounded-autonomous-loop.md) · **Español**

**Un contrato que permite a un agente iterar sin un humano entre turnos, sin que el argumento
«el objetivo todavía no se ha cumplido» se convierta en autoridad para hacer cualquier cosa.**

## El contrato

Siete elementos, todos obligatorios antes de dejar que un bucle corra sin supervisión:

| Elemento | Significado |
| --- | --- |
| Objetivo verificable | Enunciado de forma que algo distinto del agente pueda decidir que se ha cumplido |
| Acción por turno | Una unidad de trabajo por turno, no «lo que haga falta» |
| Evaluador independiente | Quien juzga no es quien actuó |
| Límites | Turnos máximos, tiempo de reloj máximo, gasto máximo |
| Autoridad | Enumerada **por efecto**, nunca por objetivo |
| Checkpoint duradero | El estado sobrevive a que el proceso muera a mitad del bucle |
| Escalado | Una forma definida de parar y preguntar |

## Los invariantes

1. Un turno es una unidad de trabajo.
2. Cada turno observa estado fresco; nunca razonar a partir de una foto tomada hace turnos.
3. La evaluación es independiente de la ejecución.
4. **El permiso se concede por efecto, no por objetivo.** Este es el que lo sostiene todo.
5. Las acciones son idempotentes y mutuamente excluyentes, para que un reintento no sea un cargo doble.
6. *No verificable* no es un aprobado.
7. El checkpoint es duradero, o el bucle no se puede reanudar — solo reiniciar.

## Por qué el invariante 4 es el que importa

Un bucle autorizado «para conseguir X» acabará, en una ejecución suficientemente larga,
justificando enviar el mensaje, lanzar el despliegue o hacer el pago, porque cada una de esas
cosas sirve realmente a X. Un bucle autorizado «para leer esta colección y escribir en este
documento» no puede, por lejos que esté de X. **Acota la autoridad a efectos y un objetivo sin
cumplir deja de ser un argumento.**

## Qué cuesta

Fricción. Cada turno paga un checkpoint y una evaluación. Para trabajo corto, barato y
totalmente reversible, eso es sobrecoste que no necesitas.

## Cuándo no usarlo

Cuando ya hay un humano en el bucle de todos modos: entonces el humano *es* el evaluador
independiente, y formalizarlo añade ceremonia sin añadir seguridad.
