Sé que todos estamos de acuerdo en que la comunicación es clave en cada

00:05
aspecto posible. ¿Bien? ¿Pero alguna vez te has sentido perdido?

00:08
¿Cómo comunicarse eficientemente con su equipo? Bueno, yo

00:11
tener. Y como desarrollador de software BIM, ya resolví

00:13
este problema para mi equipo, y yo enseñaré

00:15
usted exactamente cómo puede mejorar su flujo de trabajo de comunicación

00:19
usando la magia de los webhooks.

00:21
En este ejercicio, aprenderá cómo construir un

00:23
Aplicación BIM hecha con ese motor abierto para enviar directamente

00:26
mensajes a un canal de Discord para los colaboradores de su proyecto.

00:29
Sí. Captura de pantalla incluida. Finalmente, no más capturas de pantalla hechas a mano de

00:34
su aplicación

00:35
que no sabes dónde poner. Usted tendrá

00:38
sus aplicaciones de comunicación Beeman

00:40
unidos después de esto.

00:42
Ya te estoy escuchando con ganas de empezar a aprender. ¿Bien?

00:45
Bueno, cuantos más recursos, mejor. Déjame decirte

00:48
Abajo de la lección tienes la guía con recursos.

00:51
para saber más, los conceptos claves de la lección, el paso a paso

00:55
paso de implementación del ejercicio,

00:57
el código de implementación completo y la misión para que puedas

01:00
aumenta tu nivel y accede a exclusivas

01:03
beneficios. Todo a sólo 1 clic de distancia. Así que consigue el código

01:07
y construyamos juntos el futuro abierto.

01:11
Bien entonces. Primero lo primero, ¿cómo vamos a

01:14
¿Integrar nuestra aplicación con el canal Discord? y la respuesta

01:17
es mediante el uso de webhooks.

01:19
Básicamente, los webhooks permiten que las aplicaciones se comuniquen en tiempo real, enviando

01:23
datos como si fuera una notificación push.

01:26
Lo bueno es que muchas aplicaciones tienen webhooks, por lo que

01:29
Puedes aplicar prácticamente los mismos conceptos que nosotros.

01:31
Verás aquí cómo enviar datos desde tu aplicación.

01:34
a un chat de proyecto en Slack, por ejemplo, o Microsoft

01:37
Teams o cualquier otra aplicación tipo chat que los tenga.

01:41
Ahora los webhooks deben ser creados por alguien con gestión

01:45
derechos en la aplicación de destino.

01:47
Hidden Discord es tan fácil como ir aquí al

01:49
pestaña de integraciones del canal.

01:51
Puedes nombrar tu webhook como quieras. El nombre

01:54
En realidad no es muy importante, ya que puedes cambiarlo.

01:57
más tarde. Pero de todos modos, hemos creado exitosamente el webhook.

02:01
Entonces, comencemos configurando la aplicación Beam.

02:03
La forma más sencilla es simplemente ejecutar este comando en

02:06
la terminal de su carpeta de trabajo.

02:10
Y desde aquí simplemente seleccione la plantilla básica.

02:13
Ahora como ves, ya tenemos algunos archivos básicos.

02:15
para comenzar a utilizar la aplicación.

02:17
Instalemos todas las dependencias.

02:20
e inicie el servidor de desarrollo.

02:23
Y eso es. Ahora tenemos una aplicación lista para

02:25
para que empecemos a darle forma a nuestras necesidades.

02:28
De hecho, esta plantilla es personalizable, por lo que puedes personalizarla de forma segura.

02:31
ve a este estilo. Archivo CSS y cambiar algunos de

02:34
los colores así.

02:37
Fresco. Así que haz tuya la plantilla.

02:40
Así que ahora es el momento de ensuciarnos las manos.

02:43
Por si no lo sabes, ese motor abierto está compuesto

02:46
de componentes, que son clases de JavaScript que utilizan la interfaz TypeScript para

02:50
garantizar la compatibilidad.

02:52
Todos los componentes suelen tener un conjunto consistente de funciones con

02:55
implementaciones variables.

02:57
Para empezar con el componente, siempre trato de usar

02:59
la misma estructura de carpetas para todos ellos, lo cual es

03:02
exactamente la misma estructura que tenemos en esa empresa abierta.

