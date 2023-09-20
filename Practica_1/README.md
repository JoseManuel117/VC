Para esta entrega hemos realizado las siguientes tareas:
    1º  Creación de una imagen con la textura del tablero de ajedrez: Lo hemos hecho de dos formas diferentes, en una de ellas hemos creado un grid de 8*8 sobre la imagen y hemos puesto a blanco los recuadros de grid correspondientes (uno sí, uno no).

        La otra forma es más "a lo bruto", hemos recorrido la imagen con un bucle anidado y hemos ido pintando un cuadrado blanco cuando tocaba.

    2º  Creación de una imagen al estilo Mondrian: Creamos un grid de 200x200 y luego pintamos los cuadrados por filas y columnas.
    
    3º  Creación de una imagen al estilo Mondrian con funciones: Hemos pintado rectangulos sobre una imagen de fondo negro para recrearlo, cada rectangulo se genera de forma aleatoria dentro de un margen pre-establecido para que no se solapen los unos a los otros, y siempre exista un cuadrado en una de las zonas.

    4º  Modificación de los valores de un plano de la imagen: Captamos las imagenes que transmite la webcam y los hemos separado los canales, acto seguido le aumentamos la intensidad de los mismos en 75 y mostramos la fusión de la imagen original junto con otras 3 imágenes que representan 2 canales unidos. El resultado podría valer como propuesta de pop-art

    5º  Pintar círculos en las posiciones del píxel más claro y oscuro de la imagen: creamos un frame en escala de grises para poder interpretar de mejor forma su "luminosidad", acto seguido empezamos a recorrer cada píxel de dicho frame y guardamos la posición del píxel con el valor más alto y el más bajo. Una vez recorrida toda la imagen, pintamos un círculo verde en el píxel más claro y uno rojo en la del más oscuro.

    6º  Propuesta de pop-art: Hemos realizado una similar a la ya implementada en el documento original pero programado de forma diferente. Recorremos el frame de la misma forma que en el ejercicio anterior y si el frame encaja dentro de uno de los 3 umbrales que hemos seleccionado (azul,rojo,verde) lo pintamos de dicho color. Lo cual lo hace muy poco eficiente pero también lo hace nuestro.