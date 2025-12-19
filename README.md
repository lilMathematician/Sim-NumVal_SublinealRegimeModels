# Agradecimientos
El presente trabajo de investigación se hizo posible gracias a la beca de trabajo del [VIII Fondo Concursable 2025 de la Facultad de Ciencia USACH](https://www.fciencia.usach.cl/noticias/viii-fondo-concursable-2025-impulsa-la-formacion-investigativa-y-la-movilidad-de-las-y-los)y al profesor PhD. Leonardo Videla Muñoz, el cual me presentó el tema de investigación y me motivó a no rendirme antes de empezar. Fue un pilar fundamental para mi entendimiento de los sistemas estocásticos y toma de decisiones respecto a mi futuro académico.

# Marco Teórico

$$
\dot{x}= \frac{x}{\theta}(1-x^{\theta})\tag{1}
$$

^ed4dcc

# Notebooks 
**Muy importante**: este proyecto se llevo a cabo simulaciones en paralelo mediante el uso de GPU potentes, los resultados dependiendo de algunos parametros pueden tardar mucho en sistemas que no posean el requerimiento adecuado


El proyecto se divide en tres notebooks Jupyter que contienen los análisis hechos a lo largo del proyecto investigativo.
- Aproximación estocástica de las soluciones deterministas de EDO
	De la EDO [[#^ed4dcc]] segun el valor del parametro $\theta$ podemos definir diferentes modelos decrecimientos poblacionales, no solo el sublineal $(-1<\theta<0)$.
- Visualización de tiempos de extinción y estimación de constante para modelo B&D
	
- Visualización de tiempos de extinción para modelo difusivo del proceso B&D