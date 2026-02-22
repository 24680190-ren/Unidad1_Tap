# Unidad1_Tap
Unidad I. 

Interfaz gráfica de usuario .  
1.1 Creación de interfaz gráfica para usuarios.

1.2 Tipos de eventos.

1.3 Manejo de eventos.

1.4 Manejo de componentes gráficos de
control.  
# Introducción
En esta unidad se estudia el desarrollo de interfaces gráficas de usuario, las cuales representan el medio principal de comunicación entre las personas y las aplicaciones digitales. A través de una GUI, el usuario puede interactuar con un sistema mediante elementos visuales como botones, campos de texto, listas, menús y ventanas, lo que facilita el uso del software sin necesidad de conocer comandos complejos. Esto convierte a las interfaces gráficas en una parte esencial para mejorar la experiencia, la accesibilidad y la eficiencia al utilizar programas informáticos.

Durante el desarrollo de la unidad se analizan los fundamentos para construir interfaces, comenzando por la creación de ventanas y la organización de los componentes mediante distintos layouts. Posteriormente, se estudian los eventos que se generan a partir de las acciones del usuario y la forma de manejarlos para que la aplicación responda de manera dinámica. Finalmente, se trabaja con los principales componentes gráficos, sus propiedades y la validación de datos, con el objetivo de crear aplicaciones funcionales, claras e intuitivas. Todo esto se aplica de manera práctica utilizando Flet, que permite diseñar interfaces modernas empleando Python de forma sencilla.

# 1.1 Creación de interfaz gráfica para usuarios.
La interfaz de usuario (UI) es el medio a través del cual una persona se comunica con un dispositivo digital o con un software. Es, en esencia, el puente que conecta al usuario con la tecnología. Cada vez que utilizas una aplicación en tu teléfono, navegas por una página web o trabajas con un programa en tu computadora, estás interactuando con una interfaz que ha sido diseñada para facilitar esa comunicación. Esta interacción ocurre mediante elementos visibles y manipulables como botones, iconos, menús, ventanas, campos de texto, imágenes, colores y sonidos. Todos estos componentes trabajan juntos para permitirte realizar acciones como seleccionar opciones, introducir información, desplazarte por contenidos o ejecutar funciones específicas.

La interfaz no solo se limita a lo que se ve en la pantalla, sino también a la forma en que responde el sistema a tus acciones. Por ejemplo, cuando presionas un botón y cambia de color, aparece un mensaje o se abre una nueva ventana, el sistema te está dando retroalimentación para que sepas que tu acción fue reconocida. Esta comunicación constante entre el usuario y el sistema es fundamental para que la experiencia resulte clara, fluida y comprensible. Sin una interfaz adecuada, incluso el software más potente o funcional puede volverse confuso o difícil de usar.

El diseño de la UI es especialmente importante porque influye directamente en la manera en que percibes y utilizas un producto digital. Una interfaz bien diseñada organiza la información de forma lógica, presenta los elementos de manera ordenada y reduce la complejidad de las tareas. Esto permite que cualquier persona, incluso sin experiencia técnica, pueda aprender a usar la aplicación con facilidad. Cuando la navegación es intuitiva y los controles son claros, se minimizan los errores y se reduce el tiempo necesario para completar acciones, lo que mejora notablemente la eficiencia.

Además, el aspecto visual también cumple un papel relevante. Los colores, las tipografías, el tamaño de los elementos y la disposición del contenido contribuyen a crear una experiencia agradable y profesional. Una apariencia cuidada genera confianza y motiva a seguir usando el producto. Por el contrario, una interfaz desordenada o poco atractiva puede causar frustración y hacer que el usuario abandone la aplicación.

En consecuencia, el diseño de la interfaz de usuario no solo tiene que ver con la estética, sino también con la funcionalidad y la comodidad. Su objetivo principal es lograr que la interacción entre las personas y la tecnología sea natural, eficiente y satisfactoria. Cuando una UI está bien diseñada, el usuario casi no nota su presencia, porque todo funciona de manera sencilla y coherente, permitiéndole concentrarse en lo que realmente quiere hacer.
<br> **Tema: Componentes de una interfaz de usuario en flet** </br>
En Flet, la interfaz se construye completamente con Python. No necesito programar HTML o CSS, sino que el framework ya trae componentes visuales listos para usar. Todo empieza con la página principal, que funciona como la ventana de la aplicación. Esa página es donde se colocan todos los elementos. Vendría siendo el equivalente al frame o formulario en otros lenguajes.

