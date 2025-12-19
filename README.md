# Agradecimientos
El presente trabajo de investigación se hizo posible gracias a la beca de trabajo del [VIII Fondo Concursable 2025 de la Facultad de Ciencia USACH](https://www.fciencia.usach.cl/noticias/viii-fondo-concursable-2025-impulsa-la-formacion-investigativa-y-la-movilidad-de-las-y-los)y al profesor [PhD. Leonardo Videla Muñoz](https://www.dmcc.usach.cl/personas/leonardo-videla-munoz/), el cual me presentó el tema de investigación y me motivó a no rendirme antes de empezar. Fue un pilar fundamental para mi entendimiento de los sistemas estocásticos y toma de decisiones respecto a mi futuro académico.

# Marco Teórico
El año 2024 se publica un [articulo](https://nsojournals.onlinelibrary.wiley.com/doi/10.1111/oik.10980) que le propone una nueva perspectiva a la paradoja ecologica "competencia y especies coexistentes v/s diversidad biologica" mediante el uso de una familia de modelos descritos por
$$
\dot{x}= \frac{x}{\theta}(1-x^{\theta})
$$
para el cual los valores de $\theta$ lleva a crecimiento en regimenes *super* o *sub* lineales que pueden explicar la estabilidad del sistema ecologico ante gran variedad de especies. 
El [articulo](https://inria.hal.science/hal-05156816v1) que da origen a este trabajo propone el analisis de estos modelos mediante procesos de nacimiento y muerte $Z^{K,\alpha}_{t}$ con tasas de cambio 
$$
b_{\alpha}(x)= \begin{cases}\frac{x}{\theta} +\alpha x& \text { if } \theta>0 \\ x|\log (x)| \mathbb{1}_{x<1}+\alpha x& \text { if } \theta=0 \\ \frac{x^{1+\theta}}{|\theta|}+\alpha x & \text { if } \theta<0\end{cases}\quad\text{y}\quad d_{\alpha}(x)= \begin{cases}\frac{x^{1+\theta}}{\theta}+\alpha x & \text { if } \theta>0, \\ x|\log (x)| \mathbb{1}_{x>1} +\alpha x& \text { if } \theta=0, \\ \frac{x}{|\theta|}+\alpha x & \text { if } \theta<0 .\end{cases}
$$
cuyo generado infinitesimal se define como 
$$
L^{K, \alpha} f(x)=K b_\alpha(x)\left(f\left(x+\frac{1}{K}\right)-f(x)\right)+K d_\alpha(x)\left(f\left(x-\frac{1}{K}\right)-f(x)\right)
$$
, y sus versiones difusivas para el cual el proceso difusivo $(Z_{t})_{t\geq 0}$ es solucion de la EDE para valores del parametro $\theta\neq 0$
$$
d Z_t=Z_t \frac{1-Z_t^\theta}{\theta} d t+\sqrt{\frac{Z_t}{K|\theta|}\left(1+2 \alpha|\theta|+Z_t^\theta\right)} d B_t
$$
y para $\theta=0$
$$
d Z_t=Z_t \log \left(1 / Z_t\right) d t+\sqrt{\frac{Z_t}{K}\left(\left|\log \left(Z_t\right)\right|+2 \alpha\right)} d B_t,
$$
Estas ecuaciones nacen de realizar una expansion de Taylor al proceso infinitesimal del proceso de B&D cuando $K\to \infty$ y cualquier termino de segundo orden lo despreciamos.

En este trabajo, se estudiaron el comportamiento de esta familia adaptada de modelos mediante metodos numericos probabilistas, en donde se validan y visualizan los resultados del articulo original. Los cuales indican que los tiempos de extincion del modelo del proceso B&D y su aproximacion difusiva para el regimen sublineal son irrealistas en terminos biologicos, puesto que, aunque la extincion de la poblacion esta asegurada, cuando partimos  desde una densidad inicial muy pequeña, la trayectoria estocastica convege asintoticamente en una poblacion espuria que no se extingue en ningun instante $t\leq \exp(VK)$ para alguna constante $V$ y la capacidad de carga $K$.

# Notebooks 
El proyecto se divide en tres notebooks Jupyter que contienen los análisis hechos a lo largo del proyecto investigativo.
- Aproximación estocástica de las soluciones deterministas de EDO
	De la EDO segun el valor del parametro $\theta$ podemos definir diferentes modelos decrecimientos poblacionales, no solo el sublineal $(-1<\theta<0)$.
- Visualización de tiempos de extinción y estimación de constante para modelo B&D
	Se hizo  una simulacion paralelizada de multiples trayectorias mediante JAX bajo el algoritmo de Gilliespie, con esto se busco aumentar la representatividad de los resultados al simular multiples trayectorias
- Visualización de tiempos de extinción para modelo difusivo del proceso B&D
	En este caso, podemos notar que los terminos difusivos de las EDE no cumplen las condiciones para una resolucion numerica mediante Euler-Maruyana (la lipchitcianidad y positividad de las soluciones) se utilizan un esquema modificado de este metodo en donde se discretiza la EDE comparando los estados presente y pasados, pero se implementa una funcion de trucamiento que preserva positividad. Detallado con mas formalidad en el [articulo](https://arxiv.org/abs/2509.22513) 