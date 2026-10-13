---
layout: default
title: "Comandos que te cambian la existencia"
date: 2024-02-24 13:38:00 -0300
categories: [IA]
tags: [bash, busquedas, shell, productividad]
permalink: /2024/02/comandos-que-te-cambian-la-existencia/
---

<section class="section-block">
  <div class="section-title-wrap">
    <p class="section-kicker">escrito</p>
    <h1>{{ page.title }}</h1>
  </div>

  <article class="post-article">
    <p class="post-meta">{{ page.date | date: "%d %B %Y" }}</p>

    <p>En este blog te dejo un arsenal de técnicas para convertirte en un maestro de las búsquedas. Desde encontrar ese video perdido de YouTube hasta descargar música de Spotify, te muestro formas de apretar el teclado y salir victorioso.</p>

    <h2>Google Search</h2>

    <h3>Videos, películas y series</h3>
    <pre>intext:"Search Term" intitle:"index.of" +(wmv|mpg|avi|mp4|mkv|mov) -inurl:(jsp|pl|php|html|aspx|htm|cf|shtml)</pre>

    <h3>Imágenes</h3>
    <pre>intext:"Search Term" intitle:"index.of/" (bmp|gif|jpg|png|psd|tif|tiff) -inurl:(jsp|pl|php|html|aspx|htm|cf|shtml)</pre>

    <h3>Música</h3>
    <pre>intext:"Search Term" intitle:"index.of/" (ac3|flac|m4a|mp3|ogg|wav|wma) -inurl:(jsp|pl|php|html|aspx|htm|cf|shtml)</pre>

    <h3>Libros</h3>
    <pre>intitle:"Search Term" (pdf|epub|mob) "name or title" -inurl:(jsp|pl|php|html|aspx|htm|cf|shtml)</pre>

    <h2>Google Drive</h2>
    <pre>site:drive.google.com
site:drive.google.com +"drive/folders" + term
site:drive.google.com +"spreadsheets" + term
site:drive.google.com +"documents" + term</pre>

    <h2>BASH</h2>

    <p>Las búsquedas de archivos también conviene hacerlas con la línea de comandos.</p>

    <pre>find . -type f | perl -ne 'print $1 if m/\.([^.\/]+)$/' | sort -u
find . -type f | awk -F. '!a[$NF]++{print $NF}'
find . -type 'f' -printf '%h\n' | sort | uniq -c</pre>

    <p>La idea no es memorizarlo todo, sino construir una caja de herramientas con comandos que te ahorren timepo y te den control.</p>
  </article>
</section>
