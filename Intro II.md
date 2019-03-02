Introducción II - La Interfaz de Grasshopper
--------------------------------------------

En esta breve introducción a Grashopper presentaremos cómo Grasshopper difiere de Rhino y cómo trabajar con listas de datos para crear la geometría de un modelo. Este ejemplo utiliza dos listas de puntos para crear una serie de líneas.

Grashopper es un lenguaje visual de escritura que está disponible a manera de *plugin* para Rhino 5.0 y se incluye como default a partir de Rhino 6.0. Grasshopper crea geometría en Rhino extactamente de la misma manera como la interfaz de Rhino crea geometría, con la excepción de que Grasshopper utiliza listas de datos de entrada en lugar de información introducida a mano. Por ejemplo, para definir una línea entre dos puntos en Rhino, sería necesario teclear 'line' en la línea de comandos de Rhino y después, proveer dos puntos.

![alt text](https://user-images.githubusercontent.com/44324576/49101914-afd80500-f277-11e8-94aa-1774b9f9ae24.jpg)

**ii.00** Para crear la misma línea entre dos puntos en Grasshopper, es necesario crear dos listas de puntos en Grasshopper, colocar un punto en cada lista, y finalmente conectar estas listas con un componente 'line'.

![alt text](https://user-images.githubusercontent.com/44324576/49102500-46f18c80-f279-11e8-826f-ef1b23d084b1.png)

**ii.01** Para crear esta definición desde cero, es necesario instalar Grasshopper. Después, teclear 'Grasshopper' en la línea de comando en Rhino para inicializar el programa.

![alt text](https://user-images.githubusercontent.com/44324576/49103686-53c3af80-f27c-11e8-98b5-6d59251de1be.JPG)

**ii.02** Esto activará la interfaz de Grasshopper. Las pestañas en la parte superior (Params, Maths, Sets, Vector, Curve, etc.) contienen componentes que pueden ser arrastrados en el área de trabajo de la parte inferior, también denominada el "lienzo". Los componentes son los elementos fundamentales para la construcción gráfica de algoritmos, es posible considerar a los componentes como si fuesen trabajadores con un enfoque limitado y altamente especializado,realizando una sola tarea a la vez. Las pestañas de Grasshopper ordenan los componentes disponibles de acuerdo con el tipo de tareas que desempeñan.

![alt text](https://user-images.githubusercontent.com/44324576/49116780-f68d2580-f29e-11e8-9e16-06e0622e8fcd.JPG)