La estructura básica de una app en Flet consiste en una función principal que recibe un objeto llamado page. Con ese objeto puedo cambiar propiedades como el título de la ventana o agregar componentes. Por ejemplo, para crear una ventana sencilla con un texto, escribiría algo así:
```python
import flet as ft

def main(page: ft.Page):
    page.title = "Mi app"
    page.add(ft.Text("Hola mundo"))

ft.app(target=main)
```
Aquí aprendí que page.add() sirve para colocar elementos en la pantalla.

También entendí que para organizar los componentes se usan contenedores, que funcionan como layouts. Si quiero poner elementos uno debajo de otro, uso Column. Esto es útil para formularios, porque primero va la etiqueta, luego el campo de texto y después el botón.
```python
ft.Column(
    controls=[
        ft.Text("Nombre"),
        ft.TextField(),
        ft.ElevatedButton("Guardar")
    ]
)
```
Si quiero que los elementos estén uno al lado del otro, uso Row, que se comporta como un FlowLayout horizontal.
```python
ft.Row(
    controls=[
        ft.ElevatedButton("Sí"),
        ft.ElevatedButton("No")
    ]
)
```
Para organizar cosas en forma de cuadrícula, como una galería o varios botones distribuidos uniformemente, puedo usar GridView. Eso se parece a un GridLayout.

También vi que existe Container, que sirve para agrupar elementos y darles estilo, como fondo, espacio interno, bordes o tamaño. Es útil para que la interfaz se vea más ordenada.
```python
ft.Container(
    content=ft.Text("Caja"),
    padding=20,
    bgcolor="blue"
)
```
Algo importante que anoté es que no solo se trata de que funcione, sino de que se vea bien y sea fácil de usar. Hay que evitar saturar la pantalla, usar textos claros, agrupar elementos relacionados y mantener colores y tamaños consistentes. Si la interfaz es confusa, el usuario se pierde aunque el programa funcione correctamente.

En resumen, en Flet la página es la ventana principal, los controles son los botones, textos y campos, y los layouts se logran con filas, columnas, rejillas y contenedores. Combinando todo eso puedo construir cualquier interfaz gráfica de forma sencilla usando solo Python.
<br> **TEMA 2: Layouts (formas de acomodar elementos): GridLayout,Flexbox/Grid (web)** </br>
Estos son mis apuntes de estudio sobre Layouts (formas de acomodar elementos) y cómo aplicarlos en Flet.

Cuando diseño una interfaz gráfica, entendí que no basta con agregar botones o textos a la pantalla, sino que también debo decidir cómo acomodarlos. A eso se le llama layout. El layout es la forma en que organizo los elementos dentro de la ventana para que todo se vea ordenado, alineado y fácil de usar. Si no uso un buen layout, los componentes pueden quedar amontonados o desordenados, y la aplicación se vuelve confusa.

Primero estudié el GridLayout. Este tipo de distribución organiza los elementos como si estuvieran dentro de una tabla, es decir, en filas y columnas. Cada componente ocupa una posición específica dentro de esa cuadrícula. Me di cuenta de que es muy útil cuando quiero simetría o repetición, por ejemplo, en una calculadora, un teclado numérico, una galería de fotos o un menú con muchos botones del mismo tamaño. La ventaja principal es que todo queda bien alineado y visualmente ordenado.

En Flet no existe algo llamado exactamente “GridLayout”, pero se puede lograr el mismo efecto usando GridView, que acomoda automáticamente los elementos en forma de rejilla. Por ejemplo:
```python
import flet as ft

def main(page: ft.Page):
    grid = ft.GridView(
        expand=True,
        max_extent=120,
        spacing=10,
        run_spacing=10,
        controls=[
            ft.ElevatedButton(f"Botón {i}") for i in range(1, 10)
        ]
    )

    page.add(grid)

ft.app(target=main)
```
Aquí los botones se organizan en forma de cuadrícula y se ajustan solos según el tamaño de la ventana. Esto se parece mucho a un GridLayout tradicional.

