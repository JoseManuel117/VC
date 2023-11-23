## Práctica 5. Reconocimiento de matrículas
**Autores:** Josito Manuel Hernández Aparicio & Sheila Cazorla Rodriguez

### Contenidos
 [Descripción General](#descripción-general-de-la-práctica)
 [Tarea 1](#tarea-1)
 [Tarea 2](#tarea-2)
 [Instalacion Cuda](#instalación-cuda)
 [Entrenamiento Modelo Custom](#entrenamiento-modelo-custom-yolov8)

### Descripción general de la práctica 
En esta práctica la tarea propuesta consiste en desarrollar un **prototipo** de sistema que identifique la matrícula de un vehículo mediante dos formas diferentes, para la primera, denominada **tarea 1**, hemos usado exclusiamente la detección de contornos. Para la segunda, hemos entrenado un modelo de [***yolov8***](https://docs.ultralytics.com/es/).

### Tarea 1
Para identificar las matrículas de los coches, primero empleamos el modelo estándar de [***yolov8***](https://docs.ultralytics.com/es/) para identificar los coches, una vez encontrado los coches visibles en la imágen, empleamos una función llamada **encontrar_matricula** que se encarga de identificar la matrícula dentro de la imagen pasada como parámetro, como este tipo de detección puede ser muy precaria, debemos facilitarle la detección lo máximo posible. 

Para ello, sabiendo de antemano que la inmensa mayoría de las matrículas se encuentran en la parte inferior de los coches, le pasamos a la función únicamente la mitad inferior del coche detectado, como se muestra a continuación:

<figure>
  <img src="./readmeResources/zona%20de%20deteccion.png" alt="Imagen de la zona de detección" title="Imagen Zona Detección" width="600" height="350">
  <figcaption><strong>Zona de detección en azul, matrícula encontrada en verde</strong></figcaption>
</figure>

#### Primer Prototipo
Para la detección de la matrícula en el primer prototipo, nos hemos valido de la detección de contornos de la biblioteca de [***cv2.findContours***](https://docs.opencv.org/4.x/d4/d73/tutorial_py_contours_begin.html), hacer que una detección de este tipo funcione correctamente en la mayoría de situaciones reales (matrículas giradas, poco visibles, etc...) se hace extremadamente difícil, al principio lo intentamos hacer mejorando la detección de contornos rectangulares, intentando hallar una relación correcta entre ser más estrictos a la hora de encontrar rectángulos, lo cual hace que no encuentre algunas matrículass, y ser más flexíbles a la hora de identificarlos, algo que hace que encuentre rectángulos donde, a interpretación humanda, no los hay. Un resultado de un primer prototipo sería el siguiente:

<figure>
  <img src="./readmeResources/Reconocimiento regular.png" alt="Primer prototipo" title="Imagen Detección Matrículas" width="600" height="350">
  <figcaption><strong>En verde lo detectado por la función</strong></figcaption>
</figure>

Como se puede observar, identifica correctamente la matrícula, pero también muchos otros contornos, conseguimos volver la detección más estricta especificando un número de vértices máximo, ya que un rectángulo solo tiene 4, si bien la detección mejoró considerablemente, la detección seguía siendo demasidado precaria. Tras otra tanda de futiles intentos, se nos ocurrió lo que acabó siendo nuestro prototipo final.

#### Prototipo Final

Para el prototipo final de esta tarea, lo que hicimos fue hacer que **detectar_matricula** identificase contornos estríctamente rectangulares, lo cual nos dio el siguiente resultado:

<figure>
  <img src="./readmeResources/rectangulos sin comprobar.png" alt="Prototipo final sin verificar" title="Imagen Detección Matrículas PF" width="600" height="350">
  <figcaption><strong>Detección de rectángulos</strong></figcaption>
</figure>

Como se puede observar, la matrícula la identifica a la perfección, también encuentra multitud de rectángulos de diversas dimensiones. Llegados a este punto, nos parecía imposible diferenciar de forma convencional entre los rectángulos detectados y el que contenía la matrícula usando exclusivamente funciones [***opencv***](https://opencv.org). 

La lógica nos dicta que, de todos esos rectángulos, el único que contiene texto (por texto entendemos más de 2 dígitos) es el que contiene la matrícula, así pues, usamos [***easyocr***](https://github.com/JaidedAI/EasyOCR) para buscar texto en los rectángulos y, en caso de que encuentre 2 o más dígitos, lo identifica como la matrícula deseada
```
reader = easyocr.Reader(['es'])
results = reader.readtext(crop_rgb)
if results:
                matricula_text = results[0][-2]
                if len(matricula_text) >= 2:
                    cv2.drawContours(car_img, [box], 0, (0, 255, 0), 3)
                    return matricula_text
```
Lo cual hace que la detección sea algo lenta, pero muy precisa
<figure>
  <img src="./readmeResources/Reconocimiento Regular 1.PNG" alt="Prototipo final verificando" title="Imagen Detección Matrículas PF" width="600" height="350">
  <figcaption><strong>Detección del prototipo final</strong></figcaption>
  <img src="./readmeResources/Reconocimiento Regular 2.PNG" alt="Prototipo final verificando" title="Imagen Detección Matrículas PF" width="600" height="350">
  <figcaption><strong>Detección del prototipo final</strong></figcaption>
</figure>

### Tarea 2

#### Instalación CUDA
Para esta tarea hemos empleado 2 modelos de [***yolov8***](https://docs.ultralytics.com/es/), el estándar y uno entrenado por nosotros. El proceso para entrenarlo es el siguiente:

Como no es ideal tener el ordenador trabajando exclusivamente en esto durante varias horas, lo ideal es usar la GPU para entrenarla, para ello, debemos instalar [***CUDA***](https://developer.nvidia.com/cuda-toolkit) y hacer que sea compatible con nuestro environment de anaconda. 

Para ver qué versiones son compatibles con nuestro environment sin tener que realizar pasos adicionales, debemos ejecutar el siguiente comando dentro del ***anaconda prompt***

```
conda search cudatoolkit
```

Lo cual nos devuelve lo siguiente:

<figure>
  <img src="./readmeResources/conda search.PNG" alt="Output comando" title="OutpuT conda search" width="600" height="350">
  <figcaption><strong>Versiones compatibles</strong></figcaption>
</figure>

Como podemos ver, la versión compatible más alta es la 11.8.0, una vez [***descargado***](https://developer.nvidia.com/cuda-11-8-0-download-archive?target_os=Linux) e instalado, debemos realizar el siguiente comando en el ***anaconda prompt*** para instalar pytorch dentro del environment en el que queremos utilizar CUDA

```
conda install pytorch torchvision torchaudio pytorch-cuda=11.8 -c pytorch -c nvidia
```

Una vez instalado todo correctamente, podemos verificar que funciona mediante el siguiente comando de ***pytorch*** 

```
import torch
print(torch.cuda.is_available())
```
Debería de devolvernos True

Ahora que hemos confirmado que tenemos bien emplementado CUDA, pasaremos al entrenamiento del modelo

#### Entrenamiento modelo custom yolov8


