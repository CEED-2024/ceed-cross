# Proyecto de Desarrollo Web en Entorno Cliente 2024-2025

## Fase I

En esta fase tendrás que hacer que se muestren las casillas del juego. La aplicación deberá ser un proyecto
Vite con al menos los scripts por defecto (dev, build y preview) aunque es recomendable añadir uno más para
pasar el linter.

No se admitirán para las entregas evaluables proyectos que no pasen el linter.

### HTML

El HTML de tu aplicación debe ser como el proporcionado en el ejemplo. No puedes crear elementos distintos
de los proporcionados, lo único que variará son las letras generadas dentro de `#grid`.

Debe utilizar las mismas clases en los elementos, y no puedes añadir estilos o clases adicionales.
Se puede añadir un id a los elementos si lo necesitas.

### Iconos

Para que los iconos se muestren debes añadir las dependencias al proyecto:

- `@fortawesome/fontawesome-svg-core`
- `@fortawesome/free-solid-svg-icons`

E importar el modulo `./lib/fontawesome.js` para que funcionen.

### Datos de las casillas

Los datos de las casillas del juego los puedes obtener de la siguiente manera:

```js
const game = new Game(id);
const wordPositions = game.worPositions;
```
Le puedes pasar un `id` a `Game` para obtener una partida específica, o bien no pasarle nada
y obtener una aleatoria. El `id` va de cero al número de juegos definidos en `./lib/game.js` menos uno.

La clase `Game` la puedes importar de `./lib/Game.js`. La estructura de `wordPositions` es:
```js
[
  {
    origin: [x,y],          // La casilla superior izquierda es 0,0. La inferior derecha es 9,9
    direction: 'horizontal' // Puede ser <"vertical" u "horizontal">,
    length: n               // Longitud de la palabra
  },
  ...
]
```

### Centrado de las casillas del juego

La estructura devuelta siempre colocará el juego lo más izquierda y lo más arriba posible. Tienes que centrarla
en grid de la aplicación. Para ello, tienes que utilizar la función center de `./lib/center.js`. La función recibe cuatro parámetros:

- `maxColumn`: Máxima columna que ocupan las casillas. Por ejemplo, si el juego tiene cinco columnas la máxima
columna será la 4 (la primera columna es la 0)
- `maxRow`: Máxima fila que ocupan las casillas. Por ejemplo, si el juego ocupa tres filas la máxima fila será la 2
(la primera fila es la 0)
- `gridWidth`, `gridHeight`: tamaño del grid. Será 10x10

Devolverá un array `[despX, despY]` que indicará cuánto hay que desplazar las casillas para que queden centradas.

### Creación de juegos para pruebas

Puedes crear nuevos juegos modificando el contenido de `./lib/game.js`. Ten en cuenta que la aplicación debe
funcionar con cualquier conjunto de casillas —no sólo con las que hay de ejemplo— siempre y cuando quepan en la
rejilla.

En la web https://crosswordlabs.com/ puedes generar nuevos puzzles si lo necesitas.