Después estudié Flexbox, que es muy usado en diseño web. Este sistema acomoda los elementos en una sola dirección, ya sea horizontal o vertical, y reparte el espacio automáticamente. Lo que más me llamó la atención es que permite centrar, alinear o espaciar los componentes fácilmente, incluso si cambia el tamaño de la pantalla. Es ideal para barras de navegación, filas de botones o listas.

En Flet, Flexbox se parece mucho a usar Row y Column. Row coloca los elementos en horizontal y Column en vertical. Por ejemplo, con Row:
```python
def main(page: ft.Page):
    layout = ft.Column(
        expand=True,
        controls=[
            ft.Container(content=ft.Text("Encabezado"), bgcolor="blue", height=60),
            ft.Row(
                expand=True,
                controls=[
                    ft.Container(content=ft.Text("Menú"), bgcolor="grey", width=120),
                    ft.Container(content=ft.Text("Contenido principal"), expand=True)
                ]
            ),
            ft.Container(content=ft.Text("Pie de página"), bgcolor="blue", height=40)
        ]
    )

    page.add(layout)
```
Aquí los botones se acomodan en línea y el espacio se distribuye automáticamente. Esto funciona como Flexbox horizontal.

Con Column sería vertical:
```python
def main(page: ft.Page):
    columna = ft.Column(
        controls=[
            ft.Text("Correo"),
            ft.TextField(),
            ft.Text("Contraseña"),
            ft.TextField(password=True),
            ft.ElevatedButton("Iniciar sesión")
        ]
    )

    page.add(columna)
```
Esto es perfecto para formularios, porque los elementos se apilan uno debajo del otro.

También aprendí sobre el Grid de la web, que combina filas y columnas al mismo tiempo y permite crear diseños más complejos, como dividir la pantalla en secciones (encabezado, menú lateral, contenido, pie de página). En Flet puedo simular esto combinando Row, Column y Container. Por ejemplo:
```python
def main(page: ft.Page):
    layout = ft.Column(
        expand=True,
        controls=[
            ft.Container(content=ft.Text("Encabezado"), bgcolor="blue", height=60),
            ft.Row(
                expand=True,
                controls=[
                    ft.Container(content=ft.Text("Menú"), bgcolor="grey", width=120),
                    ft.Container(content=ft.Text("Contenido principal"), expand=True)
                ]
            ),
            ft.Container(content=ft.Text("Pie de página"), bgcolor="blue", height=40)
        ]
    )

    page.add(layout)
```
Aquí combino filas y columnas para dividir la ventana en varias áreas, parecido al Grid web.

En resumen, anoté que GridLayout sirve para organizar en forma de tabla, Flexbox para acomodar en una sola dirección de forma flexible, y el Grid web para diseños más completos. En Flet todo esto se logra usando principalmente Row, Column, GridView y Container. Saber combinarlos es clave para construir interfaces limpias, ordenadas y profesionales.
# 1.2 Tipos de eventos
Cuando trabajo con interfaces gráficas entendí que la aplicación no ejecuta todo en orden como un programa tradicional de consola, sino que está esperando a que el usuario haga algo. Cada acción del usuario genera un evento. Un evento es cualquier interacción que ocurre dentro de la interfaz, como hacer clic, escribir, mover el mouse o cambiar el tamaño de la ventana.

Esto se basa en el modelo de programación dirigido por eventos. En este modelo, el programa está “escuchando” constantemente y, cuando detecta una acción, ejecuta una función específica para responder. O sea, no controlo el flujo paso a paso, sino que reacciono a lo que el usuario haga.

Los eventos más comunes que debo conocer son los del mouse, como los clics o cuando se presiona un botón; los del teclado, que detectan teclas presionadas; los eventos de la ventana, como cerrar o redimensionar; y los eventos de formularios, que ocurren cuando el usuario cambia información o envía datos.
En Flet, estos eventos se capturan asignando funciones a propiedades especiales del componente, por ejemplo on_click, on_change o on_submit. Cada vez que se dispara el evento, Flet manda un objeto evento con información sobre lo que pasó.

