# El paquete recursion y el módulo rsquare

Esta práctica se estructura en forma de un paquete llamado `recursion` que contiene un módulo llamado `rsquare`. Dicho módulo implementará una clase llamada `RSquare` que representa una figura fractal basada en cuadrados.

***

## Actividad 1: Inicialización del paquete `recursion`

Abre una terminal Bash de Linux y sitúate en el directorio donde quieras mantener organizadas las prácticas de la asignatura (dentro de `$HOME/W` si estás en el escritorio DSIC-Linux de Polilabs). A continuación, crea el directorio de la práctica actual y sitúate en él:

{% code title="" %}
```bash
mkdir p2
cd p2
```
{% endcode %}

{% hint style="warning" icon="eyes" %}
Tened en cuenta que `p2` será nuestro directorio de trabajo de partida durante toda la práctica. Todos los ficheros y paquetes deberán estar organizados a partir de este directorio.
{% endhint %}

Ahora vamos a inicializar el paquete `recursion`. Crea el subdirectorio del paquete, e incluye en él un fichero `__init__.py` vacío con el comando `touch` para que Python lo reconozca como un paquete importable.

{% code title="" %}
```bash
mkdir recursion
touch recursion/__init__.py # Creamos un fichero vacío
```
{% endcode %}

### Módulo `rsquare`

El módulo `rsquare` contendrá la clase `RSquare`, además de un `main` para probar la clase.

### Clase `RSquare`

#### Descripción de la clase

Un `RSquare` de orden $$n$$ se define por un cuadrado central de centro $$(x,y)$$, lado $$l$$, y color $$c$$, y cuatro instancias de `RSquare` de orden $$n-1$$ situados en sus esquinas (excepto si se trata de un cuadrado de orden 1, que es el caso base de la recursión). Por lo tanto, los 4 `RSquare` "hijos" tendrán lado $$l/2$$ y estarán situados en las esquinas del cuadrado central.

Esta clase encapsula tanto los datos (orden, tamaño, posición, color) como el comportamiento (cómo se construye la jerarquía y cómo se dibuja la figura en Matplotlib).

En el momento de crear una instancia de `RSquare`, se invocará un método **pseudo-recursivo** que construye la jerarquía de objetos `RSquare` descrita anteriormente. Posteriormente, cuando se pretenda dibujar el `RSquare` o guardarlo en un fichero, se invocará otro método **pseudo-recursivo** que recorrerá la jerarquía y dibujará cada `RSquare` en el objeto `Axes` de Matplotlib correspondiente. De esta forma, se separa la construcción de la jerarquía, del dibujado/renderizado de la misma.

{% hint style="info" icon="shapes" %}
Decimos que los métodos son **pseudo-recursivos** porque, si bien se invocarán sobre objetos `RSquare` distintos, y por tanto, técnicamente, desde el punto de vista de la programación, operan sobre contextos distintos, conceptualmente, desde el punto de vista de la geometría fractal, sí son recursivos.
{% endhint %}

#### Atributos

<table><thead><tr><th width="115.96875">Nombre</th><th width="143.35546875">Tipo</th><th width="120.84375">Visibilidad</th><th>Descripción</th></tr></thead><tbody><tr><td><code>order</code></td><td>de instancia</td><td>privado</td><td>Orden <span class="math">n</span> del <em>RSquare</em> <span class="math">(n \ge -1)</span>.</td></tr><tr><td><code>side</code></td><td>de instancia</td><td>privado</td><td>Longitud <span class="math">l</span> del <em>RSquare</em> <span class="math">(l > 0)</span>.</td></tr><tr><td><code>center</code></td><td>de instancia</td><td>privado</td><td>Tupla <code>(x, y)</code> con las coordenadas del centro del <em>RSquare</em>.</td></tr><tr><td><code>color</code></td><td>de instancia</td><td>privado</td><td>Color de las líneas del dibujo. Debe ser un string admitido por Matplotlib (<a href="https://matplotlib.org/stable/gallery/color/named_colors.html#base-colors">ver aquí</a>).</td></tr><tr><td><code>corners</code></td><td>de instancia</td><td>privado</td><td>Tupla que contiene las 4 instancias de <code>RSquare</code> de las esquinas.</td></tr></tbody></table>

#### Métodos

<table><thead><tr><th width="218.55859375">Perfil</th><th>Visibilidad</th><th>Tipo</th><th>Descripción</th></tr></thead><tbody><tr><td><code>__init__(order, side, center, color)</code></td><td>-</td><td></td><td></td></tr><tr><td><code>order()</code></td><td>público</td><td></td><td></td></tr><tr><td><code>side()</code></td><td>público</td><td></td><td></td></tr><tr><td><code>center()</code></td><td>público</td><td></td><td></td></tr><tr><td><code>color()</code></td><td>público</td><td></td><td></td></tr><tr><td><code>show()</code></td><td>público</td><td></td><td></td></tr><tr><td><code>save(filename)</code></td><td>público</td><td></td><td></td></tr><tr><td><code>init_recursive()</code></td><td>privado</td><td></td><td></td></tr><tr><td><code>draw_recursive(ax)</code></td><td>privado</td><td></td><td></td></tr><tr><td><code>plot_square(ax, cx, cy, l)</code></td><td>privado</td><td></td><td></td></tr></tbody></table>
