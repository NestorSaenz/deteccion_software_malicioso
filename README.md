# <h1 align="center">**`Detección de software malicioso`** <br> </h1>

<p align="center">
<img src="https://github.com/NestorSaenz/deteccion_software_malicioso/blob/main/imagenes/Malware-que-afecta-a-Mac-detectado-00.jpg"  width="300" height="200" >
</p>

## **Contexto**

EL desarrollo del presente proyecto surge de la necesidad de poder clasificar un sofware como benigno o malware, los datos son extraidos de la pagina oficial del instituto canadiense de ciberseguridad [link](https://www.unb.ca/cic/datasets/iotdataset-2023.html) el objeto de la presente investigación es mejorar las metricas del modelo de Machine Learnig que maneja el instituto.

## **Analisís exploratorio de los datos**

La calidad de los datos proveniento de la pagina oficial es buena por lo tanto no amerita ninguna transformacion inicial, despues de explorar los datos se evidencia que las variables independientes estan muy desbalanceadas, hay clases con muy pocos datos, a continuacion se puede visualizar: <p align="center">
<img src="https://github.com/NestorSaenz/deteccion_software_malicioso/blob/main/imagenes/Captura%20de%20pantalla%202024-05-28%20004828.png"  width="500" height="300" >
</p>

Para darle solución a este problema lo que hice fue tomar la etiqueta con la minima cantidad y tomar ejemplos aleatorios de las otras etiquetas con esa misma cantidad exceptuando la etiqueta de benigno, asi quedaron los datos despues de dicho proceso:
<p align="center">
<img src=""  width="500" height="300" >
</p>