Por ejemplo, para detectar un clic:
```python
import flet as ft

def main(page: ft.Page):

    def clic(e):
        page.add(ft.Text("Se hizo clic"))

    page.add(ft.ElevatedButton("Botón", on_click=clic))

ft.app(target=main)
```
Aquí el botón genera un evento de mouse y ejecuta la función.

Para detectar cambios en un campo de texto:
```python
def cambio(e):
    print(e.control.value)

ft.TextField(on_change=cambio)
```
Esto me permite saber qué está escribiendo el usuario.

Si quiero detectar teclas:
```python
def teclado(e: ft.KeyboardEvent):
    print("Tecla presionada:", e.key)

page.on_keyboard_event = teclado
```
Así sé qué tecla se presionó.
 #1.3 Manejo de eventos.
<br>Después de entender qué es un evento, aprendí que el manejo de eventos consiste en decidir qué va a hacer el programa cuando ocurra ese evento. Es decir, no solo detectarlo, sino programar la respuesta.</br>

<br>Para manejar eventos se usan funciones llamadas handlers o listeners. Estas funciones se ejecutan automáticamente cuando ocurre la acción. En Flet, simplemente creo una función y la paso como parámetro del evento.</br>

<br>Por ejemplo, si quiero que un botón cambie un texto:</br>
```python
def main(page: ft.Page):

    mensaje = ft.Text("Hola")

    def cambiar(e):
        mensaje.value = "Botón presionado"
        page.update()

    boton = ft.ElevatedButton("Cambiar", on_click=cambiar)

    page.add(mensaje, boton)
```
<br>Aquí el evento modifica la interfaz en tiempo real. Aprendí que cuando cambio propiedades debo usar page.update() para refrescar la pantalla.</br>

<br>También puedo habilitar o deshabilitar componentes según eventos. Por ejemplo, activar un botón solo cuando el usuario escriba algo:</br>
```python
def main(page: ft.Page):

    boton = ft.ElevatedButton("Enviar", disabled=True)

    def escribir(e):
        boton.disabled = (e.control.value == "")
        page.update()

    entrada = ft.TextField(on_change=escribir)

    page.add(entrada, boton)
```
<br>Esto hace la aplicación más interactiva y evita errores.</br>

<br>Otra cosa importante es que el objeto evento trae información útil. Por ejemplo, e.control me dice qué componente generó el evento, e.control.value el valor actual, y en eventos de teclado e.key la tecla presionada. Con esto puedo tomar decisiones más específicas.</br>

<br>En resumen, primero debo entender qué tipos de eventos existen y luego aprender a manejarlos asignando funciones que respondan a cada acción. En Flet esto es muy directo porque cada control ya trae sus propiedades de eventos. Gracias a esto la interfaz deja de ser estática y se vuelve dinámica, respondiendo a todo lo que hace el usuario.</br>

# 1.4 Manejo de componentes gráficos de control.
 
Cuando hablo de manejo de componentes gráficos me refiero a trabajar directamente con los elementos visuales de la interfaz, es decir, todo lo que el usuario puede ver y manipular. No solo se trata de colocarlos en la pantalla, sino también de controlar su comportamiento, modificar sus propiedades y hacer que reaccionen a lo que el usuario hace. En esta parte ya no solo diseño la estructura, sino que hago la interfaz interactiva y funcional.

Primero identifiqué los componentes más comunes que se usan casi en cualquier aplicación. Las etiquetas o Label sirven para mostrar texto informativo. Los botones permiten ejecutar acciones. Los campos de texto o TextField permiten que el usuario escriba datos. Los Checkbox sirven para seleccionar opciones múltiples. Los RadioButton permiten elegir solo una opción dentro de un grupo. Los ComboBox o desplegables muestran varias opciones en una lista compacta. También existen listas para mostrar elementos repetidos y tablas para mostrar datos organizados en filas y columnas.

