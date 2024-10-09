# VC_P2 Carlos Tomás Quevedo Olivares

Para el desarrollo de esta práctica he reutilizado el envirorment de la práctica 1. Ha sido necesario instalar la libreria de mediapipe para la última tarea.

# Tarea 1
Realiza la cuenta de píxeles blancos por filas (en lugar de por columnas). Determina el valor máximo de píxeles blancos para filas, maxfil, mostrando el número de filas y sus respectivas posiciones, con un número de píxeles blancos mayor o igual que 0.95*maxfil.

Para esta tarea tan solo he he tenido que modificar el parametro que determina el eje sobre el cual actua la función que cuenta los pixeles blancos de la ya proporcionada en la práctica para contar los pixeles de las columnas. Es decir, en la función "row_counts = cv2.reduce(canny, 1, cv2.REDUCE_SUM, dtype=cv2.CV_32SC1)" lo que era un 0 antes y actuaba sobre el eje x ahora es un uno y actua sobre el eje y. Calcular el número máximo de pixeles blancos en una fila con la función de la libreria numpy de python para el vector que almacena los pixeles de cada fila, y multiplicarlo por 0,95 para obtener el valor con el que vamos a seleccionar las filas que superen o igualen ese valor que representa el numero de pixeles blancos.
Finalmente se imprimen los datos solicitados por pantalla.

# Tarea 2
Aplica umbralizado a la imagen resultante de Sobel (convertida a 8 bits), y posteriormente realiza el conteo por filas y columnas similar al realizado en el ejemplo con la salida de Canny de píxeles no nulos. Calcula el valor máximo de la cuenta por filas y columnas, y determina las filas y columnas por encima del 0.95*máximo. Remarca con alguna primitiva gráfica dichas filas y columnas sobre la imagen. ¿Cómo se comparan los resultados obtenidos a partir de Sobel y Canny?

Aplicamos umbralizado a la imagen resultante de Sobel reutilizando las funciones ya disponibles en la practica. Para el recuento de pixeles blancos por filas y columnas se reutiliza el codigo de la tarea anterior cambiando el nombre de las variables.

# Tarea 3
Proponer un demostrador que capture las imágenes de la cámara, y les permita exhibir lo aprendido en estas dos prácticas ante quienes no cursen la asignatura :). Es por ello que además de poder mostrar la imagen original de la webcam, incluya al menos dos usos diferentes de aplicar las funciones de OpenCV trabajadas hasta ahora.

Seguimos los pasos para umbralizar el frame de la camara y lo mismo para el detector de bordes Sobel usando para ello las funciones que hemos aprendido de OpenCV. Una vez hecho esto se muestran por pantalla todos los resultados al mismo tiempo junto a la imagen original.

# Tarea 4
Tras ver los vídeos [My little piece of privacy](https://www.niklasroy.com/project/88/my-little-piece-of-privacy), [Messa di voce](https://youtu.be/GfoqiyB1ndE?feature=shared) y [Virtual air guitar](https://youtu.be/FIAmyoEpV5c?feature=shared) proponer un demostrador reinterpretando la parte de procesamiento de la imagen, tomando como punto de partida alguna de dichas instalaciones.

Para esta tarea inspirandome en el video de Virtual air guitar y la detección de manos me parecio ocurrente desarrollar un detector de peinetas que las censure cuando aparecen en camara. Para ello comence a buscar una libreria para la detección de manos y en este video https://www.youtube.com/watch?v=_zjKszdAVG8&t=600s encontre la libreria de mediapipe y una pequeña implementación que utilizaba la deteccion de manos para contar los dedos levantados. Familiarizandome un poco con la libreria y modificando la clase para que me detecte cuando se levanta solo el dedo corazón desarrolle la tarea. 

El codigo utiliza la función encontrarmanos() para detectar si hay manos en el frame, a continuación detecta y devuelve la posición de las manos en el frame junto a un vector que segmenta las partes de la mano en diferentes puntos, con la funcion dedosarriba() haciendo uso del vector mencionado según la posición en el frame de los puntos en los que se ha segmentado la mano se detecta si hay dedos levantados o no, y cuales, finalmente con la función corazón arriba me aseguro de que solo el anular este levantado gracias al vector que devuelve dedosarriba(). Si se detecta una peineta pinta de negro la posición en la que se ha encontrado.
