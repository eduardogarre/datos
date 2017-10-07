# cfg
Herramienta de control y configuración en Español.


## Resumen:
Esta herramienta interpreta y almacena la información como una lista de claves
estructuradas jerárquicamente formando un árbol. Como almacén de la información,
usa el sistema de archivos habitual de nuestro ordenador.
Una clave `abc.def.ghi` se tratará como el archivo `abc/def/ghi`.

Hay 2 posibles almacenes de información:
1. Global o del sistema, en `/cfg`
2. Local o del usuario actual, en `~/.config`

De forma predeterminada se asume que el usuario accede a su información local:
`config lee usr.nombre` accede al archivo `~/.config/usr/nombre` y nos muestra su
contenido.

Si se pretende acceder a la configuración global o del sistema, el primer nombre
de la clave debe ser `sis`:
`config ls sis.hostname` accede al archivo `/cfg/hostname` y nos muestra su
contenido.


## Uso:
```
config [--info | --charlatan] (lista | ls) <clave>
config [--info | --charlatan] lee <clave>
config [--info | --charlatan] tipo <clave>
config [--info | --charlatan] pon <clave> <valor> [--texto | --booleano | --entero | --real]
config [--info | --charlatan] (mueve | mv | renombra | rnm) <clave-antigua> <clave-nueva>
config [--info | --charlatan] (borra | br | quita | qt) <clave>
config [--charlatan] --ayuda
config [--charlatan] --version
```

#### Opciones:
```
 -a --ayuda           Muestra esta pantalla.
 -v --version         Muestra la version.
 -t --texto           <valor> es 'texto' (es el tipo asumido).
 -b --booleano        <valor> es 'booleano'
 -e --entero          <valor> es 'entero'
 -r --real            <valor> es 'real'
 -i --info            Opcion 'habladora'.
 -c --charlatan       Opcion 'verborreica', MUY habladora.
```
#### Subcomandos:
```
 lista/ls        Enumera todas las claves bajo la raiz <clave> (incluyendo
                 a esta ultima), e imprime sus valores.

 tipo            Imprime el tipo de la <clave> proporcionada.
                 Puede ser: 'texto', 'booleano', 'entero' o 'real'.

 pon             Asigna un <valor> a la <clave> proporcionada. Si <clave>
                 no existe, se crea. Si bien este comando es capaz de
                 detectar el tipo de dato proporcionado, se proporcionan
                 opciones para establecer el tipo del dato directamente.

 mueve/mv/renombra/rnm   Cambia el nombre de <clave-antigua> por el de
                         <clave-nueva>.

 borra/br/quita/qt       Elimina la <clave> proporcionada.
```
#### Argumentos:
```
 <clave>         Si <clave> comienza por 'sis', se accede a las claves
                 globales del sistema, en " ~ SISTEMA ~ ".
                 En cualquier otro caso, se accede a las claves del usuario
                 actual, en " ~ RUTA ~ ".

 <valor>         Texto | Entero | Real | Booleano.
```

## Ejemplos:
`config ls sis` Lista todas las claves globales.

`config ls` Lista todas las claves locales.

`config pon sis.hostname nombredelsistema` Establece el nombre del sistema

`config pon usr.askpwd sí -b` ¿Exigir contraseña para entrar a nuestra sesión? Sí.

`config mv usr.askpwd usr.pwd` Cambiar el nombre de `usr.askpwd` por el de `usr.pwd`.

 `config borra usr.pwd` Borra la clave `usr.pwd`


## Licencia:
El programa es libre y gratuito, lo publico bajo la licencia ISC.