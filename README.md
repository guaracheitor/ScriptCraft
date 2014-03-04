# Comencemos...

He creado ScriptCraft para hacer más fácil para los niños (y para cualquier persona
interesada en la programación) la creación de sus propios Mods de Minecraft. 
ScriptCraft hace que sea más fácil para los nuevos programadores crear
Mods de Minecraft. Los Mods se crean utilizando el lenguaje de programación Javascript
y una vez instalado el mod ScriptCraft, puedes añadir tus
propios Mods añadiendo archivos Javascript (. js) en un directorio.

 * Si eres nuevo programando y quieres empezar con el modding de Minecraft, entonces [Empieza aquí][ypgpm].
 * Si ya has usado [Scratch][scr], has recibido algunas sesiones de [CoderDojo][cd], o ya conoces Javascript, entonces [Empieza aquí][cda].

 * Mira algunos [ejemplos][ytpl] de lo que puedes hacer con ScriptCraft.

Este es un mod simple en un archivo llamado greet.js en la carpeta scriptcraft/plugins...

```javascript
exports.saludo = function( jugador ) {
   jugador.sendMessage('Hola ' + jugador.name );
};
```

En la consola de comandos del juego escribe...

    /js greet(self)... para ver el saludo. Todo lo que puedes hacer con la API de CraftBukkit en Java, puedes hacerlo usando ScriptCraft en Javascript.

# Descripción

ScriptCraft es un plugin para servidores Minecraft que permite a operadores,
administradores y creadores de plugins personalizar el juego usando javascript.
ScriptCraft te facilita crear tus propios mods. Los mods
pueden escribirse en javascript se puede usar toda la [API de Bukkit][bukkit].  El mod
ScriptCraft también permite usar comandos javascript en la consola de comandos.  Para que aparezca la consola de comandos presiona la tecla `t` y escribe `/js ` seguido de una instrucción javascript.  Por ejemplo. `/js 1+1` devolverá
2.


Scriptcraft también incluye muchos objetos y funciones para construir y 
hacer modding fácilmente usando javascript.
El objeto Javascript `Drone` incluido con ScriptCraft
bundled with ScriptCraft proporciona una forma fácil de construir a escala en
Mira en el archivo adjunto [cottage.js][cottage] un ejemplo de como
puedes usar el plugin Drone para crear nuevas contrucciones en Minecraft.

[drone]: https://github.com/walterhiggins/ScriptCraft/tree/master/src/main/javascript/drone/drone.js
[cottage]: https://github.com/walterhiggins/ScriptCraft/tree/master/src/main/javascript//drone/cottage.js
[bukkit]: http://dl.bukkit.org/

# Prerrequisitos

Necesitas tener instalada las versiones 6 o 7 de Java en tu ordenador.
Chequea la versión escribiendo  `java -version` en una consola de comandos.
Necesitas  [instalar Bukkit][ib] en tu ordandor. Bukkit
es una versión de Minecraft (servidor) que facilita instalar 
plugins y personalizar Minecraft.  Puedes [descargar el servidor CraftBukkit
aquí.][cbdl]

# Instalación

Si no quieres compilar desde las fuentes, puedes [descargar el 
plugin compilado aquí][dl] y copiarlo en la carpeta de plugins 
de craftbukkit.

# Postinstalación

Una vez instalado, se crea automáticamente una nueva carpeta js-plugins 
en la misma carpeta que la carpeta plugins. Todos los ficheros en la carpeta
js-plugins serán leídos automáticamente cuando arranque CraftBukkit.
* Solo los operadores pueden usar este plugin.* Puedes dar privilegios de
`operador` a un jugador escribiendo 'op <nombre de usuario>' en la consola
comandos del servidor o añadiendo ese 'nombre de usuario' a ops.txt en 
tu carpeta de craftbukkit.

Lanza CraftBukkit, arranca el cliente de Minecraft y crea una nueva conexión
de servidor. La IP será `localhost`. Cuando estés conectado a tu servidor 
bukkit y hayas comenzado a jugar, mira al nivel del suelo y escribe...

    /js up().box('35:15', 4, 9, 1)

...Esto creará una estructura monolítica de 4 bloques de ancho por 
9 bloques altura y un bloque de largo. Échale un vistazo al archivo 
src/main/javascript/drone/drone.js y mira lo que el drone de ScriptCraft
puede hacer. Si estás interesado en personalizar minecraft más allá de
crear nuevas construcciones, mira en [./homes/homes.js][homes]
y [./chat/color.js][chatcolor] ejemplos de cómo crear un 
plugin javascript para Minecraft.

