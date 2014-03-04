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

A Javascript mod for minecraft is just a javascript source file (.js)
located in the craftbukkit/js-plugins directory. All .js files in this
directory will be automatically loaded when the craftbukkit server
starts. To get started writing your own mod, first take a look at some
of the existing mods in the [homes][ho], [chat][ch], [arrows][ar] and
[signs][si] directories. The chat/color.js mod is probably the
simplest mod to get started with.

# Additional information

Because the Bukkit API is open, all of the Bukkit API is accessible
via javascript once the ScriptCraft plugin is loaded. There are a
couple of useful Java objects exposed via javascript in the Bukkit
ScriptCraft plugin...

 * `__plugin` - the ScriptCraft Plugin itself. This is a useful
   starting point for accessing other Bukkit objects. The `__plugin`
   object is of type [org.bukkit.plugin.java.JavaPlugin][api] and all
   of its properties and methods are accessible. For example... `js
   __plugin.server.motd` returns the server's message of the day
   (javascript is more concise than the equivalent java code:
   __plugin.getServer().getMotd() ).

 * `server` - The top-level org.bukkit.Server object. See the [Bukkit API docs][bukapi] for reference.

 * `self` - The player/command-block or server console operator who
   invoked the `/js` command. Again, this is a good jumping off point for
   diving into the Bukkit API.

[dl]: http://scriptcraftjs.org/download
[api]: http://jd.bukkit.org/apidocs/org/bukkit/plugin/java/JavaPlugin.html
[ib]: http://wiki.bukkit.org/Setting_up_a_server
[cbdl]: http://dl.bukkit.org/downloads/craftbukkit/
[bukapi]: http://jd.bukkit.org/apidocs/

# Contributing

If you would like to contribute source code and/or documentation changes please [read contributing.md][contrib]

## Status

[![Travis Build Status](https://api.travis-ci.org/walterhiggins/ScriptCraft.png)](http://travis-ci.org/walterhiggins/ScriptCraft)

# Configuration

ScriptCraft is a Bukkit Plugin and uses the Bukkit Configuration
API. On first loading, ScriptCraft will create a config.yml file in
the plugins/scriptcraft/ directory. This file looks like this...

    extract-js:
      plugins: true
      modules: true
      lib: true

This file allows scriptcraft admins to turn on or off re-unzipping of the `modules`,
`plugins` and `lib` folders when deploying a new version of
scriptcraft. It's strongly recommended that the `lib` directory always
be set to true to get the latest core scriptcraft code . The modules
and plugins directories are optional and not part of scriptcraft core.

# Further Reading

ScriptCraft has [its own website][website] with further information.

 * To get started using ScriptCraft to Learn Javascript, read [The Young Person's Guide to Programming in Minecraft][yp].
 * The ScriptCraft [API documentation][api].
 * To delve deeper into creating your own minecraft mod for use by others, read [Creating a complete Minecraft Mod in  Javascript][mm].
 * Take a look at some [examples][ex]

You can find more information about [ScriptCraft on my blog][blog].

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
