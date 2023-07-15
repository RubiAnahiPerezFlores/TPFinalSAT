# TPFinalSAT
Trabajo Integrador Final de SAT (81.75) - Fundamentos del desarrollo de software y análisis de datos en Python

Repositorio para TP Final

Para este trabajo, se planteo explorar y analizar una base de datos de abandono de clientes en un banco financiero.
Análisis de la tasa de abandono de clientes:

El abandono de clientes es un fenómeno bien conocido en todas las empresas, cada negocio tiene clientes y les vende productos y servicios que éstos pueden dejar de comprar o consumir. Lo que se vende es irrelevante para el hecho de que el cliente siempre está presente. Incluso si el negocio es B2B, hay clientes, sólo que esta vez son otros negocios. Por lo tanto, el cliente tiene un rol indispensables en cada negocio y el perderlos es terrible sin importar lo que se venda.

Implementando lo visto en la cursada del SAT, se tiene como objetivo en una primera instancia ver cómo se puede reducir la tasa de abandono de clientes, haciendo uso de las herramientas de Machine Learning.
Una vez definido el problema con el que se va a trabajar, es relevante mencionar que el aumento de las tasas de retención de clientes en un 5% aumenta los beneficios entre un 25% y un 95% en el negocio. Y por otro lado cuesta cinco veces más atraer a un nuevo cliente que mantener uno existente.

Se decidió plantear un modelo de análisis de abandono de clientes, se tuvieron en cuenta ciertas características de los clientes que pueden llegar a influir en la continuacion o abandono del cliente:

RowNumber (Numero de fila)

CustomerId (Identificación del cliente)

Surname (Apellido)

CreditScore (Puntaje crediticio)

Geography (Geografía)

Gender (Género)

Age (Edad)

Tenure (Tenencia)

Balance (Balance)

NumOfProducts (Número de Productos)

HasCrCard (TieneCrCard)

IsActiveMember (EsMiembroActivo)

EstimatedSalary (Salario Estimado)

Exited (Salido) En este caso, es un clasificador binario ya que tenemos 2 clases –‘abandona’ y ‘no abandona’

Luego del análisis se buscará estar en condiciones para identificar si efectivamente estos atributos afecta, o tiene una influencia en la decisión del cliente de abandonar o no la empresa.

4.Analisis realizado:

Para hacernos una idea breve de cómo se relacionan nuestros datos con nuestro label (la columna “Exited”, que marca si ese cliente se fue del banco o no) vamos a explorar visualmente los datos con algunos gráficos básicos.

Así podremos empezar a tener una idea de qué atributos pueden ser importantes a la hora de predecir el abandono. Esta exploración de variables puede ser mucho más compleja, pero es importante hacerla de manera al menos de un modo básico porque nos puede dar pistas sobre varios puntos fundamentales de aquí en adelante como por ejemplo:

  - Qué atributos pueden ser importantes por sí mismos (si ayudan a diferenciar claramente los clientes que abandonan de los que no)
  - Qué atributos pueden ser útiles para generar atributos compuestos para incrementar el rendimiento del algoritmo
  - Potenciales problemas de calidad de datos
  - Presencia de nulos

4. 1  Una de las columnas que puede ser importante en el análisis puede ser Edad. 

Vemos que al segmentarla por el label, diferencia los casos 0 (no abandona) y 1 (abandona) de manera significativa. 

Sin embargo, el hecho de que por sí misma diferencie el label no es una garantía de que al entrenar nuestro modelo de predicción de abandono tenga una gran importancia, ya que la mayoría de los modelos de Machine Learning actuales se aprovechan de las relaciones entre atributos además de su importancia individual.

4.2  Para las variables categóricas (aquellas no-numéricas que representan categorías, como “Género” o “País”) podemos crear histogramas en vez de boxplots para representar la distribución de los valores.

En un primera instacia no parece que estos atributos segmenten bien el hecho de que un cliente abandone a la empresa.

4.3 Como vemos, esta codificación sólo nos traduce de texto a números. Esto hace que ahora el modelo pueda entrenar con éstas variables. Sin embargo, no suele ser la mejor manera de codificar porque da a entender al modelo que hay una relación de magnitud (como la hay entre los números) y esto no es cierto en muchos casos.

Además de codificar también hemos partido el dato en dos conjuntos, entrenamiento y test. Entrenamiento tiene 7000 filas y test 3000 para poder medir el rendimiento de nuestro modelo con dato que nunca haya visto (como los nuevos clientes que tenga que analizar cuando lo estemos usando en producción en la empresa).

4.4 Nuestro primer modelo de análisis de abandono de clientes

 Ahora que ya tenemos el dato separado en entrenamiento y test y con la forma adecuada para que trabajar con él. Vamos a usar un bosque de decisión (la combinación de muchos árboles de decisión individuales) por ser un modelo potente y robusto, rápido de entrenar y con una fácil interpetación.
Una vez entrenado, usaremos el conjunto de test para evaluar el rendimiento de nuestro modelo prediciendo qué clientes abandonarán nuestro negocio y cuáles no.
En este caso, la detección de aquellos casos que SÍ abandonan, y dada la codificación de del label (0 -> se queda / 1 -> abandona) se busca ver Precision (abandonos predichos correctamente / (abandonos predichos correctamente + abandonos falsamente predichos)). 
Las métricas son bastante buenas si vemos el acierto (accuracy) del 87%. Pero si vemos la precision tenemos un valor de 46%, no es tan buena como parecía en un principio.

Conclusion
El abandono de clientes se basa en cientos de factores,se consider que tener modelos más simples (siempre y cuando funcionen lo suficientemente bien) suele ser mejor que los modelos demasiado complicados, ya que normalmente generalizan mejor con nuevos datos (funcionarán mejor contra los datos no vistos).
Sabiendo qué clientes son más propensos a irse se pueden diseñar campañas de retención y evitar su abandono.
Se recomienda conocer las razones por las que los clientes que probablemente abandonan asi se dirige la atención a los perfiles adecuados y diseñar acciones correpondientes.


