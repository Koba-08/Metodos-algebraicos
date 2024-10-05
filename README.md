# Metodos algebraicos
Estos metodos son utilizados para para obtener un determinado comportamiento en un sistema de lazo cerrado, esto se logra mediante metodos algebraicos en donde la solucion a ellos es encontrar el valor de un controlador.
para obtener un resultado a este metodo la base fundamental es modificar la funcion de transferencia en lazo cerrado para asi encontras la respuesta deseada.

existen dos enfoques:
1. por igualacion de modelo
2. por igualacion de coeficientes
   
$$r->(|c(z)->G(z)->|Go(z))y$$
         
   
## Igualacion de modelo por metodos algebraicos
teniendo o sabiendo que G(Z) es la funcion de lazo abierto donde G(Z) es conocida y asi mismo conociendo la respuesta deseada que se representa en una funcion de transferencia de lazo cerrado Go(z) se puede realizar este metodo por igualacion de modelo para encontrar la fincion de transferencia del controladorC(z) para asegurar esa respuesta.

se asume que G y Go son funciones causales entonces:

$$G_{0}\left( S \right)= \frac{C\left( z \right)G\left( Z \right)}{1+C\left( z \right)G\left( Z \right)}$$

despejando para encontrar el valor del controlador se obtiene

$$C\left( Z \right)= \frac{G_{0}\left( Z \right)}{G\left( z \right)-G_{0}\left( Z \right)G\left( Z \right)}$$

NOTA: si se tiene polos fuera del circulo unitario o en z=-1, la retroalimentacion unitaria no puede ser implementada en cualquier $$G_{0}\left( Z \right)$$; debido a que los controladores podrian ser no implementables.

💡 Ejemplo

para la planta: $$G\left( Z \right)= \frac{0.01\left( Z+1 \right)}{Z^{2}-2.01Z+1}$$
obtener la funcion de transferencia en lazo cerrado con las condiciones:
-para hacer estable el sistema
-con respuesta subamortiguada
-sobreimpulso menor a 5%

se encuentra la funcion de transferencia en lazo cerrado:

$$G_{0}\left( Z \right)= \frac{0.009Z+0.008}{Z^{2}-1.801+0.818}$$

se remplaza en:
$$C\left( Z \right)= \frac{G_{0}\left( Z \right)}{G\left( z \right)-G_{0}\left( Z \right)G\left( Z \right)}$$

y se obtiene que la funcion de transferencia del controlador C(z) es:

$$C\left( Z \right)= \frac{0.934^{3}-1.004z^{2}-0.822z+0.973}{z^{3}-0.81z^{2}-z+0.81}$$


## Igualacion de coeficientes

Conociendo la funcion de lazo abierto G(z) y la ubicacion de los polos que se desean(se dan o se les coloca un valos aleatoreo donde se cancelen dendro del circulo unitario), se puede representar un polinomio caracteristico

💡 Ejemplo
diseñar un controlador de accion proporcional para los polos ubicados en lazo cerrado en:
P1=0.91+j0.23;P2=0.91-j0.23

$$G\left( Z \right)= \frac{0.0043}{Z^{2}-1.819Z+0.8187}$$

el polinomio caracteristico deseado en lazo cerrado es:

$$\left( z-0.91+j0.23 \right)\left( z-0.91-j0.23 \right)=z^{2}-1.82z+0.881$$

calculando la funcion de transferencia de lazo cerrado se obtiene :

polinomio caracteristico deseado: $$Z^{2}-1.82Z+0.881$$
polinomio caracteristico lazo cerrado:  $$Z^{2}-1.819Z+0.8187+k*0.0043$$

al igualar los 2 polinomios y asi mismo sus coeficientes se evidencia que no se puede solucionar ya que no son iguales y no se pueden tampoco igualar.

Para poder solucionar esto se utiliza las funciones causales propias en donde se colocan mas variables al controlador para asi poder generar una mayor cantidad de incognitas en cada coeficiente para asi despejar un valor en el que puedan quedar igualados

NOTA: El orden C(z) debe ser 1 grado menor con respecto a la planta en lazo abierto.

se utiliza el controlador con la siguiente función:

$$C(Z)=\frac{B_{0}+B_{1}Z}{A_{0}+A_{1}Z}$$

ahora el sistema es de tercer orden por eso se deben ubicar 3 polos
Z=0.91+j0.23
Z=0.91-j0.23
Z=0.91
reemplazando en

$$G_{0}\left( S \right)= \frac{C\left( z \right)G\left( Z \right)}{1+C\left( z \right)G\left( Z \right)}$$

se obtiene:

$$G_{0}\left( z \right)=\frac{0.0043\left( B_{0}+B_{1}Z \right)}{A_{1}Z^{3}+Z^{2}\left( A_{0}-1.819A_{1} \right)\left(  +0.8187A_{1}-1.819A_{0}+0.0043BA_{1}\right)Z+0.8187A_{0}+0.0043B_{0}}$$

se igualan los polinomios caracteristicos  y se despejan las incognitas para asi encontrar el valor de la función de transferencia del controlador

al igualar y remplazar se encuentran A0-B0-A1-B1
A0=-0.911
A1=1
B0=-12.99
B1=14.23

El controlador seria:

$$C\left( Z \right)= \frac{B_{0}+B_{1}Z}{A_{0}+A_{1}Z}= \frac{-12.99+14.23Z}{-0.911+Z}$$


# Ejercicios

📚 Ejercicio 1:
Diseño de Controlador por Igualación de Modelo

se da la planta
$$G(Z) = \frac{0.01(Z + 3)}{z^2 - 1.8Z + 0.81} 
$$

se encuentra la funcion de trnasferencia en lazo cerrado:
$$G_0(Z) = \frac{0.04z + 0.02}{Z^2 - 1.6Z + 0.64}$$

se reemplaza en :

$$G_0(z) = \frac{C(z)G(z)}{1 + C(z)G(z)}$$

$$C(z) = \frac{G_0(z)}{G(z) - G_0(z)G(z)}$$

sustituyendo

$$C(z) = \frac{\frac{0.04z + 0.02}{z^2 - 1.6z + 0.64}}{\frac{0.01(z + 3)}{z^2 - 1.8z + 0.81} - \frac{0.04z + 0.02}{z^2 - 1.6z + 0.64} \cdot \frac{0.01(z + 3)}{z^2 - 1.8z + 0.81}}$$

obtenemos:

$$C(Z)=\frac{0.04Z + 0.02}{\frac{0.01(Z + 3)(Z^2 - 1.6Z + 0.64) - (0.04Z + 0.02)(0.01(Z + 3))}{(Z^2 - 1.8Z + 0.81)(Z^2 - 1.6Z + 0.64)}}$$


📚Ejercicio 2:
Diseñar un controlador para la planta:
$$G\left( Z \right)= \frac{0.004\left( Z+1 \right)}{Z^{2}-1.6Z+0.64}$$
Polos deseados:
$$P_{1}= 0.5+j0.5, P_{2}=0.5-j0.5$$

el polinomio caracteristico deseado es:

$$\left( Z-P_{1} \right)\left(  Z-P_{2} \right)=\left( Z-0.5+j0.5 \right)\left( Z-0.5-j0.5 \right)=Z^{2}-Z+0.5$$

se encuentra que el controlador es dado por:

$$\frac{A_{0}+A_{1}Z}{B_{0}+B_{1}Z}$$

por ende se encuentran 3 polos:
$$P_{1}= 0.5+j0.5, P_{2}=0.5-j0.5, P_{3}=0.5$$

reemplazando para encontrar $$G_{0}\left( Z \right)$$ obtenemos que:

$$G_{0}\left( Z \right)=\frac{\frac{A_{0}+A_{1}Z}{B_{0}+B_{1}Z}.\frac{0.004\left( Z+1 \right)}{Z^{2}-1.6Z+0.64}}{1+\frac{A_{0}+A_{1}Z}{B_{0}+B_{1}Z}.\frac{0.004\left( Z+1 \right)}{Z^{2}-1.6Z+0.64}}$$

simplificando obtenemos :

$$G_{0}\left( Z \right)=\frac{0.004\left( A_{1}Z^{2}\left( A_{0}+ A_{1}\right)Z \right)+A_{0}}{\left(  B_{0}+B_{1}Z\right)\left( Z^{2}-1.6Z+0.64 \right)+0.004\left( A_{0}\left( Z+1 \right)+A_{1}Z\left( Z+1 \right) \right)}$$

se igualan los coeficientes de los polinomios y se encuentran los valores de:

A0=7, 
A1=185, 
B0=1, 
B1=-0.26

dando que el controlador es:

$$C(Z)=\frac{7+185Z}{1-0.26Z}$$

## Conclusiones

Los métodos algebraicos son herramientas poderosas en el diseño de controladores para sistemas de lazo cerrado, permitiendo ajustar el comportamiento dinámico de un sistema a través de la determinación de funciones de transferencia del controlador. Mediante la igualación de modelo y la igualación de coeficientes, es posible derivar controladores que aseguren la estabilidad y el rendimiento deseado del sistema. Sin embargo, no se puede olvidar las limitaciones de estos métodos, como la implementación de controladores con polos fuera del círculo unitario, que la planta tenga sus parametros bien definitos, etc. , que pueden afectar la viabilidad del sistema en la práctica.