03:05
La plantilla ya viene con esta carpeta de componentes bin. Entonces

03:09
Dentro, crea otra carpeta con el nombre del componente.

03:13
Integración de Discord en este caso o cualquier otro nombre de

03:16
tu gusto. No hay ningún problema.

03:18
Dentro de esta carpeta, este archivo de índice que estoy creando es donde

03:21
el código principal del componente

03:23
existirá.

03:24
Ahora, si te pillo desprevenido con esto

03:27
repetitivo, déjame explicarte.

03:29
Aquí estoy creando y también exportando la clase que

03:32
representa mi componente.

03:34
En esa empresa abierta, siempre llamamos a los componentes igual

03:37
como carpeta o viceversa para mantener las cosas como

03:39
lo más uniforme posible. Ahora bien, la E también siempre se extiende desde

03:42
la clase de componente Base, pero lo más importante,

03:45
Los componentes están destinados a ser singletons.

03:47
Eso significa no más de 1 instancia del mismo

03:50
El componente debe existir en nuestra aplicación.

03:53
Entonces, ¿cómo garantizamos eso? Bueno, añadiendo nuestro

03:56
componentes a la lista de componentes utilizando este método.

04:00
Ahora, para dejar las cosas aún más claras,

04:02
este componente argumento es básicamente un administrador a cargo de

04:05
contener todas las instancias de componentes de su aplicación y

04:08
Haz algunas otras cosas en segundo plano también. Cómo

04:11
¿Hace un seguimiento de los componentes?, te preguntarás.

04:14
Pues precisamente añadiendo el componente a la lista con

04:17
este método.

04:18
¿Y cómo garantiza que solo tengamos 1 instancia?

04:21
del mismo componente?

04:23
Eso es lo que este UUID

04:25
es para.

04:26
La forma más rápida de conseguir 1 de estos es

04:28
yendo al sitio web del generador de UUID.

04:31
Cópialo desde aquí

04:32
y pégalo en tu código aquí mismo. Es bonito

04:35
Es muy imposible que alguien en el mundo obtenga la misma identificación.

04:39
dos veces. Entonces estamos listos para comenzar. Excelente. Y ahora

04:43
Podemos exportar el componente desde la carpeta.

04:46
Regrese al archivo principal.

04:49
Importar el componente en la parte superior.

04:52
y obtenga una instancia a continuación.

04:55
En este momento ya tenemos nuestro componente

04:58
registrado, pero no hace nada. Así que trabajemos en eso.

05:01
Como te dije antes, el motor viene con algunos

05:04
interfaces que puedes usar para mantener las cosas como

05:06
lo más consistente posible entre los diferentes componentes.

05:09
1 de las interfaces es configurable.

05:12
Básicamente, usamos esta interfaz cada vez que queremos que el componente

05:16
para ser configurado

05:17
una vez que creamos una instancia en la aplicación.

05:20
Ahora la interfaz nos pregunta con un genérico donde

05:23
establecemos el tipo de objeto de configuración que tiene el componente.

05:28
Básicamente, una interfaz con todos los parámetros de configuración posibles en

05:31
el componente.

05:32
Así que creemos la interfaz aquí.

05:35
Normalmente configuro el nombre de la interfaz como el nombre de

05:37
el componente

05:39
y configuración al final.

05:41
La pregunta ahora es qué parámetros de configuración tenemos

05:44
en este componente? Y puede depender, pero en esto

05:47
En este caso, es una URL de webhook.

05:50
Ahora los webhooks funcionan enviando una solicitud de publicación a un sitio proporcionado

05:53
URL, que se llama punto final, desde la aplicación que estamos

05:56
conectarse a, como Discord, para desencadenar acciones específicas como

06:00
enviando mensajes. Te mostraré dónde conseguir el

06:02
URL del webhook en breve, pero por ahora, informemos al configurable

06:06
interfaz sobre el objeto de configuración que usaremos.

06:09
Ahora bien, lo bueno de las interfaces es que te obligan

06:12
tener ciertas cosas en tu clase. Eso es lo que hace

06:15
componentes compatibles entre sí. Esta interfaz configurable en particular requiere 4

06:21
cosas:

06:22
un método de configuración,

06:24
una propiedad de configuración,

06:26
1 evento que debe activarse una vez que el componente ha

