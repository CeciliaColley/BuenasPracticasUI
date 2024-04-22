# Buenas Prácticas de UI - Optimización

En base a lo aprendido en clase, he armado esta escena con un poco de UI básico para demostrar cómo he incorporado los conocimientos a mi flujo de trabajo.

He dividido los ítems del UI en tres grandes categorías:

- **Nunca cambian**
- **A veces cambian**
- **Cambian frecuentemente**

La razón por la que decidí hacer esto es porque aprendimos que cuando actualizas un elemento del canvas, se vuelven a redibujar todos los elementos del canvas, no solo aquellos que cambiaron. Mi intención es aislar aquellos elementos que cambian con mucha frecuencia de aquellos que cambian con poca frecuencia, y a su vez, de aquellos que nunca cambian, para no malgastar recursos.

Esto me dejó con dos grupos de tamaño moderado y uno con muchísimos elementos. El que tenía muchos elementos fue "A veces cambian". Esta resolución no era buena, porque ahora si un elemento se actualizaba, aunque fuera con poca frecuencia, todo el canvas tendría que redibujarse. Y con varios elementos que se actualizan en diferentes momentos, aunque sea infrecuentemente, el canvas realmente termina redibujándose con bastante frecuencia. Esto no es óptimo. Hay dos soluciones posibles:

- 1. Agrupar elementos que se actualizarían en el mismo frame.
- 2. Dividir el canvas en varios canvas, para que no se tenga que redibujar un canvas gigante, más bien unos cuantos canvas pequeños (levantar una piedra de una tonelada, versus levantar varias cubetas de arena que equivalen a una tonelada).

Opté por la solución dos porque, en mi caso, no creo tener elementos que se actualizarían en el mismo frame. Dividí los elementos en clickeables y no clickeables.

Revisé todos los elementos, y a aquellos que no registran clics les apagué el Raycast Target. Me aseguré de posicionar cuidadosamente los elementos, sin utilizar un layout group.

Finalmente, mis canvas no utilizan cámaras, y tampoco he animado ningún elemento con un componente. Si lo fuera a hacer, lo haría con código.
