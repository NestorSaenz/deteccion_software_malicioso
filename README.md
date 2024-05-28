# <h1 align="center">**`Detección de software malicioso`** <br> </h1>

<p align="center">
<img src="https://github.com/NestorSaenz/deteccion_software_malicioso/blob/main/imagenes/Malware-que-afecta-a-Mac-detectado-00.jpg"  width="300" height="200" >
</p>

## **Contexto**

EL desarrollo del presente proyecto surge de la necesidad de poder clasificar un sofware como benigno o malware, los datos son extraidos de la pagina oficial del instituto canadiense de ciberseguridad [link](https://www.unb.ca/cic/datasets/iotdataset-2023.html) el objeto de la presente investigación es mejorar las metricas del modelo de Machine Learnig que maneja el instituto.

## **Analisís exploratorio de los datos**

La calidad de los datos provenientes de la pagina oficial es buena por lo tanto no amerita ninguna transformacion inicial, despues de explorar los datos se evidencia que las variables independientes estan muy desbalanceadas, hay clases con muy pocos datos, a continuación, se puede visualizar: <p align="center">
<img src="https://github.com/NestorSaenz/deteccion_software_malicioso/blob/main/imagenes/Captura%20de%20pantalla%202024-05-28%20004828.png"  width="500" height="300" >
</p>

Para darle solución a este problema lo que hice fue tomar la etiqueta con la minima cantidad y tomar ejemplos aleatorios de las otras etiquetas con esa misma cantidad exceptuando la etiqueta de benigno, asi quedaron los datos despues de dicho proceso:
<p align="center">
<img src="https://github.com/NestorSaenz/deteccion_software_malicioso/blob/main/imagenes/etiquetas_balanceado.png"  width="500" height="300" >
</p>

Revisando la etiqueta objetivo tambien se observa un desbalanceo muy fuerte como se ve en la siguiente imagen:
<p align="center">
<img src="https://github.com/NestorSaenz/deteccion_software_malicioso/blob/main/imagenes/target_desbalanceado.png"  width="500" height="300" >
</p>

Despues del balanceo quedó con la siguiente estructura:
<p align="center">
<img src="https://github.com/NestorSaenz/deteccion_software_malicioso/blob/main/imagenes/tarjet_balanceado.png"  width="500" height="300" >
</p>

una vez los datos han sido balanceados y ajustados se procede a la creación del modelo, para llevar a cabo la predicción se utilizo *`las redes neuronales convolucionales`.*

## **Deep Learnig**
Se carga el dataset procesado, y se codifican las variables, el modelo de clasificación se separa en *`malware`* = 1 y *`BenignTraffic`* = 0, con el metodo *`SMOTE`* se aumentan todos los datos del dataframe para que al modelo le sea mas facil reconocer las clases de las variasbles independientes, y asi obtener mejores resultados.

se establecen 4 Callbacks para controlar el corte temprano del entrenamiento y asi optimizar recursos calibrando por ejemplo la tasa de aprendizaje. antes de intanciar el modelo se realiza un scalado en este caso se utilizó el StandarScaler(), Se instancia el modelo con capas convolucionales, agrupamiento, densas, drop out y normalización. la regularización empleada para evitar el sobreajuste es "L2", se compila el modelo con el optimizador, función de perdida y metricas de evaluación, se especifica la cantidad de iteraciones, callbacks, etc, una vez entrenado se visualizan las graficas:

* Función de perdida.
* Accuracy.
* Tasa de aprendizaje.

Los resultados del modelo se pueden ver a continuación
