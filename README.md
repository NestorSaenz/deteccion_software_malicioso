# <h1 align="center">**`Detección de software malicioso`** <br> </h1>

<p align="center">
<img src="https://github.com/NestorSaenz/deteccion_software_malicioso/blob/main/imagenes/Malware-que-afecta-a-Mac-detectado-00.jpg"  width="300" height="200" >
</p>

## **Contexto**

EL desarrollo del presente proyecto surge de la necesidad de poder clasificar un software como benigno o malware, los datos son extraídos de la pagina oficial del instituto canadiense de ciberseguridad [link](https://www.unb.ca/cic/datasets/iotdataset-2023.html). El objeto de la presente investigación es mejorar las métricas del modelo de Machine Learnig que maneja el instituto.

## **Análisis exploratorio de los datos**

La calidad de los datos provenientes de la página oficial es buena, por lo tanto no amerita ninguna transformación inicial. Después de explorar los datos se evidencia que las variables independientes estan muy desbalanceadas, hay clases con muy pocos datos; a continuación, se puede visualizar: <p align="center">
<img src="https://github.com/NestorSaenz/deteccion_software_malicioso/blob/main/imagenes/Captura%20de%20pantalla%202024-05-28%20004828.png"  width="500" height="300" >
</p>

Para darle solución a este problema lo que hice fue tomar la etiqueta con la mínima cantidad y tomar ejemplos aleatorios de las otras etiquetas con esa misma cantidad, exceptuando la etiqueta de benigno. Así quedaron los datos después de dicho proceso:
<p align="center">
<img src="https://github.com/NestorSaenz/deteccion_software_malicioso/blob/main/imagenes/etiquetas_balanceado.png"  width="500" height="300" >
</p>

Revisando la etiqueta objetivo también se observa un desbalanceo muy fuerte como se ve en la siguiente imagen:
<p align="center">
<img src="https://github.com/NestorSaenz/deteccion_software_malicioso/blob/main/imagenes/target_desbalanceado.png"  width="500" height="300" >
</p>

Después del balanceo quedó con la siguiente estructura:
<p align="center">
<img src="https://github.com/NestorSaenz/deteccion_software_malicioso/blob/main/imagenes/tarjet_balanceado.png"  width="500" height="300" >
</p>

Una vez los datos han sido balanceados y ajustados se procede a la creación del modelo. Para llevar a cabo la predicción se utilizó una *`red neuronal convolucional`.*

## **Deep Learnig**
Se carga el dataset procesado y se codifican las variables. El modelo de clasificación se separa en *`malware`* = 1 y *`BenignTraffic`* = 0. Con el metodo *`SMOTE`* se aumentan todos los datos del dataframe para que al modelo le sea más fácil reconocer las clases de las variables independientes y así obtener mejores resultados.

Se establecen 4 Callbacks para controlar el corte temprano del entrenamiento y así optimizar recursos, calibrando, por ejemplo, la tasa de aprendizaje. Antes de instanciar el modelo se realiza un escalado; en este caso se utilizó el StandarScaler(). Se instancia el modelo con capas convolucionales, agrupamiento, densas, dropout y normalización. la regularización empleada para evitar el sobreajuste es "L2". Se compila el modelo con el optimizador, función de pérdida y métricas de evaluación; se especifica la cantidad de iteraciones, callbacks, etc.Una vez entrenado se visualizan las gráficas:

* Función de pérdida.
* Accuracy.
* Tasa de aprendizaje.

Los resultados del modelo se pueden ver a continuación:

## Métricas entrenamiento
<p align="center">
<img src="https://github.com/NestorSaenz/deteccion_software_malicioso/blob/main/imagenes/metricas_entrenamiento.png"  width="300" height="200" >
</p>

## Métricas prueba
<p align="center">
<img src="https://github.com/NestorSaenz/deteccion_software_malicioso/blob/main/imagenes/metricas_entrenamiento.png"  width="300" height="200" >
</p>

