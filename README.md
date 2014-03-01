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
exports.greet = function( player ) {
   player.sendMessage('Hola ' + player.name );
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

# Installation

If you don't want to compile from source, you can [download the
compiled plugin here][dl] and copy it the craftbukkit's plugins
directory.

# Post Install

Once installed, a new js-plugins directory is automatically created in
the same directory as the plugins folder.  All files in the js-plugins
directory will be automatically loaded when CraftBukkit starts.  *Only
players who are ops can use this plugin.* You can grant a player `op`
privileges by typing 'op <username>' at the server console prompt or
by adding the player's username to the ops.txt file in your
craftbukkit directory.

Launch CraftBukkit, then launch the Minecraft client and create a new
server connection. The IP address will be `localhost` . Once you've
connected to your bukkit server and have entered the game, look at a
ground-level block and type ...

    /js up().box('35:15', 4, 9, 1)

... This will create a black monolith structure 4 blocks wide by 9
blocks high by 1 block long.  Take a look at the
src/main/javascript/drone/drone.js file to see what ScriptCraft's
drone can do.  If you're interested in customizing minecraft beyond
just creating new buildings, take a look at [./homes/homes.js][homes]
and [./chat/color.js][chatcolor] for examples of how to create a
javascript plugin for Minecraft.

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
