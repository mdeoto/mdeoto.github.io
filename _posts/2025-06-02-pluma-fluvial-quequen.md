---
layout: post
title: "Pluma fluvial del Quequén-Salado: un caso visible desde el espacio"
date: 2025-06-02 18:00:00 -0300
categories: [oceanografía, modelado]
tags: [pluma fluvial, Quequén-Salado, OpenDrift, GOES-16, Sentinel-2]
image: /assets/img/pluma_quequen_teaser.jpg
disqus_comments: true
---

En marzo de 2025, una serie de lluvias excepcionales afectaron al sudoeste de la Provincia de Buenos Aires. Como consecuencia, varios ríos y arroyos desbordaron, entre ellos el **río Quequén-Salado**, que presentó una **pluma fluvial superficial (PFS)** claramente visible desde el espacio.

Durante este evento, trabajamos junto a mi colega Diana Rodríguez en la detección y modelado numérico de dicha pluma utilizando imágenes satelitales y simulaciones con **OpenDrift**, un modelo lagrangiano de código abierto.

## ¿Qué es una pluma fluvial?

Es una masa de agua dulce y sedimentos que se extiende desde la desembocadura de un río hacia el mar. Dependiendo de las condiciones ambientales (viento, mareas, corrientes), esta pluma puede cambiar su forma, dirección y extensión rápidamente.

---

## Observaciones satelitales

Utilizamos dos sensores clave:

- **GOES-16 / ABI (GeoColor)**: con imágenes cada 10 minutos, ideal para seguir procesos costeros rápidos.
- **Sentinel-2 / MSI**: con mayor resolución espacial, para validar visualmente los bordes de la pluma.

![Imagen Sentinel](/assets/img/pluma_quequen_sentinel2.png)

Las imágenes nos permitieron **delimitar manualmente** el área ocupada por la pluma durante varias horas del 13 de marzo. Estas delimitaciones se usaron luego para validar las simulaciones.

---

## Simulaciones con OpenDrift

Realizamos **35 simulaciones** de la pluma usando OpenDrift. Introducimos una **fuente artificial de descarga fluvial** en la desembocadura del río, y forzamos el modelo con:

- **Corrientes barotrópicas** del modelo SIMMAR-PCA (Resultado del Proyecto PRONOMAR)
- **Viento de 10 m** del modelo WRF-SMN

Exploramos distintos escenarios para evaluar la sensibilidad al forzante, pero también cambiando parametros clave en la dispersión 2D como el coeficiente de turbulencia horizontal y los errores aleatorios del viento y las corrientes. 

---

## Validación de resultados

Medimos la **coincidencia espacial** entre la pluma simulada y la observada usando dos indicadores:

- **POD (Probability of Detection)**
- **FAR (False Alarm Ratio)**

![Comparación de polígonos](/assets/img/poligono_comparacion.png)

El mejor resultado (POD: 0.96, FAR: 0.27) se obtuvo cuando se incluyeron las **corrientes marinas y la descarga fluvial**, destacando su importancia frente a simulaciones forzadas solo con viento o pluma sintética. Los cambios en el parámetro de turbulencia horizontal y la introducción de errores aleatorios en el viento y las corrientes no influyeron en la translación media de la pluma pero sí en el spread de su superficie.

---

## Conclusiones

- El evento fue visible desde el espacio y se pudo modelar de forma 2D con buena precisión.
- Las imágenes GeoColor demostraron gran utilidad para seguimiento rápido.
- Las corrientes marinas resultaron ser el forzante más relevante para este caso.
- El trabajo resalta el potencial del uso combinado de **observaciones satelitales + simulación numérica** en el litoral argentino.

---

📬 Para más información podés escribirme a [mdeoto@smn.gob.ar](mailto:mdeoto@smn.gob.ar)  
📎 Referencias y datos completos en desarrollo para publicación futura.
