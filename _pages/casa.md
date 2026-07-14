---
layout: page
title: La casa del tío Gustavo
permalink: /casa/
nav: true
nav_order: 5
---

# La casa del tío Gustavo

Esta es la bitácora de un proceso de restauración, pero también de recuperación de una historia.

Durante años, la casa del tío Gustavo fue acumulando las marcas del tiempo y del abandono. Recuperarla significa mucho más que reparar paredes, techos o aberturas: implica observar lo que quedó, comprender cómo fue construida, conservar aquello que todavía puede contar algo y reconstruir, poco a poco, la historia de quienes la habitaron.

Pero esta historia no trata solamente de restaurar una casa. También trata de volver a habitarla.

Habitarla significa darle una nueva vida sin convertirla en algo completamente distinto. Significa hacerla nuevamente hogar, incorporarla al presente, adaptarla a nuevas necesidades y, al mismo tiempo, intentar no borrar las huellas de quienes estuvieron antes.

En esta sección voy a documentar ese proceso completo: el estado inicial de la vivienda, los trabajos de recuperación y restauración, los hallazgos, las decisiones, los errores, los aprendizajes y su transformación a lo largo del tiempo.

No se trata de devolver la casa a un supuesto estado perfecto ni de reconstruirla como si el tiempo no hubiera pasado. Se trata de rescatarla del abandono, conservar aquello que merece permanecer y darle una nueva oportunidad.

De tomarla, cuidarla y volver a hacerla parte de una vida.

Esta bitácora está organizada según la fecha de los acontecimientos narrados. Algunos capítulos fueron escritos retrospectivamente a partir de recuerdos, fotografías y registros conservados durante el proceso.

Esta es la historia de cómo una casa que parecía perdida volvió, poco a poco, a ser habitada.

---

## La casa

<div class="text-center my-4">
  <img src="{{ '/assets/img/casa-tio-gustavo/fachada.jpeg' | relative_url }}"
       alt="Fachada del edificio"
       class="img-fluid"
       style="max-width:900px;">
  <div class="small text-muted">
    Foto 1. La fachada. Desde la calle, nada anticipa del todo la historia que guarda el interior. Este es el frente del edificio donde comenzó la recuperación de la casa del tío Gustavo.
  </div>
</div>

<div class="text-center my-4">
  <img src="{{ '/assets/img/casa-tio-gustavo/entrada.jpeg' | relative_url }}"
       alt="Entrada al departamento"
       class="img-fluid"
       style="max-width:900px;">
  <div class="small text-muted">
    Foto 2. La entrada. La puerta que separaba el abandono de todo lo que vendría después. Cruzarla por primera vez fue el comienzo de esta historia.
  </div>
</div>

---

## Capítulos

{% assign casa_posts = site.casa | sort: "date" | reverse %}

{% for post in casa_posts %}

### [{{ post.title }}]({{ post.url | relative_url }})

{{ post.date | date: "%d/%m/%Y" }}

{% if post.description %}
{{ post.description }}
{% endif %}

---

{% endfor %}
