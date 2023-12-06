# Práctica 6: Análisis facial

**Autores:** José Manuel Hernández Aparicio & Sheila Cazorla Rodriguez

Durante el desarrollo de esta práctica, exploramos diversas funcionalidades de [***DeepFace***](https://github.com/serengil/deepface) y nos centramos en dos funciones clave que consideramos relevantes para nuestros objetivos. A continuación, detallamos nuestras observaciones y decisiones.

## 1. Función Stream
La función *stream* de DeepFace captó nuestra atención inicialmente debido a su capacidad para reconocer expresiones faciales, edad y sexo.

## 2. Función Find
Sin embargo, tras una evaluación más detallada y considerando nuestro objetivo específico de encontrar la persona más parecida en un conjunto de datos, nos inclinamos hacia la función *find* de DeepFace. Aunque esta función no proporciona información detallada sobre expresiones faciales, edad o sexo, nos brindó la capacidad esencial de analizar imágenes y encontrar características faciales más parecidas a la fuente de origen, en este caso, la cámara web.

Después de decidirnos por la función *find* de DeepFace, procedimos a implementar un programa que determina a qué personaje te pareces con dos modos en los que se puede alternar dándole a la tecla 'm', siendo el primer modo de personajes de Juego de Tronos y el segundo de personajes del universo Marvel. Para iniciar el análisis y encontrar el personaje al que te pareces, simplemente se debe presionar la tecla 's' (puede que haya que darle un par de veces). Esto activará el análisis facial utilizando la función *find* de DeepFace y proporcionará al usuario una respuesta personalizada basada en la similitud facial encontrada en el conjunto de datos.

Para asegurarnos del funcionamiento, creamos un dataset de nosotros y nuestro grupo de amigos, y una vez comprobamos este, continuamos con el desarrollo del programa. También, para asegurarnos, pusimos una foto del único e inigualable Josito en el repertorio de Marvel.
