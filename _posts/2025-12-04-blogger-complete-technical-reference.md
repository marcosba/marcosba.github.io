---
layout: default
title: "Blogger Complete Technical Reference"
date: 2025-12-04 12:45:00 -0300
categories: [Tecnología]
tags: [blogger, api, urls, blogger-api, feeds]
permalink: /2025/12/blogger-complete-technical-reference/
---

<section class="section-block">
  <div class="section-title-wrap">
    <p class="section-kicker">escrito</p>
    <h1>{{ page.title }}</h1>
  </div>

  <article class="post-article">
    <p class="post-meta">{{ page.date | date: "%d %B %Y" }}</p>

    <p>Este documento compila una referencia completa de URLs públicas, endpoints de la API, feeds, parámetros, data-tags del template, rutas internas del dashboard y patrones no documentados de Blogger.</p>

    <h2>Overview</h2>

    <p>La idea es tener un mapa de referencia para saber cómo funciona Blogger por dentro: tanto la parte pública como la operativa y la parte técnica.</p>

    <p>Incluye convenciones de placeholder, URL pública del blog, URLs de posts, páginas, feeds Atom/RSS, URLs por año y por etiqueta, y rutas del dashboard.</p>

    <h2>Placeholders</h2>

    <pre>{blogUrl}
{customDomain}
{blogId}
{postId}
{pageId}
{year}
{month}
{label}
{query}</pre>

    <p>Estas convenciones sirven para entender rápidamente qué tipo de recurso se está consultando y para mantener consistencia al armar referencias técnicas.</p>

    <h2>URLs públicas</h2>

    <pre>https://{blogUrl}/
https://{blogUrl}/?m=1
https://{blogUrl}/search?q={query}
https://{blogUrl}/{year}/{month}/{slug}.html</pre>

    <p>La ventaja de contar con esta referencia es poder navegar rápidamente entre la estructura pública del blog y la estructura que usa la API o el template.</p>

    <h2>Feeds y API</h2>

    <p>Blogger tiene feeds de tipo Atom y RSS, así como endpoints de la API v3. Esto es útil para automatizar sincronización, extraer contenido o generar índices de archivos.</p>

    <p>Si entendés cómo se exponen las rutas internas, podés construir herramientas que interactúen con Blogger sin depender del interfaz visual.</p>

    <h2>Template y data tags</h2>

    <p>El template de Blogger usa una serie de data-tags y rutas de acceso para mostrar entradas, widgets, comentarios y contenido por fecha o categoría.</p>

    <p>La referencia sirve como guía para crear plantillas más avanzadas, automatizar contenido o comprender la estructura del sistema.</p>
  </article>
</section>