06:29
configurado y un valor booleano para usar una vez que

06:32
El componente se ha configurado por primera vez.

06:35
Comencemos definiendo el objeto de configuración. Como ves,

06:38
la propiedad debe haber definido todos los parámetros que configuramos

06:42
en la configuración

06:43
interfaz. Eso es lo que significa este requisito. Así que lo que sea que hagamos

06:47
Lo establecido aquí es una configuración predeterminada del componente.

06:50
Dicho esto, necesitamos definir un webhook predeterminado.

06:52
URL. El caso es que no queremos forzar

06:55
las personas que usan este componente tengan siempre la misma URL.

06:59
Es mejor establecer el valor predeterminado como nulo

07:03
y configurar el componente estableciendo la URL una vez que

07:06
obtener la instancia en la aplicación. Entonces vamos a configurar

07:09
el componente

07:10
y pasar un objeto con la URL.

07:13
¿Pero de dónde obtenemos la URL? En esto

07:15
caso particular usando Discord, obviamente, depende del software

07:18
estás usando,

07:19
está justo aquí en el mismo lugar donde creamos

07:22
el webhook antes.

07:24
Este es el punto final. En otras palabras, ¿la URL

07:27
Discord ha creado para enviar mensajes a través de Internet a

07:31
nuestro canal. Entonces, sí, cualquiera que tenga este enlace y un

07:34
un poco de conocimiento sobre webhooks

07:36
Puedes enviar mensajes libremente al canal, así que mantenlo.

07:39
en mente.

07:40
Ahora solo necesitamos corregir esta URL

07:42
aquí en la configuración del componente y listo.

07:45
Bastante básico. Trabajemos ahora en el método de configuración.

07:48
Como puede ver, el método toma un argumento de configuración opcional.

07:52
Usamos eso para permitir que el desarrollador

07:54
anular el objeto de configuración predeterminado. Así que siempre me gusta

07:57
use la sintaxis extendida aquí para anular la configuración del componente

08:00
con la configuración que viene en el método de configuración.

08:04
Entonces, ¿de qué se trata la configuración? Bueno, depende completamente

08:07
a ti y lo que quieres hacer con esto

08:09
componente que está creando. Lo que quiero en este caso

08:12
es establecer accesores o en otras palabras, captadores y

08:16
establecedores al objeto de configuración. Así que en cualquier momento 1 de los

08:19
las propiedades en el objeto de configuración cambian,

08:22
Algo específico sucede en mi componente. Para configurar el descriptor de acceso

08:25
en la propiedad URL del webhook, puedo hacer lo mismo

08:28
siguiente. Ahora lo más importante al definir los descriptores de acceso es

08:31
el nombre de la propiedad aquí coincide con el nombre de

08:34
la propiedad en el objeto de configuración.

08:37
Y también el valor solicitado en el configurador es el

08:40
Mismo tipo que en la configuración.

08:42
interfaz. Eso es bastante importante.

08:44
Entonces, cuando configuramos la propiedad URL del webhook,

08:47
establecer un interno

08:48
propiedad privada en el objeto de configuración como este.

08:52
Además, en el captador, devolvemos esa propiedad. Eso es

08:55
Parte fácil. Pero aquí viene lo más importante.

08:58
Cuando configuramos la URL del Webhook en un valor distinto de nulo,

09:01
queremos abrir una conexión a ese punto final para que

09:04
podemos enviarle una solicitud. Así que definamos

09:07
aquí una función llamada abrir conexión

09:10
que acepta una URL. Y si el desarrollador establece un

09:13
URL, entonces queremos abrir la conexión a ella.

09:16
Fácil.

09:18
Pero, ¿cómo se supone que vamos a abrir la conexión?

09:21
Bueno, usando XMLHttpRequest

09:24
instancias.

09:25
Esperar. Esperar. Esperar. Si eres un desarrollador experimentado y

09:28
Antes de que saltes de tu servidor, conozco el

09:31
La solicitud HTTP XML se reemplaza básicamente por la API de recuperación.

09:35
Sin embargo, usaré la solicitud HTTP XML solo para

09:39
tener una buena excusa para mostrarte un buen uso

09:41
caso de la función de configuración, que en este caso,

09:44
están utilizando para configurar los descriptores de acceso en el objeto de configuración para

