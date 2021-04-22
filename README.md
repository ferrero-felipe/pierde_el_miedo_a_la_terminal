# Pierde el miedo a la terminal 

---
En ese workshop veremos algunos conceptos basicos para empezar a utilizar la terminal en nuestro favor. Vamos a ver algunos conceptos sobre que es la terminal, para que sirve y como funciona. Veremos los comandos más básicos de navegación para iniciar la interación con el ordenador y la sintáxis básica de bash.
Por ultimo veremos algunos ejemplos practicos que podemos utilizar y algunos tips para customizar nuestra terminal y hacerla **nuestra**.

---

![](https://upload.wikimedia.org/wikipedia/commons/thumb/9/9f/DEC_VT100_terminal_transparent.png/1200px-DEC_VT100_terminal_transparent.png)

## Que es la terminal?
La terminal es una manera de interactuar con el ordenador, pero en lugar de hacerlo a traves de iconos y movimientos del raton, en lo que conocemos como **GUI** (Graphical User Interface), se hacen con líneas de comandos. Y por eso la terminal es una **CLI** (Command Line Interface).

_Lo que llamamos rosa, con cualquier otro nombre..._
\- Romeo y Julieta

En el caso de nuestra querida terminal, muchos nombres se usan como sus sinonimos: bash, shell, zsh, iTerm, etc. Aunque hayan particularidades a cada una de esas cosas, nos estaremos referiendo en ese workshop a los emuladores de terminal de tipo _Unix-like_ que usen lenguaje _Bash_. Es el más utilizado y más standard en la industria cuando hablamos de eso, por lo tanto será nuestro foco.

Si usas macOS 🍎 o Linux 🐧, _no worries_, por defecto la terminal que estarás usando cumple esos requisitos.

En Windows 🪟, entretanto, la cosa es un poquito diferente. El *CLI* de Windows, también conocido como _cmd.exe_ o _Command Prompt_. Aunque comparta muchas similaridades en la sintaxis, también hay muchas incompatibilidades. 
> Por ejemplo, el comando _ls_ usado en ambos mac y Linux, tiene como equivalente el _dir_ en cmd.exe

Pero no temáis, caros usuarios de Windows, podéis tener lo mismo, con algunas opciones diferentes como Git BASH, WSL (Windows Subsystem for Linux), Cygwin, etc. Vide la sección de Referencias al final de ese documento.

No nos enganemos por su antiguedad y estética sencilla. La terminal es una tecnologia muy concisa y que permanece muy actual.

![](https://i.pinimg.com/originals/9e/b4/16/9eb4164e55781372ac1ebe21ce056f6c.jpg)

## Por que aprender la terminal?
Es popular
- Según el Developer Survey 2020 de Stack Overflow, Bash/Shell está entre los 6 [lenguajes de programación más usado por desarrolladores profesionales](https://insights.stackoverflow.com/survey/2020#technology-programming-scripting-and-markup-languages-professional-developers).

Es valorado
- En la misma investigación, se ve también una gran correlación entre esse [lenguaje de programación y el sueldo](https://insights.stackoverflow.com/survey/2020#top-paying-technologies), más que otros como Python, Javascript y R.

Tiene utilidades muy importantes
- Es esencial para usar [git](https://git-scm.com/) para control de versiones.
- Es esencial para tecnologias `cloud`.
- Teclear es más rápido que usar el ratón.

Bonus:
- Postureo de Hacker. 😂💻

<img src="https://external-preview.redd.it/4lnFFyQJ8ZuV11zAkHW9q3VUfPHS-KL29kb76c0RM2s.jpg?auto=webp&s=20de54cd38fe99d817d283f802053c16f08e4ad9" height=400/>

Vamos a ello!

## Prompt
Al abrir la terminal, lo primero que veremos será algo parecido a:
```
# En Mac
MacBook-Pro:~ core$

# En Ubuntu
core@linux-desktop: ~$ 

# En Windows cmd.exe (para comparación)
C:\Users\Core>
```
A esa información con el cursor pulsando al lado se llama el _prompt_, que es el señal de nuestra entrada, es la manera como el ordenador nos dice que está escuchando y esperando lo que le vayamos decir.
La información contenida en general es:
- nombre del Ordenador
- nombre de usuario
- directorio actual
- signo de prompt
> En general, el prompt se representará con uno de esos signos: `$`, `%`, `#`, `:`, `>`, `_`
>
> Pero puede cambiar segun el sistema y como esté configurado. Hay muchas posibilidades de personalización!

## Directorio y rutas
Terminal abierta, ordenador esperando, necesitamos saber donde estamos.

Por suerte, como hemos visto antes, el directorio actual en general sale en el prompt, en ese caso es el directorio "`~`".

### **Home ( ~ )**
La virgulilla (`~`), es un nombre especial, un alias (cognombre), que se refiere a la carpeta `home`, o sea, tu carpeta de usuario. En el caso de Windows, vemos toda la dirección ("C:\Users\Core"). En los demás caso, el mote más corto. 

Para ver las coordinadas exactas del directorio donde estamos, podemos utilizar el primer de los comandos que aprenderemos:

## ➥ pwd
Los programas y comandos en la terminal suelen tener un nombre que significa algo (para facilitarnos la vida), pwd significa (_Print Working Directory_), i.e.: Imprime en pantalla el directorio actual (donde estamos trabajando).

La respuesta poderá ser algo similar a:
```
/Users/core
```

El path completo de la carpeta home del usuario `core`. Nos resta conocer el contenido de esa carpeta.

## ➥ ls
Para ver todo el contenido del `cwd` (Current Working Directory), i.e.: la carpeta donde estamos, podemos utilizar el comando `ls` (_list_), para listar. Pruebalo.

Obtendremos un resultado como el siguiente:
```
Applications    Downloads       Music           
Public          core            Desktop         
Library         Pictures        Documents       
Movies          code
```

En ese listaje vemos (_casi_) todos las carpetas y ficheros que tenemos en nuestra carpeta `home`. Por que casi? Porque hay ficheros y carpetas ocultos. Para poder verles, tenemos que usar de una opción del comando `ls`.

## Options

En lugar de usar solo el comando `ls`, vamos añadirle la opción `a` (_all_). Las opciones siempre van después del comando y con el caracter `-`. Prueba el comando:

```
ls -a
```

Ha cambiado el resultado? Que notas en los ficheros y carpetas ocultos? Todos sus nombres empiezan con `.`.

```
TIP: Si quieres hacer un fichero o carpeta oculto, pon un punto al principio de su nombre.
```

Hay otras opciones para ls, por ejemplo, al hacer el comando `ls -l`, vemos la versión (_long_) larga del listado del directorio.

## ➥ cd

![](https://infx511.github.io/img/command-line/matrix-cli.jpg)

Hemos visto como localizarnos y saber que contenido tenemos disponible en esa localidad, pero como nos movemos entre los diferentes directorios?
Usemos el comando `cd` (Change Directory) y el nombre de la carpeta a la cual queremos acceder, prueba, por ejemplo:

```
cd Downloads
```

Eres capaz de ver el contenido de _Downloads_ con el comando `ls` ahora?

>NOTE: Si quieres volver al directorio anterior, puedes utilizar el comando `cd ..`
>
>En la lenguaje de la terminal, `..` significa el directorio superior al en que nos encontramos.
>
>A un conjunto de direcciones le llamamos ruta o path. En él, los diferentes directorios en el camino se separan por `/` .
>
>Si estamos en la carpeta _Downloads_ (es nuestro _cwd_), podríamos hacer 
>
> `cd ../Music/Beatles`
>
>para salir de _Downloads_, entrar en _Music_ y dentro de ese, entrar en _Beatles_.

## Arguments

Al hacer `cd`, le tenemos que decir un path a un directorio. Pero al contrário de lo que hemos visto anteriormente, eso no es una opción. Es un argumento que se pasa al comando (o programa).

De manera general todos los comandos en la terminal van seguir la misma forma:

```bash
command [ --options ] [Arguments]
```
### Command
Es cualquier programa que esté disponíble en el CLI. Además de los que vienen por defecto, puedes instalar los que necesites y incluso escribir tus proprios programas para la terminal.

### Options
Son algunos de los parametros que podemos selecionar en un programa. Pueden presentarse como una unica letra con `-` o en un formato más largo con `--`.

```
-a -l -s --verbose --update-server
```

En el caso de las opciones (también llamadas `flags`) que son letras individuales, se pueden combinar en secuencia, eso es, los dos comandos abajo funcionan exactamente igual:

```
ls -a -l
ls -al
```

### Arguments
Los argumentos son valores exteriores que pasamos al programa, pueden ser directorios, ficheros, numeros, palabras o cualquier otro tipo de dato.

Los diferentes argumentos siempre se separan por espacios! Así que si tu argumento contiene un espacio, debes utilizar commillas o usar la `\` para _escapar_ el espacio.

>Algunas veces los argumentos necesitan que se indique a que parametro se asocia, en ese caso, debemos ponerlo despues de una opción, por ejemplo:

```
convert help.wav --format mp3 --output help.mp3
```

## Ayuda y manual

Pero como podremos saber todas las opciones y argumentos que podemos o tenemos que pasar a un comando?

La verdad es que, aunque los que más usamos se fijan en la memoria, muchas veces necesitamos un recordatorio. Y no hace falta ni siquiera salir de la terminal. 

La mayor parte de los programas acepta un flag de ayuda `-h` o `--help`.

Prueba `vi -h` para ver la ayuda de VIM, el editor de texto por defecto en terminales Unix. Sobretodo en las páginas de ayuda es util la seccion _usage_  al principio que te resume como tienes que usar a ese programa. 

Otra posibilidad, mas extensa y con más información es mirar el manual del programa. Eso no se hace con un _flag_, sino que con un comando proprio:

```
man vi
```

Usa las flechas para subir y bajar en el manual, y cuando estés listo, pulsa la `q` (_quit_) para salir. 

## Creando y borrando

Además de navegar por los diferentes ficheros y directorios de nuestro ordenador, queremos ser capaces de hacerle cambios. Abajo tenemos algunos comandos basicos que podéis investigar.

### ➥ mkdir
Ese es el comando `make directory`, que nos permite crear una carpeta nueva vacia. Lo único que necesitamos es pasarle como argumento el nombre o path de la carpeta que queremos crear.

`mkdir code/projects/rest_api`

### ➥ touch
El comando `touch` es similar al anterior, pero en lugar de crear un directorio, crea un fichero vacio.

`touch server.py`

### ➥ cat
<img src="https://i.pinimg.com/originals/25/09/9d/25099dcc3d439291d3b44c3c17400934.jpg" height=400/>

Ese comando que recibe su nombre de la palabra `concatenate`, lo que hace es enseñarnos el contenido de un fichero.

`cat index.html`

Hay comandos similares que podemos investigar, como el `head` y el `tail`, que nos enseñan el principio y el final del contenido de un fichero respectivamente.

### ➥ rm
El comando `remove` hace exactamente lo que dice, nos borra un fichero o una carpeta. La diferencia es que para borrar un directorio necesitamos añadir el flag `-r`, de `recursive`.

`rm index.html`

`rm -r code/projects/rest_api`

>WARNING: El comando `rm` **no** te hace una pregunta de confirmación y es un proceso sin vuelta. Ten cuidado al usarlo para no borrar cosas importantes.

## Redirecting y Piping

Por supuesto que no queremos que nuestros ficheros se queden en blanco, vacios. Queremos añadirles contenido. 

Como hemos visto anteriormente, existe en la propria terminal un editor de texto, en realidad hay una serie de posibilidades: `VIM`, `nano`, `emacs`, etc.

Pero una otra manera de introducir datos a un fichero es a partir de la ejecución de un otro comando, en una operación que se llama:

### Redirecting
Para esa operación, utilizamos un operado, el `>`. Antes del operador le añadimos el comando cuyo `output` queremos escribir en un fichero, y después de él, el nombre del fichero, por ejemplo:

`cal > calendario`

Al ejecutar esa línea de comando, el output de `cal` (el calendario del mes actual) se guardará en un fichero llamado _calendario_.

### Append
Si volvieramos a ejecutar un comando con el operador `>`, sobrescribiriamos el contenido del fichero y el calendario que estaba puesto anteriormente.

Hay, entretanto, otro operador que en lugar de sobrescribirlo, lo añade al final del fichero, manteniendo el contenido original y incluyendo el nuevo. Ese operador es el `>>`, probamos:

`date >> calendario`

Si miramos ahora el contenido del fichero _calendario_, ambos el calendario y la fecha y hora actual estaran disponibles.

### Pipe

<img src="https://images-wixmp-ed30a86b8c4ca887773594c2.wixmp.com/f/25247b92-6844-4fef-8ed8-5055cc35bf58/ddzqjp9-2c0f4355-53fa-4a92-bde6-f61c25ecaf25.png?token=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJzdWIiOiJ1cm46YXBwOiIsImlzcyI6InVybjphcHA6Iiwib2JqIjpbW3sicGF0aCI6IlwvZlwvMjUyNDdiOTItNjg0NC00ZmVmLThlZDgtNTA1NWNjMzViZjU4XC9kZHpxanA5LTJjMGY0MzU1LTUzZmEtNGE5Mi1iZGU2LWY2MWMyNWVjYWYyNS5wbmcifV1dLCJhdWQiOlsidXJuOnNlcnZpY2U6ZmlsZS5kb3dubG9hZCJdfQ.iNtkgGQmX0a3czOFNvtyWlyfmztUlhGw4gSgUyW0yec" height=200/>

No siempre queremos que el _output_, i.e.: la respuesta, de un comando se guarde en un fichero. Muchas veces queremos que ese _output_ sea el _input_ (el argumento) de un otro comando. No lo podemos hacer con el operador de redirección, hay un operador específico para eso, el operador `pipe`, representado por el caracter `|`.

Vamos probar ver los ficheros y carpetas que tenemos en la carpeta `home`, pero solo las ocultas. Ya sabemos que `ls -a` nos enseña ocultos y no ocultos.

Podemos filtrar con el comando `grep`, la simplificación del nombre muy complejo `globally search for a regular expression and print matching lines`. En resumen, que nos busca patrones. El patrón que queremos es buscar los ficheros y carpetas cuyos nombres empiezan con `.` .

Grep utiliza [regular expressions](https://regexone.com/) y la expresión para buscar objetos que empiecen con un punto es "`^\.`".

Probemos `ls -a | grep "^\."` y deberemos ver solo los ficheros y carpetas cuyos nombres empiezan por un punto. En ese sentido la combinación del `pipe` con el comando `grep` es muy util para buscar información. 

Por ejemplo, si queremos saber que procesos de _MySQL_ están activos en nuestro ordenador, poderíamos hace `ps -ax | grep mysql`


## Creando alias
Si un comando lo usamos mucho y queremos darle un alias, es muy sencillo. Y así podemos facilitar nuestra vida. Por ejemplo, vamos hacer un atajo que nos lleve directamente al _Desktop_.

```bash
alias cddk='cd ~/Desktop'
```

A partir de ese momento, el comando `cddk` nos llevará directamente al _Desktop_. Pero, si cerraramos la terminal y volvieramos a abrirle, el alias ya no estaria en efecto. Para que el efecto sea permanente, tenemos que incluir el alias en un fichero de configuración de la shell.
Ese fichero estará en la carpeta `home` y se llamará `.bashrc` si usas Bash o `.zshrc` si usas Zsh. Y podemos escribir al fichero desde la terminal con el comando `echo`.

```bash
echo "alias cddk='cd ~/Desktop'" >> ~/.zshrc
```

Pero también podemos abrir el fichero en algún editor de texto. Los alias son muy utiles para facilitar tareas rutineras, por ejemplo, podemos asignar los siguente aliases `ga='git add'`, `gc='git commit'` cuando usamos `git` para control de versiones de software.

## TIPS and TRICKS 

La practica y fluidez en el uso de la `CLI` viene con la practica, pero hay muchos tips que podemos utilizar para facilitar y ahorrar tiempo.

### Cycle commands

![](https://elijahmanor.com/_next/static/chunks/images/pun-history-9ae10e7b5db47f3ff1326f01fbbd2a25.jpg)

La terminal guarda un historico de los comandos que ejecutaste, si quieres volver a encontrar un comando, puede navegarles utilizando las flechas `↑ ↓`.

También puedes verles como un listado usando el comando `history`.

### bck-i-search
Si no te acuerdas completamente del comando o hace mucho que lo usaste, puedes hacer una busqueda. Pulsa `Ctrl + r` y empieza a escribir cualquier parte del comando. 

### Auto complete
En general, las terminales permiten el uso del `TAB`, `↹`, para auto-completar los comandos, nombres de directorios y ficheros. De esa manera con pocos caracteres y el uso del tab ya tenemos todo listo!

## Ejemplos molones y practicos
### Haz hablar a tu ordenador
```
NOTE: El comando 'say' es exclusivo de macOS. En otros sistemas, puedes instalar 'espeak' o otro `TTS` (Text-to-Speech)
```
Ese programa es muy sencillo, simplemente pongale seguido de una frase y disfruta. 
La voz puede customizarse con la opción `-v`.
Para ver todas las voces instaladas, use el comando `say -v '?'`

Aunque por si solo pueda no parecer mucho, puedes utilizar say e integrarlo a tus programas para una interfaz más ' humana'.

### Vaquita de la suerte
Hay 3 tres programitas interesantes y que pueden ser todavía más cuando les combinamos. Los links para instalación están en las referencias al final.

Hemos visto el comando `cat`, pero y `lolcat`?

Ese nuevo comando hace exactamente lo mismo que el anterior, pero con 
	<span style="color:#e6b85b">c</span><span style="color:#b8e65b">o</span><span style="color:#5be65b">l</span><span style="color:#5be6b8">o</span><span style="color:#5bb8e6">r</span><span style="color:#5b5be6">i</span><span style="color:#b85be6">n</span><span style="color:#e65bb8">e</span><span style="color:#e65b5b">s</span>.

El segundo comando es el `fortune`, que simplemente te da una cita o frase aleatoria. Si en algun momento necesitas algo de inspiración, puedes buscar la suerte en tu terminal.

Y por ultimo, un clasico inalgurado en el 1999, el `cowsay`. Todo mola más cuando se lo dice un animalito hablante

```
 ______________________
< CODE. REPEAT. ENJOY. >
 ----------------------
        \   ^__^
         \  (oo)\_______
            (__)\       )\/\
                ||----w |
                ||     ||
```

El combo `fortune | cowsay | lolcat` es la sabiduria bovina.

### Fast Image processing
Imaginate que necesitas cambiar el tamaño a miles de imagenes, sea para thumbnails en una web o para algun proyecto de computer vision. Que trabajo sería abrirlas una a una en photoshop...

Para eso (y muchas otras operaciones sobre imagenes) está el `ImageMagick`, cuyo comando es `mogrify`.

Puedes hacer todo lo que harias con photoshop directamente de la terminal, por ejemplo:

```
mogrify -resize 800x600 core.png
```

### Huye de los pop-ups, anuncios y otras molestias
Nos ha pasado a todos, queremos descargar un video de youtube, buscamos una de las mil paginas iguales que prometen hacer lo mismo, eligimos una y esperamos que funcione. Para hacerlo simple, hazlo directo de tu terminal con `youtube-dl`.

Lo mismo con verificar la velocidad de nuestra internet. Resulta que el proprio `Speedtest` tiene una versión CLI!

Si quieres, puedes huy por completo de los navegadores!!! Bueno, en realidad, no. Pero si algun día quieres impresionar a un colega prueba buscar algo en Google directamente de la terminal con `w3m`.

### Monitora tus procesos y procesadores
En lugar de abrir el monitor de actividades, si quieres ver de manera visual y rapida como están actuando cada uno de los núcleos de tu ordenador, usa el comando `htop`, la versión mejorada de `top` que viene por defecto.

## Haz tu terminal TUYA.
Lo mejor para dominar la terminal es usarla! Necesitas cambiar unos ficheros de lugar, hazlo por la terminal. Quieres borar unos documentos, igual. Al principio puede parecer un camino más largo, pero esos pequeños ejercicios daran frutos en tus habilidades. Y no os olvidéis que el uso de la terminal es una habilidad esencial para desarolladores, programadores, data scientists.

Pero lo mejor para poder usar la terminal es hacerla más personal para ti, así que

## Customiza!
Hay muchas maneras de customizar la terminal, no solo para dejarla más bonita, sino como para facilitar el trabajo.

Una de ellas ya la hemos visto, los `alias`. Cuando haya algun comando o proceso que uses mucho, hazle un alias! Ese pequeño ahorro de tiempo va acumulandose.

Si usas macOS, puedes instalar `iTerm2` como alternativa a la terminal por defecto. Se agradece el cambio, pues te dará más posibilidades de configuración.
Si tienes Linux, aunque haya alternativas, la terminal por defecto es super!
En Windows, tendras que buscar una de las alternativas citadas anteriormente para tener una terminal bash o zsh.

Uno de los frameworks más populares es Oh My Zsh, con muchos plugins y muchos temas, el más popular es el `agnoster`, aunque otro genial (y mi favorito) es el `Powerleve10k`, que tiene muchas configuraciones.

```
Web devs, quizas queráis mirar Hyper, una alternativa a la terminal completamente customizable con HTML y CSS. 😉
```

Investiga los ficheros de configuración (`.zshrc` y `.bashrc`). Empieza con pequeños cambios como crear aliases, etc. Y con ayuda de internet podrás descubrir cada vez más posibilidades. 

Utiliza los recursos de internet, si se te ocurre algo, lo más probable es que lo haya pasado a alguien antes y habrá recursos en internet. Y, por supuesto, `Code. Enjoy. Repeat.`

## Referencias

- [Oh My ZSH (macOS y Linux)](https://github.com/ohmyzsh/ohmyzsh)
- [Oh My Zsh (Ubuntu, alternativa)](https://geekytheory.com/como-instalar-oh-my-zsh-en-ubuntu)
- [Oh My Zsh (Windows)](https://medium.com/@lemmusm/cool-windows-terminal-with-oh-my-zsh-8d2c1c759805)
- [espeak](http://espeak.sourceforge.net/)
- [Windows Subsystem for Linux](https://docs.microsoft.com/en-us/windows/wsl/install-win10)
- [Git Bash](https://gitforwindows.org/)
- [Powerlevel10k](https://github.com/romkatv/powerlevel10k)
- [fortune, cowsay, lolcat](https://gist.github.com/zlorb/4a3eff8981fcec8ca1c7)
- [ImageMagick](https://imagemagick.org/script/download.php)
- [htop](https://htop.dev/)
- [Speedtest](https://www.speedtest.net/apps/cli)
- [youtube-dl](https://github.com/ytdl-org/youtube-dl/)
- [w3m](http://w3m.sourceforge.net/)
- [iTerm2](https://iterm2.com/)
- [iTerm color schemes](https://iterm2colorschemes.com/)
- [Hyper](https://hyper.is/)
- [Gnome Terminal (Linux) color schemes](https://www.linuxuprising.com/2019/07/179-color-schemes-for-your-gtk-based.html)
