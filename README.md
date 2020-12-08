# APP-PRACTICA-6


### Crear el proyecto con dos Activities  


<img src="img\1.JPG"/>        
<img src="img\2.JPG"/>
<img src="img\3.JPG"/>

+ Cree la segunda Activity yendo al panel Project > Android y dar clic derecho sobre la carpeta app de su proyecto y dar a New > Activity > Empty Activity, nombre este activity como Segunda

<img src="img\4.png"/>
<img src="img\4.JPG"/>


 ### Diseñando la primera Activity

 Se crea el diseño de la interfaz de usuario para la aplicación Dos Actividades en el editor
de diseño mediante las características ConstraintLayout.

### Detallando las propiedades del activity_main

+ Abra activity_main.xml desde el panel Proyecto > Android si aún no está
abierto. Si la pestaña Design (diseño) aún no está seleccionada, haga clic en ella.


+ A continuación, se le presenta la estructura del activity, su trabajo será diseñar
en base a lo mostrado, es posible que no obtenga el mismo diseño solicitado,
pero se le recomienda explorar al momento de crear, es libre de diseñar a su
manera, pero cuidando la estructura otorgada.


Estructura del activity_main, observe que al lado del tipo de elemento se establecen los
identificadores posibles, es libre de cambiar ese identificador. Luego dentro de cada
elemento se muestra el posible valor del texto.

De forma generalizada, se ve que las dos pantallas agrupan las vistas usando
ConstraintLayout, le corresponde diseñar con mucho empeño para obtener un buen
resultado. Tenga en cuenta que los EditText se les establece la propiedad hint y no la
propiedad text, en el caso de que la propiedad text disponga de algún valor establecido
debe borrarse.

<img src="img\6.JPG"/>


<img src="img\9.JPG"/>
<img src="img\10.JPG"/>

A como se puedde apreciar en la imagen ya tenemos la estructura de nuestra aplicación web agregando primeramente los contenedores en los 2 archivos XML
(constraint layount) con sus respectivas restricciones ademas de los botones text view y lo demas .



+ Establezca la propiedad visibility a invisible a los TextView del activity_main,
estos serán activados en el momento en que la segunda activity le mande un
resultado, en primera instancia están ocultos.

<img src="img\11.JPG"/>
<img src="img\12.JPG"/>


+ Establezca el evento onClick al botón del activity_main que tiene el
identificador btEnviar, puede usar el siguiente código XML. Puede usar la
corrección automática para generar el código correspondiente a este manejador
de evento.

<img src="img\13.JPG"/>

+ En el caso de que no pueda generar el método a través de las correcciones
automáticas, tiene la siguiente estructura 
<img src="img\14.JPG"/>

###  Agregando un Intent al MainActivity.kt

+ Abra el fichero MainActivity.kt
<img src="img\15.JPG"/>

+ Agregue un object companion dentro de la clase MainActivity, no dentro de
algún método, este servirá para simular un objeto estático que no cambia el valor
de sus propiedades en toda la aplicación. El valor EXTRA_MESSAGE nos
servirá para la clave del extra en el intent.

<img src="img\16.JPG"/>

+ Agregue el siguiente código en el método lanzarSegundaActivity, relacionado a
la creación de un intent.

<img src="img\18.JPG"/>



+ Muestre el resultado en el momento en que la segunda activity fue lanzada

<img src="img\19.JPG"/>
<img src="img\20.JPG"/>

+ Regrese a la activity principal e indique que instancias del ciclo de vida del
activity se han ejecutado



###  Compartiendo datos de Activity principal a la segunda

En la tarea anterior, agregó un intent explícito a MainActivity que lanzó SecondActivity.
También puede usar un intent para enviar datos de una activity a otra mientras la inicia.
Los extras de intent son pares clave/valor en un paquete (Bundle). Un paquete (Bundle)
es una colección de datos almacenados como pares clave/valor. Para pasar información
de una actividad a otra, coloque claves y valores en el paquete adicional de intención de
la actividad de envío y luego vuelva a obtenerlos en la actividad de recepción.

+ Agregue el siguiente código para enviar datos activities, debe reemplazar el
código anterior del método lanzarSegundaActivity. Muetre los resultados

<img src="img\21.JPG"/>


### Modificando la segunda activity para obtener los extras

+ Abra el fichero Segunda.kt para agregar código al método onCreate()
+ Obtenga el intent que activó esta activity

<img src="img\22.JPG"/>

+ Obtenga la cadena que contiene el mensaje de los extras de Intent usando el
valor del objeto creado en la activity principal y obtenerlo usando la clave
MainActivity.EXTRA_MESSAGE: 

<img src="img\23.JPG"/>


+ Use findViewById() para obtener la referencia del TextView para el mensaje
del layout

<img src="img\24.JPG"/>

+ Establezca el texto del TextView con la cadena obtenida del extra del intent

<img src="img\25.JPG"/>


+ Ejecute la aplicación. Cuando escriba el mensaje en el MainActivity, haga clic
en el botón Enviar, se lanza la SegundaActivity y se muestra el mensaje
+ Muestre resultados a través de capturas de pantalla y comentarios
<img src="img\26.jpg"/>

<img src="img\27.jpg"/>

A como se puede apreciar en las capturas de pantallas escribimos un mensaje en el plain text y al momento de dar click en el boton enviar ese mensaje es enviado a la segunda plantilla .

### Devolver datos al activity principal