09:46
especificar lo que queremos hacer una vez que la URL del webhook

09:50
La propiedad está establecida.

09:51
Entonces lo que tenemos que hacer es crear el

09:54
Solicitud XMLHttp

09:55
instancia. Así que hagámoslo como una propiedad privada de

09:58
nuestro componente así. Luego de abrir la conexión,

10:02
aquí en la función podemos escribir lo siguiente.

10:05
Entonces, cada vez que configuramos una nueva URL de webhook, esta función

10:08
será invocado y abriremos una conexión

10:11
a esa URL específica.

10:13
Esta conexión específica es de tipo post, lo que significa que

10:16
enviará datos al punto final.

10:19
Así como POST, existen otros tipos de tipos de conexión.

10:22
conocidos como métodos API REST que utilizan los servidores. Tengo

10:26
le guié un recurso sobre eso en la guía de

10:28
Esta lección.

10:29
Ahora bien, aquí viene lo importante. Como somos

10:32
reemplazando esta propiedad del objeto de configuración, necesitamos

10:35
restablecer el valor original que tenía antes de configurar el

10:39
accesores.

10:40
Para hacerlo, sólo es cuestión de crear un

10:42
copia del objeto de configuración

10:45
y luego restablecer el valor inicial de la configuración

10:48
objeto como este.

10:50
Lindo. Ahora podemos habilitar el componente.

10:53
Configure que el componente ya esté configurado, lo que también

10:56
significa que si el componente ya está configurado, entonces

10:59
no hará nada.

11:01
Y finalmente, activar el evento correspondiente para avisar

11:04
En el mundo exterior el componente tiene su configuración.

11:08
listo.

11:09
Fresco. Siguiente paso, cree la función para enviar los mensajes.

11:12
Como único argumento, pidamos el mensaje para

11:15
ser enviado al canal. Bueno.

11:18
Antes, te dije que usamos conexiones de correo para enviar

11:20
datos a los puntos finales del servidor.

11:22
La forma más sencilla de especificarlo es utilizando el

11:25
formar objeto de datos.

11:27
Aquí, podemos usar el método establecido por datos de contenido.

11:30
queremos enviar.

11:32
El caso es que no podemos enviar lo que queramos solo

11:35
como eso. Necesitamos enviar algo que el punto final acepte.

11:39
En otras palabras, la información que enviamos depende enteramente de

11:42
el punto final al que nos estamos conectando. Entonces, ¿cómo hacemos?

11:45
saber qué cosas podemos enviar a un Webhook de Discord

11:47
punto final? Bueno, esta página es un buen recurso.

11:51
Aquí mismo, podemos ver los datos en Discord Webhook.

11:54
activos. Vemos que la clave de contenido es donde está el mensaje.

11:57
se mantenga.

11:58
Por lo tanto, debemos tomar este contenido escrito tal como

12:01
lo es y reescribirlo en el primer argumento de

12:04
el método de envío.

12:06
En el segundo argumento, es sólo el mensaje real que

12:09
quieres enviar, que en este caso es el argumento

12:12
tenemos.

12:13
Bien. Después de haber configurado todas las cosas que queremos

12:16
para enviar a través del webhook, es hora de decirle al

12:18
Solicitud XMLHttp

12:20
instancia para enviar los datos. Eso es muy fácil. Ahora 1

12:23
Lo importante a tener en cuenta es lo siguiente.

12:26
Esta cosa envía los datos al punto final que tenemos.

12:29
configurado al abrir la conexión. ¿Bien? Bueno, si no lo hemos hecho

12:32
configurar la URL todavía, esto arrojará un error que indica

12:36
ese no es un punto final válido para enviar los datos

12:39
a. Es nuestro trabajo simplemente invocar el método de envío.

12:42
si el componente tiene toda la información requerida

12:46
para que podamos configurar estas comprobaciones antes.

12:48
Lindo. Nada demasiado extraño aquí. Sólo estamos lanzando un

12:51
error si el componente aún no se ha configurado y

12:54
devolver la función si el componente no está habilitado o

12:58
no hay ningún webhook

12:59
especificado en la configuración.

13:01
Fresco. Entonces es hora de enviar un mensaje de prueba. Para las pruebas

13:04
propósitos, enviemos un mensaje al canal justo después

13:07
el componente ha sido configurado así.

