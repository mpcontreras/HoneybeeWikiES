Wiki Honeybee Página de Inicio
==============================

Bienvenido al Wiki Oficial de Honeybee, para guías de modelado energético usando Honeybee.

La guía de **Modelado de Zona Unitaria** cubre la creación de geometría apropiada en Rhino, la especificación de datos de entrada y la configuración de un modelo energético, el envío de un modelo energético a un motor de cálculo y la interpretación de resultados de esa simulación. Honeybee utiliza componentes de Ladybug, que es otro plugin *open source* para Grasshopper diseñado para importar, visualizar y analizar gráficamente datos climáticos.

La guía de **Comparación de Estrategias Pasivas** complementa el Modelado de Zona Unitaria, explicando el marco de trabajo que Honeybee emplea para incorporar más niveles de detalle a una simulación. Esta sección enseña cómo estudiar cinco estrategias de diseño comunes y pretende ser un paso intermedio hacia tópicos más avanzados.

En **Tópicos**, el formato de estos tutoriales cambia. En vez de avanzar a través de una serie de instrucciones paso-a-paso, la guía se divide y se enfoca en métodos para referirse a técnicas específicas de modelado y situaciones particulares de diseño. Estas son algunas de las razones para esta transición:

1. Sería imposible para nosotros escibir un solo tutorial secuencial que cumpla las necesidades de cada persona.
2. Los diseñadores buscan frecuentemente métodos para evaluar problemas específicos de diseño, de esta manera la guía puede fungir como un repositorio de métodos / buenas prácticas.
3. Este formato hace mucho más fácil que otros puedan contribuir a la guía.

Vista General del Proceso de Modelado Energético de Honeybee
------------------------------------------------------------

La relación entre Rhino, Grasshopper, Ladybug, Honeybee y los motores de simulación con los que Honeybee se comunica se describe en el diagrama mostrado más abajo. Ladybug es la herramienta más simple de utilizar y provee muchos recursos muy útiles en las fases más tempranas del diseño. Honeybee hace posible involucrarse mucho más a fondo y proveer un análisis más detallado.

![alt text](https://user-images.githubusercontent.com/44324576/51753145-60685680-20b9-11e9-8526-299586429511.png "Proceso de modelado con Honeybee")

Honeybee y Ladybug son ambos necesarios para seguir esta guía, pero no es necesario leer las guías sobre Ladybug antes de proceder. Los fundamentos necesarios acerca de Ladybug serán aquí cubiertos. Si estás solamente interesado en análisis geométrico, Ladybug puede ser soficiente. Por ejemplo, Ladybug puede calcular la dirección de la luz del sol en cualquier momento específico, e incluso el número de horas de luz solar directa impactando un objeto a lo largo del año. Sin embargo, Honeybee es necesario para cualquier cosa que tenga que ver con materiales, como el rastreo de trayectorias para la iluminación natural difusa, tomar en cuenta las ganancias de calor resultante en un espacio, simular variaciones térmicas o estimar los consumos energéticos anuales de un edificio.

![alt text](https://user-images.githubusercontent.com/44324576/49177299-298df280-f34d-11e8-9f48-40bc1bac363c.jpg "Relaciones entre Honeybee y motores de cálculo")

Es importante dejar en claro una distinción: Honeybee en realidad no ejecuta simulaciones. Honeybee es una interfaz que crea instrucciones para que otros programas de software ('motores de cálculo') corran las simulaciones. Hasta noviembre de 2018 Honeybee posee interfaces con cinco motores de cálculo:

1. Radiance para simular iluminación en un punto específico del tiempo
2. Daysim (que utiliza Radiance) para iluminación a lo largo del tiempo
3. EnergyPlus para simulaciones de balances térmicos y modelación de consumos energéticos 
4. OpenStudio para la integración de Radiance y EnergyPlus
5. Therm para simular la conducción de calor y evaluar riesgos de condensación en modelos de construcciones

Para mayor información, es posible consultar la sección *Our Story* en el [website de Ladybug](https://www.ladybug.tools/about.html).

Motor de Cálculo EnergyPlus
---------------------------

Este tutorial tratará primordialmente con el tercer motor de cálculo, EnergyPlus. Técnicamente, estaremos empleando OpenStudio para enviar la simulación a través de EnergyPlus, pero lo importante es comprender que EnergyPlus crea un modelo energético que rastrea el movimiento del calor hacia y desde el edificio. El motor de cálculo EnergyPlus es una inmensa colección de trabajo realizado por **múltiples colaboradores alrededor del mundo y es coordinado por el Departamento de Energía de los Estados Unidos.**

Zonas Térmicas
--------------

Al trabajar en un modelo energético, los edificios son descritos utilizando zonas tridimensionales creadas en un entorno gráfico. Cada zona representa un espacio térmicamente distinto. Por lo tanto, un edificio puede ser tratado como una sola zona térmica, o puede ser estudiado más a detalle al descomponerlo y caracterizar cada espacio interior como una zona térmica independiente. Honeybee incluye herramientas para crear estas zonas a partir de geometría tridimensional modelada en Rhino. Cada zona es modelada como una forma 3D, delimitada por múltiples superficies que encierran un volumen; Honeybee asigna propiedades físicas para cada una de estas superficies. Las ventanas y puertas son tratadas como sub-elementos que 'pertenecen' a una superficie específica dentro de una zona.

Las zonas son la únidad básica de análisis. Para rastrear el calor que se desplaza desde y hacia cada zona, a través de un periodo de tiempo (i.e. un año completo), la simulación correrá en pasos de tiempo (i.e. intervalos de 10 minutos). A medida que una simulación va siendo ejecutada, características específicas serán calculadas y asignadas para cada uno de estos pasos de tiempo. Por ejemplo, es posible referirse a los datos climáticos para simular las condiciones en el exterior de una zona, como la temperatura hora-por-hora del aire exterior. También podemos simular condiciones en el interior de la zona, empleando datos de entrada como horarios de ocupación o de utilización de equipamiento. Es posible también especificar cómo el equipamiento responderá a estas condiciones interiores y exteriores, por ejemplo especificando temperaturas de consigna interiores.
