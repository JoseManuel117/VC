## Práctica 2. Funciones básicas de OpenCV

**Tarea 1:**

Hemos aprovechado el mismo código ya existente en la práctica para hacer el conteo de columnas. Para hacer el de filas, únicamente hay que modificar el segundo parámetro de la función `cv2.reduce()`, poniendo un 1 en vez de un 0.

**Tarea 2:**

Como dicta el enunciado, hemos repetido el mismo proceso pero cambiando únicamente la imagen. Hemos cambiado el incivilizado mandril por una foto del Nano (Fernando Alonso).

**Tarea 3:**

Realizamos los procesos pertinentes previos al análisis de la imagen y luego realizamos el cálculo de bordes tanto horizontal como vertical con Sobel. Después, lo convertimos a una imagen de 8 bits y realizamos el conteo tanto por filas como por columnas por encima del 0.95*máximo. Una vez representadas las gráficas, se pueden comparar con las de Canny ascendiendo en el código.

**Tarea 4:**

La tarea 4 está realizada en el cuaderno.

**Tarea 5:**

Para la tarea 5 hemos decidido crear un censurador de caras. Para ello, usamos un clasificador de cascada llamado "haarcascade_frontalface_alt.xml", el cual se puede descargar desde [este enlace](https://github.com/opencv/opencv/tree/master/data/haarcascades).

El esquema de funcionamiento es el siguiente:
- Cargamos el clasificador en el objeto `face_detect`.
- Seguimos el proceso típico que hemos utilizado hasta ahora para analizar las imágenes de un video.
- Para seleccionar las caras dentro de la imagen, debemos usar la función `detectMultiScale()` dentro del objeto `face_data`, ya que pueden haber múltiples caras en la misma imagen.
- Ahora creamos un rectángulo sobre esas mismas caras y lo difuminamos usando `GaussianBlur()` y sustituimos la región de la cara de la imagen original por la versión difuminada.