13:10
Lindo. Tan pronto como guardo el archivo y voy

13:13
al navegador,

13:14
Ese código se activará y deberíamos verlo

13:17
el mensaje en el canal de Discord. Dime que esto no es

13:20
Genial y también suéltalo. Pero bueno, hay 2.

13:23
cosas que pasan aquí. Primero, queremos establecer el

13:26
mensaje directamente desde la aplicación,

13:28
no del código. Y segundo, ¿qué pasa con la captura de pantalla?

13:32
Trabajemos también en eso. Así que como ya sabrás

13:35
Ya sabes, tenemos un conjunto completo de componentes de interfaz de usuario ansiosos.

13:38
para ser utilizado por usted. De hecho, esas mismas UI

13:41
Los componentes son los que tiene la plantilla que estamos usando.

13:44
No es necesario instalarlos. En nuestra empresa abierta, nosotros

13:47
Siempre recomendamos mantener la lógica de sus componentes desconectada.

13:50
desde la interfaz de usuario que los utiliza. De hecho, así es como

13:53
lo hacemos internamente. Para los fines de este componente,

13:56
Creo que con solo 1 botón se activa la funcionalidad.

13:59
y 1 modelo donde el usuario puede personalizar el mensaje

14:02
es más que suficiente. Así que trabajemos en eso.

14:05
Ahora, para mantener las cosas lo más organizadas posible, creemos

14:07
una carpeta de origen dentro de la carpeta de componentes

14:10
y un archivo llamado interfaz de usuario o lo que quieras

14:13
para crear la interfaz de usuario.

14:16
Luego cree un archivo de índice en la carpeta de origen para

14:19
exportar la interfaz de usuario.

14:27
Ahora la razón por la que esto se queja.

14:29
es porque no estamos exportando nada del usuario

14:32
archivo de interfaz ahora mismo. Así que trabajemos en el usuario.

14:35
interfaz.

14:36
Ahora bien, si alguna vez has trabajado con React antes, esto

14:38
Te resultará muy familiar. Con el sistema de interfaz de usuario

14:41
de ese motor abierto, creas una interfaz de usuario como funciones

14:45
que regresa

14:47
Sintaxis HTML. Bueno, en React, no es exactamente sintaxis HTML.

14:50
pero algo llamado JSX. Pero, de todos modos, en nuestro sistema es

14:53
algo muy parecido.

14:55
Si quieres saber más sobre esto, puedes

14:57
consulte este tutorial de nuestra documentación pública,

14:59
que te enseña lo fácil que es crear un estado

15:02
lista y componentes con estado para potenciar su aplicación.

15:05
Además, la misma plantilla que estamos usando en el ejercicio.

15:08
tiene muchos ejemplos de UI creadas con el sistema

15:11
para que puedas comprobarlos.

15:13
La interfaz de usuario para el componente de integración de Discord no es difícil.

15:16
en absoluto, por lo que podemos mantenerlo tan simple como

15:18
una interfaz de usuario sin estado. Eso significa que la interfaz de usuario no necesita

15:22
ser actualizado en cualquier momento ya que toda su información es

15:25
estático.

15:26
Ahora que sé que hay como un millón

15:28
opciones para crear la interfaz de usuario reactiva basada en

15:31
marco que utilizas, mantendré esta parte lo más breve

15:33
lo más conciso posible. Entonces, para empezar, exportemos

15:37
una función como esta

15:38
y devolver un componente como este.

15:41
Ahora bien, esta BUI es prácticamente el alias para eso.

15:44
Abra la interfaz de usuario del motor.

15:49
Lo que quiero es agregar una sección de barra de herramientas personalizada.

15:51
al lado de este 1. Así que aquí en el componente UI,

15:54
Devolveré una sección de la barra de herramientas Beam que tiene un

15:56
botón en el interior.

15:58
Ahora el objetivo del botón es mostrar una

16:00
modelo al usuario. Así que justo arriba,

16:02
creemos un modelo. Adjuntémoslo al documento.

16:06
cuerpo

16:08
y defina un evento de clic en el botón para que

16:10
corta el modelo.

16:13
Bien.

16:14
Además, usemos estos estilos simples para modificar la apariencia.

16:17
del modelo en sí, que no es más que un elemento de diálogo.

