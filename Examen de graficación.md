~~~
y = mx + b
~~~
### <span style="color:#50fa7b;">Algoritmo DDA</span>
El analizador diferenciador digital (DDA - Digital Differential ANalyzer) es un algoritmo de conversión de rastreo que se basa en el calculo ya sea de Δy o Δx por medio de ecuaciones.
Se efectúa un muestreo de la línea en intervalos unitarios en una coordenada y se determina los valores enteros correspondientes mas próximos a la trayectoria de la línea para la otra coordenada.

De un elemento matemático continúo e infinito se debe discretizar (representar a través de pixeles) para representar en una pantalla.

### <span style="color:#8be9fd;">Algoritmo de Bresenham Básico (1965)</span>
Hace mas de medio siglo.
Dicho algoritmo lo que busca es un par de pixeles que estén mas cerca según la trayectoria de la línea recta.
Si se hace la suposición de que se debe desplegar el pixel (Xk, Yk), a continuación se necesita decidir que pixel se debe desplegar en la columna Xk+1.
Las alternativas son (Xk+1, yk), y (Xk+1, Yk+1).
Al realizar el muestreo en la posición Xk+1 designamos la separación en pixeles verticales de la trayectoria de la línea matemática como d1 y d2. 
![[Pasted image 20230530071748.png]]
d1 = y - yk = m(Xk+1) + b - Yk
d1 = (Yk + 1) - y = Yk + 1 - m(Xk + 1) - b
#### Resumen
1. Se capturan los dos extremos de la línea y se almacena el extremo izquierdo en (x0, y0)
2. Se carga (x0, y0) en el bufer de estructura, o sea, se trata del primer punto
3. Se calculan las constantes Δy, Δx, 2Δy - 2Δx, y se obtiene el valor inicial para el parámetro de decisión como p0 = 2Δy - Δx
4. En cada xk a lo largo de la línea, que inicia en k = 0, se efectúa la prueba siguiente: si pk < 0, el siguiente punto que se debe trazar es (xk+1, yk) y __pk+1 = pk +2Δy__. De otro modo, el siguiente punto a trazar es (xk+1, yk+1) y  pk+1 = pk + 2Δy - 2Δx.
5. Se repite el paso 4 otras Δx veces.

| <span style="color:#ff79c6;">__Valor de $P_k$__</span> | Punto a trazar | <span style="color:cyan;">__Valor de $P_k + 1$__</span> |
| --------- | --------- | --------- |
| $P_k < 0$  | $(x_k + 1,y_k)$   | $P_k + 1 = P_k +2Δy$   |
| $P_k > 0$   | $(x_k+1, y_k+1)$   | $P_k + 1 = P_k + 2Δy - 2Δx$   |

### <span style="color:#6AA56E;">Educación paramétrica de la línea recta </span>
$L:\vec{P}=\vec{P_0}+t\vec{u}$
Dónde:
$L$: Línea recta
$\vec{P_0}$ : Vector de posición de un punto cualquiera de la línea recta
$t$: Parámetro cualquiera
$\vec{u}$: Vector director de la línea recta
![[Pasted image 20230530133026.png]]
$\vec{u}=\vec{P_0P_1}=\vec{P_1}-\vec{P_0}$
### <span style="color:#6AA56E;">Educación paramétrica de la Circunferencia </span>
Usando la identidad trigonométrica: $sen^2θ+cos^2θ=1$ y la ecuación de la cartesiana de la circunferencia en su forma ordinaria $(x-h)^2+(y-k)^2=r^2$ .
La ecuación anterior la podemos convertir en lo siguiente:  $(\frac{x-h}{r})^2+(\frac{y-k}{r})^2=1$ . Con lo anterior es posible parametrizar, y quedaría lo siguiente:

| $\frac{x-h}{r}$ | $\frac{x-h}{r}=cosθ$ |  $x=h+rcosθ$ |
| --------- | --------- | --------- |
| $\frac{y-k}{r}$ | $\frac{y-k}{r}=senθ$   | $y=k+rsenθ$  |

### <span style="color:#6AA56E;">Educación paramétrica de la Elipse </span>
Ecuación general: $((x-h)/a)^2+((y-k)/b)^2=1$
Se usa la misma lógica y se obtiene lo siguiente:

| $\frac{x-h}{a}$ | $\frac{x-h}{a}=cosθ$ |  $x=h+acosθ$ |
| --------- | --------- | --------- |
| $\frac{y-k}{b}$ | $\frac{y-k}{b}=senθ$   | $y=k+bsenθ$  |

### <span style="color:#6AA56E;">Educación paramétrica de la Parábola </span>
La parábola __no__ se puede parametrizar con una sola regla de correspondencia.
Partiendo de $y=x^2$ podemos desplazar la parábola con centro en el origen de la siguiente manera: $4p(y-k)=(x-h)^2$ .
La parábola con centro en el origen puede ser parametrizada de la siguiente manera:
1. $x=t$
2. $y=t^2$ 
Ahora podemos agregar la parametrización a la ecuación desplazada de la siguiente manera:
1. $x-h=t$
2. $4p(y-k)=t^2$  
Y finalmente teniendo en cuenta lo anterior podemos despejar x y y para dejarlas parametrizadas en función de t:
1. $x=h+t$
2. $y=\frac{1}{4p}t^2+k$

### <span style="color:#6AA56E;">Educación paramétrica de la Hipérbola</span>
A diferencia de la circunferencia la ecuación general de la hipérbola es una resta de cuadrados $(\frac{x-h}{a})^2-(\frac{y-k}{b})^2=1$ , por lo que es necesario usar de la misma manera una identidad trigonométrica que sea una resta de cuadrados. En este caso se usará la siguiente: $sec^2θ-tan^2θ=1$ pudiendo igualar de la siguiente manera:

| $\frac{x-h}{a}$ | $\frac{x-h}{r}=secθ$ |  $x=h+asecθ$ |
| --------- | --------- | --------- |
| $\frac{y-k}{b}$ | $\frac{y-k}{r}=tanθ$   | $y=k+btanθ$  |
Como en unity no se tiene la secante se puede utilizar la siguiente equivalencia:
$x=h+\frac{a}{cosθ}$
Entonces las ecuaciones paramétricas quedan así:
1. $x=h+\frac{a}{cosθ}$
2. $y=k+btanθ$

### <span style="color:#FF79C6;">Resumen y ecuaciones paramétricas de las conicas</span>
#### <span style="color:#6AA56E;">Línea Recta</span>
$L:\vec{P}=\vec{P_0}+t\vec{u}$
#### <span style="color:#6AA56E;">Circunferencia </span>
1. $x=h+asecθ$
2. $y=k+rsenθ$
#### <span style="color:#6AA56E;">Elipse </span>
1. $x=h+acosθ$
2. $y=k+bsenθ$
#### <span style="color:#6AA56E;">Parabola </span>
1. $x=h+t$
2. $y=\frac{1}{4p}t^2+k$
#### <span style="color:#6AA56E;">Hipérbola </span>
1. $x=h+\frac{a}{cosθ}$
2. $y=k+btanθ$


