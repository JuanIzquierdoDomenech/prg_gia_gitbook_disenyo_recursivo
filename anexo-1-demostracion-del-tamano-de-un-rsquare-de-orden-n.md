# Anexo 1: Demostración del tamaño de un RSquare de orden n

Cuando dibujamos un _RSquare_ de orden $$n$$, la figura no ocupa solo el cuadrado central. Sus cuatro hijos sobresalen por las esquinas, los hijos de esos hijos sobresalen un poco más, y así en cada nivel.&#x20;

La pregunta que resolvemos aquí es sencilla: ¿cuánto mide de ancho la figura completa, desde su borde izquierdo hasta su borde derecho?

### ¿De dónde sale la suma?

Colocamos el cuadrado central con su centro en el origen. Si su lado mide $$l$$, entonces su borde derecho está a una distancia $$l/2$$ del centro, porque el borde de un cuadrado está siempre a medio lado de distancia de su centro.

Cada hijo tiene la mitad de lado que su padre, es decir $$l/2$$, y está centrado en una esquina del padre. El hijo de la esquina derecha añade su propio medio lado hacia afuera, que vale $$l/4$$. Por tanto, su borde derecho llega hasta $$l/2 + l/4$$.

El nieto repite la operación con la mitad de tamaño. Añade $$l/8$$, y su borde derecho llega hasta $$l/2 + l/4 + l/8$$.

Si seguimos bajando nivel a nivel hasta el cuadrado de orden $$1$$, la distancia desde el centro hasta el borde más externo es la suma de todos esos salientes:

$$
\frac{l}{2} + \frac{l}{4} + \frac{l}{8} + \cdots + \frac{l}{2^{n}}
$$

Como la figura es simétrica, el lado izquierdo mide exactamente lo mismo que el derecho. El ancho total es el doble de esa distancia:

$$
W = l + \frac{l}{2} + \frac{l}{2^2} + \cdots + \frac{l}{2^{n-1}}
$$

### ¿Cómo se suma esta lista de fracciones?

Sumar muchas fracciones a mano sería lento, pero esta lista tiene una propiedad que la hace fácil: cada término es la mitad del anterior. Una lista así se llama serie geométrica, y tiene una fórmula que da el total sin necesidad de ir sumando uno por uno.

La fórmula de la suma de los primeros $$n$$ términos de una serie geométrica, cuando el primer término es $$a$$ y cada término se obtiene multiplicando el anterior por una razón $$r$$ es:

$$
a \cdot \frac{1 - r^{n}}{1 - r}
$$

En nuestro caso el primer término es $$a = l$$ y la razón es $$r = \tfrac{1}{2}$$, porque cada cuadrado tiene la mitad de lado que el anterior. Sustituimos esos dos valores:

$$
W = l \cdot \frac{1 - \left(\tfrac{1}{2}\right)^{n}}{1 - \tfrac{1}{2}} = l \cdot \frac{1 - \tfrac{1}{2^{n}}}{\tfrac{1}{2}}
$$

Dividir entre $$\frac{1}{2}$$ es lo mismo que multiplicar por $$2$$, así que:

$$
W = 2l \cdot \left(1 - \frac{1}{2^{n}}\right) = 2l - \frac{l}{2^{n-1}}
$$

### ¿Qué significa el resultado?

El ancho de un _RSquare_ de orden $$n$$ es:

$$
W = 2l - \frac{l}{2^{n-1}}
$$

El término que restamos $$\frac{l}{2^{n-1}}$$​, se hace cada vez más pequeño a medida que el orden $$n$$ crece, porque su denominador se duplica en cada nivel. Cuando $$n$$ es muy grande, ese término se aproxima a cero, y el ancho se aproxima a $$2l$$.

Dicho de otra manera, por muy profunda que sea la recursión y por muchos cuadrados que se dibujen, la figura completa nunca llega a medir el doble del lado del cuadrado central. Se acerca a ese valor sin superarlo.