16:21
Bueno. Como dije antes, queremos tener un texto.

16:24
entrada en el modelo para permitir al usuario personalizar el

16:26
mensaje a enviar. Así que creemos un texto BIM.

16:29
aporte.

16:31
Agregue la entrada de texto al modelo aquí mismo,

16:34
y agregue otro evento de clic al botón en el

16:37
Modelo para enviar mensajes.

16:39
Fresco. 1 de las mejores cosas de los componentes del motor.

16:42
es que puedes usarlos desde cualquier lugar de tu

16:44
solicitud siempre que tenga acceso a la entrada

16:46
punto. Así que solicitemos aquí los sistemas componentes, que una vez

16:49
nuevamente es el punto de entrada de cualquier aplicación OpenBean,

16:54
y tome de allí la instancia de integración de Discord como esta.

16:57
Recuerde que los componentes son únicos, por lo que esta instancia es la misma

17:01
como el 1 que configuramos en el principal

17:04
archivo. Entonces ahora podemos hacer lo siguiente en el

17:05
Función de envío de mensaje que creamos para el botón. Y

17:08
eso es todo. Bastante simple. Ahora es el momento de agregar la interfaz de usuario.

17:11
a la barra de herramientas. Así que volvamos a lo principal.

17:13
archivo.

17:14
Importar la interfaz de usuario de integración de Discord

17:18
y úselo aquí mismo en la barra de herramientas invocando

17:20
él. Recuerde que esto es una función. Y pasar en el

17:22
instancia de componentes.

17:25
Ahora podremos borrar esto sin ningún problema.

17:28
Y volviendo a la aplicación,

17:30
vemos que aparece el botón en la barra de herramientas, que

17:32
es increíble. Al hacer clic en él, se nos solicita que escribamos un

17:34
mensaje. Podemos configurar lo que queramos aquí. Y como

17:37
Verás, eso es lo mismo que vemos en el

17:40
Canal de Discord, que es genial.

17:42
Ahora casi hemos terminado. ¿Lo que queda? Exactamente. El

17:45
captura de pantalla.

17:46
Para ello, simplemente seguí esta documentación de 3. Js.

17:49
Asombrosamente,

17:50
Es muy fácil. En el método de enviar mensaje desde el

17:53
componente, primero debemos tomar el renderizador del visor. Ahora,

17:56
desde la versión 2 del Open Engine,

18:00
Hemos introducido el concepto de mundos.

18:02
Un mundo es básicamente escena, cámara y, opcionalmente, grupos renderizados.

18:07
donde puedes poner cosas 3d. El punto

18:10
es el renderizador no es parte de los sistemas componentes

18:13
pero parte del mundo que estamos usando para mostrar

18:16
nuestros modelos.

18:17
Eso significa que debemos pedirle al mundo

18:20
cual se va a tomar la captura de pantalla y obtener

18:23
la escena, la cámara y el renderizador fuera de él.

18:27
Ahora, como necesitamos que el renderizador tome capturas de pantalla, pero

18:29
el renderizador es opcional en el mundo, lancemos un

18:32
error en caso de que el mundo proporcionado no tenga un renderizador.

18:35
Ahora estamos seguros de que el mundo tiene un renderizador y

18:37
entonces podemos tomarle el elemento DOM. Ahora

18:40
este elemento DOM es un elemento de lienzo HTML y un lienzo

18:43
Los elementos tienen un método llamado toBlob.

18:46
Cuando se invoca, podemos pasar una devolución de llamada,

18:48
que nos dan acceso al blob generado por el

18:51
función. Ahora bien, para simplificar las cosas, un blob es básicamente

18:54
datos binarios que representan algo, una imagen en este caso. A

18:58
enviar estos datos a través de la web que llama al

19:00
mensaje, necesitamos crear un nuevo archivo a partir de

19:02
el blob y asígnale un nombre.

19:05
Ahora en este caso, el nombre no importa

19:07
honesto. Entonces podría ser una captura de pantalla dot png para

19:10
ejemplo. Sí. Necesitamos establecer la distinción. Es

19:13
siempre PNG

19:14
en el caso de estos webhooks de código.

19:17
Ahora la captura de pantalla será parte de

19:19
el objeto de datos del formulario que hemos creado anteriormente. Entonces vamos