En Flet, cada uno de estos componentes ya viene como un control listo para usar. Por ejemplo, una etiqueta se crea con Text:
```python
ft.Text("Bienvenido al sistema")
```
Un botón se crea con ElevatedButton:
```python
ft.ElevatedButton("Guardar")
```
Un campo de texto:
```python
ft.TextField(label="Nombre")
```
Un checkbox:
```python
ft.Checkbox(label="Aceptar términos")
```
Un grupo de opciones tipo radio:
```python
ft.RadioGroup(
    content=ft.Column([
        ft.Radio(value="M", label="Masculino"),
        ft.Radio(value="F", label="Femenino")
    ])
)
```
Un desplegable (ComboBox) se puede hacer con Dropdown:
```python
ft.Dropdown(
    options=[
        ft.dropdown.Option("México"),
        ft.dropdown.Option("Colombia"),
        ft.dropdown.Option("Argentina")
    ]
)
```
Después aprendí que cada componente tiene propiedades que puedo modificar. Estas propiedades controlan el tamaño, color, texto, visibilidad o si está habilitado o no. Por ejemplo, puedo cambiar el ancho y alto, el color de fondo o el texto que muestra.
```python
ft.Container(
    content=ft.Text("Caja"),
    width=200,
    height=100,
    bgcolor="blue",
    alignment=ft.alignment.center
)
```
Otra parte importante es la validación de datos. Esto significa comprobar que lo que el usuario escribe sea correcto antes de procesarlo. Por ejemplo, verificar que un campo no esté vacío o que la edad sea un número. En Flet puedo hacerlo usando eventos como on_change o on_submit.
```python
def main(page: ft.Page):

    resultado = ft.Text()

    def validar(e):
        if e.control.value.isdigit():
            resultado.value = "Edad válida"
            resultado.color = "green"
        else:
            resultado.value = "Solo números"
            resultado.color = "red"
        page.update()

    edad = ft.TextField(label="Edad", on_change=validar)

    page.add(edad, resultado)
```
Aquí el programa revisa el contenido y muestra un mensaje dependiendo si es válido o no.

En resumen, el manejo de componentes gráficos consiste en crear los controles, modificar sus propiedades y hacer que respondan a eventos. En Flet todo se hace manipulando objetos como Text, Button, TextField, Checkbox, Dropdown o DataTable. Saber usar bien estos componentes es clave para construir aplicaciones claras, funcionales y fáciles de usar.
# Aplicación de los conocimientos 
En el siguiente enlace se encuentra la forma en que aplicque los conocimientos obtenidos en esta unidad 

# Conclusión 
En conclusión, el estudio de las interfaces gráficas de usuario permite comprender cómo construir aplicaciones más amigables y fáciles de usar. No se trata únicamente de colocar elementos visuales en la pantalla, sino de organizarlos correctamente, controlar su comportamiento y hacer que reaccionen a las acciones del usuario mediante eventos. La combinación de layouts, componentes y manejo de eventos es lo que da vida a una aplicación interactiva.

Además, trabajar con herramientas como Flet facilita el aprendizaje, ya que permite implementar ventanas, botones, formularios y validaciones de manera práctica y directa, ayudando a entender mejor cómo funciona la interacción entre el usuario y el sistema. Gracias a estos conocimientos es posible desarrollar aplicaciones más ordenadas, funcionales y profesionales, mejorando la experiencia del usuario y garantizando que el software cumpla su propósito de forma eficiente.
# Bibliografias

1. https://www.lenovo.com/mx/es/glosario/que-es-la-interfaz-de-usuario/?orgRef=https%253A%252F%252Fwww.google.com%252F&srsltid=AfmBOopAV_yO2-X5NNB2UV15sSjeszaNqV6FS_Wf4QPJoN50Zsu4Cmk8
2. https://youtu.be/MpkTYMzhV0A?si=EIhgzrEN1-eg3Hc2
3. https://es.scribd.com/presentation/812394937/Clase-Digu
4. https://docs.flet.dev/controls/button/
5. https://docs.flet.dev/controls/row/
6. https://docs.flet.dev/controls/container/
7.https://docs.flet.dev/controls/column/
8. https://docs.flet.dev/controls/gridview/
9. https://developer.mozilla.org/es/docs/Learn_web_development/Core/Scripting/Events
10. https://keepcoding.io/blog/que-son-los-eventos-en-los-web-components/
11. https://youtu.be/XVgA-kMkOdo?si=0DzZQ6QAfLLEBh9f
12. https://docs.flet.dev/controls/checkbox/
13. https://docs.flet.dev/ads/types/paidadevent/