Ahora que tiene una aplicación que lanza una nueva activity y le envía datos, el paso
final es devolver los datos de la segunda activity a la actividad principal. También usa
un intent y extras de intención para esta tarea. 

+ Abra el fichero activity_segunda.xml y verifique que dispone de la estructura
indicada al principio de estas tareas con sus identificadores correspondientes.

+ Establezca el evento onClick al botón con identificador btRes, si lo hace en el
XML lo puede realizar de esta manera:


<img src="img\28.JPG"/>

+ Paso opcional por si no hizo el anterior: Si desea establecer el manejador del
evento Clic a través de código Kotlin en el método onCreate()

<img src="img\29.JPG"/>

+ Solamente queda crear el método devolverRespuesta(), el cual puede agregarlo
después del cierre de llave del método onCreate()

<img src="img\30.JPG"/>


### Crear respuesta del intent en la segunda Activity
Los datos de respuesta de la segunda actividad a la actividad principal se envían en un
Intent extra. Construye este intent de retorno y coloca los datos en él de la misma manera
que lo hace para el intento de envío.

+ Abre Segunda.kt por si aún no lo está

+ Agrega un companion object para obtener una sola instancia de objeto sin
necesidad de crear una nueva, esto se debe agregar después de la apertura de la
llave de la clase Segunda, al inicio para no generar confusiones

<img src="img\31.JPG"/>

+ Agregue el código del método devolverRespuesta() creado en la tarea anterior


<img src="img\32.JPG"/>

### Obtener la respuesta en el MainActivity y mostrarlo en el TextView

Cuando usa un intent explícito para iniciar otra activity, es posible que no espere
recuperar ningún dato; solo está activando esa actividad. En ese caso, use startActivity()
para iniciar la nueva activity como lo hizo anteriormente en esta práctica. Sin embargo,
si desea recuperar datos de la activity activada, debe iniciarla con
startActivityForResult().

En esta tarea, modifica la aplicación para iniciar Segunda Activity esperando un
resultado, para extraer los datos devueltos del Intent y para mostrar esos datos en los
elementos TextView que creó en la última tarea.

+ Abra el fichero de MainActivity.kt
+ Borre o comente la línea de startActivity(intent) a startActivityForResult(intent,
TEXT_REQUEST), recuerde que TEXT_REQUEST está dentro del companion
object

<img src="img\33.JPG"/>

+ Pasaremos a anular el método onActivityResult(), vamos a Code > Override
methods o simplemente CTRL + O, busque el método onActivityResult()
<img src="img\34.png"/>

+ Agregue el siguiente código a este método para obtener el extra y establecer en
el TextView indicado para esto que se identifica con datoRecibido.

<img src="img\34.jpg"/>

 Ahora cuando envíes datos de la segunda Activity hacia la principal, deberías de
obtener el mensaje.


<img src="img\35.jpg"/>

<img src="img\36.jpg"/>
<img src="img\37.jpg"/>



### Crear el activity de Scrolling
Muestra el componente de interfaz de usuario de ScrollView. ScrollView es un
ViewGroup que en este ejemplo contiene un TextView. Muestra una página de texto
larga, en este caso, una reseña de un álbum de música, que el usuario puede desplazarse
verticalmente para leer deslizando el dedo hacia arriba y hacia abajo. Aparece una barra
de desplazamiento en el margen derecho. La aplicación muestra cómo puede usar texto
formateado con etiquetas HTML mínimas para configurar el texto en negrita o cursiva, y
con caracteres de nueva línea para separar párrafos. También puede incluir enlaces web
activos en el texto.

o Agregue un nuevo Activity dando clic derecho en la carpeta app o en res en el
proyecto



<img src="img\39.JPG"/>

<img src="img\40.JPG"/>

<img src="img\38.JPG"/>

<img src="img\41.JPG"/>

Estructura de SCROLLING

<img src="img\42.jpg"/>

<img src="img\43.jpg"/>

<img src="img\44.jpg"/>


+ El texto es aleatorio, puede usar alguno de Wikipedia o un generador de texto,
pero debe cumplir con un título del artículo, un subtítulo, Texto con saltos de
línea
+ Es opcional agregar el botón regresar, pero para pruebas puede agregarlo y
generar su manejador del evento clic y mandar a llamar al método finish(), para
que observe que puede manipular el regreso, aunque también lo puede hacer con
el botón de retroceso
+ Deslícese hacia arriba y hacia abajo para desplazarse por el artículo y observe
que el subtítulo ahora se desplaza junto con el artículo mientras el título
permanece en su lugar. Esto se debe a que el título está fuera del ScrollView


### Agregue un Activity Aritmética

Con este Activity se pondrá a prueba todo lo aprendido hasta el momento, constará de
dos EditText, de los cuales tomará sus valores, los convertirá a entero y obtendrá la suma
de estos dos valores, los cuales serán mostrados mediante un Toast y en un TextView.
Esta Activity estará conectada a la Segunda Activity, la cual será llamada desde el botón
Sumar.

La estructura debe seguirse a como se demuestra a continuación:

<img src="img\45.JPG"/>

<img src="img\46.JPG"/>

+ Agregue un nuevo Activity, yendo a la carpeta res, dar clic derecho sobre ella e
ir a New > Activity > Empty Activity.

<img src="img\47.JPG"/>


+ Utilice la estructura mostrada con anterioridad, agregando los elementos
necesarios con sus identificadores correspondientes
<img src="img\49.jpg"/>