19:22
Ponga lo que hicimos antes dentro de la devolución de llamada y agregue

19:25
la captura de pantalla a los datos.

19:27
En este caso, a diferencia de los datos de contenido, podemos

19:30
Pon el nombre que queramos aquí. Realmente no importa

19:34
porque el webhook sabe que se trata de datos binarios y lo hará

19:37
envíelo solo como archivo adjunto del mensaje. Entonces

19:40
Finalmente, aquí está la parte realmente importante.

19:43
Justo antes

19:44
invocamos el canvasToBlob

19:47
función blob, necesitamos forzar al renderizador a renderizar

19:50
como esto. Eso es sumamente importante porque si no, la imagen

19:54
será negro. Según la documentación de 3 JS I

19:57
te mostré antes, eso se debe a que el navegador borra el lienzo

20:00
en algunos intervalos de tiempo. Así que básicamente estamos forzando

20:03
para renderizar la escena justo antes de tomar la

20:06
captura de pantalla.

20:07
Y eso es prácticamente todo. Antes de hacer la prueba final,

20:10
asegurémonos de que el componente UI acepte un mundo

20:14
y proporcionar el mundo en el archivo principal. Fresco. Tiempo

20:18
para hacer la prueba final.

20:20
Cargaré cualquier modelo.

20:22
Nos acercaremos a esta parte.

20:24
Incluso puedo seleccionar elementos que aparecerán resaltados en

20:27
la captura de pantalla.

20:28
Haga clic en el botón y establezca algún mensaje.

20:32
Envíalo y volviendo a Discord ahí vamos.

20:35
Aquí está el mensaje con la captura de pantalla.

20:37
Muy lindo. Estoy seguro de que impulsarás

20:40
su flujo de trabajo usando esto, y solo ha gastado menos

20:43
¿que qué? ¿20 minutos, tal vez? ¿Degradado?

20:46
Si esto fue genial, ahora imagina la posibilidad de dejar que

20:49
el usuario decide a qué canal quiere enviar

20:52
mensajes. Eso es genial porque entonces puedes enviar un mensaje.

20:55
a un canal de tema específico como estimación de costos o construcción

20:58
seguimiento, por ejemplo. Para hacerlo te invito a

21:01
vea esta búsqueda de lecciones al final de la guía

21:04
lo encuentras debajo del video. Al completar esta misión,

21:07
tendrá la oportunidad de crecer. Te permitirá

21:09
aumenta tu nivel para ganar diferentes insignias y obtener acceso

21:13
beneficio que sólo personas con ciertos niveles pueden alcanzar,

21:16
como obtener recompensas, recompensas en efectivo por contribuir a esa apertura

21:19
bibliotecas de código abierto del motor o regalos especiales. Ahora de esto

21:23
Adelante, las posibilidades son infinitas. Más importante aún, ya

21:27
saber cómo resolver una brecha de comunicación en su proyecto

21:29
equipos conectando sus aplicaciones BIM y de comunicación

21:33
usando la magia de los webhooks

21:35
y componentes de viga en esa abertura.

21:37
Pero haber resuelto este problema me ha llevado a pensar en

21:40
otra cosa. A menudo nos encontramos haciendo comentarios sobre Beam.

21:44
modelos. ¿Bien?

21:45
Especialmente al hacer reseñas,

21:47
Mucha gente toma capturas de pantalla del modelo y las pega en

21:50
un muelle de texto y escriba los comentarios allí. El problema

21:53
¿Tus comentarios se van a perder en algún momento?

21:56
punto. Allí no hay una buena digitalización. yo estaba en ese mismo

22:00
situación anterior. Pero como desarrollador de software Beam, estaba

22:03
Me sorprendió lo fácil que mejoré este proceso usando un

22:06
truco sencillo de 3 gs y te enseñará paso a paso

22:09
paso cómo puedes hacerlo tú también. Entonces en

22:11
En el ejercicio de la próxima semana, aprenderá a construir

22:15
un sistema de comentarios en 3D dentro de su aplicación creado

22:18
sin Open Engine, igual que el 1 que estás viendo

22:20
ahora mismo. Entonces, sí, no más documentos de texto que escribir.

22:24
comentarios del modelo una vez que implemente esto. Así que nos vemos a continuación

22:28
Semana y feliz codificación. Nos vemos.