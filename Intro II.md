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

**ii.03** Los componenetes de parámetros sirven para recibir datos de entrada por parte del diseñador; pueden considerarse como cubos vacíos que pueden ser llenados con información. Para crear un componente de parámetro de punto, es necesario dirigirse a la pestaña *Param*, después, dentro de la sección *Geometry* se debe buscar un componente marcado con una 'x' y que despliega el texto 'Point' al pasar el cursor por encima de él. Al dar click izquierdo sobre él y arrastrarlo a nuestro lienzo, éste se convertirá en el inicio de nuestra línea.

![alt text](https://user-images.githubusercontent.com/44324576/49116976-9185ff80-f29f-11e8-8135-317e1668c38f.JPG)

*Nota acerca de la Apariencia: Los componentes en tu computadora podrían tener diferentes íconos en lugar de 'Pt'. Para cambiar esto, ir al menu 'Display' en Grasshopper (al centro de la parte superior) y seleccionar 'Draw Icons'. Además, a menos que el plugin 'Bifocals' la etiqueta 'Point' sobre el componente de punto no será visible. A lo largo de esta guía hemos usado el plugin 'Bifocals' para que puedas ver en cada momento el nombre del tipo de componente. Si deseas instalar 'Bifocals' puedes descargarlo desde* [este vínculo.](https://www.food4rhino.com/app/bifocals)

**ii.04** Repetir el paso anteriorpara crar el segundo parámetro de punto que será utilizado para el final de nuestra línea.

![alt text](https://user-images.githubusercontent.com/44324576/49116783-f725bc00-f29e-11e8-90a8-48d6bf10e9e0.JPG

**ii.06** Cambiar el nombre del primer punto haciendo click derecho en el componente de punto en el lienzo y escribiendo 'Start Point' (sin comillas) en el primer recuadro de entrada. Es una buena práctica mantener el tipo de parámetro en el nombre del componente, como en 'Start Point" o "End Point", en vez de simplemente 'Start' o 'End'. Esto obedece a que los componentes aceptan sólo tipos específicos de datos como entrada, y es importante mantener estos tipos de datos por separado. Un componente que trabaja con puntos no puede aceptar curvas, superficies o sólidos como datos de entrada.

![alt text](https://user-images.githubusercontent.com/44324576/49116787-f7be5280-f29e-11e8-9964-2f000631d239.JPG)

**ii.06** El siguiente paso es llenar nuestro 'cubo' Start Point con un punto. Regresa a Rhino, dibuja dos puntos y remueve de la selección todo al presionar ESC.

![alt text](https://user-images.githubusercontent.com/44324576/49103695-558d7300-f27c-11e8-8a17-c7c33cbd6baf.JPG)

*Nota: Cada pieza de geometría en Rhino es creada con un identificador único, visible en la pestaña de propiedades bajo 'Details'*

**ii.07** Abre el lienzo de Grasshopper y da clic derecho en la parte central del componente 'Start Point'. Selecciona 'Set One Point'.

![alt text](https://user-images.githubusercontent.com/44324576/49116788-f856e900-f29e-11e8-8693-37a53400b0e8.JPG)

**ii.08** Esto hará aparecer la interfaz de Rhino, donde debes seleccionar uno de los puntos que acabas de dibujar. Los puntos de Grasshopper aparecen como 'x' rojas en Rhino por defecto.

![alt text](https://user-images.githubusercontent.com/44324576/49116789-f856e900-f29e-11e8-847c-d3ff4850338c.JPG)

*Nota 1: Si un punto en Rhino ya había sido seleccionado al momento de dar click en 'Set One Point', Rhino podría automáticamente seleccionar tal punto e instantáneamente hacer regresar el lienzo de Grasshopper. De cualquier manera, el componente 'Set One Point' deberá cambiar de naranja a gris, indicando que está recolectando datos adecuadamente.*

**ii.09** A continuación, repite estos pasos para el punto del final. Cambia el nombre del segundo componente de punto a 'End Point'.

![alt text](https://user-images.githubusercontent.com/44324576/49116791-f9881600-f29e-11e8-8b84-a2a50190bffc.JPG)

**11.10** ... y asigna el segundo punto desde Rhino haciendo clic derecho y presionando 'Set One Point'.

![alt text](https://user-images.githubusercontent.com/44324576/49116792-fa20ac80-f29e-11e8-9bc8-a833fec793bf.JPG)

**ii.11** Esto hará aparecer de nuevo la interfaz de Rhino. Selecciona el segundo punto que dibujaste.

![alt text](https://user-images.githubusercontent.com/44324576/49116794-fa20ac80-f29e-11e8-8e23-d3aee454652e.JPG)

**ii.12** Para conectar los dos puntos necesitaremos un nuevo tipo de componente. Dirígete a la pestaña 'Curve', ve hacia la sección 'Primitive' y arrastra un componente de línea al lienzo.

![alt text](https://user-images.githubusercontent.com/44324576/49117443-f8f07f00-f2a0-11e8-84bf-38ad6e431809.JPG)

**ii.13** Grasshopper ejecuta todas las operaciones de izquierda a derecha. El lado izquierdo de los componentes recibe los datos de entrada, mientras que en el lado derecho se arrojan los resultados. Conecta los datos de salida del componente 'Start Point' a los datos de entrada del componente de línea marcado como 'A'. Esto se realiza al hacer clic izquierdo y arrastrando desde un punto de conexión hasta el siguiente. La conexión puede hacerse en cualquier sentido entre dos puntos cualquiera (el cómputo siempre se ejecutará de izquierda a derecha).

![alt text](https://user-images.githubusercontent.com/44324576/49116796-fab94300-f29e-11e8-8822-b7793b1fe592.JPG)

**ii.14** Realiza la segunda conexiín entre 'End Point' y el componente de línea.

![alt text](https://user-images.githubusercontent.com/44324576/49116797-fab94300-f29e-11e8-91a6-302beaa6a4d6.JPG)

**ii.15** Una línea roja debe ahora aparecer entre los dos puntos en Rhino. Esta es solamente una pre-visualización y no será posible seleccionar esta línea en Rhino. Es importante hacer notar que esta línea no ha sido guardada en Rhino y ésta desaparecería cuando Grasshopper fuese cerrado. Este comportamiento ocurre para mantener a Grasshopper corriendo de manera ágil; si toda la geometría generada se guardara inmediatamente en Rhino el programa correría muy lentamente.

![alt text](https://user-images.githubusercontent.com/44324576/49116800-fab94300-f29e-11e8-8a79-568a0be092f5.JPG)