[ho]: blob/master/src/main/javascript/plugins/homes/homes.js
[ch]: blob/master/src/main/javascript/plugins/chat/color.js
[ar]: blob/master/src/main/javascript/plugins/arrows/arrows.js
[si]: blob/master/src/main/javascript/modules/signs/menu.js

Un mod Javascript para Minecraft es un archivo fuente javascript (.js)
localizado en la carpeta craftbukkit/js-plugins. Todos los archivos (.js)
de esa carpeta serán leídos automáticamente cuando arranque el servidor
craftbukkit. Para empezar a crear tu propio mod, primero revisa algunos 
de los mods ya existentes las carpetas [homes][ho], [chat][ch], [arrows][ar] y
[signs][si]. Probablemente el mod más simple para empezar es chat/color.js.


# Información adicional

Como la API de Bukkit API es abierta, toda la API de Bukkit es accesible
desde javascript una vez que se carga el puglin ScriptCraft. Aquí tenemos 
un par de útiles objetos Java accesibles via javascript en el plugin 
ScriptCraft de Bukkit...


 * `__plugin` - el propio plugin ScriptCraft. Este es un punto de partida
   útil para acceder a otros objetos Bukkit. El objeto `__plugin` es del tipo
   [org.bukkit.plugin.java.JavaPlugin][api] y todas sus propiedades y métodos
   están accesibles. Por ejemplo...`js  __plugin.server.motd` devuelve el 
   mensaje del día del servidor(javascript es más conciso que el código Java 
   equivalente: __plugin.getServer().getMotd() ).

 * `server` - El nivel más alto del objeto org.bukkit.Server. Revisa como referencia
   la [documentación de la API de Bukkit][bukapi].

 * `self` - El player/command-block o la consola de servidor del operador 
   que invoca el comando `/js`. Nuevamente, este es un buen punto para adentrarnos
   en la API de Bukkit.

[dl]: http://scriptcraftjs.org/download
[api]: http://jd.bukkit.org/apidocs/org/bukkit/plugin/java/JavaPlugin.html
[ib]: http://wiki.bukkit.org/Setting_up_a_server
[cbdl]: http://dl.bukkit.org/downloads/craftbukkit/
[bukapi]: http://jd.bukkit.org/apidocs/

# Para contribuir

Si quisieras contribuir al código fuente y/o la documentación por favor, [lee contributing.md][contrib] 

## Estado

[![Travis Build Status](https://api.travis-ci.org/walterhiggins/ScriptCraft.png)](http://travis-ci.org/walterhiggins/ScriptCraft)

# Configuración

ScriptCraft es un plugin de Bukkit y usa la configuración de la API
de Bukkit. Al inicio, ScriptCraft creará un archivo config.yml in la
carpeta plugins/scriptcraft/. Este archivo luce así...

    extract-js:
      plugins: true
      modules: true
      lib: true

Este archivo permite a los administradores de scriptcraft permitir o no la
re-descompresión de las carpetas `modules`, `plugins` y `lib` cuando se 
despliega una nueva versión de scriptcraft. Es altamente recomendable que la
carpeta `lib` siempre esté en true para tener la última versión del núcleo del
código de scriptcraft. Las carpetas de módulos y plugins son opcionales y no forman
parte del núcleo de scriptcraft.

# ¿Dónde seguir?

ScriptCraft tiene [su propio sitio web][website] con información adicional.

 * Para empezar a usar ScriptCraft para aprender javascript, lee la [Guía de programación
   en Minecraft para jóvenes][yp].
 * La [documentación de la API][api] de ScriptCraft.
 * Para profundizar en la creación de su propio mod minecraft para su uso por otros, lee [Creando un Mod de Minecraft    completo en Javascript][mm].
 * Échale un vistazo a algunos [ejemplos][ex]

Puedes encontrar más información sobre [ScriptCraft en mi blog][blog].

[blog]: http://walterhiggins.net/blog/cat-index-scriptcraft.html
[buk]: https://github.com/walterhiggins/ScriptCraft/blob/master/bukkit.md
[yp]: docs/YoungPersonsGuideToProgrammingMinecraft.md
[mm]: docs/Anatomy-of-a-Plugin.md
[api]: https://github.com/walterhiggins/ScriptCraft/blob/master/docs/API-Reference.md
[website]: http://scriptcraftjs.org/
[ypgpm]: docs/YoungPersonsGuideToProgrammingMinecraft.md
[cd]: http://coderdojo.com/
[scr]: http://scratch.mit.edu/
[cda]: http://cdathenry.wordpress.com/category/modderdojo/
[ytpl]: http://www.youtube.com/watch?v=DDp20SKm43Y&list=PL4Tw0AgXQZH5BiFHqD2hXyXQi0-qFbGp_
[ex]: ../../tree/master/src/main/javascript/plugins/examples
[contrib]: contributing.md
