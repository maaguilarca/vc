# Rendering
# Lightcuts
## Motivos de uso 
Lightcuts es una forma de acelerar el proceso de renderizado cuando hay multiples puntos de luz, no 10 o 100, se están hablando de miles o millones de puntos de luz.

## Conocimientos previos
Incluso cuando se quiere hacer una imagen en 3d con una sola fuente de luz, para que sea realista, se necesita tener en cuenta los reflejos. Toda luz reflejada puede ser reflejada por otros objetos y así hasta que todas las luces hayan sido reflejadas en todos los objetos posibles. Si se añaden más fuentes de luz, estos cálculos aumentan y los tiempos para terminar de renderizar se hacen cada vez más largos. 

![iluminando cara original](/docs/sketches/Taller2/a.gif)


## solución por Lightcuts
![Comparación de tiempos](/docs/sketches/Taller2/comparacion.png)

### Se definen los "Light Clusters"
Se define un punto de luz representativa que, al iluminar un objeto, es la suma de todos los puntos que iluminan al mismo objeto de la misma manera. Todo esto teniendo en cuenta los distintos valores: la reflectividad del material, la posición de los puntos de luz, la visibilidad del objeto por los puntos de luz y por último la intensidad de la luz.

![Formula light clusters](/docs/sketches/Taller2/formulalightcuts.png)


M se refiere a la propiedad del material que incluye la función de distribución de reflectancia bidireccional y la superficie de Lambert para el ángulo de incidencia.

G se refiere a la atenuación de la luz de acuerdo con la distancia.

V se refiere a la visibilidad del objeto por la luz con una escala de 1, totalmente visible, a 0, completamente oscurecido.

I es la intensidad de la luz.


### Se crea el árbol de luz
Se crea el árbol teniendo en cuenta que las hojas son todos los puntos de luz originales y la raíz el punto cluster que contiene TODOS los puntos de luz.

![árbol de luz](/docs/sketches/Taller2/cluster.png)

### Se definen los puntos que se utilizaran(cuts)
Para cada punto en el objeto se crean los clusters que "mejor" lo iluminan. Para esto se coje el árbol de luz y se observa la raíz, si el umbral de aceptación no se cumple, se divide el cluster y así hasta que se llegue al umbral.

![Lightcuts](/docs/sketches/Taller2/lightcut.png)

![Iluminando cara con Lightcuts](/docs/sketches/Taller2/b.gif)


## referencias
- Bruce Walter, Sebastian Fernandez, Adam Arbree, Kavita Bala, Michael Donikian, and Donald P. Greenberg. 2005. Lightcuts: a scalable approach to illumination. 
-Stochastic Lightcuts: http://www.cemyuksel.com/research/stochasticlightcuts/
-Oliver Taubmann. Lightcuts on modern graphics hardware

> :ToCPrevNext