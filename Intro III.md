Intro III - La Interfaz de Honeybee
===================================

Esta sección cubrirá cómo construir un script muy sencillo de Honeybee desde cero. Comenzaremos con una breve introducción a la interfaz de Honeybee, continuaremos con la creación de una definición básica de Honeybee y finalmente, concluiremos con una lista de convenciones usadas en los scripts de Honeybee- Esta sección te permitirá empezar a expandir de manera independiente tu conocimiento al recorrer la librería de componentes.

La Interfaz de Honeybee
-----------------------

La interfaz de Honeybee organiza los componentes por cada tipo de simulación. La sección 00 es primordialmente par definir la geometría de las zonas en una simulación energética.

![alt text](https://user-images.githubusercontent.com/44324576/49173594-77522d00-f344-11e8-8b38-1faf1714ac00.png)

Las secciones 02-04 son para cálculos de iluminación natural. No utilizaresmos estos componentes en este turorial.

![alt text](https://user-images.githubusercontent.com/44324576/49173589-76b99680-f344-11e8-84e5-aa729d9f1dc8.png)

Las secciones 05-10 son para modelado energético en EnergyPlus. Nos enfocaremos en este tipo de componentes en este tutorial.

![alt text](https://user-images.githubusercontent.com/44324576/49173915-47575980-f345-11e8-8abd-4b181702c279.png)

Los componentes de la sección 11 se emplean para realizar simulaciones en THERM. No utilizaremos estos componentes en este tutorial.

![alt text](https://user-images.githubusercontent.com/44324576/49173595-77522d00-f344-11e8-8b87-9fe09ec4bec0.png)

Los componentes de la sección 12 sirven para actualizar Honeybee y los componentes de la sección 13 son experimentales o están en desarrollo.

![alt text](https://user-images.githubusercontent.com/44324576/49173592-77522d00-f344-11e8-8928-abd3b9476adf.png)

A manera de ejemplo sobre cómo funcionan estos grupos de componentes, consideremos el tutorial en simulaciones energéticas para zona unitaria en EnergyPlus. Este tutorial solamente utiliza componentes de la sección 00, las secciones de energía 05, 06, 07, 08, 09, 10 y la sección de actualización 12. No se utilizan componentes de las secciones 02-04 de iluminación natural, o de la sección 11 de THERM.

![alt text](https://user-images.githubusercontent.com/44324576/49173591-76b99680-f344-11e8-8a88-550f37222797.png)

Ubicando Componentes en Honeybee
--------------------------------

Para ayudarte a localizar componentes, comenzaremos refiriéndonos a ellos usando el nombre de la pestaña de Grasshopper, el nombre o número de la sección y el nombre del componente. Por ejemplo: 'Honeybee|04 Energy Material|Honeybee_EnergyPlus Window Material' significaría que debes buscar en la pestaña 'Honeybee', en la sección 04 que se emplea para especificar materiales en las simulaciones energéticas y finalmente, deberías buscar el nombre 'Honeybee_EnergyPlus Window Material'. También es posible hacer doble clic en el lienzo y escribir 'EnergyPlus Window Material' (sin comillas) y seleccionar de la lista dinámica que aparece.

Si encuentras un componente que no reconoces, hay un par de cosas que puedes hacer:

+ Puedes mover el ratón sobre el ícono en el centro del componente para ver el nombre del componente.
+Si el componente está fuera de Ladybug y Honeybee, puedes también presionar y sostener ctrl+ alt al mismo tiempo para activar el modo informativo. Esto te muestra la ubicación en el menú de los componentes que ya se encuentran en el lienzo. Desafortunadamente, para Ladybug y Honeybee, esto solamente indicará hacia un componente Python.
