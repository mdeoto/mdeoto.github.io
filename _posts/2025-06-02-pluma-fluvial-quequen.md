---
layout: post
title: "Pluma fluvial del Quequén-Salado: un caso visible desde el espacio"
date: 2025-06-02 18:00:00 -0300
categories: [oceanografía, modelado]
tags: [pluma fluvial, Quequén-Salado, OpenDrift, GOES-16, Sentinel-2]
image: /assets/img/pluma-quequen-2025/figs/pluma_quequen_sentinel2.png
disqus_comments: true
---

<style>
/* Evita desbordes y centra contenido visual EN ESTE POST */
.post-content img, .post-content video { max-width: 100%; height: auto; }
.centered { display: block; margin: 0 auto; }
</style>

En marzo de 2025, una serie de lluvias excepcionales afectaron al sudoeste de la Provincia de Buenos Aires. Como consecuencia, varios ríos y arroyos desbordaron, entre ellos el **río Quequén-Salado**, que presentó una **pluma fluvial superficial (PFS)** claramente visible desde el espacio.

Durante este evento, trabajamos junto a mi colega Diana Rodríguez en la detección y modelado numérico de dicha pluma utilizando imágenes satelitales y simulaciones con **OpenDrift**, un modelo lagrangiano de código abierto.

## ¿Qué es una pluma fluvial?

Es una masa de agua dulce y sedimentos que se extiende desde la desembocadura de un río hacia el mar. Dependiendo de las condiciones ambientales (viento, mareas, corrientes), esta pluma puede cambiar su forma, dirección y extensión rápidamente.

---

## Observaciones satelitales

Utilizamos dos sensores clave:

- **GOES-16 / ABI (GeoColor)**: con imágenes cada 10 minutos, ideal para seguir procesos costeros rápidos.
- **Sentinel-2 / MSI**: con mayor resolución espacial, para validar visualmente los bordes de la pluma.

<div class="text-center my-3">
  <img src="{{ '/assets/img/pluma-quequen-2025/figs/pluma_quequen_sentinel2.png' | relative_url }}"
       alt="Pluma del Quequén-Salado vista por Sentinel-2"
       class="centered" style="max-width:900px;" loading="lazy">
  <div class="small text-muted">Figura. Pluma observada por Sentinel-2/MSI.</div>
</div>

Las imágenes nos permitieron **delimitar manualmente** el área ocupada por la pluma durante varias horas del 13 de marzo. Estas delimitaciones se usaron luego para validar las simulaciones.

---

## Simulaciones con OpenDrift

Realizamos **35 simulaciones** de la pluma usando OpenDrift. Introdujimos una **fuente artificial de descarga fluvial** en la desembocadura del río, y forzamos el modelo con:

- **Corrientes barotrópicas** del modelo SIMMAR-PCA (resultado del Proyecto PRONOMAR).
- **Viento de 10 m** del modelo WRF-SMN.

Exploramos distintos escenarios para evaluar la sensibilidad al forzante y cambiamos **parámetros clave** de la dispersión 2D (coeficiente de turbulencia horizontal y errores aleatorios del viento y las corrientes).

---

## Animaciones

### Seguimiento satelital y poligonización (GOES-16 / ABI)
Durante el período visible del **13 de marzo de 2025**, el producto **GeoColor** de GOES-16 permitió un **seguimiento continuo** de la pluma cada 10 minutos. En la animación se muestra la **poligonización de la observación** (en **rojo**), que usamos para cuantificar extensión y forma de la PFS y luego **validar** las simulaciones.

<div class="text-center my-3">
  <img src="{{ '/assets/img/pluma-quequen-2025/video/ABI_GOES16_20250313.gif' | relative_url }}"
       alt="Seguimiento satelital de la pluma con poligonización en rojo (GOES-16)"
       class="centered" style="max-width:900px;" loading="lazy">
  <div class="small text-muted">Animación 1. GeoColor/GOES-16 (10 min) con poligonización observada (rojo).</div>
</div>

### Pluma artificial modelada (OpenDrift)
Simulación **2D** con **OpenDrift** inicializada en la desembocadura, forzada con **viento WRF-SMN** y **corrientes SIMMAR-PCA**. El **sombreado** representa la **concentración de partículas**; el **polígono característico** reconstruido con **AlphaShape** aparece en **azul** y el **polígono de observación ABI** en **rojo**, para la comparación cualitativa y cuantitativa.

<div class="text-center my-3">
  <img src="{{ '/assets/img/pluma-quequen-2025/video/pluma_1_B.gif' | relative_url }}"
       alt="Pluma modelada: sombreado de concentración, AlphaShape (azul) y polígono ABI (rojo)"
       class="centered" style="max-width:900px;" loading="lazy">
  <div class="small text-muted">Animación 2. Pluma modelada (OpenDrift): sombreado de concentración; AlphaShape (azul) y observación ABI (rojo).</div>
</div>

---

## Validación de resultados

Medimos la **coincidencia espacial** entre la pluma simulada y la observada usando dos indicadores:

- **POD (Probability of Detection)**
- **FAR (False Alarm Ratio)**

<div class="text-center my-3">
  <img src="{{ '/assets/img/pluma-quequen-2025/figs/poligono_comparacion.png' | relative_url }}"
       alt="Comparación GOES-16 vs simulación"
       class="centered" style="max-width:900px;" loading="lazy">
  <div class="small text-muted">Figura. Contornos: GOES-16 (rojo) vs simulación (azul).</div>
</div>

El mejor resultado (**POD: 0.96**, **FAR: 0.27**) se obtuvo cuando se incluyeron las **corrientes marinas y la descarga fluvial**, destacando su importancia frente a simulaciones forzadas solo con viento o pluma sintética. Los cambios en el parámetro de turbulencia horizontal y la introducción de errores aleatorios en el viento y las corrientes no influyeron en la translación media de la pluma pero sí en el *spread* de su superficie.

---

## Conclusiones

- El evento fue visible desde el espacio y se pudo modelar de forma 2D con buena precisión.
- Las imágenes GeoColor demostraron gran utilidad para seguimiento rápido.
- Las corrientes marinas resultaron ser el forzante más relevante para este caso.
- El trabajo resalta el potencial del uso combinado de **observaciones satelitales + simulación numérica** en el litoral argentino.

---

📬 Para más información podés escribirme a [mdeoto@smn.gob.ar](mailto:mdeoto@smn.gob.ar)  

<div class="alert alert-info my-3" role="alert">
  <strong>Material:</strong>
  <a href="{{ '/assets/pdf/pluma_fluvial_2025_ctid.pdf' | relative_url }}" target="_blank" rel="noopener">PDF del trabajo completo</a> ·
  <a href="https://github.com/mdeoto/pluma-quequen-2025" target="_blank" rel="noopener">Repositorio con código y datos</a> (próximamente)
</div>
