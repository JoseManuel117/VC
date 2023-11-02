# Tareas Realizadas

A continuación, se detallan las tareas que hemos completado en esta entrega:

1. **Creación de una Imagen con Textura de Tablero de Ajedrez:**
    - Hemos abordado esta tarea de dos maneras distintas. En una de ellas, creamos una cuadrícula de 8x8 sobre la imagen y alteramos los cuadros de la cuadrícula correspondientes, alternando entre blanco y otro color.
    - En la segunda aproximación, hemos empleado un enfoque más directo, recorriendo la imagen con bucles anidados y pintando los cuadrados a blanco cuando era necesario.

2. **Creación de una Imagen al Estilo Mondrian:**
    - Creamos una cuadrícula de 200x200 y procedimos a pintar cuadrados por filas y columnas.

3. **Creación de una Imagen al Estilo Mondrian con Funciones:**
    - Hemos pintado rectángulos sobre un fondo negro para recrear el estilo Mondrian. Cada rectángulo se genera de forma aleatoria dentro de un margen predefinido para evitar la superposición y garantizar la presencia de un cuadrado en cada zona.

4. **Modificación de los Valores de un Plano de la Imagen:**
    - Capturamos imágenes de la cámara web y separamos sus canales. A continuación, aumentamos la intensidad de cada canal en 75 unidades y mostramos la fusión de la imagen original junto con otras tres imágenes que representan la unión de dos canales. Este resultado podría considerarse como una propuesta de pop-art.

5. **Pintura de Círculos en las Posiciones del Píxel Más Claro y Más Oscuro de la Imagen:**
    - Creamos un fotograma en escala de grises para mejorar la interpretación de la "luminosidad". Luego, recorrimos cada píxel de este fotograma y registramos la posición del píxel con el valor más alto y más bajo. Posteriormente, pintamos un círculo verde en la posición del píxel más claro y otro rojo en la posición del píxel más oscuro.

6. **Propuesta de Pop-Art:**
    - Hemos desarrollado una propuesta similar a la anterior, pero implementada de manera diferente. Recorrimos el fotograma de la misma manera que en el ejercicio anterior y si el valor del píxel estaba dentro de uno de los tres umbrales predefinidos (azul, rojo, verde), lo pintamos del color correspondiente. Esto hace que la propuesta sea poco eficiente pero también lo hace nuestro.


**Referencias**
- https://docs.opencv.org/4.x/dc/da5/tutorial_py_drawing_functions.html
- https://chat.openai.com
- https://docs.opencv.org/4.x/df/d9d/tutorial_py_colorspaces.html