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

+ Si el componente está fuera de Ladybug y Honeybee, puedes también presionar y sostener ctrl + alt al mismo tiempo para activar el modo informativo. Esto te muestra la ubicación en el menú de los componentes que ya se encuentran en el lienzo. Desafortunadamente, para Ladybug y Honeybee, esto solamente indicará hacia un componente Python.

+ Un método alternativo para componentes dentro de Ladybug y Honeybee es hacer doble clic en el ícono del componente de Ladybug o Honeybee, lo que abrirá el código en su interior. Posteriormente, debes desplazarte hasta encontrar la línea que empieza con 'ghenv.Component.SubCategory =' la cual deberá estar seguida por algo parecido a '07|Energy|Schedule'. Esto funciona de la misma manera que la dirección anterior, así que en este caso sabemos que el componente está ubicado en la pestaña 7 bajo 'Energy' y que se llama Honeybee_Schedule.

+ Si prefieres ver nombres en vez de íconos, también es posible acceder a la pestaña 'Display' en la barra de menú de Grasshopper y modificar la opción 'Display Icons', de manera que se desplegará el nombre del componente en vez del ícono.

+ También es posible hacer doble clic en el lienzo de Grasshopper y empezar a teclear el nombre de un componente para buscar en todas las pestañas de Grasshopper. Todos los componentes de Honeybee y Ladybug incicial ya sea con 'Honeybee' o 'Ladybug', de manera que empezando con alguna de esas palabras clave es una forma de buscar solo dentro de nuestros plugins.

+ Otra herramienta muy útil es el componente 'Bifocals', el cual crea una etiqueta encima de cada componente de manera que sea posible para ti ver tanto el ícono de un componente como su nombre. El componente 'Bifocals' está disponible en <https://www.food4rhino.com/app/bifocals>.

Creando una Definición de Honeybee
----------------------------------

**iii.00** El primer paso para crear cualquier script de Honeybee es *siempre* colocar el componente Honeybee_Honeybee en el lienzo. Esto es importante porque este component contiene múltiples librerías internas que son necesarias para el funcionamiento de casi todos los demás componentes de Honeybee. A diferencia de casi todos los scripts en Grasshopper, no es necesario conectar un cable entre el componente Honeybee_Honeybee y otros componentes; las librerías se activan simplemente al colocarlo en el lienzo. Este componente se localiza en la pestaña '0 Honeybee|Honeybee' y a la acción de colocar este componente en el lienzo se le conoce como 'echar a volar Honeybee'.

![alt text](https://user-images.githubusercontent.com/44324576/49170763-2d197d80-f33d-11e8-96fb-ca46f7fa79df.png)

**iii.01** Muchos componentes de Honeybee funcionan conjuntamente con componentes de Ladybug, así que *casi siempre* es necesario echar también a volar Ladybug. Puedes encontrar el componente Ladybug_Ladybug en la pestaña Ladybug, en la sección 0.

![alt text](https://user-images.githubusercontent.com/44324576/49170767-2db21400-f33d-11e8-8269-ddf02cd3f166.png)

**iii.02** El siguiente paso crucial antes de empezar a crear una simulación es asegurarse que contamos con datos climáticos adecuados en los que se basará nuestra simulación. Para esto requerimos de una conexión a internet. Para empezar, encuentra la sección 0 de Ladybug y arrastra el component 'Open EPD and STAT Weather File' al lienzo.

![alt text](https://user-images.githubusercontent.com/44324576/49170768-2db21400-f33d-11e8-993e-66d13f1727ab.png)

**iii.03** Este componente descargará automáticamente los datos climáticos desde el internet a partir de una URL proporcionada por el usuario. Utilizaremos un componente panel para ingresar la dirección buscada.

![alt text](https://user-images.githubusercontent.com/44324576/49170769-2db21400-f33d-11e8-8461-b6c947b936a5.JPG)

**iii.04** Haz doble clic en el componente panel y pega la siguiente URL, sin espacios antes o después:

+ <https://www.energyplus.net/weather-download/north_and_central_america_wmo_region_4/USA/CA/USA_CA_Van.Nuys.AP.722886_TMY3/all>

Es importante evitar presionar ENTER después de ingresar el texto en el componente panel, ya que Grasshopper interpreta ENTER como la creación de un segunto ítem en la lista de datos dentro del panel. Para aclaraciones sobre listas de datos, consulta el paso 2.20.

Estos datos provienen del Departamento de Energía de los Estados Unidos y corresponden al aeropuerto de Van Nuys, California. Al pasar el cursor sobre este componente es posible obtener más detalles sobre cómo encontrar más datos para otras ubicaciones. De igual manera pueden encontrarse y descargarse directamente del siguiente link: <https://www.energyplus.net/weather>.

El siguiente link contiene información sobre el origen y la generación de estos datos: <https://energyplus.net/weather/sources>.

![alt text](https://user-images.githubusercontent.com/44324576/49170770-2e4aaa80-f33d-11e8-9a83-fa2d5160dc66.JPG)

*Consejo sobre paneles: Utilizaremos paneles para ingresar información frecuentemente. En vez de arrastrar un panel al lienzo cada vez, simplemente haz doble clic en el lienzo y escribe '//' seguido de los datos que quieras introducir en el panel.

**iii.05** Conecta el panel que contiene la URL del archivo de datos climáticos deseados al puerto de entrada 'weatherFileURL' del componente 'Open EPW and STAT Weather Files'. Notarás que el componente 'Open EPW and STAT Weather files' habrá cambiado de naranja a gris, indicando que ha obtenido los datos climáticos sin errores.

![alt text](

**iii.06** Si conectas un panel a la salida 'epwFile' del componente'Open EPW and STAT Weather files' y pasas el cursor por encima del texto 'epwFile', verás que Ladybug ha descargado el archivo EPW y lo ha guardado en tu disco local. La ubicación por defecto es: c:\ladybug.

![alt text](

**iii.07** Estos datos climáticos pueden ahora ser usados para múltiples simulaciones. Concluiremos este tutorial demostrando cómo explorar los datos que acabas de importar. Empecemos arrastranto un componente 'Ladybug_Import EPW" hasta el lienzo.

![alt text](

**iii.08** Posteriormente, conecta los datos que acabamos de descargar a este componente. Esto nos permitirá recorrer los distintos tipos de datos contenidos en el archivo inicialmente importado.

![alt text](

**iii.09** El componente 'Ladybug_Import EPW' deberá cambiar ahora de naranja a gris, indicando que los datos climáticos fueron recopilados sin errores.

![alt text](

**iii.10** Ahora podemos acceder a los distintos tipos de datos contenidos en el archivo EPW, conectemos paneles a los primeros cuatro datos de salida y demos un vistazo más cercano a la información ahora disponible.

![alt text](

**iii.11** El puerto de salida 'readMe!' provee valiosa información acerca de si el componente funcionó correctamente. Esto es particularmente importante si el componete se vuelve naranja, lo que inidica que hubo un error.

![alt text](

*Nota cómo desconectando la dirección URL que hemos ingresado antes afecta estos datos de sallida.

![alt text](

**iii.12** La latitud proveerá la latitud en la que los datos fueron recopilados. Esto es extremadamente importante para confirmar la precisión de la geometría solar.

![alt text](

**iii.13**
